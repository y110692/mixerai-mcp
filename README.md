<p align="center">
  <img src="assets/logo.png" width="96" height="96" alt="Mixer AI">
</p>

<h1 align="center">Mixer AI MCP</h1>

<p align="center">
  Create and edit photos, video, music and voice with 100+ AI models — right inside ChatGPT, Claude, Claude Code, Cursor and Codex.<br>
  <a href="https://mixerai.org/en/knowledge/connect-mcp/">Setup guide</a> · <a href="https://mixerai.org">mixerai.org</a> · <a href="#на-русском">На русском</a>
</p>

---

**Server URL:** `https://mcp.mixerai.org/mcp`
**Transport:** Streamable HTTP · **Auth:** OAuth 2.1 with PKCE (sign in with your Mixer AI account — no API keys)

## What you can do

| Task | Example prompt |
|---|---|
| Create a photo | `@Mixer AI award winning portrait photograph of a bizarro fashionista sphere cyborg, pastel yellow clothing, bright yellow background, minimalism` |
| Edit a photo | `@Mixer AI remove the helmet and change her hair to light brown` (attach the photo) |
| Create a video | `@Mixer AI a showdown on the dusty main street of an Old West town, slow push-in, 4 seconds` |
| Edit a video | `@Mixer AI replace the office with a space station, keep the motion and the hero` (attach the video) |
| Make music | `@Mixer AI create a 20-second instrumental for a travel reel` |
| Voice over | `@Mixer AI narrate this short script in a calm voice` |
| Work on the canvas | `@Mixer AI build a 4-scene storyboard on my canvas and animate each scene` |

<p>
  <img src="assets/example-create-photo.webp" width="280" alt="Create a photo">
  <img src="assets/example-edit-photo.webp" width="280" alt="Edit a photo">
</p>

Models include Nano Banana, GPT Image, Seedream, Seedance, Kling, Veo, Grok Imagine and more — the assistant picks the right one or uses the one you name.

## Connect

### Claude (claude.ai and Claude Desktop)
1. Open **[Add custom connector](https://claude.ai/customize/connectors?modal=add-custom-connector)**, then enter the connector name **Mixer AI** and URL `https://mcp.mixerai.org/mcp`. Do not rely on the link to prefill the form.
2. Click **Add**, sign in to Mixer AI through OAuth and allow access.
3. Enable Mixer AI in your Claude conversation and ask for a supported task. If a file upload from Claude's code execution gets HTTP 403, check **Settings → Capabilities → Code execution and file creation → Allow network egress**, or use the browser upload page.

### ChatGPT
1. Open **[chatgpt.com/plugins](https://chatgpt.com/plugins)**, click **+ → Add custom MCP server** (available on eligible plans).
2. Name: `Mixer AI`, URL: `https://mcp.mixerai.org/mcp`, authentication: OAuth → **Create**.
3. Sign in to Mixer AI and ask in a chat: `@Mixer AI …`

### Claude Code
```bash
claude mcp add --transport http --scope user mixerai https://mcp.mixerai.org/mcp
claude mcp login mixerai
```
Then verify the **mixerai** connection using `/mcp` inside Claude Code.

### Cursor
**[Install in Cursor](https://cursor.com/install-mcp?name=mixerai&config=eyJ0eXBlIjoiaHR0cCIsInVybCI6Imh0dHBzOi8vbWNwLm1peGVyYWkub3JnL21jcCJ9)** — or add to `~/.cursor/mcp.json`:
```json
{ "mcpServers": { "mixerai": { "type": "http", "url": "https://mcp.mixerai.org/mcp" } } }
```

The repository also includes a **Cursor Marketplace plugin package** with
`.cursor-plugin/plugin.json`, root `mcp.json`, and a compact
`skills/mixerai/SKILL.md`. The plugin connects to the same remote OAuth server;
no bundled binaries, API keys or local generation services are needed.
Cursor discovers this native plugin format and its relative logo at
`assets/logo.png`. The Marketplace submission requires a separate owner action
at [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish).
The `LICENSE` file proposes MIT for the public integration files; the rights
holder must approve the license and copyright notice before distribution.
The Mixer AI brand name and logo are not licensed as trademarks by MIT.

### Codex
```bash
codex mcp add mixerai --url https://mcp.mixerai.org/mcp
codex mcp login mixerai
```

### VS Code
Add a remote MCP server to `.vscode/mcp.json`, then authorize it through your VS Code MCP panel:
```json
{ "servers": { "mixerai": { "type": "http", "url": "https://mcp.mixerai.org/mcp" } } }
```

### Any other MCP client
Add a remote MCP server under the alias `mixerai` with URL `https://mcp.mixerai.org/mcp` (Streamable HTTP) and sign in with OAuth. If your client does not support MCP Apps, tools work in text mode and can return links to open in your browser.

## Using the tools
- Check the connection with `aimixer_profile` and find live image, video or audio models with `aimixer_catalog` and `aimixer_options`.
- Price without charge via `aimixer_estimate`; then use `aimixer_quote` → your explicit approval → `aimixer_submit` → `aimixer_status` → `aimixer_result`. Recover older work through `aimixer_history_search`.
- For an attachment, send its **actual file bytes** using supported ChatGPT `fileParams`, `aimixer_chatgpt_upload`, or `aimixer_media_upload_prepare`. Otherwise use the MCP App file picker or the temporary web page from `aimixer_media_upload_session`. An attached chat image alone is not a remote file. Ordinary uploads return a reference you then attach to Canvas; `aimixer_canvas_import_attachment` can directly attach to an existing node or create a media node. Neither operation starts paid generation.
- For Canvas use `aimixer_canvas_capabilities`, `aimixer_canvas_read`, `aimixer_canvas_preview` / `aimixer_canvas_apply`. Open an interactive Canvas only in clients supporting MCP Apps (`aimixer_canvas_open`); other clients can use `aimixer_canvas_view_session` in a JavaScript-capable browser. Price and approve Canvas execution separately.

The authoritative **tool names and input schemas** are in [`lhm.plugin.json`](lhm.plugin.json). The MCP server shows only tools allowed for the connected account and host; optional UI tools may be absent.

## Pricing and consent
- Connecting is free. Generations are paid in Mixer AI coins from your account.
- The assistant must show the exact model and coin price first. For a **single generation**, approve through the MCP App button, the authenticated website, or a literal unambiguous answer such as **“I agree”** / **«Согласен»** to that price question. A bare "yes", generic chat acknowledgement or OAuth login is not payment consent. For batch and Canvas execution follow the separate App/website confirmation.
- Attach your own files: photos up to **30 MiB**, video and audio up to **100 MiB**, subject to each model's format and duration restrictions.
- Reference files for a generation are kept for one day; files added to a canvas — 50 days.
- If an OAuth login returns to the wrong application, reconnect using the **mixerai** entry and complete sign-in from that client. If tools are stale in ChatGPT after a server release, select **Refresh tools / «Обновить инструменты»**. For an untransferred file, use the upload window or browser page.
- Disconnect an assistant anytime in your Mixer AI profile → **Connected apps**.

## Links
- Setup guide: https://mixerai.org/en/knowledge/connect-mcp/
- Website: https://mixerai.org · Telegram bot: https://t.me/addbeer_bot
- Privacy: https://mixerai.org/privacy · Terms: https://mixerai.org/terms

---

## На русском

**Mixer AI MCP** — генерация и редактирование фото, видео, музыки и озвучки на 100+ ИИ-моделях прямо в ChatGPT, Claude, Claude Code, Cursor и Codex.

**Адрес сервера:** `https://mcp.mixerai.org/mcp` · вход через аккаунт Mixer AI, без ключей.

- **Claude:** откройте [окно добавления коннектора](https://claude.ai/customize/connectors?modal=add-custom-connector), укажите имя **Mixer AI** и адрес сервера, затем войдите через OAuth. Автозаполнение полей по ссылке не гарантировано. При блокировке загрузки проверьте Settings → Capabilities → Allow network egress.
- **ChatGPT:** [chatgpt.com/plugins](https://chatgpt.com/plugins) → «+» → добавить свой MCP-сервер с этим адресом, вход через OAuth.
- **Claude Code:** `claude mcp add --transport http --scope user mixerai https://mcp.mixerai.org/mcp`, затем `claude mcp login mixerai` и проверка `/mcp`.
- **Cursor:** [установить в Cursor](https://cursor.com/install-mcp?name=mixerai&config=eyJ0eXBlIjoiaHR0cCIsInVybCI6Imh0dHBzOi8vbWNwLm1peGVyYWkub3JnL21jcCJ9).
- **Codex:** `codex mcp add mixerai --url https://mcp.mixerai.org/mcp`, затем `codex mcp login mixerai`.
- **VS Code:** `.vscode/mcp.json`: `{"servers":{"mixerai":{"type":"http","url":"https://mcp.mixerai.org/mcp"}}}`, затем вход через OAuth.

Подключение бесплатно. Инструменты работают и в текстовом режиме, если клиент не поддерживает MCP Apps. Доступны фото, видео, музыка, озвучка, канвас и передача вложений, когда это разрешено каталогом моделей и возможностями клиента. Вложения нужно передавать реальными байтами (либо через окно загрузки), они не становятся доступными MCP автоматически. Фото до **30 МиБ**, видео/аудио до **100 МиБ**. Обычные референсы хранятся до **одного дня**, прикреплённые к канвасу медиа до **50 дней**.

Для одиночной платной генерации ассистент сначала показывает модель и точную цену. Монеты списываются только после подтверждения кнопкой в окне, на сайте или **буквальным** ответом «Согласен» на вопрос о конкретной цене. Просто «да» недостаточно. Для пакетов и запуска канваса требуется отдельное подтверждение в приложении или на сайте. При ошибке входа переподключите `mixerai` в исходном клиенте; после релиза новых инструментов в ChatGPT нажмите «Обновить инструменты».

Подробная инструкция: https://mixerai.org/knowledge/connect-mcp/
