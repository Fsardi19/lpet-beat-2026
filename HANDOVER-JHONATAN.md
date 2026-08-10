# BEAT 2026/27 — what was done, and where it lives

**Branch:** `jhonatan/wof-and-form` · **Date:** 10 Aug 2026 · **By:** Jhonatan Benavides

This branch answers Felipe's email of 9 Aug, *"BEAT — página nueva en GitHub, tres
cosas para montarla"*. It is **not merged and not deployed** — it is here so you can
see the work and decide.

Working copy lives at **github.com/jbenavides-dotcom/Beat2.0**, published at
**https://beat.lapalmayeltucan.com** (CNAME to `jbenavides-dotcom.github.io`; the
`*` wildcard on the domain still points everything else to Shopify and was not
touched).

---

## 1. The Supabase migration — done

**The file you pointed at never existed.** `SUPABASE_SETUP.md` documents
`referencias/proyectos/landing-beat-2026/migrations/003_new_policies_2026_27.sql`,
but that path is empty in both repos and on the remote — only `001` and `002` are
there. Confirmed against the GitHub API, not just locally.

It was written and run. `sponsor_status` and `consent_content` now exist, and all
20 fields the form sends were verified against the table. **A real submission
inserts with HTTP 201**, so the page has stopped losing applications.

Two things worth knowing:

- RLS is doing its job: an anonymous visitor gets `[]` from the table.
- The `CHECK` constraints are live — a short pitch is rejected at the database, not
  just in the browser.

⚠️ There are **test rows to delete**: emails starting `test+claude`, `test+upload`
and `t@t.co`, plus two left over from May.

## 2. The route from the site — ready to review, not published

Built in an **unpublished Shopify theme** called `diseños antes de lanzar`
(id `187466907951`), a copy of the live one. Production is untouched.

Preview: `https://lapalmayeltucan.com/pages/green_coffee-beat?preview_theme_id=187466907951`

- The **"Let's Talk" form is gone** from the BEAT page — it was the green-coffee
  lead form with the seven categories, a different funnel.
- In its place, a short block announcing the twenty boxes with an
  **"Apply for a BEAT box"** button, `target="_blank"` and `rel="noopener"`.
- The other four sections and all their copy are exactly as they were.
- The nav still points at the Shopify page, not at the subdomain. One way in.

## 3. The Wall of Fame — fixed, and it was worse than reported

You reported 11 wrong photos. There were more problems than that, and they were
not all missing photos: **some were crossed between people.**

- **Sam Neely** was showing a cupping scene that the mural credits to
  **Cole Torode 2020**. Both now have their own.
- **Cole Torode 2019** was a podium shot of two people.
- **Dylan Siemens 2019** was reusing his 2017 photo.
- **Sebastián Villamizar** had a wide shot of the competition floor with a crowd,
  not a portrait.
- **Dane Oliver** had a landscape photograph of Hong Kong.

All 21 portraits now come from **`HLP&ET Wall of Fame2.ai`**, the official artwork
Elisa sent, which carries the source images embedded at full resolution — including
the four that could not be found anywhere else (Dane Oliver, Lise Marie Rømo, Mark
Michaelson, Francesco Masciullo).

Two cards keep another source because the artwork has no photo for them:
**T. Ben Fischer** and **Elika Liftee**. **Fanie Botes** and **Luhle Mnyanda** keep
individual portraits, which beat the group shot the artwork uses for both.

### 🔴 One thing for you to check

**The Dane Oliver entry has a data problem, independent of the photo.** The mural
says *Denmark Brewers Cup Champion, 2016*; public sources place him at the
**2015 Australian** Brewers Cup, using La Cabra coffee. It looks like the
competitor's country got swapped for the roaster's. Worth confirming before this
goes any further.

And a smaller one: the artwork has **no 2024 block**, but the site has a Gray
Kauffman card for 2024. Is that appearance real?

### Photo permissions

None of these competitors has been asked. A draft email is ready to send, one per
person: an apology for the wrong photo, a request for a portrait they like plus
permission to publish it with credit, and an easy way to say no. As you said, it
also reopens contact with people who put our coffee on their stage.

---

## Beyond what was asked

**The Wall of Fame is a timeline again.** The grid from `92be8e6` flattened the
chronology, and the artwork is literally titled *A LIVING TIMELINE*. It now uses
the same interactive timeline as **Our Story** on Shopify — centre line that fills
on scroll, a dot per competitor, alternating sides — in the gold palette, with
Jooyeon Jeon featured the way the mural features her: larger portrait, rose ring,
World Champion tag.

**The application video can now be a file, not only a link.**

- Pasting a link is **verified as you type** against YouTube's and Vimeo's oEmbed
  endpoints. A private or mistyped video is caught before submitting, instead of
  surfacing when a juror cannot open it. Drive links cannot be checked from the
  browser, so those pass with a warning rather than a false green light.
- Uploading sends the file straight to Supabase Storage, private bucket, 200 MB
  cap, with a progress bar. Files are named
  `2026-08-10_lise-marie-romo_barista_a1b2.mp4` so the bucket stays readable.
- A new `video_source` column records which route was used.

**The national-appearances question was one free-text box.** It now asks for a
number and then shows that many boxes to name each championship. Same information,
far easier to fill, and it stops arriving as prose nobody can filter.

### Still open

**There is nowhere to review applications.** Not the linked ones and not the
uploaded ones. Today it means opening Supabase, copying a URL and generating a
signed link by hand, per applicant. With twenty places and an open call that will
not hold. This is the same gap as the May request to "upload the videos" — it was
never a place to watch them.

Also: the two free-text fields you use to filter — how many national appearances,
and which championship — are prose. The first one is now structured; the target
competition still is not, so checking the August 2026 to July 2027 window stays
manual.
