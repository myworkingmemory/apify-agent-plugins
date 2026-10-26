# Shopify Catalog Export

Export public Shopify products, prices, SKUs, variants and availability; compare storefront snapshots. Optional published inventory, panels and recommendations cost extra. Missing inventory is unknown, not zero; report partial coverage.

MCP endpoint:

```text
https://mcp.apify.com?tools=myworkingmemory/shopify-store-extractor,fetch-actor-details,call-actor&telemetry-enabled=false
```

Authenticate using your own Apify account with OAuth; metered Actor runs are charged to your account.

Example: Export 10 public products from allbirds.com, including variants, with a $0.02 spending limit.

See the repository README for Codex, workspace and API distribution instructions. This package is not an approved OpenAI public-directory listing.
