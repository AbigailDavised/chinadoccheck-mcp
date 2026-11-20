---
name: chinadoccheck
description: "Verify China Z-Visa Hague Apostille vs consular legalization requirements across 16 countries, route U.S. Federal USDOS Form DS-4194 vs 10-state SOS jurisdictions, compute 180-day police check expiry windows, and audit SAFEA translation seals via ChinaDocCheck's stateless MCP server."
homepage: https://chinadoccheck.com
version: 1.0.0
license: MIT
compatibility: "Works with Hermes Agent, Claude Code, Cursor, Windsurf, and any MCP client supporting Streamable HTTP."
metadata:
  homepage: "https://chinadoccheck.com"
  mcp_endpoint: "https://chinadoccheck.com/api/mcp"
  version: "1.0.0"
  hermes:
    category: travel
    tags: [china-visa, hague-apostille, fbi-background-check, usdos-authentication, safea-work-permit]
---

# ChinaDocCheck — Stateless China Visa Apostille & Legalization MCP Skill

Connect any MCP-compatible AI agent to ChinaDocCheck's public read-only Streamable HTTP server at `https://chinadoccheck.com/api/mcp`. Zero sign-in or API keys required.

## Endpoint Configuration

```json
{
  "mcpServers": {
    "chinadoccheck": {
      "type": "streamable-http",
      "url": "https://chinadoccheck.com/api/mcp"
    }
  }
}
```

## Direct JSON-RPC 2.0 Verification

```bash
curl -s -X POST https://chinadoccheck.com/api/mcp \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"route_country_apostille_and_legalization_authority","arguments":{"countryQuery":"US","documentTypeId":"fbi-background-check"}}}'
```

## Tools Inventory (8 Read-Only Tools)

- `route_country_apostille_and_legalization_authority`: Match issuing country and document category across 16 jurisdictions to identify Apostille vs Consular channels, statutory fees, and SAFEA compliance rules.
- `calculate_180day_document_validity_radar`: Compute remaining calendar validity on a 180-day police clearance after subtracting courier transit and SAFEA review buffers.
- `check_us_federal_vs_state_apostille_jurisdiction`: Disambiguate USDOS Federal Form DS-4194 authentication vs 10 State Secretaries of State including Remote Online Notarization (RON) risk levels.
- `inspect_country_deep_legalization_dossier`: Retrieve stage-by-stage police clearance timelines, fingerprint rules, and Tier-1 vs Tier-2 municipal enforcement nuances.
- `audit_safea_translation_and_remote_notary_compliance`: Check Chinese dual-seal requirements (翻译专用章 + stamped Business License copy) and city-level e-Apostille/RON acceptance.
- `diagnose_zvisa_document_rejection_risks`: Screen for common RFE traps such as sending FBI reports to State SOS, unsealing Japanese Keishicho envelopes, or domestic-purpose Korean checks.
- `retrieve_multilingual_police_clearance_guide`: Return complete native-script police check and Apostille instructions in `ja`, `ko`, `de`, `fr`, `ru`, or `es`.
- `generate_printable_visa_dossier_checklist`: Assemble an ordered Z-Visa, ESL teacher, dependent, or corporate POA document authentication checklist by home country.
