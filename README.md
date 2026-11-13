# Verity MCP

Run your marketing data platform and customer data platform from the AI assistant you already use.

[Verity](https://ask-verity.com) is an AI marketing data platform for ecommerce and B2C teams. It connects your ad platforms, store, analytics and email tools, shapes them into one set of definitions in your own BigQuery, and puts that data to work: answers, dashboards, reports, customer segments, audiences, journeys and onsite personalisation.

The Verity MCP server gives an AI agent the same platform. With 100+ tools, ChatGPT, Claude, Codex or Cursor can answer questions on your data, build dashboards and reports, build and size customer segments, draft journeys and onsite campaigns, and connect data sources. A person approves anything that reaches a customer.

This repository holds the documentation for the connector: what it can do, how to connect, how access works, the full tool reference and worked examples. The server itself is a managed service that comes with a Verity account. There is nothing to install or host.

- Product page: [ask-verity.com/mcp](https://ask-verity.com/mcp)
- Tool reference: [TOOLS.md](TOOLS.md), or with search at [ask-verity.com/docs/mcp](https://ask-verity.com/docs/mcp)
- Verity as a CDP: [ask-verity.com/cdp](https://ask-verity.com/cdp)
- Examples: [examples](examples)

## What you can do with it

Ask in plain language. The agent picks the tools, works on your real data and shows you what it did.

| Job | You ask | What happens |
|---|---|---|
| Analyse | "What was our blended ROAS last month, per channel?" | The agent answers from your semantic layer, with the same definitions your dashboards use. |
| Dashboards and reports | "Build a weekly performance dashboard for the board." | The agent creates the dashboard as your personal draft and submits it for review when you ask. |
| Segments | "How many first time buyers came from paid social this quarter?" | The agent looks up the fields, counts who matches and saves the segment as a draft. |
| Audiences | "Send this segment to Meta Ads and Google Ads." | The agent proposes the sync and hands you a review link. You switch it on in Verity. |
| Journeys | "Draft a win back journey for lapsed customers, with a holdout." | The agent builds the draft. Going live is one approval by a person. |
| Onsite | "Show returning customers a different homepage banner." | The agent sets up the campaign switched off and hands you a review link. |
| Data | "Which dashboards would break if we change this model?" | The agent checks lineage and usage before anything changes. |

Audiences sync to Meta Ads, Google Ads, Brevo, Klaviyo and ActiveCampaign. Onsite personalisation runs on Shopify and on your own site.

## Connect

You need a Verity account with MCP switched on. Verity enables MCP, and write access, per account.

1. In Verity, open **Settings**, then **MCP Connections**. Copy the server address shown there.
2. Add it to your assistant (see below).
3. Sign in with Google, pick the account and workspace, and choose **read only** or **read and write**.

There are no API keys to create or store. Sign in runs over OAuth in your browser.

### Claude (claude.ai and Claude Desktop)

Open **Settings**, then **Connectors**, and choose **Add custom connector**. Give it the name Verity, paste the server address and confirm. Claude opens the Verity sign in screen.

### ChatGPT

Open **Settings**, then **Apps and connectors**, and add a custom connector. Give it the name Verity, paste the server address and choose OAuth as the sign in method. ChatGPT opens the Verity sign in screen. Menu names in ChatGPT differ per plan; on some plans a workspace admin adds the connector for the team.

### Cursor

Add Verity to `.cursor/mcp.json` in your project, or to `~/.cursor/mcp.json` for all projects:

```json
{
  "mcpServers": {
    "verity": {
      "url": "YOUR_VERITY_SERVER_ADDRESS"
    }
  }
}
```

Replace `YOUR_VERITY_SERVER_ADDRESS` with the address from Settings, MCP Connections. Cursor opens the sign in screen the first time it connects.

### Claude Code

```bash
claude mcp add --transport http verity YOUR_VERITY_SERVER_ADDRESS
```

Then run `/mcp` inside Claude Code and choose Verity to sign in.

### Codex

Codex on your own computer connects the same way, as an MCP server over HTTP with the same address. Codex cloud tasks are not supported yet.

## How access works

An agent that can act on customer data needs clear limits. Verity has three.

**The agent acts as you, and never more.** Every tool runs as the person who connected the assistant. It sees the workspace you see and can do what your role allows. There is no separate agent account with wider rights.

**You choose read only or read and write.** You pick this on the sign in screen when you connect. A read only connection can answer questions and look things up. A read and write connection can also create and change things inside Verity, such as a draft segment or a dashboard.

**Anything with an effect outside Verity goes through a person.** Syncing an audience, publishing a journey, switching an onsite campaign on or setting a report schedule does not happen from the chat. The tool returns a review link. A person opens it, checks the change and approves it in Verity. The one exception is stopping: an agent can pause a live journey on its own, because pausing is safe.

Every tool in the [reference](TOOLS.md) carries one of three levels:

| Level | What it means |
|---|---|
| Read | Reads data or settings. Nothing in Verity changes. |
| Write | Changes something inside Verity. Needs a read and write connection. |
| You approve | Opens the change for a person in Verity and returns a review link. |

Also good to know:

- Segment and journey numbers come back as counts, never as a list of people.
- Every call is logged. Under Settings, MCP Connections you see what each connection did, and you can revoke it.
- Your data stays in your own BigQuery, in your own Google Cloud project.

## Tool reference

[TOOLS.md](TOOLS.md) lists every tool with its level, what it does and the input it needs, in six groups:

- Ask and analyse
- Segments and customer profiles
- Activation
- Dashboards and reports
- Data sources and models
- Workspace and help

The reference is generated from the server's own tool contract, so it matches what the server offers.

## Examples

Each example shows what you ask, what the agent does and where a person steps in.

1. [Answer a performance question](examples/01-answer-a-performance-question.md)
2. [Build an audience and send it to Meta Ads](examples/02-build-and-activate-an-audience.md)
3. [Build a weekly dashboard for the board](examples/03-build-a-board-dashboard.md)
4. [Draft a win back journey with a holdout](examples/04-draft-a-win-back-journey.md)
5. [Check what a data change would break](examples/05-check-what-a-data-change-breaks.md)

## Get Verity

Verity starts at €500 per month, excl. VAT, priced on the parts you use: Analytics, Data Management and Activation. Onboarding starts with a demo and a free trial on your own data.

- [Book a demo](https://ask-verity.com)
- [Pricing](https://ask-verity.com/pricing)
- Questions: info@ask-verity.com

## License

The documentation in this repository is licensed under [Creative Commons Attribution 4.0 International](LICENSE). You may copy and adapt it, as long as you credit Verity and link to [ask-verity.com](https://ask-verity.com). The license covers the text in this repository. It does not cover the Verity name and logo, or the Verity product and its MCP server.
