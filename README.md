
# 🤖 Discord + Gemini AI Chatbot

This project integrates Google's **Gemini Pro** model with a **Discord bot** that chats intelligently using Gemini's generative capabilities.

---

## 🌟 Features

- 📩 Chat with Gemini directly inside Discord
- 🔐 Uses **environment variables** for API key security (no hardcoding)
- 💬 Sends thoughtful replies to user prompts using `gemini-pro`

---

## 🛠️ Requirements

- Python 3.9+
- `google-generativeai`
- `discord.py`
- Environment variables for API keys set in Colab Secrets

Install dependencies:

```bash
pip install google-generativeai discord.py python-dotenv
```

---

## 1. Setup API Keys (in Google Colab)

> ⚠️ **DO NOT hardcode keys in code.** Use Colab’s secret manager instead.

```python
import os

os.environ["DISCORD_BOT_TOKEN"] = "YOUR_DISCORD_BOT_TOKEN"
os.environ["GEMINI_API_KEY"] = "YOUR_GEMINI_API_KEY"
```

---

## 2. Initialize Gemini

```python
import google.generativeai as genai

genai.configure(api_key=os.getenv("GEMINI_API_KEY"))
model = genai.GenerativeModel("gemini-pro")
```

---

## 3. Run the Bot Script

Make sure your Python script:

- Reads API keys using `os.getenv()`  
- Instantiates the Gemini model using `genai.GenerativeModel("gemini-pro")`  
- Handles messages via `discord.Client` and replies with Gemini responses  

---

## 4. Invite the Bot to Your Discord Server

Make sure your bot has the correct permissions:

- ✅ **View Channels**
- ✅ **Send Messages**
- ✅ **Read Message History**
- ✅ **Connect** (if voice features are used)
- ✅ **Use Slash Commands** (optional for advanced control)

You can generate an invite link using this site:  
[https://discordapi.com/permissions.html](https://discordapi.com/permissions.html)

---

## 5. Example Usage

**User:** `!ask How can I make this day beautiful?`  
**Gemini:** _"Making your day beautiful is all about intentionality..."_  

---

## 🧪 Test Tips

- Make sure `.env` or secrets are set before `genai.configure(...)`
- Use `print()` to debug the bot login and message events
- Ensure the bot is **invited** and **online** before chatting

---

## ❗ Notes

- Gemini's response length should be **<2000 characters** (Discord limit)
- Handle errors like `400 Bad Request` by trimming long replies

---

## 📂 Folder Structure (Suggested)

```
discord-gemini-bot/
├── bot.py
├── requirements.txt
├── README.md
└── .env (optional)
```

---

## 🤝 Contributions

Pull requests are welcome! Feel free to fork and enhance features, add slash commands, etc.

---

