# Net Zero site starter

A single-page static site in the structure of the E8 entrepreneurs page, styled from the mark:
colour above the horizon, grey below it.

```
netzero-site/
  index.html        everything, no build step
  assets/logo.png   your mark, also used as the favicon
```

## Deploy to GitHub Pages

1. Create a repo and push these two files, keeping `assets/logo.png` where it is.
2. Repo Settings, then Pages, then set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`.
3. Wait about a minute, then load `https://USERNAME.github.io/REPO/`.

Because the repo is not named `USERNAME.github.io`, the site serves from a subpath. Every link in
`index.html` is relative, so it works either way. If you add pages later, keep paths relative
(`assets/...`, not `/assets/...`) or attach a custom domain.

### Custom domain

Add a file named `CNAME` at the root containing just your domain, then point a CNAME record at
`USERNAME.github.io` in your DNS. Tick "Enforce HTTPS" in Settings once the certificate issues.

## The two things static hosting cannot do

**Forms.** GitHub Pages serves files and cannot accept a POST, so there are no forms on the page.
The footer signup is a `mailto:` link and the Apply button is an outbound link. Change
`hello@example.com` to your address and point the Apply link at wherever applications actually live,
such as Tally, Typeform, or an Airtable form.

**Image optimization.** There is no resizing service. If you add photos, pre-generate WebP at two or
three widths and use `srcset` with `loading="lazy"`.

## Customising

All colour and spacing lives in the `:root` block at the top of the `<style>` tag.

| Token | Value | Where it comes from |
|---|---|---|
| `--ink` | `#201818` | the outline in the mark |
| `--green` | `#4FB05C` | upper ribbons |
| `--azure` | `#0E9BDD` | upper ribbons, and the only interactive colour |
| `--ice` | `#E4EBFA` | pale ribbons |
| `--gray` | `#9B9B9B` | everything below the line |

The hero graphic is inline SVG, not an image. One set of ribbon paths is drawn twice: clipped above
the horizon in full colour, then clipped below and pushed through a `saturate(0)` filter with a fade
mask. Change the ribbon colours in `<g id="ribbons">` and both halves update together.

Copy is written to be replaced. The name, the numbers in the stat rail, and the sector chips are all
placeholders standing in for yours.
