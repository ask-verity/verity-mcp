# Build an audience and send it to Meta Ads

**Connection needed:** read and write.

## You ask

> Find customers who came in through paid social, bought at least twice, and have not ordered in the last 90 days. Leave out anyone who only ever bought with a discount code. Get them ready for Meta Ads.

## What the agent does

1. Looks up what a segment can filter on: orders, channels, discount use, last order date (`get_segment_fields`).
2. Counts how many customers match before it saves anything (`estimate_segment`).
3. Saves the segment as a draft, with a name and a description you can read back (`save_segment_draft`).
4. Shows how this group differs from all your customers, for example in average order value (`get_segment_insights`).
5. Checks which destinations are connected (`list_destinations`).
6. Proposes the sync to Meta Ads and hands you a review link (`request_segment_change`).

## What you get back

The numbers below are illustrative.

> Lapsed paid social buyers: 4,812 customers. Compared with all customers they order 22% more per order and 61% bought in the summer sale. The segment is saved as a draft. The sync to Meta Ads is ready for your approval: [review link]

## Where a person steps in

At the sync. The agent cannot send an audience to an ad platform on its own. You open the review link, check the segment and the destination, and switch the sync on in Verity. From then on the audience refreshes on the cadence you set, and new customers who match land in the next sync.

## Good to know

- The agent sees counts and comparisons, never a list of people.
- The same steps work for Google Ads, Brevo, Klaviyo and ActiveCampaign.
- The segment is defined on the customer profiles in your own BigQuery, so the audience you sync is the customer you report on.
