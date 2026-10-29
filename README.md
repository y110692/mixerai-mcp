<p align="center">
  <img src="assets/logo.png" width="96" height="96" alt="Mixer AI">
</p>

<h1 align="center">Mixer AI MCP</h1>

<p align="center">
  Create and edit photos, video, music and voice with 100+ AI models — right inside ChatGPT, Claude, Claude Code, Cursor and Codex.<br>
  <a href="https://mixerai.org/en/knowledge/mcp/">Setup guide</a> · <a href="https://mixerai.org">mixerai.org</a> · <a href="#на-русском">На русском</a>
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
| Work on the canvas | `@Mixer AI build a 4-scene storyboard on my canvas and animate each scene` |

<p>
  <img src="assets/example-create-photo.webp" width="280" alt="Create a photo">
  <img src="assets/example-edit-photo.webp" width="280" alt="Edit a photo">
</p>

Models include Nano Banana, GPT Image, Seedream, Seedance, Kling, Veo, Grok Imagine and more — the assistant picks the right one or uses the one you name.

## Connect

### Claude (claude.ai and Claude Desktop)
1. Open **[Add custom connector](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=Mixer%20AI&connectorUrl=https://mcp.mixerai.org/mcp)** — the form opens prefilled.
2. Click **Add**, sign in to Mixer AI and allow access.
3. In a chat enable Mixer AI under **+ → Connectors** and ask: `@Mixer AI …`

### ChatGPT
1. In ChatGPT open **Settings → Apps & Connectors** (developer mode) and add a custom MCP server.
2. Name: `Mixer AI`, URL: `https://mcp.mixerai.org/mcp`, authentication: OAuth.
3. Sign in to Mixer AI and ask in a chat: `@Mixer AI …`

### Claude Code
```bash
claude mcp add --transport http mixer-ai https://mcp.mixerai.org/mcp
```
Then run `/mcp` inside Claude Code, choose **mixer-ai** and sign in.

### Cursor
**[Install in Cursor](https://cursor.com/install-mcp?name=mixer-ai&config=eyJ0eXBlIjoiaHR0cCIsInVybCI6Imh0dHBzOi8vbWNwLm1peGVyYWkub3JnL21jcCJ9)** — or add to `~/.cursor/mcp.json`:
```json
{ "mcpServers": { "mixer-ai": { "url": "https://mcp.mixerai.org/mcp" } } }
```

### Codex
Add to `~/.codex/config.toml`:
```toml
[mcp_servers.mixer-ai]
url = "https://mcp.mixerai.org/mcp"
```
Then sign in: `codex mcp login mixer-ai`.

### Any other MCP client
Add a remote MCP server with URL `https://mcp.mixerai.org/mcp` (Streamable HTTP) and sign in with OAuth.

## Pricing and consent
- Connecting is free. Generations are paid in Mixer AI coins from your account.
- The assistant always shows the exact price first. Coins are spent **only after you confirm** — with the button in the app window or by replying “Agreed”.
- Attach your own files: photos up to 30 MB, video and audio up to 100 MB.
- Reference files for a generation are kept for one day; files added to a canvas — 50 days.
- Disconnect an assistant anytime in your Mixer AI profile → **Connected apps**.

## Links
- Setup guide: https://mixerai.org/en/knowledge/mcp/
- Website: https://mixerai.org · Telegram bot: https://t.me/addbeer_bot
- Privacy: https://mixerai.org/privacy · Terms: https://mixerai.org/terms

---

## На русском

**Mixer AI MCP** — генерация и редактирование фото, видео, музыки и озвучки на 100+ ИИ-моделях прямо в ChatGPT, Claude, Claude Code, Cursor и Codex.

**Адрес сервера:** `https://mcp.mixerai.org/mcp` · вход через аккаунт Mixer AI, без ключей.

- **Claude:** откройте [окно добавления коннектора](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=Mixer%20AI&connectorUrl=https://mcp.mixerai.org/mcp) — имя и адрес уже вписаны, нажмите «Добавить» и войдите.
- **ChatGPT:** Настройки → Приложения и коннекторы (режим разработчика) → добавить свой MCP-сервер с этим адресом, вход через OAuth.
- **Claude Code:** `claude mcp add --transport http mixer-ai https://mcp.mixerai.org/mcp`, затем `/mcp` и вход.
- **Cursor:** [установить в Cursor](https://cursor.com/install-mcp?name=mixer-ai&config=eyJ0eXBlIjoiaHR0cCIsInVybCI6Imh0dHBzOi8vbWNwLm1peGVyYWkub3JnL21jcCJ9).
- **Codex:** блок `[mcp_servers.mixer-ai]` с `url = "https://mcp.mixerai.org/mcp"` в `~/.codex/config.toml`, затем `codex mcp login mixer-ai`.

Подключение бесплатно. Ассистент сначала показывает точную цену, монеты списываются только после вашего подтверждения — кнопкой в окне или ответом «Согласен».

Подробная инструкция: https://mixerai.org/knowledge/mcp/
