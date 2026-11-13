# QA Field Notes

*Curated from the working QA log of this project (2026-11-13). The "taste corrections" below are the project owner's judgments on generated batches, recorded in the order they were made; later corrections that replace or revise earlier ones are marked as such. All 18 places in the place cards had been generated at least once by the end of this QA day.*

## Taste corrections

1. **Don't push residential streets toward the Showa era.** A first version of a night residential street leaned on old-Japan atmosphere. The correction: build it as a present-day Kanto suburb — new detached houses, carports, LED street lights, a white kei car. The corrected version was adopted.
2. **Don't push drinking alleys toward exotic "Asia."** Rows of lanterns and heavy steam effects were cut. The replacement is the real mess of an actual alley: vinyl windbreak curtains, gas meters, beer cases, fluorescent tubes and bare bulbs.
3. **Narrow does not mean dirty** (addition to 2). Even a cramped alley must be hygienic. No grimy walls or sooty air pushing it toward an "Asian street stall" look — the cleanliness of a Japanese eatery instead: wiped counters, plates lined up neatly, a stainless-steel grill.
4. **(Superseded by 5.)** An intermediate rule for a convenience-store sign — show a famous chain's colors (a blue/green/white band) under a mosaic — was replaced the same day by correction 5.
5. **No mosaic by default.** This is not commercial use, so there is no need to hide signs and logos behind mosaics. Signage may appear naturally, in the chain's colors and shapes; text just needs to be naturally unreadable through distance and angle. A mosaic (or a similar crushing of features) is used only when the mosaic itself means something — applied to people, where it raises realism (see "Faces," below).
6. **Muse can be bigger.** In a QA batch, Muse repeatedly came out small in distant and back views, reading as a figurine rather than a presence. The prescription: raise Muse's share of the frame by one notch, sized so that roughly 1 m of real presence can be read off against nearby reference objects (doors, fences, torii pillars). Also from this batch: a round tail-like protrusion and a center seam appeared on Muse's back — neither is in the reference image, so don't produce them. *(Revised by correction 8.)*
7. **Cafes skewed too Japanese.** A matcha cafe is fine, but on its own it biases the memory of "cafes in Japan." A new candidate place was tried as a counter-proposal — a small independently run neighborhood cafe (neither a chain nor a Japanese-style cafe) — and it held up: the owner's back at the espresso machine, a chalkboard menu in unreadable scrawl, bookshelves, potted plants by the window, the shopping street and bicycles outside, coffee, pudding, and a glass of water on the table. Not a single Japanese-style element, and a strong everyday feel.
8. **Muse's size is a range, not a fixed value** (revises 6). Don't make Muse uniformly bigger. A smaller placement is also valid — the across-the-table izakaya shot works small. The right approach is to vary the size deliberately with the place and the composition. The only failing line is "so small, in a distant view, that it reads as a figurine." Correction 6's "one notch bigger" should be read as "vary it within the range where its real presence can be read."
9. **Shibuya SKY's key feature is the panorama, not the crossing below.** The first version framed the scramble crossing underneath the deck — the obvious postcard — and the owner rejected it as missing the point. What defines the place is the unbroken panorama of the whole city seen *from* Shibuya. The corrected composition puts the deck itself in the foreground (striped deck floor, the glass rim, the outdoor escalator) and lets the city run to the horizon as the main subject. Both a daytime and a night version, built from the owner's own reference photos, passed. See the worked example below.
10. **Takeshita Street is brick, arch, and crowd — not a quiet shopping street.** A morning version came out as a generic shopping street: asphalt surface, small muted signs, almost no people. Against the owner's real photos, the key features are: interlocking brick-pattern paving (not asphalt); the flower-motif entrance arch with its banner as the landmark; loud pink signage and a crepe stand's display case packed in densely; a gentle downhill slope; and a crowd of young visitors even in the morning — a "quiet Takeshita Street" is itself off-key. The regenerated daytime version, built on the arch photo, was adopted.
11. **Omoide Yokocho's key feature is the layer overhead** (refines 2). A daytime version that showed only shutters and backstreet clutter — "closed" drawn literally — read as any back alley. The real alley carries a permanent overhead layer: dense clusters of paper lanterns in mixed white, red and yellow, varied in shape, tangled with vines, greenery and seasonal streamers, present even when the shops are shut. Below, the mess has specific protagonists: stacks of red beer crates, round red stools, handwritten menu boards; people stand in small clusters rather than flowing through; the green bulb-trimmed entrance gate is the face of the place at night. What correction 2 rejects is not lanterns but *staged* lanterns — identical red ones in uniform rows. The real ones are mixed, named, and tangled with everything else. Both regenerated versions (day and night) were adopted, the night one replacing the earlier adopted night shot.

## Working principles that came out of the QA

### Signage, logos, and text

The default is correction 5: no mosaics, signage in natural colors and shapes, text kept naturally unreadable by distance and angle. Two field results qualify this:

- **At Don Quijote's density, "zero text" doesn't hold.** In the first Donki shot, price numbers ("199 yen" and the like) came out half-readable while product names were pseudo-text — at that density, the image fell on the realism side, and that was accepted. In the final version, some generated text came out quite readable ("特価!!!" / "SALE!!!", "今だけ" / "now only", "お得" / "a bargain"), but because none of it was a real brand name, it raised realism instead of breaking the image.
- **Correctly readable generated text can pass.** On a noren curtain in Asakusa's Nakamise, the generated text "浅草仲見世" came out correctly readable, and the shot was confirmed OK as-is.

### Faces

People's faces blurred to the point of looking mosaic-processed were praised by the owner ("funny") — explicitly not a defect to fix. Keep faces unidentifiable. This is the one place where a mosaic-like treatment carries meaning: it reads the way real snapshots of strangers do.

### Shrines and temples: how much to show is the design center

Because form matters so much at shrines and temples, *how much of the place to show* is the center of the design. The more of the whole you show, the more nonexistent buildings and wrong shapes appear. The default is parts, frame-edge cuts, and the air of the approach or the surroundings; showing the form itself is reserved for cases that can be verified. (This is the guide's ladder — full view → part → distant view → fragment → atmosphere — confirmed in practice, with the rule that a shot which no longer reads as the place is not shipped under that place's name.)

Two concrete cases:

- **Meiji Jingu**: the first version showed a worship hall in the distance beyond the torii — an error, since no hall is visible from there. The fix removed it: the approach just curves away into the forest. The plain-wood torii color, on the other hand, came out right — it did not drift to vermilion.
- **Kiyomizu-dera**: a shot that never showed the hall, cutting only the wooden pillar structure from below, worked. A recorded note adds tolerance rather than a redo: for Kiyomizu, a somewhat fuller view — a distant view including the stage and the main hall — is also acceptable.

### Muse's size

See corrections 6 and 8: roughly 1 m of presence, varied deliberately by place and composition — large in some shots, small in others (a small appearance peeking from between shelves is also a valid use). Too small to read as a ~1 m character is the only failure line.

### Muse's back: the one recurring defect

The character's back is a single continuous felt surface — no tail, no pom-pom, no center seam. This is the defect that kept recurring across the QA: it appeared in an early back view, again at Himeji Castle, and again in an evening onsen shot (a seam running down the back of the head and body, plus a small round bump at the base). Back views at close range are where it happens. Two data points on wording: an ordinary "no tail, no seam" line did *not* prevent the onsen recurrence, while a strengthened, explicit formulation — the back is one single continuous smooth felt surface from head to feet, like the plain back of a simple plush toy, with nothing attached at all — produced a completely clean back in a deliberate re-test at Meiji Jingu, and clean backs also held in the final advance batch (Golden Gai morning, Kiyomizu evening). The strengthened wording is not a guarantee either: in a later Takeshita Street regeneration it was used in full and a small pom-pom still appeared, on a small back view inside a crowd. Treat the strengthened wording as the default for any back-facing composition, and still check every back view by eye: the wording lowers the rate, it does not eliminate it.

### Judging standard: a missed directive is not automatically fatal

In one Miyajima QA shot, high tide was specified and low tide came out (the great torii standing on wet sand instead of water), and a second small torii appeared in the far distance — yet the owner judged the image high-quality. The standard that emerged: as long as a missed directive (a condition the model didn't honor) doesn't collapse the image as a whole, it is not a fatal flaw. The shape of the torii itself and the deer were intact in that shot. The same standard covered a Shibuya night shot whose signage came out considerably readable, and whose colors leaned cinematic: neither lowered the verdict.

## Worked example: verbalizing Don Quijote (Donki)

The Donki card's key feature — "merchandise stacked to the ceiling and a flood of POP cards" — got close but not all the way ("it should be possible to make it more Donki"). The fix that worked was verbalization from real photos: the owner supplied actual in-store photos, and the key features were pinned down in words before regenerating.

The six elements of Donki-ness:

1. **The ceiling is a display surface.** Signs, POP cards, and products hang in several slanted layers, until the ceiling's structure is invisible.
2. **Zero blank space in the field of view.**
3. **Giant price numbers and short shouted copy** ("特価!!!" — "SALE!!!"; "限界値引" — "lowest price") repeated as a rhythm.
4. **Dominant colors: red, black, and yellow, plus fluorescent white.** The floor stays shiny and clean.
5. **Maze-like aisles where the genre keeps changing.**
6. **Layers of multilingual POP cards.**

Diagnosing the failed intermediate version against this list: elements 1 and 3 were missing, the boxes fell back to abstract patterns, and the aisle read as "a warehouse." With all six elements in the prompt, the result was confirmed as the final version ("the best of the best — this is it"). The same six-element verbalization also reproduced in a different aisle (sweets × party goods), which suggests the verbalization, not the single prompt, is the reusable asset.

The same pattern — real photos first, words second, generation third — rescued Golden Gai. The first version was rejected as too dark and cinematic, sliding into a generic "Asian alley" type. The key features read off real photos were: bright, colorful sign boxes; a mix of katakana and Latin lettering; beer cases and clutter at foot level; and the liveliness of people walking. The regenerated version passed, and the mitten hand also returned to smooth in it.

## Worked example 2: Shibuya SKY — when the "obvious" key feature is wrong

Shibuya SKY shows a different failure mode from Donki: not a missing verbalization, but a wrong one. The first prompt reached for the famous view *down* at the scramble crossing, and the resulting image was competent — glass corner, visitors from behind, the crossing and a train below. The owner rejected the premise: the crossing is what you see in every photo of Shibuya; the experience of SKY is the city panorama spreading to the horizon. The owner supplied two of their own photos (a night shot over the outdoor escalator, a daytime shot across the deck), the key features were re-read from them — striped deck flooring and the glass rim as foreground, the outdoor escalator as a diagonal at night, the city unbroken to the horizon as the subject — and both regenerated versions passed immediately. The lesson generalizes: the key feature of a place is what the visit *feels* like from inside it, which is not always its most photographed view; when a knowledgeable person corrects the premise, re-derive the composition from their photos rather than patching the old one.

## What tested strongest

- **A convenience store at midday.** Rated by the owner as having "an incredible amount of realism." The combination that is currently strongest: an everyday scene × daylight × real clutter (drink cases, a vending machine, bicycles). Muse peeks from behind a pillar, raising one hand; the sign is color plus natural blur, its text unreadable (correction 5 in action).
- **Day/night pairs for the same place.** The convenience store exists in both a night and a noon version, and both hold up. Place card × time of day is a design dimension in its own right — and inside a trip, it also works as revisiting the same place at a different hour.
- **Everyday scenes beat famous shapes.** Across the batches, the most reliable shots were ordinary places with the right details; the famous-shape (type C) cases were where directives were missed and forms drifted — exactly the split the generation guide predicts.
- **Closed hours work as a variation.** In the final advance batch, two night-famous alleys were generated outside their famous hour: Omoide Yokocho in the daytime before opening (shutters down, gas meters, crates and buckets, one distant figure) and Golden Gai in the morning after closing (crows on a wire, bottle crates, a mop left out, nobody around). Both held up — a place at its "wrong" hour reads as a memory of having wandered there, not as a missed shot. The same pairing held for an onsen (morning / dusk) and the Yamanote line (night / midday).
- **Weather is a usable axis.** A vending-machine alley regenerated in falling snow — snow settled on the machines, the bicycle, the outdoor units, footprints in the lane, snow resting on Muse's hood and shoulders — held up completely, with the modern suburb intact underneath. Season and weather can vary a place the way time of day does.
- **Landmark × transit.** The strongest of the tourist-leaning shots paired a landmark with the experience of moving: Mt. Fuji seen from a Shinkansen window in winter (one peak, correct snow cap, only the foreground streaming past, an ekiben and tea on the tray inside). The window frame does the "how much to show" work that shrines and temples need — the landmark arrives pre-cropped by the situation.

## Judgment summary: the 18 place cards

Every card was generated at least once and judged by the owner on 2026-11-13. This table is the summary; the narrative sections above hold the detail. On verification by a person who knows the place: the owner's own photographs served as the reference for Takeshita Street and Omoide Yokocho (and for Shibuya SKY, which is not a card place). For the other places, the owner's verdicts are the record — an independent local check has not been run per card.

| Place | Generated | Owner verdict | Known issues |
|---|---|---|---|
| Shibuya Scramble Crossing | yes (evening; rain night) | passed | Rain-night shot: signage quite readable, colors cinematic — neither lowered the verdict |
| Meiji Jingu | yes (approach; sake barrels; back-view test) | passed | First version invented a worship hall in the distance; fixed in the remake. Strengthened back wording test came out clean |
| Takeshita Street | yes (day; morning; v2 day) | v2 adopted | Morning version rejected as a generic shopping street; key feature re-derived from real photos (correction 10). v2 carries a small pom-pom recurrence — accepted |
| Senso-ji | yes (Nakamise morning; Kaminarimon night) | passed | A glowing panel on the lantern's underside was questioned; did not lower the verdict. A correctly readable noren inscription was accepted |
| Miyajima | yes (afternoon; morning) | passed | Morning shot: high tide specified, low tide delivered, plus a second small torii far off — accepted under the tolerance standard. The afternoon shot's back carried the seam/pom-pom defect; replaced as the pack's example by the morning shot (see below) |
| Fushimi Inari | yes | passed | Tail-like protrusion and a center seam on the back in one shot; a small donor inscription visible where the card's principle says it should not be |
| Kiyomizu-dera | yes (fragment; distant view; evening fragment) | passed | Owner's note: a fuller distant view including the stage is also acceptable for this place |
| Arashiyama bamboo grove | yes (morning; crowded midday) | passed | — |
| Omoide Yokocho | yes (several versions, day and night) | v2 day and night adopted | Earlier versions missed the overhead layer entirely; key feature re-derived from real photos (correction 11) |
| Golden Gai | yes (night v1 → v2; morning) | passed after remake | v1 rejected: too dark and cinematic, a generic "Asian alley." The morning after-closing version also passed |
| Don Quijote | yes (v1–v4; second aisle) | v4 adopted ("the best") | v3 failed as a "warehouse" — elements 1 and 3 of the verbalization were missing. Occasional mis-set characters in POP copy did not lower verdicts |
| An ordinary izakaya | yes (counter; across the table) | passed | In the across-table shot Muse reads as seated on the table itself; noted, not blocking |
| Matcha cafe | yes | passed | Minor tabletop clutter noted |
| Convenience store | yes (night ×2; midday) | passed | Midday version rated the strongest shot in the pack. Night v1 (blank sign) and v2 (mosaic sign) were superseded by correction 5 |
| Yamanote Line platform | yes (day; night; midday) | passed | Night version: Muse too small and standing on the tactile paving — both fixed in the midday version |
| Residential back street | yes (v1 → v2; evening) | v2 adopted | v1 leaned Showa-era; rebuilt as a present-day suburb (correction 1). Evening shot: a dog appears without an owner; not flagged |
| Onsen | yes (foot bath; morning bath; evening) | passed | Evening shot: the back seam and pom-pom recurred under ordinary wording (see "Muse's back") |
| Alley with a vending machine | yes (night prototype; midday; snow evening) | passed | The prototype's can was a Western tin with English text — the guide's §0 records the fix |

## Post-review fixes (2026-11-13)

An external review of the publish draft (by the owner's ChatGPT-side reviewer) found that the documents, the QA verdicts, and the samples did not fully agree with each other. The fixes adopted:

- **Example image replaced.** The Miyajima afternoon example carried the back seam/pom-pom defect that these notes list as the recurring failure, while the README presented it as a confirmed sample. It was replaced with the judged morning shot.
- **One template.** The guide's main template was rebuilt so the card variables slot in directly, in the order the original "how to use" sheet specifies; the auxiliary template that asked for variables the cards don't have was removed; a fully substituted convenience-store midday prompt was added as a worked example.
- **Cards updated from the corrections.** Takeshita Street and Omoide Yokocho were rewritten from corrections 10 and 11 (both had still described the pre-correction places); the convenience store gained its midday variant; the Donki card was aligned with the six-element verbalization; the residential card was marked present-day.
- **Guide wording aligned with the QA record.** Camera height is a reference, not a fix; correctly rendered short text may stay readable; the type-A stability claims were softened to what this QA record supports.
- **One ladder.** The failure ladder now reads the same in the guide, these notes, and the reproducibility note, with the recognizability floor stated at every step.
