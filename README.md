# LOL BOSS AI — Telegram Funny Group Bot

A Bengali/Banglish Telegram bot for friendly group banter, jokes, truth/dare, daily challenges, XP, profiles, and a leaderboard.

## Files
- `main.py` — bot source
- `requirements.txt` — Python dependencies
- `render.yaml` — Render Background Worker blueprint
- `README.md` — setup notes

## Required environment variables
- `TELEGRAM_BOT_TOKEN`: token from Telegram `@BotFather`
- `GEMINI_API_KEY`: API key from https://aistudio.google.com/apikey
- `GEMINI_MODEL`: optional; defaults to `gemini-2.5-flash`
- `BOT_DB_PATH`: optional SQLite path; defaults to `lolboss.sqlite3`

Never commit tokens or API keys to GitHub.

## Render deployment
Create a **Background Worker** connected to this repository.
- Build command: `pip install -r requirements.txt`
- Start command: `python main.py`
Add the environment variables above in Render.

Run only one instance for a given Telegram bot token. If Telegram logs `Conflict: terminated by other getUpdates request`, stop any other service/terminal running the same bot token.

## Telegram setup
1. Create the bot via `@BotFather` using `/newbot`.
2. Add it to your group.
3. To let the bot read ordinary group messages, adjust BotFather group privacy settings if you intentionally want that; otherwise it reliably responds to mentions/replies.
4. Admins can use `/enablechat` and `/stopchat` to control occasional automatic chat.
5. Commands include `/joke`, `/truth`, `/dare`, `/mood`, `/challenge`, `/daily`, `/profile`, `/leaderboard`.

## Important limitations
- This project is provided as source code; it has not been deployed with your credentials.
- Auto-chat scheduling is in-memory and must be enabled again after a worker restart.
- SQLite data may reset on a non-persistent Render filesystem. Configure persistent storage if you need durable records.
- Gemini API quotas, model availability, and billing depend on Google's current account policies.
