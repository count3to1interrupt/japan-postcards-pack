# Reproducibility and context: what travels with this pack, and what doesn't

This pack is a travel report as much as a kit. A human judged the generated
images one small batch at a time — roughly forty images over the QA process —
and the pack's quality comes from that loop as much as from its documents.
This note separates what a reader can reproduce from the documents alone
from what depended on that context, so nobody mistakes the report for a
one-click recipe.

## Layer 1 — Reproducible from the text alone

These parts are fully contained in the pack, specified completely enough to execute as written:

- The **prompt template** in the generation guide: the fixed wording that
  makes an image read as an unpolished smartphone snapshot (tilt, crop,
  flat light, no color grading) rather than a tourist poster.
- The **place cards' facts** — the details where the real place differs
  from an AI's average image of it. Kinkaku-ji's ground floor is *not* gold.
  Meiji Jingu's great torii is plain unpainted wood, not vermilion. An
  onsen bath scene has no people in it. Getting these wrong is what breaks
  recognition, and they are all written down.
- The **failure ladder**: when a place won't hold up, step the shot down —
  full view, then a part, then a distant view, then a fragment, then
  atmosphere only. The recognizability check applies at every step: a
  shot that no longer reads as the place is not shipped under that
  place's name.
- The **handwritten line is composited afterwards**, never generated as
  part of the photo.
- The **character specification** (about 1 m tall, mitten hands with no
  fingers, varied appearances) together with a reference image. Getting
  the reference image: use an image of your own Muse's default avatar
  (for example, a screenshot from the Muse app). The pack cannot
  redistribute the character's image, so the reference is the one input
  you supply yourself.

## Layer 2 — Travels as calibrated starting values

These travel in the text, but as *someone else's calibration*. Expect to
re-tune them with your own judging:

- The **judging tolerance** recorded in the QA field notes: legible shop
  signs are fine if they occur naturally; generic sale copy ("SALE!!",
  "Half price!!") may be readable; a shot can miss one stated condition
  (a tide, a time of day) and still pass if the whole stands. Conversely,
  small recurring character breakages — a tail or a center seam appearing
  on the character's back, an ear that isn't in the reference — are watch
  items even when everything else works. These lines were drawn by a
  human's verdicts, including cases where the human was *more* permissive
  than the AI's self-check (a distant tower tip the AI graded as
  unrecognizable was accepted as a valid distant landmark).
- The **taste corrections** in the field notes (don't lean Showa, don't
  lean exotic, keep the character's size a range rather than a fixed
  value, and so on). The *format* — a running correction log, appended
  verdict by verdict — is part of the method and fully reusable. The
  *contents* are one person's taste, calibrated against one person's
  memories of these places. If you fork this pack for your own city,
  your log will grow different entries. That is the log working as
  intended, not a defect.

## Layer 3 — Does not travel with the documents

- **Discovering each place's key feature.** The place cards state each
  place's key feature as a conclusion, but finding it took a loop:
  generate, get a human verdict, verbalize what made the difference.
  Don Quijote only worked after its features were verbalized from real
  photos. Shibuya Sky's first version aimed at the scramble crossing far
  below and missed the point entirely; the key feature — the open
  panorama over the whole city, with the deck itself in the foreground —
  was identified from the author's own photographs of the place. For
  places already in the pack, the conclusions are yours to use. For a
  *new* place, the loop is the method; no document replaces it, and a
  first attempt that misses the key feature is the normal starting
  point, not a failure of the pack.
- **The selection of places.** The list reflects one person's model of
  what visitors to Japan actually miss, and one person's geography.
  A fork gets the list, not the sense that produced it.
- **Personal reference material.** A few generations used the author's
  own photographs as place references (Shibuya Sky above). Those
  photographs are not included; only the verbalized conclusions drawn
  from them are.
- **The generation pipeline.** The sample images were produced with the
  image-generation pipeline available to the author in November 2026,
  with a character reference image attached to each call. Behavior that
  this pack quietly relies on — for example, that short Japanese sale
  copy often renders correctly while long text is kept out of focus by
  the prompt — is a property of that pipeline at that time. A different
  model, or the same model later, will shift the yield. If you publish
  results from this pack, note your pipeline and date alongside them,
  the way you would note a protocol version.
- **The samples' production record.** The four example images were
  generated in November 2026 with the author's Muse image-generation
  pipeline, from this guide's template and the place cards, and judged
  by the owner. The exact per-sample prompts were not archived; the
  guide's §2 worked example shows the fully substituted form for the
  convenience-store midday shot.

## If you fork this

1. Start from Layer 1 as written; it is the scaffold.
2. Keep a correction log from your first batch. Judge in small batches,
   write the verdict down, and let the log — not your memory of the
   session — carry the calibration.
3. For each new place, expect one generate → judge → verbalize round
   before the card is real.
4. Treat your Layer 2 lines as yours to redraw. The pack's lines are
   evidence that the lines exist, not where yours should be.

In one sentence: the documents carry the scaffold and one calibrated
example of the judging; the judging itself has to happen again, with
your eyes, wherever the pack is used.
