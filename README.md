<div align="center">

# Fortuna

### The fully-headless account reroller for **Umamusume: Pretty Derby (Global)**

*Mint accounts, spend every carat on the banner you want, and harvest SSRs — all over the game's own API, with the game closed.*

[![Download](https://img.shields.io/badge/Download-on%20Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/wpbd3hTBDc)
[![Platform](https://img.shields.io/badge/Windows-10%20%7C%2011-2b2b2b?style=for-the-badge&logo=windows&logoColor=white)](#requirements)
[![Region](https://img.shields.io/badge/region-Global%20only-e8e8e8?style=for-the-badge)](#global-only-by-design)

**[Download on Discord](https://discord.gg/wpbd3hTBDc) · [How it works](#how-a-reroll-actually-runs) · [Is it safe?](#built-to-look-human)**

</div>

---

> ### Where to download
> Fortuna is distributed **only through our Discord server**. Join, then grab the latest build from the downloads channel:
>
> **[discord.gg/wpbd3hTBDc](https://discord.gg/wpbd3hTBDc)**
>
> Each release is posted with its **SHA-256 checksum** and a **VirusTotal** scan. This repository contains no downloads — if you find a Fortuna build anywhere else, it isn't from us.

---

## Why Fortuna is different

Most rerollers drive the game: they open a window, tap through menus, and read the screen with OCR or a memory plugin. That's slow, fragile, and obvious.

**Fortuna doesn't touch the game.** It talks to Cygames' servers directly — the exact same API the client uses — and does the whole reroll headlessly:

> **Delete the slot → mint a brand-new account → claim the login & present-box gifts → spend every last carat on your chosen banner → save a recoverable transfer password → sweep the mission/archive rewards and pull again → record everything → repeat.**

No game window. No Frida on the reroll loop. No OCR. No screen scraping. No memory patching. Just clean API calls, paced to look exactly like a person tapping through the client.

The result: **dozens of freshly-minted accounts an hour**, each with its full pull history and recovery credentials, browsable in a local dashboard you can leave running while you do something else.

<div align="center">

|  | Typical macro rerollers | **Fortuna** |
|---|:---:|:---:|
| Opens the game to reroll | Yes, every account | **Never** (closed after setup) |
| Reads the screen (OCR) | Yes | **No, direct API** |
| Needs a plugin / Frida / memory patch | Yes | **No, pure API mint** |
| Account name / gender / birthday | you set them | **auto, realistic, gender-matched** |
| Spends carats on **your** banner | sometimes | **Spend-all, every time** |
| Keeps a recoverable account + password | rarely | **Every reroll** |
| Full pull history & SSR ledger | No | **Local DB + Excel export** |
| Speed | menu-tapping slow | **~1 account per minute** |

</div>

---

## Features

### Reroll that actually gets you the banner
- **Pure API account mint** — a fresh account is a direct call sequence (`delete slot → signup`), so the game never opens to reroll.
- **Spend-all on your banner** — free daily 10-pull if offered, then 10-pulls, then singles, until the carats are gone. It empties the wallet on the banner *you* picked, not a default.
- **Post-pull reward sweep** — after the carats run out, Fortuna does what the live client does: opens the Archive, claims completed missions and present-box payouts, then goes **back to the same banner and pulls again** with the reward carats. Up to three rounds, until a round pays out less than a single pull.
- **Recoverable accounts** — every account gets a published **Data Link transfer password** and Trainer ID, so any roll you like can be claimed in-game later. Nothing is throwaway unless you delete it.

### A dashboard built like a control panel
- **Icarus design language** — a fixed header / sidebar / status-bar shell, matte black and strictly grayscale (card rarity is the only colour). No gradients, no glow, no noise.
- **100% offline & self-hosted** — every font and asset is served locally. No CDN, no external JavaScript, no telemetry. It runs on `127.0.0.1` and stays there.
- **An activity rail that answers two questions** — *can I start a run right now?* and, once one is going, *how far along is it?* Idle, it is a preflight: Steam, device identity, banner, watchlist and Discord, each with a verdict, and a button for the first thing standing in the way. Live, it is a dial — which account is in flight, the percentage done, and roughly how long is left. It rides every page, and pops out into its own window.
- **Live log in plain English** — one line per step, grouped per account, with a glyph on every line (`✓` done · `▸` step · `!` warning · `✕` error · `★` goal hit). Filter to **Milestones** or **Problems**, search it, or flip to **raw** engine output.
- **Search anything** — `Ctrl K` (or `/`) jumps to any page, section, setting or help topic, with the matching letters highlighted.

### A watchlist that fills itself + Discord alerts
- **Pick a banner and the watchlist follows** — it fills with that banner's cards at 5 copies each, so "what counts as a hit" is set the moment you choose where to pull. Change any number, or add anything else from the catalogue picker (support cards filtered to **SSR** by default).
- **Works on character banners too** — a character's star rating counts as its rarity (3★ = SSR), so watchlists, Discord posts and the SSR column all work whether you're pulling for support cards or trainees.
- **Rich Discord webhooks** — every hit posts which card matched, the account's full SSR/SR list, Trainer ID, pulls and carats spent (**never** the transfer password), with the suite mark, the account's best pull pictured, and a **Best pull** field. Choose to post on **goal hits only** (@-mentions you), **every account**, or **off** — and a **Send test message** button tells you exactly what Discord replied before a long run.

### Paced for the game's edge protection
- **A refusal costs you nothing.** Global blocks a connection that creates too many accounts over an hour or two. When that happens Fortuna waits and retries the same slot instead of burning fresh accounts against a closed door, and stops with a plain explanation if the block outlasts the wait.
- **It holds before it is refused.** Accounts minted are counted in a rolling window that survives restarts — and seeds itself from what you have already harvested — so a run pauses at your ceiling rather than discovering the limit the hard way. Visible on Settings › Reroll and on the activity rail; set it to 0 to turn it off.

### Banners, done right
- **Probe live** to read the current banner list straight from the server, then pick **the one** every account pulls on — cached, so you can pick without a live account after the first load.
- **Select-banner support** — tick the exact rate-up cards you're aiming for.
- The picked banner is **unmistakable**: a bright ring, a lifted card, and a bold **● PULLING ON THIS** flag, mirrored in the header and status bar.

### Your harvest, organized
- **Accounts table** with bulk **select** (per row, or "select all shown" honouring your filters), search by trainer id or name, a *holding card* filter, and sorting by **Most SSR**, newest, most unique or most copies.
- **Every row shows what it pulled** — up to six SSRs (the watchlist's first, when there is one), and expanding a row lists every SSR *and* every SR with copy counts.
- **Excel export** — **Export all / Export selected** writes a real `.xlsx` with two sheets: *Accounts* (Trainer ID, transfer password, transition code, harvest date, pull counts, SSR/SR/R totals, carats spent, and the SSR/SR cards written out) and *Cards* (one row per card, ready to pivot). No spreadsheet software required — Fortuna writes the workbook itself, fully offline.
- **Delete selected** cleans rows, their cards and the secured-pool entries locally — and warns you when a row still holds a recoverable password.

---

## Quick start

1. **[Join the Discord](https://discord.gg/wpbd3hTBDc)**, download the latest release from the downloads channel, and unzip it anywhere — keep everything in the folder together.
2. Run **`Fortuna.exe`**. It opens your browser to the dashboard automatically. *If the one-time identity capture later fails to read the game, right-click → **Run as administrator** and try again — that's the usual fix, and double-clicking does not elevate.*
3. **Sign in to Steam** (the account that owns Umamusume) and **capture the device identity** once — one click, one brief game launch. *After this, every reroll runs with the game closed.*
4. **Pick a banner → set how many accounts → Start reroll.** Watch them land under **Accounts**.

That's it — it's plug-and-play. Nothing to install.

---

## How a reroll actually runs

1. **Open session** — mint a fresh Steam session ticket and load this region's captured identity (device keys + `app_ver`). *The game is not launched.*
2. **Create** — log in as the Steam slot's current occupant → the **main-account guard** confirms it's safe to delete → disconnect (Delete User Data) → wait for the slot to release → **mint** a fresh account with a new device id. Retries the whole dance on transient server codes.
3. **Identity** — pick a realistic, **gender-matched** trainer name (5000-name pool), a random gender, and a random adult birthday.
4. **Reroll** — adopt the account → claim the present box → pull the selected banner **spend-all** → publish the transfer code (now recoverable) → **collect-and-spend sweep** (Archive → missions → present box → pull again) → store everything to the local DB.
5. **Next account** — the following cycle deletes this now-secured account first. There's no wasted "return to title" step.

Every step is narrated in the live log, and every finished account — Trainer ID + transfer password — is saved for you to browse, export, or claim in-game.

---

## Built to look human

A headless farm trips anti-bot systems faster than a game-gated one, and *constant* timing is what gives a bot away. So **every delay in Fortuna is randomized and shaped like real play** — and **none of it is operator-adjustable**. There is no pacing control in the dashboard; a hand-edited config changes nothing.

| Layer | What it does |
|---|---|
| **Per-call spacing** | A small jittered gap in front of every API call, tightened inside the gacha window where the client is strict. |
| **Per-endpoint delays** | Lognormal think-time in front of lifecycle calls (tutorial skip, name entry), with an occasional "distraction" pause. |
| **Pull rhythm** | Shaped like the in-game loop — tap → skip → results → tap — with the odd long look at the results screen. |
| **Account tempo** | Each account draws its own speed multiplier, skewed so outliers run *slow*, never suspiciously fast. |
| **Account floor & breaks** | Every account spans a randomized minimum wall-time; ~1 in 12 is followed by a short break. |
| **Batch cap** | 50 accounts per run — no infinite loops. **Stop** halts within a single pull, and the account in flight is still saved with its transfer password. |

In practice each account runs **around a minute** (with the occasional slow one), and a full 50-account batch lands in **roughly an hour**.

### The main-account guard
The first cycle deletes whatever account holds the Steam slot — but the guard **refuses** to delete an occupant that isn't provably disposable. Deletion is allowed only if the account is brand-new (tutorial not done), already saved with a transfer password, or was minted by Fortuna itself. Otherwise the run aborts with a clear message. There's a **Force first delete** override for when you're certain the slot account is disposable.

---

## Updates

New versions are announced and posted in the **[Discord](https://discord.gg/wpbd3hTBDc)**. To update, download the new release, close Fortuna, and replace the old folder with the new one. Each release comes with a `.sha256` checksum so you can confirm the download is genuine.

Your data directory (settings + harvested accounts) lives outside the program folder and is never touched by an update, so everything carries over.

> **Only run one instance at a time.** Close every Fortuna window before starting a new one — the dashboard detects a stale server and shows a restart banner if features are missing.

---

## The Icarus Suite

Fortuna is one tool in a family. The dashboard's **Catalogue** page lists them all, and every one of them is available on the **[Discord](https://discord.gg/wpbd3hTBDc)**:

- **Fortuna** — *(this)* a fully headless Global account reroller (pure API mint, no game, no plugin).
- **Icarus** — capable of 5-minute MANT runs; a native API automation platform that fully automates careers without screen scraping or OCR. Every scenario, intelligent training, multi-account, multi-instance, auto training and dailies.
- **Un-Follower** — reads your follower list straight from the Cygames server, works out who's inactive and removes them via the game's own `friend/un_follower` API.
- **Navigator** — the developer tool that captures and decodes the game's native API traffic. It's what the rest of the suite is built on.

---

## Global only, by design

Fortuna is dedicated to the **Global** region. There is no JP support, and that's intentional — the entire wire protocol, catalog and identity flow are tuned for the Global client.

---

## Requirements

- **Windows 10 / 11.**
- **Umamusume: Pretty Derby (Global)** installed via **Steam**, on a Steam account that owns it — needed only for the **one-time** device-identity capture, and briefly after a game patch (which Fortuna handles by itself).
- **Administrator** — *sometimes* needed for the one-time identity capture, which reads the running game. It often works without it, but when the attach is refused, elevation is the fix: **right-click `Fortuna.exe` → Run as administrator; double-clicking does not elevate.** Day-to-day rerolling never needs it.

### After a game patch
**Nothing to do — Fortuna handles this itself.** `res_ver` self-corrects, and `app_ver` (which a Cygames patch otherwise invalidates) is refreshed automatically at launch: Fortuna notices the patch from Steam and only opens the game if it actually has to, for about a minute. The banner list re-checks itself in the background too.

---

## Data & privacy

Everything stays on your PC. All state — Steam credentials (encrypted with Windows DPAPI), the captured device identity, tickets, the account database, and your config — lives under `%LocalLow%\Icarus\Fortuna`, isolated from every other tool. The one thing kept where you can find it is your account spreadsheets: those go in an **`Exports`** folder next to `Fortuna.exe` (and fall back to the data folder if the app is installed somewhere unwritable). Treat that file carefully — it contains transfer passwords. The only outbound traffic is to Steam, the game's servers, and **your own** Discord webhook.

**No personal data ships** — the build fails if any login, saved account, password or personal-data path is present in the tree. Transfer passwords are never put in Discord messages.

---

## Support & bugs

- **[Join the Discord](https://discord.gg/wpbd3hTBDc)** for downloads, help, updates and announcements.
- Hit a bug? In the app: **Live Log → Download diagnostics** writes a single scrubbed text file (version, OS, pacing, current run, server-log tail — passwords, webhook URLs and Steam id removed). Attach it to your report on Discord.

---

## License

Fortuna is **proprietary** software — © 2026 the Fortuna developers, all rights reserved.

You're welcome to **download and use the official release** from the Discord. You may **not** reuse Fortuna or any part of it in your own projects, or copy, modify, or redistribute it.

---

<div align="center">

**Fortuna** · part of the **Icarus Suite** · Global only

*Not affiliated with Cygames. Umamusume: Pretty Derby is a trademark of its respective owners.*

[Download on Discord](https://discord.gg/wpbd3hTBDc) · [Discord](https://discord.gg/wpbd3hTBDc)

</div>
