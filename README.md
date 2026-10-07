# Duesback

Duesback builds AI agents that get people and small businesses back the money they're owed.

Our first product runs inside Meta's Muse assistant. It finds forgotten subscriptions, padded phone and internet bills, and refundable bank fees in the transactions a user shares. Muse makes the calls, and Duesback is paid a share of what comes back. Nothing is owed when nothing is won.

Website: [duesback.com](https://duesback.com) · Contact: hello@duesback.com

## Connect

- **Muse:** say *"Set up the Duesback connector: follow https://duesback.com/muse"*. Full guide: [docs/connect-muse.md](docs/connect-muse.md).
- **Other agents and MCP clients:** [docs/connect-other-clients.md](docs/connect-other-clients.md).

## What's in this repo

| Path | What it is |
|---|---|
| [docs/connect-muse.md](docs/connect-muse.md) | Setting up Duesback in Muse, what Muse asks before it acts, fees, stopping |
| [docs/connect-other-clients.md](docs/connect-other-clients.md) | MCP endpoint, OAuth 2.1 (code + PKCE, device flow), REST and OpenAPI |
| [docs/tools.md](docs/tools.md) | The MCP tools, when an agent should call each one, and read-only connections. Full reference: [duesback.com/tools](https://duesback.com/tools) |
| [examples/prompts.md](examples/prompts.md) | Things to say to Muse once Duesback is connected |
| [examples/demo-data.md](examples/demo-data.md) | A public demo dataset for trying an audit without real bank data |
| [llms.txt](llms.txt) | Copy of [duesback.com/llms.txt](https://duesback.com/llms.txt), the instructions agents read. The live file wins if they differ. |
| [CHANGELOG.md](CHANGELOG.md) | What changed, week by week |

## How it works

1. **Audit.** Muse sends up to 12 months of transactions. Duesback finds recurring charges, classifies them (subscription, telecom/internet/TV bill, bank fee, unknown "gray" charge) and returns findings ranked by savings.
2. **Act.** Each finding carries a playbook: cancel, call for a retention rate, or request a fee refund. Muse asks the user before every cancellation, call or payment, and quotes the exact fee before reporting a win. Users who only want the audit can connect read-only, which never creates a fee.
3. **Verify.** Muse reports the outcome with evidence. Duesback checks it against later transactions. If the saving doesn't stick within 90 days, the fee is refunded.

## Fees

Success only: 30% of the first year's saving, 25% of a refund, minimum $1. The fee exists only after a win is reported with evidence, the user has 48 hours to object, and no card is stored unless the user turns on autopay. Full rules: [duesback.com/fees](https://duesback.com/fees).

## Privacy

Duesback never sees a bank login. It keeps recurring-charge signatures only (merchant, cadence, amount, last date), never raw transactions, account numbers or cards. Disconnecting deletes them. [duesback.com/privacy](https://duesback.com/privacy).

Duesback is independent and not affiliated with Meta.
