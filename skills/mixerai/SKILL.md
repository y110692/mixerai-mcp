---
name: mixerai
description: Use the connected Mixer AI MCP server for user-requested photo, video, music, voice, Canvas, media import, model pricing or existing results.
---

# Mixer AI MCP for Cursor

Use this skill when the user explicitly asks for Mixer AI or work in their Mixer AI account. Do not redirect unrelated requests or pretend that a tool has performed an action it has not performed.

## Connect and inspect

- Connect the installed `mixerai` remote HTTP server via the OAuth sign-in prompt. Do not ask for API keys, login passwords, or tokens in chat.
- Check `aimixer_profile` and `aimixer_catalog`. Get live parameters with `aimixer_options` before choosing a mode, size, duration or reference input. Never guess a model's availability or cost.
- The catalog determines whether image, video, music, narration or sound generation is available for this account. Work with the model names returned by the server.

## Attachments and Canvas

- A path in the Cursor workspace is not a file that the remote MCP server can open by itself. Only transfer the user's original, authorized file bytes.
- For a host-readable file, call `aimixer_media_upload_prepare`, execute its returned upload instructions locally without exposing the temporary upload credential, then check the supplied `upload_id` to obtain the owned media reference. For a very small original file, `aimixer_media_import` can accept real Base64 bytes. If direct upload cannot run, use `aimixer_media_upload_session` and its temporary browser upload page.
- General limits: photo 30 MiB, video or audio 100 MiB. The selected model may have stricter file, format or duration limits. Ordinary unattached references expire within one day; Canvas-attached media follows the 50-day Canvas policy.
- General media uploads return a reference; they do not start generation or create a Canvas node. `aimixer_canvas_import_attachment` can attach an authorized file to a node or create a media node in an owned Canvas project.
- To inspect or edit a Canvas, start with `aimixer_canvas_capabilities`, then list/read the owned project. Use `aimixer_canvas_preview` before `aimixer_canvas_apply`, preserve the current project revision and the original request ID. When MCP Apps UI is unavailable, show text results or use `aimixer_canvas_view_session` in a JavaScript-capable browser.

## Price, approve, submit and recover

1. For a price comparison without generating, use `aimixer_estimate`; it does not spend coins. For actual generation, import the required references, read `aimixer_options` again and request `aimixer_quote`.
2. Show the exact model and coin amount from that quote. For a **single** generation, obtain the user's unambiguous approval through a supported UI button, the authenticated approval page or an explicit answer such as "I agree" / «Согласен» to that exact-price question. A bare "yes" / «да» or an assistant-inferred acknowledgement is insufficient. If consent was given in text, pass the literal human reply as `aimixer_submit.user_consent_text`.
3. Use `aimixer_submit` only with the same signed quote, original `approval_handle` and stable `idempotency_key`. OAuth login alone is not permission to spend. Batch and Canvas execution require their own separate authenticated approval flow; do not apply the single-generation text rule to them.
4. Check `aimixer_status`, then `aimixer_result` for the real output. Use `aimixer_history_search` to recover an older request. If a submission times out, recover its existing ID instead of submitting a new paid job.

For disconnects, missing scopes or a failed OAuth callback, use `aimixer_connection_help` and reconnect the `mixerai` server from Cursor. If an attached file did not transfer, use the authorized upload route instead of inventing a URL. Do not expose signed links, OAuth tokens or temporary upload credentials in messages or documents.
