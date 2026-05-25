# Yuki Bot — Setup Guide 🌸

## Files in this project
```
yuki-bot/
├── bot.py           ← main bot code
├── requirements.txt ← Python dependencies
├── Procfile         ← tells Railway how to run the bot
└── memory.json      ← auto-created when bot first runs
```

---

## Step 1 — Create your Discord Bot

1. Go to https://discord.com/developers/applications
2. Click **New Application** → name it (e.g. "Yuki")
3. Go to **Bot** tab → click **Add Bot**
4. Under **Privileged Gateway Intents**, enable:
   - ✅ Message Content Intent
5. Click **Reset Token** → copy the token (you'll need it soon)
6. Go to **OAuth2 → URL Generator**:
   - Scopes: ✅ `bot`
   - Bot Permissions: ✅ `Send Messages`, `Read Message History`, `Read Messages/View Channels`
7. Copy the generated URL → open it in browser → invite Yuki to a server

---

## Step 2 — Get your Groq API Key

1. Go to https://console.groq.com
2. Sign up / log in
3. Click **API Keys** → **Create API Key** → copy it

---

## Step 3 — Deploy to Railway

1. Go to https://railway.app → log in with GitHub
2. Click **New Project → Deploy from GitHub repo**
   - Push this folder to a GitHub repo first (or use Railway's drag & drop)
3. Once deployed, click your project → go to **Variables** tab
4. Add these two environment variables:

```
DISCORD_TOKEN     =  (paste your Discord bot token here)
GROQ_API_KEY      =  (paste your Groq API key here)
```

5. Railway will auto-deploy. Check the **Logs** tab — you should see:
   ```
   Yuki is online as Yuki#1234
   ```

---

## How the bot works

- **DMs**: Yuki responds to any DM sent directly to her
- **Servers**: Yuki only responds when @mentioned
- **Memory**: stored in `memory.json` — relationship depth increases every 10 messages
- **Depth system**:
  - 0–3 messages → tsundere (cold, dismissive)
  - 4–7 messages → softening up
  - 8+ messages → yandere mode (obsessive, possessive)

---

## Customising Yuki

Open `bot.py` and find the `SYSTEM_PROMPT` section to change:
- Her name, age, backstory
- Japanese phrases she uses
- How quickly she shifts personality (change `% 10` to a smaller number for faster depth growth)

---

## Pushing to GitHub (if you haven't before)

```bash
git init
git add .
git commit -m "yuki bot"
git branch -M main
git remote add origin https://github.com/YOURUSERNAME/yuki-bot.git
git push -u origin main
```
