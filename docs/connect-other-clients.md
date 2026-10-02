# Connect from other agents and MCP clients

Duesback is built for Meta's Muse, but the server speaks standard protocols. Any agent that holds a user's transaction data and can call an MCP server or a REST API can use it.

## Endpoints

| What | URL |
|---|---|
| MCP (Streamable HTTP) | `https://duesback.com/mcp` |
| OAuth metadata | `https://duesback.com/.well-known/oauth-authorization-server` |
| REST, OpenAPI 3 | `https://duesback.com/openapi.json` |
| Agent instructions | `https://duesback.com/llms.txt` |
| Demo transactions | `https://duesback.com/demo/transactions.json` |

## Auth

Agents should never ask the user for a key, token or password.

**Hosts with a browser callback:** OAuth 2.1 authorization code with PKCE. Dynamic client registration and client-ID metadata documents are supported. One scope: `duesback`.

**Agents without a callback** (for example a custom connector written inside an agent's sandbox): the OAuth device flow.

1. `POST /oauth/register` with `{"client_name":"<your agent>","redirect_uris":["http://localhost/callback"],"token_endpoint_auth_method":"none"}` returns a `client_id`.
2. `POST /oauth/device/authorize` with form `client_id=<client_id>&scope=duesback` returns `device_code`, `user_code` and `verification_uri_complete`.
3. Open `verification_uri_complete` for the user, or show the `user_code` and `https://duesback.com/connect`. The user signs in with email or Google.
4. Poll `POST /oauth/token` with form `grant_type=urn:ietf:params:oauth:grant-type:device_code&device_code=<device_code>&client_id=<client_id>` every 5 seconds. `authorization_pending` and `slow_down` mean keep waiting.
5. Call the MCP server with `Authorization: Bearer <access_token>`. Device-flow access tokens last 30 days. The refresh token lasts 90 days and rotates: `POST /oauth/token` with `grant_type=refresh_token`.

A key from [duesback.com/start](https://duesback.com/start) works as a bearer token, but only as a fallback if the user insists.

## REST

| Method | Path | Does |
|---|---|---|
| POST | `/v1/audit` | Audit transactions, return findings |
| GET | `/v1/findings` | Open findings, best savings first |
| GET | `/v1/findings/{finding_id}/playbook` | Provider notes for one finding |
| POST | `/v1/outcomes` | Report what happened after acting |
| POST | `/v1/outcomes/{outcome_id}/verify` | Check one outcome against fresh data |
| GET | `/v1/fees` | Fees due and their payment links |
| GET | `/v1/account` | Account status |
| POST | `/v1/disconnect` | Revoke access and delete stored data |

The MCP tools map to the same operations. See [tools.md](tools.md).
