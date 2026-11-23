# AI Agency Studio — Starter PWA

This is a responsive, installable Progressive Web App starter for creating live-streaming agency promotional posters and separate emblem PNGs.

## Included in this starter
- Responsive website UI for mobile and desktop
- Installable PWA manifest and service worker for offline shell caching
- Agency name, agency ID and platform label fields
- Optional agency screenshot upload as a visual reference (manual verification/input is required in this starter)
- Model photo upload OR a locally rendered illustrative placeholder
- Host type, theme, mood, symbol and outfit choices
- Canvas-generated poster PNG and separate emblem PNG

## Important limitations of this starter
- It does not yet perform OCR on profile screenshots. Users enter and verify the agency name and ID manually.
- The “AI-style model” choice currently draws an illustrative placeholder; it is not a generative AI image. Connect a secure image-generation backend to provide real AI model generation.
- No accounts, cloud storage, payments, admin dashboard or server-side generation are included.
- The generated artwork is a functional first-pass layout. Typography and exact text placement can be refined in the next iteration.

## Run locally
Serve this folder over HTTPS or localhost (service workers require a secure context). For example:

```bash
python -m http.server 8080
```

Then open `http://localhost:8080`.

## Android
The PWA can be installed from a supported Android browser using “Install app” / “Add to Home screen”. A signed APK/AAB is not included; that requires a packaging step (for example, a Trusted Web Activity or Capacitor wrapper), app icons, signing credentials and release testing.

## Production architecture recommended
- Frontend: this PWA, later wrapped with Capacitor for Android
- Backend: authenticated API with rate limits
- OCR: server-side image text extraction with user confirmation before saving ID/name
- Image generation: secure server-side provider integration; never expose API keys in browser code
- Storage: private object storage with explicit retention/deletion controls
- Export: deterministic text/layout compositing after image generation so agency name and ID remain accurate
