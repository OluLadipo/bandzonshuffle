Bandz on Shuffle

Your Nano is back on. Silly Bandz are falling onto the click wheel. Catch one and the song plays. Miss one and you hear it.

🎧 Play it now
If you were there in 2009

You remember trading bandz at the lunch table. Spinning that wheel on the bus. Fighting over who made your Top 8.

So the tracks are named after all of it: Recess, Bus Ride Home, Top 8 and Credits. Each one paints the whole screen a new neon color, straight off an old iPod billboard.

What everyone's chasing
PERFECT catches. Close enough only gets you a NICE.
Combos. String catches together and your points climb to 4x.
Crown mode. Fill the glow meter and everything doubles.
A full bag. Every band you catch gets saved. Your bag only fills if you play.

Somebody you know already has a better score than you. Just saying.

Behind the scenes

A few crumbs from the code. The rest stays in the vault.

Reading the click wheel. Your finger's position turns into an angle around the center of the wheel, the same way a real iPod tracked your thumb.

js
function angleOf(e){
  var r = wheel.getBoundingClientRect();
  return Math.atan2(e.clientY - (r.top + r.height/2),
                    e.clientX - (r.left + r.width/2)) * 180 / Math.PI;
}

Perfect, Nice or Miss. When a band lands, the game measures how far your marker is from it. Tighter means more points.

js
var d = angDiff(n.a, markerA), sp = span();
if (d <= sp*0.45)   hit(n, 100, "PERFECT");
else if (d <= sp+2) hit(n, 50, "NICE");
else                fb("MISS");

Music with zero audio files. Every note, kick and clap is built live in your browser with the Web Audio API. Notes start as MIDI numbers and get turned into pitch:

js
function freq(m){ return 440 * Math.pow(2, (m - 69) / 12); }

The kick drum? A sine wave that drops from 160Hz to 44Hz in about a tenth of a second.

How the songs are written, how the bandz fall in time, how Crown mode works... you'll have to play to figure that out.

Built with

One HTML file. Vanilla JavaScript, the Web Audio API, and a canvas. No frameworks, no audio files, no build step.

Made by

Olu Ladipo Portfolio · LinkedIn

🎧 Your bandz are waiting
