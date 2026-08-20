# Banner source

`banner.html` / `banner-dark.html` render the header image at the top of the
profile README. Same design language as danielgtmn.com: IBM Plex Mono, the
warm gray-green paper, and the status lamps that lead every row on the site.

Regenerate after editing:

```bash
cd assets/src
python3 -m http.server 8971 &
for v in banner:banner-light banner-dark:banner-dark; do
  "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
    --headless --disable-gpu --hide-scrollbars \
    --force-device-scale-factor=2 --window-size=880,310 \
    --screenshot="../${v##*:}.png" "http://localhost:8971/${v%%:*}.html"
done
kill %1
```

Fonts are copied from `my_websites/apps/portfolio/public/fonts`. Chrome must
load them over http — `file://` will not apply the `@font-face` rules.
