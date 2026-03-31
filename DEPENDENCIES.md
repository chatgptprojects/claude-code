# Claude Code — Dependency Reference

All direct dependencies identified from the unpacked source code, with version research.
Generated: March 31, 2026.

---

## SECURITY ALERT: axios Supply Chain Attack (March 30–31, 2026)

**Compromised versions — DO NOT INSTALL:**
- `axios@1.14.1` — RAT dropper via `plain-crypto-js@4.2.1`
- `axios@0.30.4` — same payload

**Safe versions:**
- `axios@1.14.0` — last known safe (shasum: `7c29f4cf2ea91ef05018d5aa5399bf23ed3120eb`)
- `axios@1.13.6` — version found in Claude Code's bundled source

**Source:** https://www.stepsecurity.io/blog/axios-compromised-on-npm-malicious-versions-drop-remote-access-trojan

**IOCs to check on your machine:**
```bash
# macOS
ls -la /Library/Caches/com.apple.act.mond 2>/dev/null && echo "COMPROMISED"
# Linux
ls -la /tmp/ld.py 2>/dev/null && echo "COMPROMISED"
```

---

## Direct Dependencies (npm packages)

These are packages directly imported by `src/` and `vendor/`. Version columns:
- **Source** = version embedded in unpacked source (if found)
- **npm latest** = latest on npm right now
- **Recommended** = what to put in package.json

### Core / Anthropic SDKs

| Package | Source | npm latest | Recommended | Notes |
|---------|--------|------------|-------------|-------|
| `@anthropic-ai/sdk` | 0.74.0 | 0.80.0 | `^0.74.0` | Pin to source — API may have changed between 0.74→0.80 |
| `@anthropic-ai/bedrock-sdk` | — | 0.26.4 | `^0.26.4` | Latest should be fine |
| `@anthropic-ai/vertex-sdk` | — | 0.14.4 | `^0.14.4` | Latest should be fine |
| `@anthropic-ai/foundry-sdk` | — | 0.2.3 | `^0.2.3` | Latest |
| `@anthropic-ai/mcpb` | — | 2.1.2 | `^2.1.2` | Latest |
| `@modelcontextprotocol/sdk` | — | 1.29.0 | `^1.29.0` | MCP SDK, latest |

### AWS SDKs

| Package | npm latest | Recommended | Notes |
|---------|------------|-------------|-------|
| `@aws-sdk/client-bedrock` | 3.1020.0 | `^3.1020.0` | v3 stable, latest fine |
| `@aws-sdk/client-bedrock-runtime` | 3.1020.0 | `^3.1020.0` | Must stay in sync with above |
| `@aws-sdk/credential-provider-node` | 3.972.28 | `^3.972.28` | Latest |
| `@aws-sdk/credential-providers` | 3.1020.0 | `^3.1020.0` | Latest |
| `@smithy/core` | 3.23.13 | `^3.23.13` | AWS internals, latest |
| `@smithy/node-http-handler` | 4.5.1 | `^4.5.1` | Latest |

### Azure

| Package | npm latest | Recommended | Notes |
|---------|------------|-------------|-------|
| `@azure/identity` | 4.13.1 | `^4.13.1` | Latest |

### OpenTelemetry (keep in sync!)

| Package | Source | npm latest | Recommended | Notes |
|---------|--------|------------|-------------|-------|
| `@opentelemetry/api` | 1.9.0 | 1.9.1 | `^1.9.0` | Pin to source major.minor |
| `@opentelemetry/api-logs` | — | 0.214.0 | `^0.214.0` | Must stay in sync with sdk-logs |
| `@opentelemetry/core` | 2.2.0 | 2.6.1 | `^2.2.0` | Pin to source, safe to upgrade within ^2 |
| `@opentelemetry/exporter-logs-otlp-http` | — | 0.214.0 | `^0.214.0` | Keep in sync |
| `@opentelemetry/exporter-trace-otlp-http` | — | 0.214.0 | `^0.214.0` | Keep in sync |
| `@opentelemetry/resources` | — | 2.6.1 | `^2.2.0` | Match core version range |
| `@opentelemetry/sdk-logs` | — | 0.214.0 | `^0.214.0` | Keep in sync |
| `@opentelemetry/sdk-metrics` | — | 2.6.1 | `^2.2.0` | Match core version range |
| `@opentelemetry/sdk-trace-base` | — | 2.6.1 | `^2.2.0` | Match core version range |

### CLI / Terminal

| Package | npm latest | Recommended | Notes |
|---------|------------|-------------|-------|
| `chalk` | 5.6.2 | `^5.6.2` | ESM-only (matches source). Latest fine |
| `commander` | 14.0.3 | `^14.0.3` | Latest |
| `@commander-js/extra-typings` | 14.0.0 | `^14.0.0` | Must match commander major |
| `cli-boxes` | 4.0.1 | `^4.0.1` | Latest |
| `cli-highlight` | 2.1.11 | `^2.1.11` | Latest |
| `figures` | 6.1.0 | `^6.1.0` | Latest |
| `strip-ansi` | 7.2.0 | `^7.2.0` | ESM-only. Latest |
| `wrap-ansi` | 10.0.0 | `^10.0.0` | ESM-only. Latest |
| `supports-hyperlinks` | 4.4.0 | `^4.4.0` | Latest |
| `indent-string` | 5.0.0 | `^5.0.0` | ESM-only. Latest |
| `emoji-regex` | 10.6.0 | `^10.6.0` | Latest |
| `asciichart` | 1.5.25 | `^1.5.25` | Stable |

### React (UI rendering via Ink)

| Package | Source | npm latest | Recommended | Notes |
|---------|--------|------------|-------------|-------|
| `react` | 19.2.0 | 19.2.4 | `^19.2.0` | Safe to use latest patch |
| `react-reconciler` | — | 0.33.0 | `^0.33.0` | Must match React 19 |

### HTTP / Networking

| Package | Source | npm latest | Recommended | Notes |
|---------|--------|------------|-------------|-------|
| `axios` | 1.13.6 | ~~1.14.1~~ | `1.14.0` | **PIN EXACT** — 1.14.1 is COMPROMISED. Use 1.14.0 or 1.13.6 |
| `undici` | — | 7.24.6 | `^7.24.6` | Node.js HTTP client. Latest |
| `https-proxy-agent` | — | 8.0.0 | `^8.0.0` | Latest |
| `ws` | — | 8.20.0 | `^8.20.0` | WebSocket. Latest |
| `google-auth-library` | — | 10.6.2 | `^10.6.2` | Latest |

### File System / Process

| Package | npm latest | Recommended | Notes |
|---------|------------|-------------|-------|
| `chokidar` | 5.0.0 | `^4.0.0` | **CAREFUL** — v5 is brand new, may have breaking changes. v4 safer |
| `execa` | 9.6.1 | `^7.2.0` | **CAREFUL** — source structure matches v7. v8/v9 have breaking API changes |
| `signal-exit` | 4.1.0 | `^4.1.0` | Latest |
| `tree-kill` | 1.2.2 | `^1.2.2` | Stable, hasn't changed |
| `proper-lockfile` | 4.1.2 | `^4.1.2` | Stable |
| `shell-quote` | 1.8.3 | `^1.8.3` | Latest |
| `sharp` | — | 0.34.5 | `^0.34.2` | Matches existing optionalDeps |
| `picomatch` | 4.0.4 | `^4.0.4` | Latest |
| `ignore` | 7.0.5 | `^7.0.5` | Latest |
| `p-map` | 7.0.4 | `^7.0.4` | ESM-only. Latest |
| `cacache` | 20.0.4 | `^20.0.4` | Latest |

### Data / Parsing

| Package | Source | npm latest | Recommended | Notes |
|---------|--------|------------|-------------|-------|
| `zod` | 4.0.0 | 4.3.6 | `^4.0.0` | Zod 4 is new. Pin to ^4.0.0, safe to upgrade within |
| `ajv` | — | 8.18.0 | `^8.18.0` | JSON schema. Stable |
| `yaml` | — | 2.8.3 | `^2.8.3` | Latest |
| `marked` | — | 17.0.5 | `^17.0.5` | Markdown parser. Latest |
| `turndown` | — | 7.2.2 | `^7.2.2` | HTML→Markdown. Latest |
| `plist` | — | 3.1.0 | `^3.1.0` | Apple plist parser. Stable |
| `highlight.js` | — | 11.11.1 | `^11.11.1` | Syntax highlighting. Latest |
| `xss` | — | 1.0.15 | `^1.0.15` | XSS filter. Latest |
| `qrcode` | — | 1.5.4 | `^1.5.4` | Stable |
| `fflate` | — | 0.8.2 | `^0.8.2` | Compression. Latest |
| `diff` | — | 8.0.4 | `^8.0.4` | Text diffing. Latest |

### Utility

| Package | npm latest | Recommended | Notes |
|---------|------------|-------------|-------|
| `lodash-es` | 4.17.23 | `^4.17.21` | Never changes. Stable forever |
| `semver` | 7.7.4 | `^7.7.4` | Stable |
| `lru-cache` | 11.2.7 | `^11.2.7` | Latest |
| `auto-bind` | 5.0.1 | `^5.0.1` | Stable |
| `bidi-js` | 1.0.3 | `^1.0.3` | Stable |
| `code-excerpt` | 4.0.0 | `^4.0.0` | Stable |
| `env-paths` | 4.0.0 | `^4.0.0` | ESM-only. Latest |
| `fuse.js` | 7.1.0 | `^7.1.0` | Fuzzy search. Latest |
| `get-east-asian-width` | 1.5.0 | `^1.5.0` | Latest |
| `stack-utils` | 2.0.6 | `^2.0.6` | Stable |
| `type-fest` | 5.5.0 | `^5.5.0` | Type utilities. Latest |
| `usehooks-ts` | 3.1.1 | `^3.1.1` | React hooks. Latest |
| `vscode-languageserver-protocol` | 3.17.5 | `^3.17.5` | LSP types. Stable |

### Feature Flags

| Package | npm latest | Recommended | Notes |
|---------|------------|-------------|-------|
| `@growthbook/growthbook` | 1.6.5 | `^1.6.5` | Feature flags. Latest |

---

## Packages NOT on npm (need stubs or skip)

### Anthropic-internal (`@ant/*`)
These won't install from npm. Need local stubs or feature-flag them out:
- `@ant/claude-for-chrome-mcp`
- `@ant/computer-use-input`
- `@ant/computer-use-mcp`
- `@ant/computer-use-swift`
- `@anthropic-ai/claude-agent-sdk` (not published on npm)

### Native addons (platform-specific binaries)
These are native Node.js addons compiled for the original build. Need stubs:
- `audio-capture-napi`
- `audio-capture.node`
- `image-processor-napi`
- `modifiers-napi`
- `url-handler-napi`

### Bun-specific
- `bun:bundle` — build-time feature flag system, needs shim
- `bun:ffi` — foreign function interface, needs shim/stub

---

## Packages That Need Extra Caution

| Package | Why | Recommendation |
|---------|-----|----------------|
| **axios** | Supply chain attack March 30–31 2026 | Pin exact `1.14.0` or `1.13.6`. NEVER `1.14.1` or `0.30.4` |
| **execa** | Source is v7 structure, latest is v9 with breaking changes | Use `^7.2.0` |
| **chokidar** | v5 just released, major rewrite | Use `^4.0.0` for safety |
| **@anthropic-ai/sdk** | Source built against 0.74.0, latest 0.80.0 may break | Use `^0.74.0` |
| **@opentelemetry/*** | All OTel packages must stay version-synchronized | Use versions from same release line |

---

## Dev Dependencies Needed

These are needed for TypeScript compilation but not at runtime:

| Package | Version | Notes |
|---------|---------|-------|
| `typescript` | `^5.8.0` | Latest TS 5.x |
| `@types/node` | `^22.0.0` | Node.js types (matches Node 22+) |
| `@types/react` | `^19.0.0` | React 19 types |
| `bun-types` | `^1.2.0` | For `bun:bundle`, `bun:ffi` type defs |

---

## Summary Counts

- **Direct npm dependencies:** ~79 packages
- **Anthropic-internal (no npm):** 5 packages
- **Native addons (need stubs):** 5 packages
- **Bun-specific (need shims):** 2 modules
- **Dev dependencies:** 4 packages
