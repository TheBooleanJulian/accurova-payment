# accurova-payment

Client-facing payment details page for Accurova: payment schedule and PayNow details. Replaces the Pixieset share gallery that previously held the PayNow QR.

A single static page. No build step and no dependencies apart from Google Fonts. Styled with Julian Unified UI; `brand/tokens.css` is managed by `tbjsync`, so don't edit it by hand.

## Tabs

- **Business** (default): 50/50 payment schedule, PayNow QR, and PayNow to UEN `201628225CIUI`.
- **Personal**: personal PayNow QR and mobile number. Link to it directly with `#personal`.

The "After you pay" section (WhatsApp / email confirmation) shows on both tabs.

## Files

| Path | What |
|---|---|
| `index.html` | The page: markup, styles and script in one file |
| `brand/tokens.css` | Unified UI design tokens (synced from `thebooleanjulian-branding`) |
| `assets/paynow-business.jpg` | Bank-generated PayNow QR image, served by **Save QR** |
| `assets/paynow-business-qr.jpg` | The QR cropped from it, shown on the page |
| `assets/paynow-personal.png` | Personal PayNow QR. **Not added yet.** The QR card stays hidden until this file exists |
| `assets/accurova-mark.png` | Logo mark and favicon |

To add the personal QR, drop the image at `assets/paynow-personal.png`. If it's a different format, update both `src` and `href` in the Personal tab of `index.html`.

## Save QR

On iPhone/iPad, **Save QR** opens the share sheet so "Save Image" puts the QR in Photos, where banking apps can import it. A plain download would go to Files. Every other device downloads the image.

## Run locally

```sh
python -m http.server 8000
```

Then open http://localhost:8000. Opening `index.html` straight from disk also works, but copy-to-clipboard falls back to the legacy copy command there.

## Deploy

Not deployed yet. The intended target is Cloudflare Workers static assets, like the other Accurova static sites; the domain is still to be decided.
