# Build a weekly dashboard for the board

**Connection needed:** read and write.

## You ask

> Build a weekly performance dashboard for the board: revenue excluding VAT, orders, new against returning customers, ad spend and ROAS per channel, and how we are doing against this quarter's targets.

## What the agent does

1. Reads Verity's own guidance for building dashboards, so the layout follows the same rules a person would (`get_playbook`).
2. Looks up which fields the dashboard can be built on (`get_catalog`).
3. Creates an empty dashboard as your personal draft (`create_dashboard`).
4. Lays out the page from your sentence and fills each block (`compose_dashboard`, `fill_block`).
5. Sets the period filter and formats the numbers (`set_filters`, `format_block`).
6. Reads the result back and tells you what is on it (`get_dashboard`).

## What you get back

A link to the draft dashboard in Verity, with a summary of the blocks: scorecards for revenue, orders and ROAS, a table per channel, a new against returning chart and a targets block.

You can keep going in the same conversation:

> Add a table with revenue per customer segment, and move the targets block to the top.

## Where a person steps in

At publishing. The dashboard starts as your own draft. When you are happy with it, you ask the agent to submit it for review (`submit_dashboard_for_review`), and a reviewer in Verity publishes it to the team. Sending it as a scheduled report works the same way: the agent proposes the schedule (`request_schedule`) and a person confirms it in Verity.
