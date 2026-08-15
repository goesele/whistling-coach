# Pointing whistly.goesele.org here

The site is served by GitHub Pages at

    https://goesele.github.io/whistly-site/

To move it to `whistly.goesele.org`, at the DNS provider for `goesele.org`:

1. **Delete** the existing `A` record for the `whistly` host. It currently points
   at `217.160.233.222`, which serves the hosting provider's default page. A
   `CNAME` cannot coexist with other records for the same name, so this is not
   optional.
2. **Add** a `CNAME` record:

   | Host | Type | Value |
   |---|---|---|
   | `whistly` | `CNAME` | `goesele.github.io.` |

3. Once it resolves, set the custom domain in **Settings → Pages** on this repo.
   GitHub then issues a free Let's Encrypt certificate automatically, usually
   within the hour — after which **Enforce HTTPS** can be ticked.

## Why the custom domain is NOT configured yet

Setting it writes a `CNAME` file, and GitHub then **redirects its own
`github.io` URL to the custom domain**. With DNS still pointing elsewhere that
leaves no working URL at all — which is exactly what happened here once. Set the
custom domain *after* the DNS record resolves, not before.

Check with:

    dig +short whistly.goesele.org        # want: goesele.github.io + GitHub IPs
