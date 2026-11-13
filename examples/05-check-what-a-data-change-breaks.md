# Check what a data change would break

**Connection needed:** read only.

## You ask

> We want to change how we calculate net revenue, so returns are taken off in the month of the return instead of the month of the order. What would that touch?

## What the agent does

1. Finds the models behind net revenue and what feeds them (`list_data_models`, `get_data_model_lineage`).
2. Looks up everything you can open that uses them: dashboards, reports, monitors, targets and financial statements (`get_dbt_usage`).
3. Runs the same impact check that guards a change before it ships (`check_dbt_impact`).

## What you get back

The list below is illustrative.

> Changing net revenue touches 3 dashboards (Board weekly, Finance monthly, Channel performance), 1 scheduled report (Monthly management report), 2 targets for this quarter and the P&L. Nothing breaks, but every one of them will show different monthly numbers after the change. The Q4 targets were set on the old definition.

## Where a person steps in

Nowhere yet. This is a question, so nothing changes. If you then ask the agent to make the change on a read and write connection, it saves a draft of the model (`save_data_model_draft`). A draft changes nothing in your warehouse until a person publishes it in Verity.

## Why this matters

Changing a definition is easy. Knowing who relied on the old one is the hard part. Because dashboards, reports, targets and segments all run on the same definitions, Verity can tell you before the change instead of after the board meeting.
