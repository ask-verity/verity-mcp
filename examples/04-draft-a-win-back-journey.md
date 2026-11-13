# Draft a win back journey with a holdout

**Connection needed:** read and write.

## You ask

> Draft a win back journey for customers who have not ordered in 120 days. Start our reminder email in Brevo, wait a week, and add those who still have not come back to the Meta audience for the 10% discount campaign. Keep 10% as a holdout so we can see what it really adds.

## What the agent does

1. Finds or builds the segment of lapsed customers and counts it (`list_segments`, `estimate_segment`, `save_segment_draft`).
2. Checks which destinations the journey can use (`list_destinations`).
3. Saves the journey as a draft: the entry segment, the steps, the wait and the holdout (`save_journey_draft`).
4. Asks for it to go live and hands you a review link (`request_journey_change`).

## What you get back

A summary of the journey step by step, the number of customers who would enter today, and a review link.

Verity does not send the email itself. The journey decides who is in which step and when, and passes that on: it starts your automation in Brevo and adds people to a Brevo list or a Meta audience.

## Where a person steps in

At going live. A draft runs nothing. You open the review link, check the steps and the audience, and publish the journey in Verity.

## After it is live

Ask how it is doing:

> How is the win back journey performing against the holdout?

The agent reads the journey's numbers over the period (`get_journey_stats`): how many entered, how many came back, and the difference with the holdout group. These are counts, never people.

If something looks wrong, the agent can stop it right away:

> Pause the win back journey.

Pausing is the one thing an agent may do to a live journey on its own (`pause_journey`). No one new enters and nothing more is sent. Resuming goes through a person again.
