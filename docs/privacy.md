# Myworkingmemory Apify Tools — Privacy

Updated October 26, 2026. Publisher: **Myworkingmemory LLC**. Contact: **dean@myworkingmemory.ai**.

This notice covers the Myworkingmemory Apify Tools bundle and its four Apify Actors, not the separately published Metadata Cleaner website service.

## What is processed and where

Your AI client sends selected tool arguments to Apify’s hosted MCP server. Apify authenticates your account and runs the selected Actor in your account. Tool responses return to your AI client, whose own privacy settings and policies also apply. This plugin package contains connection configuration and workflow instructions; it contains no publisher API token or separate data-collection server.

- **Shopify Store Extractor:** processes the public storefront URLs, filters and options you supply, fetches publicly available storefront content, and stores extracted products and coverage reports in your Apify run storage.
- **Document Metadata Cleaner:** receives the document input you select, processes PDF/DOCX bytes on Apify infrastructure, and stores inspection reports, hashes and any generated cleaned copy in run storage. The Actor does not send the document to an LLM or to the separate Metadata Cleaner website service; results returned to your chosen AI client are still subject to that client’s processing.
- **Email Verifier:** processes submitted addresses or an authorized Apify dataset; live verification sends addresses to MillionVerifier, and DNS fallback queries domain names through the runtime’s resolver. Results are stored in Apify datasets and key-value storage. Pilot quota enforcement uses account-related usage information. Enter supplier credentials only through the supported secret-input flow, never in a public issue or chat prompt.
- **Software Library Search:** processes query/filter/pagination inputs and returns records from a curated public catalog, including source links and review dates.

## Account access, retention and control

Apify handles the OAuth account connection and platform billing. Review the authorization screen before granting access; an Actor list in a URL is not a restriction on all permissions granted to the MCP server. Revoke a connection through your AI client and Apify account controls when no longer wanted.

Inputs, outputs, logs and storage are governed by the Actor’s behavior and your Apify retention/access settings; the plugin does not promise immediate deletion or zero retention. In particular, the document Actor does not automatically delete uploaded files and generated storage. Delete unnecessary run inputs, datasets and key-value records in Apify, and avoid making private storage public. Deleting Apify storage does not delete copies already returned to your AI client or exported elsewhere.

Myworkingmemory may receive account-related usage, run/error and billing information available to the Actor publisher through Apify, and information you provide when requesting support; these are used to operate, troubleshoot and support the Actors and administer usage. Send privacy/access/deletion requests to dean@myworkingmemory.ai without attaching private files or API keys. Requests concerning your AI-client history, Apify account or MillionVerifier account should also be directed to the respective provider.

GitHub issues are public. For confidential support, use the email above and initially provide only the Actor name, a description of the issue and non-sensitive diagnostic information. Do not post documents, email lists, tokens, or secret-bearing URLs.

## Related policies

- [Apify privacy policy](https://docs.apify.com/legal/privacy-policy)
- [Apify Actor terms](https://docs.apify.com/legal/actor-terms-and-conditions)
- [Current Actor documentation and support](https://apify.com/myworkingmemory)

Review the relevant providers’ policies before submitting data; only provide material you are authorized to process.
