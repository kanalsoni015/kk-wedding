# Kanal & Krishna · Wedding Invitation Website

A single-page, mobile-first invitation site. No build step, no npm, no external libraries.

## Folder structure

```
kk-wedding/
├── index.html          # The whole site: HTML, CSS, JavaScript and all SVG illustrations
├── README.md
└── assets/
    ├── groom.jpg       # Our Story photo (Krishna), 1200px wide
    └── bride.jpg       # Our Story photo (Kanal), 1200px wide
```

## Run locally

Open `index.html` in a browser, or serve the folder:

```
python3 -m http.server 8000
```

Then visit http://localhost:8000 on your computer, or http://<your-computer-IP>:8000 on a phone on the same Wi-Fi.

## Deploy online

Any static host works. Upload the whole folder (keep `assets/` next to `index.html`):

- **Netlify Drop**: drag the folder onto app.netlify.com/drop.
- **GitHub Pages**: push the folder to a repository, then enable Pages on the `main` branch.
- **Vercel / Cloudflare Pages**: import the folder as a static site with no build command.

## Replace the couple photographs

In `index.html`, find `<!-- ======== 5. OUR STORY ======== -->`. Each photo is a `<figure class="frame">` with an `<img>`.

- Easiest: overwrite `assets/groom.jpg` and `assets/bride.jpg` with new files of the same names.
- Or change the `src` and `alt` values. To add a third photo, copy one `<figure class="frame">` block and add a matching dot is generated automatically.

Use portrait photos (4:5 works best). Keep them under about 300 KB each.

## Change event information

Every event is a `<article class="fcard">` inside the `#carousel` element. Edit the text inside `.fcard-body`:
date, time, location, and dress code. The venue address appears in these places:

- Festivities cards 1, 2, 3 and 6 (search for `Shukan-4` and `Shree Hari`)
- Location section (`#location`)
- Google Maps link (the `GET DIRECTIONS` button)
- Calendar event (`DTSTART` and `LOCATION` lines in the `#icsBtn` script block)
- Copy-address text (`const text` in the script)

The countdown target is in the script: `Date.parse('2027-02-12T18:15:00+05:30')`.

## Add background music (optional)

No music file was supplied, so none is included. To add one:

1. Put the file in `assets/`, for example `assets/music.mp3`. Use only music you have rights to.
2. Add `<audio id="music" src="assets/music.mp3" loop preload="none"></audio>` just before `</main>`.
3. Add a button in the hero with a click handler that calls `music.play()` and fades volume up over a few seconds. Browsers only allow audio to start after a tap, so start it from the book-opening click.

## Replace the illustrations

All illustrations are inline SVG. Reusable symbols live in the hidden `<svg>` block at the top of `<body>`:
`rose`, `mari` (marigold), `diya` (brass lamp), `ganesh` (Ganesh-ji emblem), and `bowl`.
Each festivity card has its own scene, marked by a `<svg viewBox="0 0 320 220">`.
To swap a scene for a commissioned painting, replace that `<svg>` with an `<img>` of the same aspect ratio (320 × 220 or taller) and keep `alt` text.

## Calendar file

`Add to Calendar` downloads `Kanal-Krishna-Wedding-Ceremony.ics`, a 6:15 PM IST event on 12 February 2027 with the venue as the location. No end time was given in the brief, so the event has no duration; add one in your calendar app if you want a block of time.

## Accessibility and motion

- Respects the device's "reduce motion" setting: animations and petals are turned off, and all content stays visible.
- Animations on sections that are off screen are paused.
- Every button has a label, and the carousels work with arrow keys.
