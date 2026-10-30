# Myworkingmemory Apify agent plugins

Connect customer-owned AI agents to Myworkingmemory LLC’s public, metered Apify Actors: Shopify catalog exports, ordinary PDF/DOCX metadata cleanup, and curated GitHub/Hugging Face discovery.

Each customer authenticates their own Apify account. Successful billable events use the Actor’s published Apify pricing; Apify settlement determines publisher revenue. OpenAI subscription or API charges are separate. Installing a plugin does not itself start a paid run.

## Choose a tool

| Plugin | What to use it for | Actor |
|---|---|---|
| Shopify Catalog Export | Public products, variants, prices, availability, optional published inventory | [Shopify Store Extractor](https://apify.com/myworkingmemory/shopify-store-extractor) |
| Apify Document Cleaner | Inspect and clean supported PDF/DOCX metadata | [Document Metadata Cleaner](https://apify.com/myworkingmemory/document-metadata-cleaner) |
| Curated Software Finds | Curated GitHub tools and Hugging Face models with review dates | [Software Library Search](https://apify.com/myworkingmemory/software-library-search) |
| Myworkingmemory Apify Tools | All three workflows in one installation | [Publisher](https://apify.com/myworkingmemory) |

Choose individual plugins or the bundle; installing both duplicates the tools.

## Codex CLI and desktop marketplace

```sh
codex plugin marketplace add myworkingmemory/apify-agent-plugins
```

Open the Plugins Directory in the desktop app, select **Myworkingmemory Apify Tools**, install the desired plugin and complete its Apify OAuth connection using your own account. Client availability varies; the public Git catalog is distinct from an OpenAI-approved directory listing.

The catalog lives at `.agents/plugins/marketplace.json`; each portable package lives under `plugins/`. ZIPs are attached to the repository release.

## Other companies’ ChatGPT workspaces

A workspace administrator can use **Admin → Plugins → Add → Import marketplace**, enter `https://github.com/myworkingmemory/apify-agent-plugins`, leave Path empty, and select the desired branch/tag/commit. Configure role policies after import; each member needs their own authorized service connection. GitHub-imported plugins that declare MCP servers are currently desktop-only, even for remote HTTPS servers. This is a supported customer distribution path, not automatic availability to every ChatGPT account.

## Custom MCP connection

Use the endpoint in the selected plugin’s `mcp.json`. In supported ChatGPT surfaces, use **Plugins → + → Add custom MCP server**, choose OAuth and sign into your own Apify account. This installs a connection for that user; it does not publish a directory listing.

Example endpoint for Shopify only:

```text
https://mcp.apify.com?tools=myworkingmemory/shopify-store-extractor,fetch-actor-details,call-actor&telemetry-enabled=false
```

The endpoint exposes Actor metadata and execution helpers. `call-actor` is Apify’s generic runner and is not a security boundary limiting your token to these Actors; use customer-side tool permissions and account controls where appropriate. Bundled workflow instructions select only the named company Actors.

## OpenAI Responses API

Use an `examples/*-responses-tool.json` object in the request’s `tools` array; inject the customer's OAuth access token or Apify token in the tool’s `authorization` field at runtime. Never commit it. The supplied configuration uses `require_approval: "always"`; handle returned approval requests using your application's user consent flow. A developer can implement previously authorized automation under their own tool policy.

The model can select a relevant exposed tool when the user's task calls for it. This is not a global registry: the application must include the MCP tool configuration first. OpenAI API usage and Apify Actor usage are billed separately.

## OpenAI Agents API

Use an `examples/*-agents-tool.json` object in `agent.tools`. Authenticate with the customer's `transport.authorization` value (`Bearer <token>`) injected at session creation, or a matching service-origin vault credential. Never store that value in an agent definition or public ZIP.

For environment-based plugins, `agents-api-plugins/` contains compatibility packages with `.codex-plugin/plugin.json` and `.mcp.json`; the latter reads `APIFY_TOKEN` from the customer-controlled environment. Self-hosted environments register each plugin root in `environment.capability_directories`. OpenAI-hosted environments accept one plugin ZIP through `environment.plugins` and can reuse setup through environment templates. Authentication and runtime environment setup remain the customer's responsibility.

## Reliable paid execution

1. Read `fetch-actor-details` for the chosen Actor’s current input fields and tier-specific pricing.
2. Establish the user's scope and spending ceiling before a paid run.
3. Call `call-actor` with `actor`, `input`, and `callOptions.maxTotalChargeUsd`; bound the input workload too.
4. Poll the returned run ID when needed, then retrieve the returned dataset or key-value record.
5. Report actual results and partial coverage; never count owner tests as customer revenue.

Document cleanup is not redaction or a guarantee of anonymity; inspect first and respect content-change approvals. The curated software catalog is dated and finite. Storefront data can be incomplete or inaccessible.

## Discovery and publication status

The remaining public Actors were verified through Apify MCP `tools/list` and `fetch-actor-details` on October 26, 2026. These checks did not execute paid Actor runs. New-customer OAuth installation and model-driven execution through every OpenAI surface have not been verified by those protocol checks.

This repository distributes packages; it does not claim OpenAI public-directory approval. Universal-directory publication requires a separate publisher submission, eligible endpoint/domain verification, authentication, legal URLs, review materials, approval and publication. Apify owns `mcp.apify.com`; owning these Actors does not establish ownership of that hostname. Do not substitute a publisher API token or mislabel authenticated access as anonymous.

Apify’s existing discovery tools can find public Actors in configured agents; no directory ranking, automatic tool selection, new customer usage or revenue is guaranteed.

## Official documentation

- [OpenAI plugin packages and marketplaces](https://developers.openai.com/plugins/build/plugins)
- [Workspace import and desktop-only restriction](https://developers.openai.com/codex/enterprise/plugin-management)
- [Public plugin submission](https://developers.openai.com/plugins/deploy/submission)
- [Responses API MCP](https://developers.openai.com/api/docs/guides/tools-connectors-mcp)
- [Agents API MCP](https://developers.openai.com/api/docs/guides/agents-api/tools/mcp)
- [Agents API plugin environments](https://developers.openai.com/api/docs/guides/agents-api/tools/plugins)
- [Apify MCP documentation](https://docs.apify.com/mcp)

Support: use this repository’s Issues for integration problems or the specific Actor’s Issues for execution problems; omit credentials, private documents and customer records.
