# The Space: specification

This document specifies the Space that the rest of the pack feeds: what a
visitor experiences, how a trip is structured, what state is kept, and what
the content pool must contain. It is distilled from the design and
implementation documents the pack was built from; where those documents
left something provisional or unverified, this spec says so.

For *how the photos are made*, see `docs/generation-guide.md`,
`docs/place-cards.md`, and `docs/qa-field-notes.md`. For the order in which
to build everything, see `BUILD.md` at the repository root.

## What the visitor experiences

A small toy: Muse travels through Japan on the visitor's behalf, and one
postcard is waiting for the visitor each day. It is a **revisit** toy,
aimed at people who have been to Japan: Muse re-walks a region the
visitor misses, and each postcard is a photo of a place there — with the
default Muse character somewhere in the frame — plus a single
handwritten-style line. That is all a postcard carries: no long diary, no
travel information.

The core of the experience is companionship, not sightseeing information:
the feeling that your stand-in went back to the places you remember and
sent word.

## The shape of a trip

- **One postcard per day.** The first card is available as soon as the
  trip starts; after that, one new card per day.
- **One region, fixed.** A trip stays inside a single chosen region. The
  promise is not "somewhere in Japan" but "Muse walks the region you
  miss, once more."
- **The route is defined in advance.** Before the trip starts, the full
  sequence of postcards for the trip's length is fixed for that visitor
  (which place cards, in which order). Nothing is drawn at random on
  later visits; re-opening the Space never shows a different photo or a
  duplicate.
- **Days advance by the visitor's local date — opened or not.** If the
  visitor skips days, the trip still moves on. Past days are not lost:
  they wait in the album and can be read together later.
- **Mix inside the region:** roughly 3 parts sightseeing to 7 parts
  everyday life, as a guideline to tune within the region — not a fixed
  ratio. The everyday side (a convenience store, a station platform, a
  vending machine on a night street) is where the memories live.
- **Length:** 7 days (7 postcards) is the design's working default; the
  validated first-test shape is 3 days (see "The validated minimum
  shape" below).
- **Language:** English. (In the source design this is a provisional
  decision; because the text is composited on the display side, it can
  be changed later without regenerating any photo.)
- **Sharing:** the design's starting point is link sharing
  (provisional).

## Start flow

1. **Choose the region** — one region; the trip is fixed to it.
2. **Enter a name** for the letters to be addressed to. If left empty,
   the name defaults to "Traveler".
3. **Answer one question: "What do you miss most about Japan?"** — a
   single choice from:
   - Quiet streets at night
   - Little everyday food discoveries
   - The places I visited
   - Trains and wandering around
   - Surprise me

   The choice adjusts priorities inside the pre-defined route, and on
   some days it swaps that day's handwritten line for a variant matched
   to the choice. Line variants are written in advance; nothing is
   generated at display time.
4. Optionally, the visitor may add **one short line about a memory of
   their own**. In the first version this is only an aid to the choice
   above — the Space does not deeply interpret it. (Free-text memory
   input beyond this is a later extension, not part of this spec.)

The trip starts immediately: the first postcard can be opened right away.

## The letter and the postcard

Each day arrives as a **sealed letter**, not as a bare photo.

- **Front (what the visitor sees first):** an envelope-like face
  addressed "For {name}", marked "from Muse — {region}", with a
  postmark and a stamp from the region. A day that has not been opened
  yet is presented in this sealed form (in the album, too, unopened days
  show as sealed letters marked "Sealed").
- **Flip:** the visitor taps the letter and it flips over to the
  postcard. Opening a day records it as opened (see the state model);
  an opened day is thereafter presented postcard-side, with a way to
  look at the letter front again.
- **Back (the postcard itself):**
  - the photo, full-bleed at the top;
  - a small **place caption** (place name and city, with the time of
    day — e.g. "Fushimi Inari Taisha, Kyoto — morning");
  - **one handwritten-style line** on the paper band below the photo
    (see the next section);
  - small print at the bottom: **"An imaginary trip with Muse ·
    AI-generated"** — so that a postcard shared on its own still reads
    as an imaginary, AI-generated trip, not a real photograph.

## The handwritten line

- **One line per postcard.** Short, in a handwritten-style font,
  composited on the display side on the paper band — never baked into
  the photo (see "Content pool" below).
- **Never pretend to know the visitor's memories.** No lines of the
  "Remember when we came here?" kind — Muse was not there with them.
- **Leave room.** The line gestures at the place and stops; the
  visitor's own memory does the rest. The pack's canonical example:
  *"Still here, still warm."*
- Lines are prepared in advance, per place and time of day (morning /
  midday / night), built on set patterns with each place's key feature
  worked into some of them, plus the choice-matched variants described
  in the start flow.
- **The final day ends with afterglow, not "complete."** All the
  postcards line up in the album, Muse is home — a short line to that
  effect (the prototype's closing line: *"Muse is home. Kyoto is still
  there, whenever you are."*) — together with a recap of what the
  visitor said they missed ("What you missed: …"), and a path to open
  the first day's postcard once more.

## "Waiting", not "delivered"

The Space never promises a notification or a delivery. Its wording is
that a postcard is *waiting*: e.g. **"A little postcard from Japan is
waiting for you each day."** The visitor opens the Space and finds the
new card there.

## State model

State is deliberately minimal. Per visitor, the Space keeps:

| Field | Meaning |
|---|---|
| `trip_id` | Which trip (region + route) this visitor is on |
| `start_date` | The visitor's local date the trip started — day numbers are counted from this |
| `last_claimed_day` | The furthest day the visitor has been shown |
| `selected_memory` | The answer to "What do you miss most about Japan?" |
| `postcard_ids` | The fixed sequence of postcards for this trip, decided at start |
| `opened_days` | Which days have been flipped open (unopened days stay sealed) |

Rules that follow from the design:

- **Progress is per visitor and tied to their device/browser.** The
  design assumes visitor state cannot be held server-side in a public
  Space, so it lives on the visitor's side; the exact persistence
  mechanism depends on the Spaces environment and must be confirmed
  against the real thing when building (the source documents flag this
  as *to be verified* — treat any assumption here as an assumption).
- The Space must state plainly, inside itself, that progress lives on
  the visitor's device. There is **no cross-device sync and no resume
  guarantee** in the first version.
- There is **no owner admin console**. Adding or replacing pool photos
  is an operations task: generate, then update the Space.

## Content pool requirements

- **Photos are pre-generated; visitors never trigger generation.** A
  public Space cannot have each visitor run image generation, so the
  pool is produced in advance by the owner side, and the Space only
  serves from it.
- **Several photos per place card** — the implementation plan's working
  number is 3–5 per place (its estimate for a first full pool was on
  the order of 64 photos across 16 places). Each place's set mixes how
  Muse appears — standard, close-up, face peeking from behind
  something, back view — with the character's height held at about 1 m
  at generation time.
- **Every pool photo passes inspection before it enters the pool**,
  against the generation guide's checklist and its two pass conditions
  (see `BUILD.md`, step 4). A photo that fails is regenerated one step
  down the guide's ladder — full view → a part → a distant view → a
  fragment → atmosphere only — rather than shipped.
- **Text is never baked into the image.** The postcard is composed on
  the display side: photo + the paper band under it carrying the
  handwritten-style line. This keeps spelling exact, lets a line be
  swapped (or the language changed) without touching the photo, and
  means no photo ever needs regenerating for a wording fix.
- **Photo presentation:** the kept-snapshot feel is produced at
  generation time by the guide's prompt discipline (unpolished
  smartphone look). The validated prototype also applied a light
  film-style frame treatment on the display side, leaving the photo
  files themselves unmodified. The tuned values from that prototype:
  CSS filter `saturate(0.93) sepia(0.07) contrast(0.97)
  brightness(1.03)`; a warm vignette of `rgb(43 28 12 / 0.07)`; a
  grain overlay at opacity `0.16`; and a white frame padding of `4px`
  (`2px` on album thumbnails). Treat these as the starting point, not
  a requirement — the photo should still read as an ordinary phone
  snapshot underneath.

## Test controls (recommended for test builds)

The validated prototype carried two test controls, and any new build
should keep equivalents while testing:

- **Simulate next day** — advance the trip by one day without waiting
  for the calendar, so a whole trip can be walked in one sitting.
- **Reset trip** — clear the visitor state and start over.

## The validated minimum shape

The first test form, and the shape whose behavior this spec describes,
is a **3-day Kyoto trip**:

- **Day 1** — Fushimi Inari in the morning
- **Day 2** — a vending machine at night
- **Day 3** — a matcha cafe in the afternoon

It is tested against exactly one question, with 3–5 people who have
travelled to Japan:

> **Did it make you remember your own trip to Japan — and want
> tomorrow's card too?**

Only if that holds does the trip grow to the full 7 days.

## Open and unverified items

Carried over from the source documents, so a builder does not mistake
them for settled facts:

- **Platform specifics are unverified.** How a given Spaces environment
  persists per-visitor state, and its exact sharing behavior, must be
  confirmed in the real environment before building on the assumptions
  above. Notifications are not promised anywhere in this spec.
- **The character's terms of use** (trademark/brand, avoiding any
  impression of an official product) must be checked before a public
  release. This pack's own position is stated in the README's
  "Unofficial fan work" note.
- **Using the visitor's own photographs as generation references** was
  raised in the design process and is **not** part of the first
  version; it remains a possible later extension.
- Facts inside the place cards that the original documents marked as
  needing confirmation must not be treated as verified facts.
