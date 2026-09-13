# Deploying kebinternational.com

Static site, no build step. Upload these files to the **web root**:

```
index.html
privacy.html
privacy-ar.html
og-image.png
robots.txt
sitemap.xml
```

`og-image.png` must sit at the root — the pages reference it as `/og-image.png`.
If it ends up in a subfolder, link previews on WhatsApp, LinkedIn and Facebook break.

## Before you go live

Two placeholders need real values. Both are single-line edits.

| What | File / line | Until you change it |
|---|---|---|
| Formspree form ID | `index.html` — `action="https://formspree.io/f/YOUR_FORM_ID"` | The contact form does not deliver. The visitor sees the fallback message asking them to email `admin@kebinternational.com`, so nothing looks broken — but the lead never reaches you. |
| GA4 measurement ID | `index.html` — `var GA_ID = "G-XXXXXXXXXX";` | No analytics. The site and the consent banner work normally; the loader deliberately does nothing while the ID is a placeholder, so no requests go out to a property that doesn't exist. |

## If the domain is not kebinternational.com

These are absolute and assume that domain. Search and replace across all files:

- `<link rel="canonical">` on all three pages
- `og:url` on all three pages
- `hreflang` alternates on `privacy.html` and `privacy-ar.html`
- Every URL in `sitemap.xml`, and the `Sitemap:` line in `robots.txt`

## After uploading

1. Open the site and toggle EN / العربية.
2. Submit the contact form with a real address and confirm the email arrives.
3. Accept the cookie banner, then check GA4 Realtime for your visit.
4. Paste the URL into the [LinkedIn Post Inspector](https://www.linkedin.com/post-inspector/) to confirm the preview card.
5. Submit `https://kebinternational.com/sitemap.xml` in Google Search Console.

## Note on the Arabic policy

`privacy-ar.html` is a convenience translation. The page itself states that the
English version is authoritative. Have a native Arabic speaker — ideally one
comfortable with legal wording — read it before you rely on it.
