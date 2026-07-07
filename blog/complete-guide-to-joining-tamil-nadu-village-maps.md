# The Complete Guide to Joining Tamil Nadu Village Survey Maps

> A full walk-through of **[Village Map Joiner](https://villagemapjoiner.in)** — the
> browser-based tool that stitches individual Tamil Nadu cadastral / FMB village
> survey sheets into one continuous, print-ready map. Every feature, every page,
> and both ways to use it, documented in one place.

**Live site:** **https://villagemapjoiner.in** · **Editor:** https://villagemapjoiner.in/editor · **Done-for-you orders:** https://villagemapjoiner.in/request

---

## The problem this solves

When you download a village map from the Tamil Nadu **Commissionerate of Survey
and Settlement** (the [`tnlandsurvey`](https://villagemapjoiner.in/blog/how-to-download-fmb-sketch-and-village-map-tamil-nadu)
portal), you rarely get one clean picture of your land. A village is split across
many **survey sheets**, and your survey number often sits on the seam between two
or three of them. Each sheet arrives as a separate PDF with a thick black frame,
a title block, and a white margin.

These sheets **don't overlap** — they're **adjacent**. They meet along shared
boundary lines like jigsaw pieces. So there is no automatic "panorama stitch"
that can merge them for you; someone has to make the *"this edge lines up with
that edge"* call. Village Map Joiner removes every bit of friction around that
one human decision:

- It converts each PDF page into a **high-resolution image**.
- It **auto-crops the black frame** so the map content reaches the edge.
- It turns the **white background transparent** so overlapping margins don't hide
  a neighbour's roads and plots.
- It gives you **snapping, nudging and rotation** so the seams line up cleanly.
- It **exports one continuous map** as a high-resolution PNG or a print-ready PDF.

**Read the deep-dive:** [Understanding adjacent survey sheets](https://villagemapjoiner.in/blog/understanding-adjacent-survey-sheets)
· [Step-by-step: join survey sheets](https://villagemapjoiner.in/blog/step-by-step-join-survey-sheets)

---

## Two ways to use it

### 1. Self-service editor — free to build, ₹99 to export

Open **[villagemapjoiner.in/editor](https://villagemapjoiner.in/editor)**, drop in
your PDFs, and arrange them yourself. Uploading, arranging and previewing are
**completely free**. You only pay **₹99 (one-time, per export)** when you download
the final full-resolution file. Checkout runs through **Razorpay**.

> 🔒 **100% private.** The editor runs entirely in your browser. There is no
> backend and no upload — your land records never leave your device.

### 2. Done-for-you service — we do it for you

Don't want to touch the government website at all? Use the
**[request form](https://villagemapjoiner.in/request)**. Enter your District,
Taluk, Village and Survey Number, and the team sources, downloads and stitches
the maps for you, then delivers over WhatsApp.

| Service | Price | Delivery |
| --- | --- | --- |
| **Self-service export** | ₹99 one-time | Instant download |
| **[FMB sketch](https://villagemapjoiner.in/blog/fmb-sketch-service-order-online-tamil-nadu)** (done-for-you) | ₹99 per sketch | Sent on WhatsApp |
| **[Combined village map](https://villagemapjoiner.in/blog/combined-village-map-service-tamil-nadu)** (done-for-you) | ₹1,699 flat | Print-ready PDF in 1–4 hours |

Prices are fixed **server-side** so the amount can't be tampered with from the
browser.

---

## Feature audit — the editor, in full

Everything below lives inside **[/editor](https://villagemapjoiner.in/editor)**.

### Import & rendering
- **PDF upload** — every page of every PDF becomes a separate piece on the canvas.
- **High-resolution render** — pages are rasterised at roughly **2400px (Standard)**
  or **3800px (High)** on the long edge, with a low-resolution warning if a source
  scan is too small to print cleanly.

### Automatic clean-up
- **Auto frame-crop** — detects the thin black border around a survey sheet and
  crops just inside it, **non-destructively** (falls back to the full image when no
  frame is found).
- **Auto-arrange** — reads the sheet number from each filename (`…S1`, `…S2`, `…S3`,
  `…S4`) and tiles the pieces into a grid row-major (`S1` top-left, `S2` top-right,
  `S3` bottom-left, `S4` bottom-right) with a small seam overlap. One click, then
  fine-tune.
- **White-to-transparent** — near-white background becomes transparent per piece,
  with a threshold slider, so a top sheet's margin never occludes the map beneath it.

### Alignment & fine control
- **Zoomable, pannable canvas** — mouse-wheel and pinch zoom, touch drag.
- **Per-piece tools** — drag, rotate/scale handles, manual crop, mask out
  legends/title blocks, arrow-key nudge (**Shift = 10px**), layer order, lock, and
  an opacity "peek" to see what's underneath.
- **Snapping** — bounding-box edge snap with guide lines, plus **15° rotation snap**.
  Toggleable.

### Export
- **Single PNG** cropped to content, at a pixel ratio chosen to preserve the most
  detailed placed piece.
- **Print-ready PDF** fitted to **A0–A4** (or the raw image aspect) with a live
  print-DPI estimate. Large exports are encoded to a Blob and clamped to a safe
  canvas size so they download reliably instead of silently failing.

Heavy pixel work (frame detection, white-keying, masking) runs in a **Web Worker**
(OffscreenCanvas), so the interface stays responsive — even on a phone.

**Tech under the hood:** Next.js (App Router) · TypeScript · Tailwind CSS ·
`react-konva` / `konva` · `pdfjs-dist` · `jspdf` · `zustand`.

---

## Who it's for

- **Boundary disputes** — see adjacent plots as one picture instead of loose sheets.
- **Property management** — a unified view of your land without repeated revenue-office trips.
- **Legal & banking documentation** — a print-ready combined map for lawyers, banks and registration offices.
- **Agricultural planning** — visualise farmland spread across multiple survey numbers.
- **Construction & development** — understand the full layout before you build.

---

## Every page of the site

This is the full map of **[villagemapjoiner.in](https://villagemapjoiner.in)** so
you can jump straight to what you need.

### Core tools
- **[Home](https://villagemapjoiner.in)** — bilingual (English / தமிழ்) overview with a live snapping demo.
- **[Editor](https://villagemapjoiner.in/editor)** — the browser-based map joiner.
- **[Request a done-for-you map](https://villagemapjoiner.in/request)** — order form for the managed service.
- **[Reviews](https://villagemapjoiner.in/reviews)** — what customers say.

### Learn — the blog
Practical guides for anyone working with Tamil Nadu land records:

- [Tamil Nadu Village Map Joiner — overview](https://villagemapjoiner.in/blog/tamil-nadu-village-map-joiner)
- [How to download an FMB sketch & village map in Tamil Nadu](https://villagemapjoiner.in/blog/how-to-download-fmb-sketch-and-village-map-tamil-nadu)
- [Join village maps from Survey & Settlement](https://villagemapjoiner.in/blog/join-village-maps-from-survey-and-settlement)
- [Step-by-step: join survey sheets](https://villagemapjoiner.in/blog/step-by-step-join-survey-sheets)
- [Understanding adjacent survey sheets](https://villagemapjoiner.in/blog/understanding-adjacent-survey-sheets)
- [Tamil Nadu land records — a glossary](https://villagemapjoiner.in/blog/tamil-nadu-land-records-glossary)
- [Download a digital village map in Tamil Nadu](https://villagemapjoiner.in/blog/download-digital-village-map-tamil-nadu)
- [A-Register vs Patta / Chitta](https://villagemapjoiner.in/blog/a-register-vs-patta-chitta)
- [Patta transfer online in Tamil Nadu](https://villagemapjoiner.in/blog/patta-transfer-online-tamil-nadu)
- [How to read an FMB sketch](https://villagemapjoiner.in/blog/how-to-read-fmb-sketch)
- [How to read the G-line in a survey](https://villagemapjoiner.in/blog/how-to-read-g-line-in-survey)
- [What is Natham land in Tamil Nadu?](https://villagemapjoiner.in/blog/what-is-natham-land-tamil-nadu)
- [A short history of land survey in Tamil Nadu](https://villagemapjoiner.in/blog/history-of-land-survey-tamil-nadu)
- [Correlation statement: old vs new survey number](https://villagemapjoiner.in/blog/correlation-statement-old-new-survey-number)
- [Licensed surveyors in Tamil Nadu](https://villagemapjoiner.in/blog/licensed-surveyors-tamil-nadu)
- [Order an FMB sketch online](https://villagemapjoiner.in/blog/fmb-sketch-service-order-online-tamil-nadu)
- [Combined village map service](https://villagemapjoiner.in/blog/combined-village-map-service-tamil-nadu)
- [Land records: online vs an office visit](https://villagemapjoiner.in/blog/tamil-nadu-land-records-online-vs-office-visit)

### Glossary
Plain-language definitions of the terms on your documents —
**[full glossary](https://villagemapjoiner.in/glossary)**. A few of the 27 entries:
[FMB](https://villagemapjoiner.in/glossary/fmb) ·
[G-line](https://villagemapjoiner.in/glossary/g-line) ·
[Patta](https://villagemapjoiner.in/glossary/patta) ·
[Chitta](https://villagemapjoiner.in/glossary/chitta) ·
[A-Register](https://villagemapjoiner.in/glossary/a-register) ·
[Survey number](https://villagemapjoiner.in/glossary/survey-number) ·
[Subdivision number](https://villagemapjoiner.in/glossary/subdivision-number) ·
[Nanjai](https://villagemapjoiner.in/glossary/nanjai) ·
[Punjai](https://villagemapjoiner.in/glossary/punjai) ·
[Natham](https://villagemapjoiner.in/glossary/natham) ·
[Poramboke](https://villagemapjoiner.in/glossary/poramboke)

### Order by district
The done-for-you service covers all 38 Tamil Nadu districts. Popular ones:
[Chennai](https://villagemapjoiner.in/request/chennai) ·
[Coimbatore](https://villagemapjoiner.in/request/coimbatore) ·
[Madurai](https://villagemapjoiner.in/request/madurai) ·
[Salem](https://villagemapjoiner.in/request/salem) ·
[Tiruchirappalli](https://villagemapjoiner.in/request/tiruchirappalli) ·
[Erode](https://villagemapjoiner.in/request/erode) ·
[Tirunelveli](https://villagemapjoiner.in/request/tirunelveli) ·
[Viluppuram](https://villagemapjoiner.in/request/viluppuram) —
or start at the **[district index](https://villagemapjoiner.in/request)** and drill
down to your taluk and village.

### Legal
- [Privacy policy](https://villagemapjoiner.in/privacy)
- [Terms of service](https://villagemapjoiner.in/terms)

---

## Frequently asked questions

**Are my land records uploaded anywhere?**
No. The editor at [/editor](https://villagemapjoiner.in/editor) does all its work
in your browser. Nothing is sent to a server — your files never leave your device.
(The optional done-for-you order service is the only server-backed part.)

**What does it cost?**
Building and previewing your map is free. A single export costs **₹99**. The
done-for-you FMB sketch is **₹99**; a fully managed combined village map is
**₹1,699**.

**Do I need to install anything?**
No. It runs in any modern browser on desktop or mobile.

**Why can't it stitch the maps automatically?**
Because the sheets are adjacent, not overlapping — there's no shared image region
to match on. You make the edge-alignment call; the tool removes the frame, keys out
the white, and snaps the seams so it's quick. See
[Understanding adjacent survey sheets](https://villagemapjoiner.in/blog/understanding-adjacent-survey-sheets).

**Which maps does it work with?**
Tamil Nadu cadastral / FMB-style village survey sheets from the Commissionerate of
Survey and Settlement — see
[how to download them](https://villagemapjoiner.in/blog/how-to-download-fmb-sketch-and-village-map-tamil-nadu).

---

## Start here

- 🗺️ **Join your maps now:** [villagemapjoiner.in/editor](https://villagemapjoiner.in/editor)
- 🙌 **Let us do it for you:** [villagemapjoiner.in/request](https://villagemapjoiner.in/request)
- 📚 **Learn the records first:** [villagemapjoiner.in/blog](https://villagemapjoiner.in/blog)

---

*Village Map Joiner is built and maintained by **Ajay Vigneshwar GB** under
[Ajay's Apps](https://github.com/IndexerNow). Built with focus. Shipped from Tamil
Nadu, India.*
