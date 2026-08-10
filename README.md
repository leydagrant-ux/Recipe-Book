# Recipe Saver — free, serverless version

One file. No server, no backend, no monthly bill. It runs entirely in your
browser and calls Supadata and Claude directly.

Paste a link to a cooking video → it pulls the spoken transcript and caption,
has Claude write up the recipe, and saves it with a picture.

## Put it online (free, ~2 minutes)

You need it on a real web address so it works on your phone anywhere, on cell
data, with your computer off.

**Easiest — Netlify Drop:**

1. Go to <https://app.netlify.com/drop>
2. Drag the **`recipe-saver-web` folder** onto the page
3. You get a URL like `https://something-random-123.netlify.app` — that's your app

Make a free account when it offers, otherwise the site expires. You can rename
it to something memorable in Site settings → Change site name.

**Alternatives**, all free and all fine: [Cloudflare Pages](https://pages.cloudflare.com)
(drag and drop, needs an account) or GitHub Pages (needs a repo pushed).

## First run

Open your new URL and paste your two API keys:

- **Supadata** — <https://dash.supadata.ai/organizations/api-key>
- **Anthropic** — <https://console.anthropic.com/settings/keys>

They're stored only in your own browser and are sent straight to each service.
They are never uploaded to the site host or anywhere else — the page has no
server to send them to.

Then **Share → Add to Home Screen** in Safari. It launches full-screen.

### If it keeps asking for your keys

On iOS, a Home Screen web app has **its own storage, separate from Safari**.
Keys typed into Safari do not appear in the Home Screen app, and vice versa. So
does Private Browsing, which wipes storage the moment you close the tab.

The permanent fix is a **setup link** — a URL with your keys built into it:

1. In the app (wherever the keys are already working), tap **⚙ → Copy my setup link**
2. Send it to your phone and open it
3. **Share → Add to Home Screen**

That icon carries its own keys, so it can restore them itself even if storage
is ever cleared. **Treat the link exactly like the keys** — anyone who opens it
is using your API credit. Don't post it anywhere.

## Saving from the Instagram share sheet

Because there's no server to POST to, the Shortcut opens the app with the link
attached instead — the save then runs automatically.

1. **Shortcuts** → **+** → name it `Save Recipe`
2. Add **Get URLs from Input**
3. Add **URL Encode** (encode the URLs variable)
4. Add **Text**, set to: `https://YOUR-SITE.netlify.app/#add=` followed by the
   encoded variable from step 3
5. Add **Open URLs**, passing that text
6. Tap ⓘ → **Show in Share Sheet** → accept **URLs**

From a reel: **Share → Save Recipe**. The app opens and starts saving.

## Your recipes live in this browser

This is the tradeoff for having no server, and it's the same way most simple
personal apps work.

**Closing the app, closing the browser, or restarting the device does not
delete anything.** The recipes are a database on the device, not something held
open in a tab.

What can lose them:

- Recipes are on **this device, in this browser**. A different phone has a
  different library.
- Clearing Safari's website data for the site deletes them.
- iOS Safari clears a site's storage after **7 days without visiting it**.
  Adding the app to your Home Screen exempts it from that rule, and the app
  also asks the browser to mark its storage permanent on every launch.

**⚙ (settings)** shows where you stand: how many recipes are saved, how much
space they use, and whether storage is marked permanent.

So use the backup. **⚙ → Back up my recipes to a file** writes a single JSON
file containing everything, pictures included. **Restore from a backup file**
reads it back, and skips anything already saved — so restoring twice is safe.

Back up after you've added a batch you'd hate to lose, and keep the file in
iCloud or Google Drive.

## What it costs

Hosting is free forever. You pay only the two APIs:

- **Supadata** — free plan is 100 credits/month. A video with existing captions
  costs 1 credit; if it has to generate the transcript, 2 credits per minute.
- **Anthropic** — roughly a cent per recipe, from prepaid credit.

## Supported links

Instagram, TikTok, YouTube, X, and Facebook — all handled by the same
Supadata endpoint.

## Notes

- A save takes 20–60 seconds, nearly all of it waiting on transcription.
- Pictures come from the video's cover frame and are stored as real image data,
  so they survive the original being deleted. If a platform blocks the download,
  the app falls back to the link — and **Use my own photo** on any recipe lets
  you attach a shot of the finished dish from your camera roll.
- Saving the same link twice returns what you already have instead of spending
  credits again.
