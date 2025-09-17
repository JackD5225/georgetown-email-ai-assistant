# georgetown-email-ai-assistant
Gmail assistant that uses OpenAI to categorizes, summarizes, and drafts replies.
# 🎓 Georgetown Email AI Assistant

**Free, open-source email management tool for students and professionals**

Transform your Gmail inbox into an organized, AI-powered productivity system. Automatically triage emails, generate smart summaries, and draft responses - all while keeping your data private and local.

## ✨ What It Does

- **🤖 Smart Triage** - Automatically categorizes emails (Action, Calendar, Recruiter, Finance, Newsletter, FYI)
- **📝 AI Summaries** - Uses OpenAI GPT-4o-mini for concise 3-bullet summaries
- **✍️ Auto-Drafting** - Generates personalized response templates
- **🔒 Privacy-First** - Read-only Gmail access, all processing happens locally
- **⚡ Lightning Fast** - Process hundreds of emails in seconds
- **🎯 Customizable** - Works with any Gmail account, fully customizable

## 🚀 Quick Demo

```bash
# See it in action (no Gmail required)
python demo.py
```

## 📊 Real Results

**Before:** 50+ unread emails, no organization, missed deadlines
**After:** Categorized digest, AI summaries, ready-to-send drafts

```
=== Daily Digest ===
[Action] Voter Registration Information — University Registrar (id=1995972ea3daffe8)
[Calendar] Meeting Invitation — Jack Dobson (id=1995955aec0becbc)  
[Recruiter] Software Engineer Role — Tech Corp (id=1995921b33bc857b)
Total: 3
```

## 🚀 Quick Start (5 minutes)

### 1. Setup
```bash
# Clone/download the project
cd georgetown-email-ai-assistant-v2

# Create virtual environment
python3 -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### 2. Gmail Setup (One-time)
1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select existing
3. Enable **Gmail API**
4. Go to **Credentials** → **Create Credentials** → **OAuth client ID**
5. Choose **Desktop application**
6. Download the JSON file and save as `credentials.json` in the project folder
7. Add your email as a test user in OAuth consent screen

### 3. Authenticate
```bash
python cli.py auth
```
This opens your browser for Gmail authorization. The app requests **read-only** access.

### 4. Use It!
```bash
# See your email digest
python cli.py digest

# Generate response drafts
python cli.py draft
```

## 📖 Complete Guide
See [USER_GUIDE.md](USER_GUIDE.md) for detailed instructions, examples, and troubleshooting.

## Useful Gmail queries
- `in:inbox is:unread newer_than:7d`
- `from:@georgetown.edu -category:promotions`
- `from:@citizensbank.com OR subject:(HireVue OR interview)`
- `has:attachment -category:promotions`

## Enable send/labels later
- In `gmail_client.py`, uncomment `gmail.modify` / `gmail.send` scopes
- Delete `token.json`, re-run `python cli.py auth`

### Security & Privacy

- **Never share or commit** `token.json` or `credentials.json`.
- What they contain:
  - `credentials.json`: your OAuth client ID & secret
  - `token.json`: your Gmail access + refresh token
- These files are already in `.gitignore`, but double-check before pushing.
