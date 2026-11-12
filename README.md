# Lamplight Pomodoro

A warm, cozy Pomodoro study timer in a single HTML file. It has a library background, a studying cat that reacts to the timer, an alarm, automatic breaks and daily study stats.

Live page: https://claude.ai/artifact/1A81h9nAi97iyDAGg3VRXE
Source: `pomodoro.html` (everything is in this one file, no build step)

## How the timer works

| Phase | Length | What happens next |
|---|---|---|
| Focus | 25 min | A short break starts automatically |
| Short break | 5 min | The next focus session starts automatically |
| Long break | 30 min | After the 6th focus session, then the cycle resets to session 1 |

- A chime plays when each timer ends, and a banner says what has started.
- The six dots show which focus sessions of the cycle are done.
- Controls: **Start / Pause**, **Skip** (jump to the next phase), **Reset** (back to session 1). The **Space** key also starts and pauses.
- The timer uses the clock, not a counter, so it stays accurate if the tab is in the background. Keep the tab open, because a closed tab can't ring.
- Press Start once after loading. Browsers only allow sound after a click.

## The cat

Two embedded photos react to the current phase:

- **Focus:** the studying cat with glasses and a pencil, with a speech bubble.
- **Short break:** the happy cat, hopping around.
- **Long break:** the studying photo dimmed and tilted, with "zZz".
- **Alarm:** the frame jumps.

## Stats

Open **Stats** (top right) to see:

- Pomodoros and study time for today, the last 7 days and all time.
- A 7-day bar chart.
- A 24-hour strip showing when you study most, with a line such as "You focus most around 9 PM to 10 PM".

Only completed focus sessions count, 25 minutes each. Skipped sessions don't. The hour is the hour the session started.

**Where stats are saved**

- Always in your browser (`localStorage`, key `lamp-days`), so clearing site data erases them.
- When the page is open in claude.ai and you're signed in, they're also saved to your account, private to you. Existing local stats are uploaded the first time.
- The Stats panel says which mode is active.

There is no email or Google sign-up. That needs a real server, which this page doesn't have.

## Customising

All of this is in `pomodoro.html`.

- **Timer lengths:** edit `const CFG = {focus:25, short:5, long:30, sessions:6}` near the top of the script (minutes, and sessions per cycle).
- **Cat lines and tips:** edit the `SAYS` (speech bubble) and `HINTS` (text under the timer) lists.
- **Cat photos:** the two `<img id="catA">` and `<img id="catB">` tags hold the photos as base64. Replace their `src` with your own images (a 4:3 crop works best).
- **Background:** the library photo is the `#photo` rule in the CSS. Use the **Your background** button to pick a photo from your device (kept in your browser only). **Library photo** goes back to the default.
- **Colours:** the theme variables are at the top of the CSS. **Switch theme** toggles light and dark.
- **Fonts:** Cormorant Garamond (timer, headings), Nunito (text), Patrick Hand (cat bubble), Josefin Sans (buttons). They load from Google Fonts, with fallbacks if offline.

## Hosting it yourself

Upload `pomodoro.html` to any static host (GitHub Pages, Netlify, Vercel) or open it directly in a browser. Outside claude.ai:

- Stats are saved on that device only (`localStorage`).
- The account sync is skipped automatically.
- Everything else works the same.

## Known limits

- The background photo is small (736 px wide), so it looks soft on big screens.
- The cat is a photo, so there is no sleeping pose for the long break. A third photo would fix that.
- An alarm can't ring if the tab or browser is closed.

## Ideas for later

Ambient sounds (rain, lo-fi), a task list, a daily goal, an export button for stats, and real email or Google login using a service like Firebase or Supabase.
