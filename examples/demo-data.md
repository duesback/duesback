# Demo data

Try an audit without connecting a real bank. Duesback publishes a demo dataset of 12 months of made-up transactions in Plaid's shape, regenerated each day so the dates stay current:

```
curl https://duesback.com/demo/transactions.json
```

```json
{
  "note": "Demo transactions for testing Duesback. Plaid shape. Not real data.",
  "as_of": "2026-10-02",
  "transactions": [
    { "date": "2025-10-04", "amount": 11.99, "name": "PAYPAL *SPOTIFY", "merchant_name": "Spotify" },
    { "date": "2025-10-10", "amount": 9.99, "name": "XYZ SERVICES LLC", "merchant_name": null },
    { "date": "2025-10-13", "amount": 15.49, "name": "NETFLIX.COM 866-579-7172 CA", "merchant_name": "Netflix" },
    { "date": "2025-10-18", "amount": 24.99, "name": "PLANET FITNESS #1234", "merchant_name": "Planet Fitness" }
  ]
}
```

It includes the patterns an audit looks for: streaming and gym subscriptions, a telecom bill with a price increase, bank fees, and an unnamed recurring charge ("XYZ SERVICES LLC") that a person wouldn't recognize on a statement.

## With Muse

Once Duesback is connected, say:

> Audit my bills using the demo data at https://duesback.com/demo/transactions.json

Muse fetches the file and sends it to `audit_bills`. Use the demo to see findings and playbooks, and don't report outcomes on it: outcomes are for real wins, and a reported win creates a fee.
