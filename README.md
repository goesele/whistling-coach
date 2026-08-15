# whistling-coach

The public site for **Whistling Coach**, an iPhone and iPad app that teaches you to whistle in
tune. Two pages: a landing/support page, and the privacy policy that App Store Connect
requires a public URL for.

Live at <https://goesele.github.io/whistling-coach/>.

Deliberately plain: static HTML and one stylesheet, no build step, no JavaScript, no
trackers. The privacy policy says the app collects nothing, and a site that quietly
loaded analytics would make that awkward to say.

## Why there is no custom domain

A `whistly.goesele.org` subdomain was set up and then dropped. The registrar's HTTP
forward worked and preserved paths, but the host had no TLS certificate for the
subdomain, so `https://` failed at the handshake — and browsers that try HTTPS first
landed nowhere useful.

GitHub Pages serves this over HTTPS with its own certificate, for nothing, so the
`github.io` URL is not a compromise. If a custom domain is ever wanted, point DNS at
`goesele.github.io.` **first** and set the custom domain in Settings → Pages only once it
resolves — setting it first makes GitHub redirect its own URL to a domain that is not
ready, which leaves no working URL at all.

The app itself lives in a separate, private repository.
