# Smart Money Bro 💰

**A pocket-money app for kids aged 9–18.** Track what comes in and what goes out, split every dollar into jars before spending it, save for something brilliant, earn rewards, and learn how money actually works — explained by a talking coin called Cent.

Built as a single HTML file. No server, no accounts, no sign-up, no data leaving the device.

---

## Contents

1. [Quick start](#quick-start)
2. [Who it's for](#who-its-for)
3. [Feature tour](#feature-tour)
4. [Cent, the mascot](#cent-the-mascot)
5. [The rewards system](#the-rewards-system)
6. [Parent savings match](#parent-savings-match)
7. [Singapore content and how it was checked](#singapore-content-and-how-it-was-checked)
8. [Design system](#design-system)
9. [How data is stored](#how-data-is-stored)
10. [Putting it on the internet](#putting-it-on-the-internet)
11. [Phones and watches](#phones-and-watches)
12. [Testing](#testing)
13. [Taking it further](#taking-it-further)

---

## Quick start

Double-click **`index.html`**. That's it.

It opens in any browser and works offline. On first run it asks for a name, age, currency symbol and an avatar, then you're straight into the dashboard.

The default parent PIN is **`1234`** — change it in **Parents → Change PIN**.

### Files

| File | What it is |
|---|---|
| `index.html` | The entire application — HTML, CSS and JavaScript in one file |
| `README.md` | This document |
| `google-sheet-backend.gs` | Optional. A free Google Sheets backend for collecting data from testers — not needed to run the app |

There is no build step, no `npm install`, and no dependencies to manage. The only external request is a Google Fonts stylesheet, and the app falls back to system fonts if it's offline.

---

## Who it's for

Content and tone adapt automatically to the child's age:

| Age | Tier | Tone |
|---|---|---|
| 9–12 | Junior | Concrete, everyday, shop-floor examples |
| 13–15 | Middle | Budgeting, bank accounts, first cards |
| 16–18 | Senior | Interest, scams, earning and hourly rates |

Change the age in **⚙️ Settings** and the lessons, money hacks and difficulty all switch over.

---

## Feature tour

### 🏠 Dashboard

The home screen, and where a child will spend most of their time.

- **Cheer bubble** — a floating comic speech bubble with a bobbing emoji medallion and a gold starburst sticker stamping the key number: **77% SAVED**, **9 DAYS**, **$12 TOP-UP**. The message is chosen from what is actually true right now, never generic filler.
- **Four stat tiles** — money in, money spent, left to spend, saved so far. Each is colour-coded with a one-line explanation underneath, e.g. *"Most spent on Snacks: $118.50"*.
- **Budget jars** — the core idea of the app. Set how much you've got, drag the **Save %** and **Share %** sliders, and the money splits live into three jars: **Save first**, **Spend wisely**, **Give or help**. The Spend jar drives the "Left to spend" figure, which counts down as spending is logged and never drops below zero.
- **Tracker** — add an entry without leaving the page: what happened, amount, category, description.
- **Money hacks** — collectible cards (see below).
- **Where your money went** — a donut chart with a percentage breakdown and a line pointing out the biggest slice.
- **Recent activity** and **goal progress**.

### 💸 Money

The full diary, grouped by month, with in / out / kept totals for each. Every entry can be deleted, and entries can be backdated.

Income categories: pocket money, chores, gift, part-time work, sold something, other.
Spending categories: snacks, games, toys, books, clothes, fun, gifts, travel, into savings, other.

### 📊 Budget

Set a monthly limit per category. You get spend-vs-plan bars that turn amber at 80% and red when exceeded, an over-limit warning naming the categories, and a month-by-month history of money in against money out.

The tone here is deliberate: going over budget is framed as **information, not failure**. If snacks blow the limit three months running, the app suggests the limit was wrong, not the child.

### 🎯 Goals

Name a goal, price it, pick an emoji, and watch the bar fill. Each goal shows a live estimate — *"about 4 months at your current saving rate"* — calculated from how much they've actually been keeping. Adding to a goal optionally logs it as money moved into savings.

### 🎓 Money lessons

Four lessons per age tier, each narrated by Cent one beat at a time, each ending in a short quiz. See [Cent, the mascot](#cent-the-mascot).

### 🔒 Parents

PIN-protected. Locks itself the moment you navigate away from the tab.

- In / out / kept summary and a full spending breakdown with percentages
- **Talking points** — auto-generated conversation starters, e.g. *"14 small purchases this month totalling $48. Small repeated spends are usually the invisible leak."*
- **Savings match** setup and payout
- Allowance amount and cadence, plus a one-tap "log payment"
- Learning and badge progress
- **CSV export**, **JSON backup**, change PIN, erase everything

---

## Cent, the mascot

Cent is a hand-drawn SVG coin with eyes, arms and feet — **deliberately unisex**, no gender cues anywhere. He blinks every few seconds, bobs gently, waves an arm, and flaps his mouth while he's talking.

His job is to stop the lessons being a wall of text. Each lesson is broken into single-paragraph beats that he delivers in a speech bubble, with **Back / Next** and progress dots. "Your first bank account in Singapore" becomes eight short exchanges instead of one long page. At the end he hands over to the quiz.

**He talks like a kid's mate, not a teacher.** Every beat opens with a line of his own, using the child's name and plenty of contractions:

> *"Hey Aria! Let's do this one together — I'll keep it short, promise. 👋"*
> *"Fun fact: loads of grown-ups get this wrong."*
> *"This is the bit I'd tattoo on my face if I had one."*
> *"Boom — that's the whole lesson! 🎉"*

**🔊 Voice on** makes him read each beat aloud. It picks an actual children's voice if the device has one installed, otherwise the lightest, clearest voice available, then pitches it up (1.6) and slows it slightly (0.94 rate) so he sounds like a cartoon coin rather than a bank manager. Emoji are stripped before speaking so it doesn't read "fire emoji" out loud. It's off by default, remembers the choice, and the button disappears entirely on browsers without speech support. Genuinely useful for younger readers and for anyone who finds reading hard work.

Cent also does the thinking on the money-hack cards.

---

## The rewards system

Everything here is earned by doing, never by guessing at a quiz.

### Cheer messages

Tied to real numbers and chosen by priority — goal nearly finished beats high savings rate beats streak, and so on. All gender-neutral.

> 👑 **Whoa — you saved 77% this month!**
> That is $19.59 kept, Casey. Smart and rich. Most adults do not manage this. Keep it up!

When a month goes badly it stays kind and points at the fix rather than scolding:

> 🧭 **Tricky month — and that is OK**
> You spent $22 more than came in. Everyone does this sometimes. Try the jars: take savings off the top first, then spend what is left.

### Money hacks — collectible cards

A deck of eight age-appropriate hacks per tier, drawn as **thought bubbles**. Cent sits in the corner thinking 💭 *"Hmm… what is the trick here?"*; tap and the card flips over in 3D to reveal the answer. Hit **"Got it! +1"** to collect it — small confetti burst, a dot fills in green, the counter ticks up. Collected cards show their real emoji and title on the front, so the deck fills like a sticker album.

### Badges

Seven, each showing a visible hint while locked so kids know what to chase:

| Badge | How to earn it |
|---|---|
| 🎉 First Log | Log your first entry |
| 🐷 Saver | Keep 20% of your money in a month |
| 🏆 Goal Hit | Finish a savings goal |
| 📊 Budgeter | Set a budget and use it |
| 🎓 Scholar | Finish every lesson |
| 🔥 7 Days | Log something 7 days in a row |
| 🃏 Hack Hunter | Collect every money hack |

Unlocking any of them fires confetti.

---

## Parent savings match

The strongest feature for actually changing behaviour, and it's off by default.

In **Parents → Savings match**, set a percentage (say 20%) and an optional monthly cap. The child then sees a live card on their dashboard: *"Your parents add 20% of everything you keep. You have kept $52 so far, so keeping more grows this number."*

It rewards **saving**, not chores or grades — the same mechanic as an employer matching a pension, which is exactly the habit you want them to recognise later in life.

**Nothing moves automatically.** The app never touches real money. When you've actually handed the money over, press **Pay now**, which logs it as income and fires confetti. The month is then marked as paid so it can't be double-counted.

---

## Singapore content and how it was checked

The banking lesson for ages 13–15 states only facts verified in **August 2026** against bank and news sources:

- **POSB Smart Buddy** — for ages 7 to 16, with a contactless watch or card and a parent app
- **OCBC MyOwn** — launched October 2024 for ages 7 to 15; the account is in the child's own name with their own debit card and app, but a parent opens it and sets the spending limits
- **DBS/POSB ATM card** — eligible to apply from age 12 at a branch
- **Age 16** — digital banking access, a Visa Debit card, and the ability to apply as sole account holder at most banks
- **Under 16** — cannot open an account alone; a parent or guardian opens it as a joint or trust account
- Also mentioned: POSB My Account (Kids), UOB Junior Savers, CIMB Junior Saver

The lesson states when it was checked and tells the reader to confirm on the bank's own website, because these terms change.

**The shopping hacks deliberately avoid naming current prices or promotions.** "Donuts are discounted on Thursdays" would be wrong within a month and teaches nothing durable. Instead they teach the checking habit: convenience stores charge more than supermarkets for the same drink, read the price-per-100g on the shelf label, check the shop's own app before you queue, 1-for-1 only helps if you wanted two.

**Sources:** [POSB Smart Buddy](https://www.posb.com.sg/personal/deposits/bank-with-ease/posb-smart-buddy) · [OCBC MyOwn](https://www.ocbc.com/personal-banking/deposits/myown-account) · [OCBC media release](https://www.ocbc.com/group/media/release/2024/ocbc-brings-digital-banking-to-generation-alpha-with-launch-of-ocbc-myown-account) · [SingSaver](https://www.singsaver.com.sg/banking/blog/opening-first-child-savings-account) · [Wise](https://wise.com/sg/blog/minimum-age-open-account-singapore)

---

## Design system

Built for 9–15 year olds, not for adults reading a fintech dashboard.

- **Type** — Fredoka for headings (rounded, friendly), Nunito for body (heavy weights, high legibility). Headlines cap at 54px rather than magazine-sized 80px.
- **Colour** — teal, grape, pink, tangerine, sun, lime and sky, on a warm white background with four soft radial colour washes. Full dark mode via `prefers-color-scheme`.
- **Buttons** — chunky pills with a darker "lip" underneath that presses down when tapped, like a game button.
- **Cards** — 26px radius, 2px borders, soft offset shadows.
- **Motion** — bobbing mascot, blinking eyes, pulsing call-to-action, 3D card flips, wobbling stickers, confetti on wins.
- **Layout** — multi-column on desktop; below 520px the top nav becomes a fixed bottom bar; below 330px it collapses to icons for watch-sized screens.
- **Routing** — hash-based (`#dashboard`, `#money`, `#budget`, `#goals`, `#learn`, `#parent`), so every tab is a linkable URL and the back button works.

---

## How data is stored

Everything lives in **`localStorage`** in that browser, on that device. Nothing is uploaded anywhere, there's no analytics, and there are no third-party scripts.

What that means in practice:

✅ Completely private, zero hosting cost, works offline
⚠️ Data does **not** sync between the child's phone and a parent's phone — the parent view means picking up their device
⚠️ Clearing browser data wipes it

**Take a backup occasionally:** Parents → **Backup** downloads a JSON file of everything, and **Restore backup** loads one back in. Parents → **Export CSV** gives you a spreadsheet of all transactions.

### Advanced tools 🛠️

Restore, sample data and profile switching are kept out of the main interface — they'd clutter it and they're not for children.

**Where:** ⚙️ Settings → scroll to the bottom → the faint **🛠️ Advanced tools** link → parent PIN.

It's styled to disappear: small, grey, 60% opacity, no border or button styling. A parent looking for it will find it; a child scrolling past won't notice it.

| Tool | What it does |
|---|---|
| ⬆️ **Restore from file** | Loads a previously downloaded JSON backup. Validates the file first and refuses anything that isn't a Smart Money Bro backup. |
| 🎬 **Load sample data** | Adds three months of realistic entries, a goal and a budget so you can see a full dashboard immediately. Every item is tagged, so **Remove sample data** deletes exactly those and nothing you added yourself. |
| 👋 **Switch kid** | Clears the name, age and avatar so someone else can set up. All entries, goals and badges are kept. Also available in ⚙️ Settings. |
| ⬇️ Download backup · 📄 Export CSV · 💣 Erase everything | Same as the parent tab, gathered in one place. |

The panel also shows a live count of entries, goals, badges and how many of those entries are sample data.

Visible in the parent tab: Change PIN, Export CSV, Backup, Erase all.

You can also drive the app from the browser console (`F12`) — `S` is the live data object, `save()` writes it, `render()` redraws:

```js
S.tx.push({id:'t1', type:'in', amt:50, cat:'pocket', note:'Test', date:'2026-08-01'});
save(); render();

S.tx = S.tx.filter(x => x.id !== 't1'); save(); render();   // delete it again
S.profile = null; save(); location.reload();                 // back to the welcome screen
localStorage.removeItem('smartmoneybro.v1'); location.reload(); // full wipe
```

> If you ever put this in a public GitHub repo, keep backup files out of it — they contain your child's real spending history.

---

## Putting it on the internet

It's a static site, so anything that serves a file will do. All of these are free:

| Option | How |
|---|---|
| **Netlify Drop** — easiest | Go to [app.netlify.com/drop](https://app.netlify.com/drop) and drag the folder in. Live URL in about ten seconds. |
| **GitHub Pages** | Create a public repo, upload `index.html` and `README.md` to the **root**, then Settings → Pages → deploy from `main` / `(root)`. URL is `https://<username>.github.io/<repo>/` |
| **Vercel** | Run `npx vercel` in this folder, or drag and drop in the dashboard |
| **Cloudflare Pages** | Create a project → upload assets |

Upload **only** `index.html` (required) and `README.md` (optional — GitHub shows it as the repo front page). No other files are needed.

All four support custom domains for free if you want it to feel like a real product.

---

## Phones and watches

**Phone** — open the URL in Chrome or Safari and choose *Add to Home Screen*. It installs with its own icon and opens without browser chrome, like a native app.

**Watch** — the layout collapses below 330px: labels drop away, the nav becomes icon-only, and the balance stays readable. This works on Wear OS browsers. Apple Watch has no browser, so a real watchOS app would need a native build.

---

## Testing

**110 automated checks** run against a headless browser (jsdom), and the whole suite is run under three timezones (Singapore, UTC and New York) to catch date bugs. They cover:

- Setup flow and age-tier boundaries (9–12 / 13–15 / 16–18)
- Income and expense logging, balance and savings-rate maths
- Jar splits, manual overrides, and the never-negative spend jar
- The cheer engine — including an assertion that **no message is gendered**
- Cent's dialogue: greets by name, uses contractions, changes line by line
- That **no unicorn** appears anywhere in the app
- The money-hack deck: flip, collect, counters, badge on completing the set
- Narrated lessons: step splitting, Back / Next, dots, quiz handover
- The parent match: percentage, cap, payout, paid-state
- Budget limits and warnings, goals and ETA
- PIN lock and unlock, and auto-relock
- Switch kid, sample data load and clean removal, backup shape validation
- Sharing being genuinely silent with no backend configured, and the payload containing only the fields the consent text promises — no contact or identity fields, no sample data
- The advanced tools staying out of sight: absent from every screen, PIN-gated, reachable only from the quiet link in Settings
- Dates resolving to the **local** calendar day rather than UTC
- Persistence across a reload
- HTML-escaping of every piece of user input (names, notes, goal titles)

---

## Optional: collecting data from testers

The app has **no backend by default** — nothing is ever sent anywhere. If you want to watch how friends actually use it, there's a free Google Sheets backend included.

### Setting it up (about five minutes, no credit card)

1. Open **`google-sheet-backend.gs`** and follow the numbered steps at the top: new spreadsheet → Extensions → Apps Script → paste → Deploy as a **Web app** with access set to **Anyone**.
2. Copy the web app URL it gives you.
3. In `index.html`, near the top of the `<script>`, set:
   ```js
   const SYNC_URL = 'https://script.google.com/macros/s/AKfy..../exec';
   const SYNC_OWNER = 'Your name';
   ```
4. Re-upload `index.html` to your host.

Two tabs appear in your spreadsheet the first time someone shares:

- **Kids** — one row per person, updated in place: nickname, age, balance, money in and out, savings rate, goals, badges, streak, lessons done
- **Transactions** — every entry they've logged, refreshed on each sync so there are no duplicates

Apps Script is free with no paid tier, and the quotas (20,000 requests a day) are far beyond what a group of friends will use.

### How the sharing works in the app

While `SYNC_URL` is empty, none of this exists — no card, no settings section, no network calls.

Once it's set, a testing card appears on the dashboard asking permission. It's explicit about what's collected, tells them to ask a parent, and has an equally sized "No thanks". If they accept they pick a **nickname**, and their data syncs a couple of seconds after each change. They can stop at any time in ⚙️ Settings, which also shows when data was last sent and any errors.

### Privacy, honestly

You'd be holding personal data about other people's children, so:

- **Ask their parents first.** Not a formality — it's their call, not the kids'.
- The app collects a **nickname**, age, and every entry **including the notes they type** ("pizza with Sam"). It never asks for a real name, school, address, phone, email or photo, and the payload has no fields for them — there's a test asserting exactly that.
- Sample data is never shared, so demo entries won't pollute your sheet.
- Keep the spreadsheet private. Don't publish it or share the link.
- Delete the data once you've learned what you needed.
- If this becomes a real product in Singapore, the **PDPA** applies and children's data carries extra expectations. Worth proper advice at that point.

## Taking it further

The current build has no backend on purpose — it works the second you host it, and costs nothing. To go further:

1. **Accounts and sync** — Supabase or Firebase is the shortest path. Roughly a day's work to swap the `localStorage` reads and writes for a table, which would let a parent check in from their own phone.
2. **Real approval flows** — parent approves a goal or tops up an allowance from their device, with a notification to the child.
3. **Native app** — wrap it in Capacitor for the App Store and Play Store, which also unlocks a genuine Apple Watch companion.
4. **More lessons** — the content structure is a plain array; adding a lesson is one object with a body and a quiz, and Cent narrates it automatically.
5. **Bank feed** — only worth considering for an older-teen version. It involves an aggregator like Plaid and real compliance work, since financial apps aimed at minors carry genuine regulatory obligations.

---

*Built with Claude. All figures in the app are the child's own — nothing is simulated or demo data.*
