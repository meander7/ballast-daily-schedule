# Ballast

One steady "next thing" to hold onto, while the rest of the day moves around it.

## What's in here
- `index.html` — the whole app (UI + logic, no build step)
- `manifest.json` — makes it installable as a home-screen app
- `sw.js` — lets it load instantly and work offline once installed
- `icon-192.png` / `icon-512.png` — app icons

## Deploy (same pattern as Next Thing)
1. Create a new GitHub repo (or a new folder in an existing pages repo).
2. Upload all 5 files to the repo root.
3. Turn on GitHub Pages for that repo (Settings → Pages → deploy from main branch).
4. Visit the resulting URL (e.g. `yourname.github.io/ballast`) on your phone.
5. In Chrome on Android, tap the menu → **Add to Home screen**. This installs it as a real app icon.
6. Open the installed app once and tap **Turn on notifications** at the bottom.

## How it works
- **Right now card**: shows one tiny next action at a time, pulled from whatever's relevant to the current time block. Tap **Done** to log it and get a new one right away, or **Not yet** to swap it for something else without penalty.
- **Variable nudges**: a new "right now" card and a notification arrive every 8–23 minutes (randomized on purpose, so it doesn't become background noise), automatically skipped if it would land within 12 minutes of one of your fixed medical alarms.
- **Laundry**: tap "Start a load" to begin a real 55-minute wash countdown; when it hits zero, tap "Move to dryer" for a 90-minute dry countdown; "Folded & away" logs a completed load. Goal pips show progress toward 3/day.
- **Dogs**: "Out now" logs the time and resets a random 2–3 hour due window, so the app can tell you when they're due again without needing a fixed schedule.
- **House reset**: a simple daily checklist (dishwasher, living room, litter, bedroom, bathroom) — resets automatically each morning.
- **Weekday / Weekend toggle**: swaps out bus-related and after-school tasks appropriately.

## Known limitation, read this
This app fires notifications reliably while it's **open or recently open** in the browser/installed app. Android is fairly aggressive about pausing background tabs to save battery, so if you don't open Ballast for a long stretch, the variable nudges can go quiet — a plain web app without a backend server can't guarantee true background delivery the way a phone alarm can. That's exactly why the medically fixed items (meds, feeds, vests, bus times) were set up as real phone alarms instead, not inside this app — those will always fire.

Practically: keep Ballast open as a pinned tab or opened periodically during the day (e.g. glance at it whenever a fixed alarm goes off), and it'll do its job well. If background reliability becomes a dealbreaker, the next step up would be a version with a small push-notification server — happy to help with that later if this doesn't feel sturdy enough.
