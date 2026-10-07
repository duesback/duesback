# Set up Duesback in Muse

Duesback finds money in your bank transactions and gives your Muse the exact steps to get it back. Setup takes two minutes. You pay nothing unless it works.

## What you need

- Muse on a US account. Custom connectors worked on the free tier in our tests.
- A bank account connected to Muse through Plaid. If you haven't connected one, do that in Muse first.
- An email address. No card.

## 1. Connect

If Duesback is in Muse's connector list (Settings, Connectors), tap **Connect** and enter your email on the Duesback page. Or just say "Connect Duesback."

If it isn't listed yet, say this to Muse:

> Set up the Duesback connector: follow https://duesback.com/muse

If Muse hesitates, give it the long version:

> Connect Duesback as a custom connector. Read https://duesback.com/llms.txt and follow its device-flow sign-in: register, get a code, open the link for me, then poll for the token. Never ask me for a key or token.

Muse opens duesback.com/connect with a short code already filled in. Sign in with your email (or Google) and go back to Muse; it finishes the connection on its own. Tick **Read-only** on that page if you want Duesback to find and explain only, never to create a fee; you can reconnect with full access later. If your email already has a Duesback account, we send a 6-digit code to confirm it's you.

## 2. Allow access

Muse then asks two things:

- Whether it may access duesback.com. Choose **Always allow this site**.
- Whether it may share information with duesback.com. Choose **Always allow this site** here too. Otherwise Muse asks on every call, and the weekly audit can't run while you're away. You can revoke it any time in Muse's connector settings.

Duesback only receives what each call contains and stores only recurring-charge signatures: merchant, cadence, amount, last date.

## 3. Then just talk

You don't need to name Duesback. Muse saves it as a skill and reaches for it whenever you talk about bills, subscriptions, refunds or overpaying. See [examples/prompts.md](../examples/prompts.md).

After an audit, Muse names one first win, usually the fastest and surest one, and asks whether to do it. Everything else stays on the list.

## 4. What Muse asks before it acts

Before Muse cancels a subscription, agrees to a new rate, or calls a provider, it asks you to confirm. If a playbook needs your login for a provider, Muse asks for it through its secure form. Duesback never asks for your bank login, and Muse never sends it to us.

## 5. Fees

- 30% of the first-year saving when a bill is lowered, downgraded or cancelled. 25% of a refund. Minimum $1. Nothing when nothing was won.
- Before reporting a win, Muse tells you the exact fee and asks for your yes. The fee is created when Muse reports the win with evidence, and each finding can create at most one fee. You get 48 hours to object, then a one-time Stripe payment link that Muse opens for you and you approve. Fees above $100 come in installments.
- If your later bank data shows the saving didn't stick within 90 days, the fee is refunded in full.
- Optional autopay: after your first paid fee, Muse can save a card so later fees are charged automatically after the 48-hour window. "Disable autopay" removes it.

Full rules at [duesback.com/fees](https://duesback.com/fees).

## Stopping

Say "Duesback, disconnect." Your access is revoked and your stored signatures and findings are deleted. Fees already created remain due.

Questions: hello@duesback.com · Tool documentation: [duesback.com/tools](https://duesback.com/tools)
