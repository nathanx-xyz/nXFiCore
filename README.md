# 🤖 nXFiCore

**The all-in-one Telegram bot for NEAR communities - tipping, moderation, and live buy alerts in a single bot.**

Stop running three separate bots. nXFiCore combines crypto tipping, group moderation, and real-time buy notifications into one tool - fully configurable per group, no restarts needed.

https://t.me/nXFiCoreBot

---

## ✨ Why nXFiCore?

- 🪙 **Tip in NEAR or any NEP-141 token** - directly in chat, no external app
- 🛡️ **Full moderation suite** - verification, anti-spam, anti-raid, word filters, and more
- 📈 **Live buy bot** - real-time swap alerts with price, market cap, and custom branding
- ⚙️ **Everything configurable in-group** - admins control every feature from a single `/panel`, live, no downtime
- 🔐 **Secure by design** - encrypted wallets, live-verified admin checks (not stale cached roles)

---

## 🚀 Getting Started

1. Add **nXFiCore** to your group
2. Make the bot an **admin** (required for moderation + tipping to work)
3. Run `/panel` to turn on the modules you want
4. Configure each module - tipping, moderation, buy bot - right from the panel

That's it. No external dashboard, no website login - everything happens inside Telegram.

---

## 📋 Command Reference

### General

| Command | Description |
|---|---|
| `/start` | Welcome message / context-aware intro |
| `/help` | Shows available commands based on what's enabled |
| `/panel` | Main control panel - toggle modules, access settings |
| `/modhelp` | Full moderation command reference |
| `/id` | Get a user's or chat's Telegram ID |

---

### 💰 Tipping

| Command | Description |
|---|---|
| `/setup` | Register this group for tipping (admin only) |
| `/tokens` | List all tokens available to tip with |
| `/settoken SYMBOL` | Add a token to this group |
| `/settoken SYMBOL default` | Set a token as the group's default |
| `/balance` | Show the group treasury balance across all assigned tokens |
| `/register your.near` | Pre-register your NEAR wallet to receive tips automatically |
| `/claim your.near` | Claim a pending tip by registering your wallet |
| Reply to a message + `/symbol amount` | Tip that user - e.g. `/near 0.5`, `/blackdragon 1000` |

**How it works:** reply to anyone's message with `/tokensymbol amount` to tip them instantly. If they haven't registered a wallet yet, the tip is held safely - as soon as they run `/claim their.near`, it (and any other pending tips) sends automatically. No tips are lost.

> 💡 Only group admins can send tips, keeping things spam-free.

---

### 🛡️ Moderation

| Command | Description |
|---|---|
| `/warn [reason]` | Warn a user (reply to their message, or `@username`) |
| `/unwarn` | Remove a user's most recent warning |
| `/warnings` | View a user's full warning history |
| `/ban [reason]` | Ban a user |
| `/unban` | Unban a user |
| `/kick [reason]` | Remove a user without a permanent ban |
| `/mute [1h/30m/2d] [reason]` | Mute a user for a set duration |
| `/unmute` | Unmute a user |
| `/purge` | Delete every message from a replied-to message onward |
| `/pin [silent]` | Pin a message |
| `/unpin` | Unpin a message |
| `/lock [type]` / `/unlock [type]` | Lock/unlock a media type (see types below) |
| `/filter [word] [action]` | Add a word filter (`delete` / `warn` / `mute` / `ban`) |
| `/unfilter [word]` | Remove a word filter |
| `/filters` | List all active word filters |
| `/save [name] [content]` | Save a canned response |
| `/get [name]` | Retrieve a saved note |
| `/del [name]` | Delete a saved note |
| `/notes` | List all saved notes |
| `/promote` / `/demote` | Promote or demote a group admin |
| `/adminlist` | List current group administrators |
| `/report [reason]` | Report a message - pings all group admins instantly |
| `/rules` / `/setrules [text]` | View or set the group rules |
| `/settings` | Open the moderation settings panel |

**Lock types:** `stickers` `gifs` `voice` `videonote` `forwards` `checklists`

#### What's protecting your group, automatically:

- **🔐 Verification** - new members solve a quick math challenge before they can post. Anyone already in the group when the bot was added is silently verified on their first message - no disruption to existing communities.
- **🌊 Anti-Flood** - sending messages too fast triggers an automatic 1-hour mute.
- **🛡️ Anti-Raid** - mass-join attacks trigger a temporary full group lockdown.
- **🔗 Link Control** - choose who can post links: everyone, verified members only, admins only, or nobody.
- **🛑 Hate Speech Filter** - automatically detects and removes slurs, threats, and harassment, with optional AI-powered detection for sharper accuracy. Auto-warns and auto-bans repeat offenders.
- **🎰 Emoji Spam Filter** - automatically removes messages stuffed with excessive emoji (classic spam/scam pattern), with an adjustable sensitivity threshold.
- **🚫 Checklist Blocker** - blocks Telegram's checklist feature and common emoji/markdown workarounds used to bypass spam filters.
- **⚠️ Configurable Warning System** - set your own warning limit (1-10) before auto-ban kicks in. Every warning comes with one-tap admin actions: pardon, mute, kick, or ban.

All of the above are toggled live from **`/panel > Moderation Settings`** - flip them on or off per group, instantly, no restart.

---

### 👋 Welcome Message

Fully configurable per group - set up directly from `/panel → Moderation Settings → 👋 Welcome Message`.

**Settings:**

| Option | Description |
|---|---|
| 🟢/🔴 Enable/Disable | Toggle the custom welcome on or off. When disabled, a simple default message is shown and auto-deleted after 5 seconds |
| 📝 Set Text | Set your custom welcome text. Reply to the bot's prompt with your message |
| 🖼️ Set Media | Attach a photo, GIF, or video to your welcome message. Reply to the bot's prompt with the media |
| 🔗 Custom Links | Add up to 5 clickable button links below the welcome message (e.g. Website, Twitter, Discord) |
| ⏱️ Auto-delete | Set how long the custom welcome message stays before being deleted. Options: Never / 30s / 1 min / 5 min / 10 min / 30 min |
| 👁️ Preview | Send a preview of your welcome message as it will appear to new members (auto-deletes after 5 seconds) |

**Text placeholders:**

| Placeholder | Output |
|---|---|
| `{name}` | Clickable mention of the new member |
| `{username}` | @username, or first name if no username |
| `{chat}` | The group name |

**Inline links in text:**
Use HTML syntax directly in your welcome text:
```
<a href="https://yoursite.com">Click here</a>
```

**Custom link buttons:**
When adding links via 🔗 Custom Links, reply to the prompt using the format:
```
Label | https://yourlink.com
```
Example: `Website | https://nxfi.io`

**How it works:**
- If verification is **on** - the welcome message fires automatically after a user passes the math challenge
- If verification is **off** - the welcome message fires immediately when a user joins
- If the custom welcome is **disabled** - a plain default message is shown and auto-deletes after 5 seconds
- The 👁️ Preview always auto-deletes after 5 seconds so it doesn't clutter the group

---

### 📈 Buy Bot

| Where | What |
|---|---|
| `/panel > Buy Bot` | Quick enable/disable toggle |
| `/panel > Buy Bot Settings` | Full configuration menu |

**Setup is 100% inline** - no DMs, no external tools:

- **Change Token** - reply to the bot's prompt with the token's contract address
- **Emoji** - pick your buy-alert emoji from a button menu
- **Min Buy** - set the minimum USD value that triggers an alert ($1-$500)
- **Per Emoji $** - control how many emoji appear per dollar bought
- **Pool ID** - link your DEXScreener chart
- **Change Media** - reply with a photo or GIF to brand your buy alerts
- **Custom Links** - add up to 5 extra buttons (website, X, docs, etc.)

**Every buy alert shows:**
- 🎉 Custom emoji bar scaled to buy size
- 💰 Amount bought + USD value
- 📈 Live token price
- 💎 Market cap
- 🌐 Current NEAR price
- 👤 Buyer's wallet
- 🔗 Tx / Buy / Chart buttons + any custom links you've added

Real-time, fully automated, zero manual posting.

---

## 🎛️ The Control Panel

Run `/panel` in your group to see everything at a glance:

```
✅ Tipping        | 💰 Tipping Setup
✅ Moderation     | 📋 Moderation Settings
❌ Buy Bot        | 🤖 Buy Bot Settings
            ❌ Close
```

Every module is independently switchable. Turn tipping off but keep moderation on, run the buy bot solo, or run all three together - your group, your configuration.

---

## 🔒 Security & Trust

- Wallet private keys are **encrypted at rest**
- Admin permissions are **verified live against the Telegram API** on every sensitive action - not cached, not assumed
- Pending tips are **never lost** - held safely until the recipient registers a wallet
- All moderation actions can be mirrored to a **private audit log channel**

---

## 🙋 Support

Questions, feature requests, or found an issue? Contact **[@nathanx_xyz](https://t.me/nathanx_xyz)**

---

*Built for NEAR communities who want one bot that does it all.*
