# SEV — SEC Filing Discovery

A Claude Code plugin by ETSquare AI, LLC.

Search SEC 10-K and 10-Q filings in plain English. SEV finds public companies whose filings discuss your topic and returns the exact original passages, with links to the filings on SEC EDGAR, and available reported financial figures. Claude can then read each full passage and its surrounding text.

Useful for questions about shipping and supply-chain disruptions, tariffs and sourcing changes, or operational problems such as aircraft groundings.

SEV returns research leads. It does not analyze companies, draw investment conclusions or make recommendations. Coverage is limited: relevant companies can be missed, and an empty result does not mean no company has made that disclosure.

## What you need

- **Claude Code.** The plugin is tested in Claude Code, which asks for your API key when you set it up.
- **A SEV API key.** Sign in at https://etsquare.ai/account, accept the Terms and create a key.

## Set up

1. Install the plugin with `/plugin` in Claude Code.
2. When Claude Code asks for **SEV API key**, paste your key. Claude Code keeps it in secure storage, not in your settings files.
3. Run `/mcp` to confirm the `sev` server is connected.

## Tools

Both tools are read-only.

- `discover_sec_companies` finds relevant companies and one to three original passages per company. When available, it also returns reported financial figures, each labeled with its own reporting period and source filing. Check each figure's period; figures do not show what caused a change. Optional filters: explicit tickers or four-digit SIC codes (not both), an inclusive filing-date cutoff (`filed_since`) and `max_companies` (default 10, maximum 50).
- `get_sec_passage` reads the full original passage and available adjacent context, using a `passage_id` returned by discovery.

## Example questions

- Which companies said disruptions to shipping through the Red Sea or Strait of Hormuz increased their freight costs or delayed deliveries of goods?
- Which retailers said tariffs on imported apparel or footwear raised their merchandise costs or made them shift sourcing to other countries?
- Which airlines or aircraft operators said engine problems or spare-parts shortages grounded aircraft and reduced the capacity they could fly?

## What the plugin connects to and sends

- The plugin runs nothing on your computer. Claude Code connects to SEV's hosted MCP server at https://etsquare.ai/mcp over HTTPS.
- When Claude calls a tool, Claude Code sends that tool's arguments (your research question and any filters, or a passage ID) to that server, with your API key in the `Authorization` header.
- The plugin does not read your files or your conversation beyond those tool arguments. Claude Code stores your settings and API key.
- How SEV handles this data is described in the Privacy Policy: https://etsquare.ai/privacy

## Usage and limits

A successful search, including a valid empty result, uses one search from your SEV account allowance, which is shared with the SEV website and API. Searches that fail on SEV's side, and passage reads, do not use it. Run one search at a time per account; a second search sent while one is running may be refused as busy. SEV never retries a search automatically. If a search times out on your side, it can still finish on SEV's side, and then it counts as used.

## Security and support

- Revoke a key at any time from https://etsquare.ai/account.
- Support: https://etsquare.ai/support
- Security reports: email vtaya@etsquare.ai with "Security" in the subject. Never include API keys.
- Documentation: https://etsquare.ai/documentation
- Terms: https://etsquare.ai/terms

## License

MIT. This repository holds the plugin manifest. The server is SEV's hosted MCP endpoint at https://etsquare.ai/mcp.
