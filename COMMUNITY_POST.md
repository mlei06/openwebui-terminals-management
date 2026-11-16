# Terminal Management

Manage shared Open Terminal connections from chat: endpoints, enablement, access grants and connectivity checks.

## What you can do

Create/update/delete connection identity and endpoint, enable/disable, resource access and connectivity checks.

## Try asking

- “List the configured terminal connections.”
- “Test the selected terminal connection.”
- “Grant the Engineering group read access to the selected terminal connection.”

Examples describe requests to your model, not guaranteed outcomes from every model. It discovers actual resource IDs and supported fields before writing. Cross-resource requests require the corresponding individual Tools or the combined Admin Toolkit.

## Install

1. Import this listing, or paste the complete `tool.py` into **Workspace → Tools → Create Tool**.
2. Keep the Tool private and attach it to an administrator-only model preset. Enable **Native** function calling.
3. Set the `OPEN_WEBUI_URL` valve to the trusted WebUI origin reachable from its backend. The default is `http://127.0.0.1:8080` for a backend calling itself. The caller’s token is sent to this origin; HTTPS uses the runtime trust store.
4. Start a fresh chat and begin with a list or get request.

No shared admin API key, custom harness or documentation knowledge base is required. Every operation verifies the caller’s current administrator identity through the Open WebUI API. Existing resource-access checks still apply.

## Changes and confirmations

Reads and ordinary requested writes run directly. Deletions, access and membership changes, role changes, executable source/activation changes, valve updates and connection writes require an interactive browser confirmation showing the proposed change. If confirmation is unavailable or cancelled, that write does not proceed.

Updates preserve unspecified settings; attachment arrays replace the selected array. Known credential fields are redacted from results. Inspect current state after a failed write before retrying. Saving executable extensions runs server-side Python through Open WebUI; validation does not sandbox that code.

## Scope and compatibility

Manages connection configuration, not shell commands, files or container lifecycle. Use Model Management to select a preset’s default terminal. Deleting a connection does not destroy the external service or its data.

The individual management operations were exercised against Open WebUI 0.13.3; API contracts were also inspected on 0.13.0. Other releases may need compatibility changes. Python 3.11+, httpx and Pydantic 2 are required. No runtime dependency installation is requested.

The standalone repository package includes the full operation reference, synthetic tests and MIT license. Open WebUI is a separate project with its own license and branding requirements.
