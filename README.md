# iOneMicro privacy policy

Two self-contained pages, served by GitHub Pages at
<https://ionemicro.github.io/privacy/>, which is the URL given to Apple and
Google for the five IoneMax mobile apps.

## Why this exists separately from the website

The policy also lives at <https://www.ionemicro.com/privacy-policy.html>, and
that remains the canonical copy. But that host fails roughly a third of TLS
handshakes — measured repeatedly, with two unrelated HTTP clients, at TLS 1.2
and 1.3, with twenty seconds between requests, and at raw socket level, so it
is the server rather than any one client. Apple and Google both fetch the
privacy policy URL during app review, and a failed fetch reads as "privacy
policy not reachable", which is a misleading rejection to debug because the
page loads fine on the next try in a browser.

This mirror exists only to be reachable. It is deliberately one file, with
the stylesheet inlined and every navigation link pointing back at
www.ionemicro.com, so there is nothing here to fall out of date except the
policy text itself.

## Keeping it current

The source of truth is `build-pages.js` in `IoneMicro/iOneMicro-Website`.
**When the policy changes there, regenerate this page too** — the two stores
point here, so a stale copy here is the one users and reviewers actually see.

## What is here

| Page | URL | Used as |
| --- | --- | --- |
| `index.html` | <https://ionemicro.github.io/privacy/> | App Store / Play privacy policy URL |
| `support.html` | <https://ionemicro.github.io/privacy/support.html> | App Store support URL |

The support page is a mirror of `contact.html` for the same reason: Apple
fetches the support URL during review and www.ionemicro.com answered only
2 of 6 times when it was measured. Its contact form is entirely
client-side — it composes a `mailto:` link and posts nothing — so it works
identically here.

`robots.txt` disallows crawling, so these mirrors never compete with
www.ionemicro.com in search.

## The better fix

Both mirrors exist to work around one thing: the ionemicro.com server
drops roughly a third of TLS connections. **That is costing real visitors,
not just app reviewers.** Putting Cloudflare (or any CDN) in front of the
domain would fix the site itself and make these mirrors unnecessary.
