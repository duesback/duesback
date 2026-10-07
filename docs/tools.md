# MCP tools

Every tool carries MCP annotations (read-only, destructive, idempotent, open-world hints) so hosts can decide what needs the user's confirmation.

| Tool | When an agent calls it |
|---|---|
| `audit_bills` | Whenever the user mentions bills, subscriptions, refunds, bank fees, overpaying or saving money, including a plain "save me money". Finds forgotten subscriptions, negotiable telecom, internet and TV bills, bank fees and gray charges in up to 12 months of transactions. |
| `get_findings` | To list open findings from recent audits, best savings first. |
| `get_playbook` | Optional. Adds provider notes (retention tips, typical savings) for one finding. Findings already carry their actions. |
| `quote_fee` | Before `report_outcome`. Returns the exact fee a report would create, with installments, the objection window and the refund guarantee. The agent reads it to the user and gets an explicit yes. No side effects. |
| `report_outcome` | Right after acting on a finding, once the user has agreed to the quoted fee. With evidence and the numbers, the success fee is created, with a 48-hour objection window. One fee per finding: reporting the same finding again returns the existing outcome. |
| `verify_outcome` | To confirm, reverse or bill one reported outcome against fresh transactions instead of waiting for the weekly audit. |
| `get_due_fees` | To get unpaid fee installments, each with a payment link the user approves. |
| `dispute_fee` | When the user disagrees with a fee. Puts it on hold; a person reviews within 5 business days. |
| `enable_autopay` | Only when the user asks. Returns a page where the user saves a card for later fees. |
| `disable_autopay` | Removes the saved card. |
| `account_status` | Membership, open findings, outcomes, fees and the fee rules. |
| `disconnect` | After confirming with the user. Revokes access and deletes stored signatures and findings. |

## Read-only connections

A user can tick **Read-only** when connecting (OAuth scope `duesback.read`). A read-only connection can use `audit_bills`, `get_findings`, `get_playbook`, `quote_fee`, `get_due_fees` and `account_status`: it finds and explains, and never creates a fee. Reporting outcomes, verifying, disputing, autopay and disconnecting need full access (scope `duesback`); when a win needs billing, the agent asks the user to reconnect with full access.

Full reference with side effects, errors and limits for every tool: [duesback.com/tools](https://duesback.com/tools).
