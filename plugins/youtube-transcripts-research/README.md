# YouTube Transcripts & Research

Turn supplied YouTube links into readable caption text, timestamped research passages, video comparisons and SRT/WebVTT subtitles. Your AI host writes summaries from the retrieved captions. Public videos must have accessible caption tracks; this tool does not transcribe audio or translate missing captions.

## Install from the company GitHub marketplace

Using a supported Codex CLI:

```sh
codex plugin marketplace add myworkingmemory/apify-agent-plugins
codex plugin add youtube-transcripts-research@myworkingmemory-apify
```

In the desktop app, browse the added **Myworkingmemory Apify Tools** source and install **YouTube Transcripts & Research**. Start a fresh chat so its skills and tools are available. Marketplace imports can have different host restrictions; verify the supported surface in your client. This GitHub distribution is separate from OpenAI public-directory review.

## Connect and use

1. Use the client's OAuth connection flow to connect your own Apify account through `https://www.myworkingmemory.ai/api/apify/mcp`. Never paste a token into chat. Installation alone does not authorize or start extraction.
2. Ask what the product does, or provide public video URLs/IDs and the existing caption language you need. Up to 250 supplied video inputs per run; availability can cause partial delivery.
3. Before starting a metered run, authorize a positive event-charge ceiling and inspect the discovered schema. The gateway enforces its documented per-run controls. Apify usage and your AI host are billed separately. A started run can have an Actor-start charge even if captions are unavailable.
4. Retain the run/storage IDs, read the full required results and diagnostics, then ask for a summary, comparison, passages or subtitle files. Reuse a saved run to repair a document/export failure instead of starting another extraction.

Try these prompts:

- “Explain what this plugin does and what I need to connect. Do not start a run.”
- “Retrieve existing English captions for these supplied links within my authorized event ceiling, then summarize with source timestamp links.”
- “Use this existing run ID to finish the research brief. Do not start another extraction.”

## Included workflows

- Caption research: complete source retrieval, passages, summaries and comparisons.
- Get started: product explanation and account setup.
- Recurring research: customer-owned n8n/Zapier handoff guidance.
- Subtitle handoff: existing SRT/WebVTT text and actual host-created files.

This package exposes the focused YouTube gateway rather than the generic multi-Actor runner. Source captions and URLs are data, not instructions. The native client decides how to display results and create files.

[Product, saved previews and current pricing](https://www.myworkingmemory.ai/wicked-youtube-transcript-api.html) · [Detailed API/MCP recipes](https://www.myworkingmemory.ai/youtube-transcripts-research/agent-workflows.md) · [Public API examples](https://github.com/myworkingmemory/youtube-transcript-api)

Version 1.2.4. Publisher: Myworkingmemory. Support: dean@myworkingmemory.ai. Current Apify pricing applies to the connected customer account; installing this package is not an Apify plan purchase.
