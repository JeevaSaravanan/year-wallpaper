# Year Progress Wallpaper

A minimal single-file web page that renders a live year-progress wallpaper sized for iPhone. Every day of the year is shown as a grid cell — past days filled in blue, today glowing in orange, and remaining days in a muted light tone.

Designed to be hosted on **GitHub Pages** and automated via **iPhone Shortcuts** so your lock screen or home screen wallpaper updates itself every day at midnight.

---

## Preview

| Past days | Today | Future days |
|-----------|-------|-------------|
| Solid blue | Orange glow | Muted light |

The wallpaper displays:
- The current **year** and **day number** (e.g. Day 69 of 365)
- A 20-column grid of all 365 / 366 days, colour-coded by status

---

## How it works

`index.html` is a self-contained page. On load, JavaScript reads today's date, calculates the day-of-year, and renders the grid. No build step, no dependencies.

---

## Hosting on GitHub Pages

1. Push this repository to GitHub.
2. Go to **Settings → Pages**.
3. Set source to the `main` branch, root folder (`/`).
4. GitHub will give you a URL like `https://<username>.github.io/<repo>/`.

The page will always show the correct day when visited because the date is calculated at runtime in the browser.

---

## iPhone Automation (Shortcuts)

You need two apps:

- **Shortcuts** — built into iOS
- **Actions** — free on the App Store (adds the *Take Screenshot* and *Save to Photos* actions)

### Build the Shortcut

1. Open **Shortcuts → Automation → New Automation**
2. Choose **Time of Day** → set to **12:00 AM** → **Daily**
3. Turn off **"Ask Before Running"**
4. Add the following actions in order:

| # | Action | Setting |
|---|--------|---------|
| 1 | **Open URLs** | Paste your GitHub Pages URL |
| 2 | **Wait** | 3 seconds (lets the page fully load) |
| 3 | **Take Screenshot** | — |
| 4 | **Save to Photo Album** | Album: `Wallpapers` |
| 5 | **Set Wallpaper** | Lock Screen or Home Screen |

> For step 5, tap the image input in the **Set Wallpaper** action and select the screenshot from the previous step.

The shortcut runs silently every night at midnight, screenshots the page, and sets the fresh wallpaper automatically.

---

## Customisation

All styles are in the `<style>` block inside `index.html`.

| Variable | Where to change |
|----------|----------------|
| Past day colour | `.day-cell.past { background: ... }` |
| Today colour | `.day-cell.today { background: ... }` |
| Future day colour | `.day-cell.future { background: ... }` |
| Wallpaper size | `#wallpaper { width: ...; height: ... }` |
| Background gradient | `.bg-gradient { background: ... }` |

---

## License

[MIT](LICENSE)
