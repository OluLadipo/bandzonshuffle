[README (3).md](https://github.com/user-attachments/files/34595922/README.3.md)
# Bandz on Shuffle

A 2009-nostalgia rhythm game. Silly Bandz drop onto an iPod-style click wheel, and every catch plays the next note of the song.

**Play it:** https://bandzonshuffle.netlify.app/

## How it plays

- Spin the click wheel to line up with falling bandz and catch them
- Each catch plays the track, so a clean run sounds like the full song
- Tracks: Recess, Bus Ride Home, Top 8, Credits (plus a No Sound mode)
- The background color shifts per track, styled like a 2000s iPod billboard

## Built with

- A single `index.html` file: HTML, CSS and vanilla JavaScript, no build step
- Web Audio API for all music and sound, generated live in the browser
- `localStorage` for saving progress and scores on your device
- Google Fonts (Archivo Black, Figtree)

## Behind the scenes

A few pieces of how it works. The full source is in `index.html` if you want to dig.

**Reading the click wheel.** Your finger's position gets turned into an angle around the center of the wheel, the same way a real iPod tracked your thumb.

```js
function angleOf(e){
  var r = wheel.getBoundingClientRect();
  return Math.atan2(e.clientY - (r.top + r.height/2),
                    e.clientX - (r.left + r.width/2)) * 180 / Math.PI;
}
```

**Perfect, Nice or Miss.** When a band lands, the game checks how far your marker is from it on the wheel. Tighter means more points.

```js
var d = angDiff(n.a, markerA), sp = span();
if (d <= sp*0.45)   hit(n, 100, "PERFECT");
else if (d <= sp+2) hit(n, 50, "NICE");
else                fb("MISS");
```

**Music with zero audio files.** Every note, kick and clap is built live with the Web Audio API. Notes start as MIDI numbers and get converted to pitch:

```js
function freq(m){ return 440 * Math.pow(2, (m - 69) / 12); }
```

A kick drum is just a sine wave that drops fast from 160Hz to 44Hz.

**Your bag of bandz.** Collected bandz, best scores and your color pick are saved right in the browser, so they're still there next time.

## Run it locally

Download `index.html` and open it in any modern browser. That's it.

## Deploy

Hosted on Netlify. Connecting this repo to the Netlify project redeploys the site on every push to `main`.

## Author

Olu Ladipo
[Portfolio](https://oluladportfolio.netlify.app) · [LinkedIn](https://www.linkedin.com/in/oluladipoinsights/)
