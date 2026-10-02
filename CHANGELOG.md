# Changelog

## 2026-09-30

- Every MCP tool now declares whether it only reads, changes something, or can't be undone, so hosts like Muse know which calls need your confirmation.

## 2026-09-26

- **Sign in from inside Muse.** Muse can now connect Duesback on its own: it opens a short sign-in page, you confirm with your email or Google, and Muse finishes the connection. No key to copy. The connection lasts and renews itself.
- **"Save me money" just works.** You no longer need to name Duesback or ask for an audit; a plain request is enough.
- **Better at unknown charges.** Unrecognized merchant names on a statement are now identified more accurately, so gray charges are flagged instead of mistaken for subscriptions.
- **Dispute a fee.** Say you disagree and every unpaid installment goes on hold while a person reviews it.
- New home page at [duesback.com](https://duesback.com).

## 2026-09-25

- **Standard OAuth 2.1** with PKCE and dynamic client registration, for hosts that support a browser sign-in.
- **Fewer steps.** Sign-up hands you access right away, and after an audit Muse proposes one first win instead of a long list.
- **Optional autopay** after your first paid fee. Off by default; one sentence turns it off again.

## 2026-09-23

- Public demo dataset at [duesback.com/demo/transactions.json](https://duesback.com/demo/transactions.json) for trying an audit without real bank data.

## 2026-09-21

- **First release.** Bill audit for Muse: finds forgotten subscriptions, negotiable phone, internet and TV bills, refundable bank fees and unknown recurring charges in up to 12 months of transactions, each with a playbook Muse can act on.
- **Pay only for wins.** Sign up with an email, no card. A fee is created only when a win is reported with evidence, with 48 hours to object, installments above $100, and a full refund if the saving doesn't stick within 90 days.
