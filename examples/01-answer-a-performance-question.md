# Answer a performance question

**Connection needed:** read only.

## You ask

> What was our blended ROAS last month, per channel? Use revenue excluding VAT, and tell me which channel moved most against the month before.

## What the agent does

1. Looks up how your business defines the terms, so "revenue" and "ROAS" mean what they mean in your dashboards (`get_glossary`, `get_schema`).
2. Asks the combined store and ad spend data for revenue, spend and ROAS per channel, for last month and the month before (`query_composite_dataset`).
3. Checks your own plan for the period, if you entered one, so it can say whether you are ahead or behind (`get_targets`).

## What you get back

A table per channel with spend, revenue excluding VAT and ROAS for both months, the channel that moved most, and a short explanation. In Claude the answer opens as a Verity chart that you can add to a dashboard.

The numbers below are illustrative.

| Channel | Spend | Revenue excl. VAT | ROAS | Month before |
|---|---|---|---|---|
| Paid social | €18,400 | €71,800 | 3.9 | 3.2 |
| Paid search | €22,100 | €97,200 | 4.4 | 4.5 |
| Shopping | €9,300 | €50,200 | 5.4 | 5.1 |

## Where a person steps in

Nowhere. Reading changes nothing in Verity, so a read only connection is enough.

## Why the answer can be trusted

The agent does not guess what your terms mean. It answers from the semantic layer, the same definitions behind your dashboards and reports, so the number in the chat is the number on the board slide.
