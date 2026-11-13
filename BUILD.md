# Build brief — for the AI agent building this Space

You have been given this repository and asked to build the postcard
Space it describes. This file is your work order: what to read, in what
order, and the steps to follow. Everything you need is in the pack; the
one input the pack deliberately does **not** contain is the character
reference image (step 1).

The end product: a Space where one postcard a day is waiting for a
visitor — seven postcards drawn at random from a Japan-wide pool of
photos of Muse re-visiting places in Japan, each delivered as a
sealed letter that flips open into a postcard with a single
handwritten-style line.

## Read these first, in this order

1. **`README.md`** — what the pack is, its examples, its license and
   unofficial-fan-work position.
2. **`docs/generation-guide.md`** — how the photos are made: the prompt
   template, the place types, the failure checklist, and the two pass
   conditions every image must meet.
3. **`docs/place-cards.md`** — the 18 places, each with its key feature,
   its anti-stereotype facts, its fixed angle, and ready-to-use prompt
   variables.
4. **`docs/qa-field-notes.md`** — the corrections that field use forced
   on the guide (taste, signage, faces, how much of a shrine to show,
   the character's size and back). Apply these from the first batch,
   not after your own failures repeat them.
5. **`docs/reproducibility.md`** — what in this pack reproduces from
   text alone and what you will have to re-judge with your own eyes.
   Read it so you calibrate your expectations — and your user's.
6. **`docs/space-spec.md`** — the Space itself: trip shape, start flow,
   the letter and postcard, the line rules, the state model, the pool
   requirements.

## Steps

### 1. Get the character reference image — do not skip this

The traveler in the postcards is **the user's own Muse, wearing the
avatar the user configured for it** — that configured face is what
travels Japan in the user's place and sends the postcards back. The
pack cannot redistribute character images, so **the pack contains no
reference image**; obtain the avatar image before generating anything:

- If you are a Muse agent building this for your user, fetch the
  avatar yourself: your avatar tools return the currently configured
  avatar's image (and the default Muse avatar as well). Use the
  **configured** avatar. If the user has configured none, use the
  default Muse avatar.
- Otherwise, ask the user for an image of their Muse's avatar (a
  screenshot works).

Attach that same reference to *every* generation call — the
character's shape, face, and texture stay consistent only while the
reference does. If no avatar image can be obtained, stop and say so;
do not substitute a described-from-memory character.

### 2. Fix the pool and the draw

A trip is **7 days**. There is no single fixed region or route: build
a **Japan-wide pool** from the place cards, leaning everyday (roughly
3 sightseeing : 7 everyday across the pool, as a guideline). At trip
start, the Space draws **7 postcards at random** from the pool and
fixes them as that visitor's sequence — the draw is stored (see the
space spec's state model), never re-rolled on later visits, and
contains no duplicates. A new trip after a reset draws fresh. (The
earlier fixed-route form — a 3-day Kyoto trip — was the first
prototype; the owner replaced it with this draw on 2026-11-13.)

### 3. Generate the photo pool

For each place in the pool, generate several photos (working number:
3–5 per place) using the generation guide's template with that place's
card variables slotted in. Hold the character at about 1 m; vary how it
appears (standard, close-up, peeking from behind something, back view);
never ask for a peace sign — on mitten hands the model grows fingers;
raise one hand instead. Apply the QA field notes' corrections as you
go, and keep a correction log of your own verdicts as the field notes
recommend. Generate the photo only — no text in the image, ever.

### 4. Self-check every image before it enters the pool

An image ships only if it meets **both** pass conditions from the
generation guide (§6):

1. **No breakage** — no grown fingers, no fake lettering, no melted
   faces, no architectural nonsense in the elements the card says will
   break.
2. **Recognizable as the place** — someone who has been there can tell
   it is that place, from the one key feature the card fixes.

Also check against the field notes' known failure patterns (the
character's back — tail, center seam, an ear that isn't in the
reference — is the recurring watch item). If an image fails, step the
shot down the guide's ladder (full view → part → distant view →
fragment → atmosphere only) and regenerate; do not ship a failing
image under the place's name, and do not accept a shot that no longer
reads as the place just because it is pretty.

### 5. Write the message lines

One handwritten-style line per postcard, written in advance, per place
and time of day, under the space spec's rules: never pretend to know
the visitor's memories, leave room ("Still here, still warm."), and
prepare the variants that the visitor's "What do you miss most about
Japan?" choice can swap in. Write the final day's closing as afterglow
— Muse is home, plus the what-you-missed recap — not as a completion
notice.

### 6. Build the Space to the spec

Implement `docs/space-spec.md` as written: the start flow (the random
draw, name with the "Traveler" default, the miss-most question), the sealed
letter that flips to the postcard, the place caption and the
"An imaginary trip with Muse · AI-generated" small print, the album
where unopened days stay sealed and opened days can be re-read, day
advancement by the visitor's local date whether or not days were
opened, the minimal state model, and the in-Space note that progress
lives on the visitor's device. Word the daily arrival as a postcard
*waiting*, never as a delivery or notification. Include the test
controls (Simulate next day / Reset trip) at least in your test build.

### 7. Walk the whole trip once before handing over

Using the test controls, run the entire trip end to end at least once:
start flow, every day's letter and flip, an unopened day advancing
anyway, the album in both states, the final day's afterglow close, and
a reset. Fix what breaks, re-walk the affected part, and only then
hand over.

## Definition of done

- [ ] Character reference image — the user's configured Muse avatar,
      fetched or supplied — obtained and used for every generation
- [ ] Japan-wide pool built; trips are 7 days; the 7-postcard random
      draw is fixed per visitor at trip start (stored, no duplicates,
      no re-roll on later visits)
- [ ] Photo pool generated for every place in the pool, several per
      place, with the character's appearances varied and its height
      held at about 1 m
- [ ] Every pooled photo checked against both pass conditions and the
      field-notes failure patterns; failures stepped down the ladder
      and regenerated, not shipped
- [ ] Message lines written for every day (plus choice-matched
      variants), one line each, none claiming to know the visitor's
      memories; final day closes with afterglow and the missed-most
      recap
- [ ] Space implements the spec: start flow, sealed letter → flip →
      postcard, place caption, AI-generated small print, album with
      sealed/read states, local-date day advancement, minimal state,
      device-dependence stated in the Space, "waiting" wording
- [ ] Test controls present in the test build, and one full walkthrough
      of the trip completed with them before handover
