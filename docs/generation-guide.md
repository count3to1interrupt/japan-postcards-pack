# Postcard Image Generation Guide

*Designed by Claude Opus (via the user's Claude Pro, project "Claude Harness Audit"), 2026-11-13, in response to a relayed request with the second prototype (night vending machine) and a reference image of the default Muse character attached. Bracketed caveats marked as Opus's own reservations are preserved from the original answer.*

*Preliminary caveat (Opus): the characteristics of the generation model used here (Wonder) are unverified. What follows is a design that applies to image generation models in general; fine-tuning to the specific model is to be worked out through prototypes.*

## Conclusion

The "fake" feeling comes mainly from three sources. (1) Too much polish (composition, light, color and focus all too perfect). (2) Landmarks turned into symbols (the same "full view from the front" as a tourist poster). (3) Broken details (text, logos, repeated parts of buildings, people's faces and hands).

The basic approach is also threefold. (a) Specify where the photographer is standing and how sloppy the shot is. Aim for "a photo a traveler took on their phone but never turned into a work of art." (b) Don't shoot the whole landmark; convey the place through a part of it. Only one key feature. (c) Don't have the image generator draw the handwritten line — composite it in afterwards. This is the most reliable approach.

## 0. Evaluation of the second prototype (night vending machine)

What works: the white light from the vending machine falls only on Muse's right side. When the relationship between the light source and the subject is correct, the composite feeling disappears all at once. There are traces of life nobody tidied up — the wet road surface, the row of bicycles, the potted plants, the power lines. Even with Muse near the center, the alley running diagonally into the background keeps it from hardening into a poster.

What snags: the shape and label of the can. Japanese vending-machine corn soup comes in a slim short can with a Japanese label. This image shows a Western food tin with "CORN SOUP" in English — the more someone loves Japan, the more it will bother them. Specify the can as "slim short Japanese drink can, label turned away / out of focus" so the label cannot be read. The background blur is also a bit strong, leaning toward a DSLR look. For a phone feel, the blur should be a little shallower.

## 1. Typical causes of fakeness, and general principles

- **Composition**: AI makes rule-of-thirds and bilateral symmetry perfect, and puts the landmark front and center. → Tilt slightly (1–3 degrees), shift the subject off center, cut objects at the edges awkwardly, put something in the way in the foreground.
- **Field of view**: AI either fits everything in with an ultra-wide angle or compresses with a telephoto. → Fix it to a phone's main camera (about 26mm in 35mm-equivalent terms). At a landmark, "doesn't quite fit" is natural.
- **Light**: AI goes for golden evening light, rays of light, strong blur, HDR, cinematic color. → Specify the ordinary light of that time of day. Deliberately include phone quirks (blown-out highlights, noise in the shadows, color casts from mixed light sources).
- **Focus and blur**: AI blurs the background heavily. → Write "deep depth of field typical of phone cameras." Blur only the parts with text.
- **Amount of information**: AI is either uniformly high-detail everywhere, or empty and clean. → Include traces of life (power lines, traffic cones, posted notices, trash bins, bicycles, pipes). Keep the foreground detailed and let the distance go a little soft.
- **Color**: AI oversaturates, leaning teal-and-orange. → "no color grading, slightly flat colors."
- **Text**: AI produces Japanese-like gibberish and nonexistent logos. → Make anything with text "small, distant, angled, or out of focus," or leave it out of the frame. Garbled pseudo-text is the failure to avoid — a short piece of text that renders correctly (a sale slogan, a simple sign) may stay readable; in QA it raised realism rather than breaking the image (see the field notes).
- **People**: AI melts crowd faces, gives everyone a model's build, or empties the landmark of people. → People should be "few, seen from behind, distant, blurred by motion." Zero people at a landmark looks fake in the other direction, so always include a few.
- **Weather and season**: AI makes the ground wet all the time and mixes up seasons. → State the season and weather every time. Wet ground is only for night, after rain.
- **Muse looking composited in**: floating in the air, light direction not matching the background, a different size every time. → Specify a contact shadow, the direction and color of the light source, reflections on the ground, and the height, every time.
- **Character breakage**: fingers grow, the mouth opens, the fur becomes a realistic animal, it turns into a costume. → Attach the reference image every time, and put "mitten-like hands, no fingers" and "mouth is only a line" in the fixed text.
- **Fix Muse's height.** In the prototype, compared against the vending machine (about 1.8 m), Muse reads as about 1 m. If this changes from postcard to postcard, it produces the strongest series-wide fakeness. Decide on wording like "about 1 m tall" and put it in the fixed text. The camera height anchors that sense of scale (about 1 m as the reference), but don't fix every shot at it — vary the height from shot to shot (looking up, table height), or the series starts to feel stamped out.

## 2. A reusable prompt template

Structure: a fixed part (the postcard format, the phone-photo texture, Muse's features, things to avoid — identical wording every time) and variable parts in {}. English is recommended for the prompt. The template covers only the photo part (on the assumption that the handwritten line is composited in afterwards).

```
[REFERENCE]
Use the attached reference image for the character. Match its shape, face, colors and felt plush texture exactly.

[PHOTO]
{SPOT_DESCRIPTION}.
Key feature: {KEY_FEATURE}.
Accurate details — where the real place differs from the average image: {FACTS_AGAINST_STEREOTYPE}.
{ANGLE_AND_CROP}.
People: {PEOPLE}.
An unpolished, candid smartphone snapshot taken by a tourist in Japan.
Season: {SEASON}. Time: {TIME_OF_DAY}, {LIGHT}. Weather: {WEATHER}.
Shot handheld with a phone's main camera (about 26mm equivalent), from a natural phone height — about 1 m is the reference, varied from shot to shot (looking up, table height).
Slightly tilted horizon, subject a little off-center, one edge awkwardly cut off.
Deep depth of field typical of phone cameras; mild noise in the shadows; {BRIGHT_SOURCE} slightly blown out; natural mixed color casts; no color grading, no HDR look, no cinematic lighting.
Ordinary details in the scene: {CLUTTER}.
Any signs, labels or posters are small, distant, angled or out of focus. A short piece of text that renders correctly may stay readable; garbled pseudo-text is not acceptable.

[MUSE]
In the frame is the character from the reference image: a cream-beige fuzzy plush figure with a hood-like furry head, a smooth pale oval face, two small glossy black bead eyes, soft pink cheeks, a tiny curved line for a smile, rounded mitten-like arms with no fingers, short stubby legs and a pear-shaped body. It is about 1 m tall; how much of the frame it takes varies with the shot (see "Variations in how Muse appears").
It {MUSE_ACTION}.
It keeps a matte felt plush texture; it is not a real animal, not realistic fur, not a person in a costume.
It is lit by the same light as the scene: {LIGHT_ON_MUSE}. It casts a soft contact shadow on {GROUND}{REFLECTION}.

[AVOID]
No golden-hour glow unless stated, no light rays, no heavy background blur, no oversaturated colors, no logos or brand names, no fake Japanese characters, no fingers on the character, no open mouth, no people looking at the camera, no faces in sharp focus, no postcard-perfect symmetrical composition.
{AVOID — the place card's own AVOID items, appended after the common text above}
```

**The character paragraph describes the default Muse; rewrite it for the actual traveler.** The traveler is the user's own Muse avatar (see BUILD.md, step 1). The [MUSE] paragraph in the template above — cream-beige plush, mitten hands, about 1 m — is written for the default character. When the reference image is a configured avatar, rewrite that paragraph from the reference's actual features (shape, face, materials, proportions) and keep the same discipline: hold the character's size consistent across the series, describe its hands as they are (the no-fingers wording applies only to mitten-handed characters), and match its texture to the reference. The worked example below and the pack's samples use the default character.

The first five variables of [PHOTO], and the appended part of [AVOID], come from the place card, in this order: SPOT_DESCRIPTION → KEY_FEATURE → FACTS_AGAINST_STEREOTYPE → ANGLE_AND_CROP → PEOPLE, then the card's AVOID after the template's common AVOID text. Card text can itself contain variables in braces — {AREA} inside a SPOT_DESCRIPTION, Miyajima's {TIDE}, Kiyomizu-dera's {SEASON}. Resolve those nested variables first (choose one of the alternatives and substitute it) before assembling the prompt.

How to fill in the variables:

- {SPOT_DESCRIPTION} (from the card): where in that place, in front of what — not just the landmark's name. Example: the sidewalk in front of a Japanese convenience store at night, {AREA}
- {KEY_FEATURE} (from the card): the one feature that makes the place recognizable. Example: the bright white interior seen through the large glass front, glowing against the dark street
- {FACTS_AGAINST_STEREOTYPE} (from the card): the points where the real place differs from AI's average image of it. Example: open 24 hours; the store sign has a horizontal band of brand colors
- {ANGLE_AND_CROP} (from the card): the viewpoint and what the frame cuts. Where it conflicts with this template's generic angle wording, the card's ANGLE_AND_CROP takes precedence. Example: from the dark sidewalk at about 1 m; the store sign cut off at the top of the frame, only part of a color band visible
- {PEOPLE} (from the card): how many people and how they appear. Example: one or two blurred figures inside the store
- {AVOID} (from the card): the place-specific prohibitions, appended to the common AVOID text. Example: no store logo or name, no readable shelf labels or posters on the glass
- {AREA}: down to the neighborhood name. Example: Koenji, Tokyo
- {SEASON}: the season and things visible in that season. Example: early winter, people in coats
- {TIME_OF_DAY}/{LIGHT}: from the time-of-day presets. Example: night, lit only by the vending machine and a few apartment windows
- {WEATHER}: keep the weather the same across the 3 images of one day. Example: just after light rain, wet asphalt
- {BRIGHT_SOURCE}: the light source to blow out. Example: the vending machine panel
- {CLUTTER}: 3–5 ordinary things that are really there. Example: parked bicycles, potted plants, overhead power lines, a plastic trash bin
- {PEOPLE}: how many and how they appear. Example: none nearby, one blurred figure far down the alley
- {MUSE_ACTION}: from the action presets. Example: holds a slim short Japanese drink can with both mitten hands, label turned away, faint steam rising
- {LIGHT_ON_MUSE}: the direction and color of the light. Example: cool white light from the vending machine on its right side, the left side in shadow
- {GROUND}/{REFLECTION}: the ground material and reflection. Example: wet asphalt /, with a faint reflection

Worked example — a convenience store at midday, fully substituted (the card's midday variant; {AREA} resolved to Koenji, Tokyo for this example):

```
[REFERENCE]
Use the attached reference image for the character. Match its shape, face, colors and felt plush texture exactly.

[PHOTO]
The sidewalk in front of a Japanese convenience store at midday, Koenji, Tokyo.
Key feature: the everyday clutter in front of the store — stacked drink cases, a vending machine, parked bicycles — with the bright interior visible through the large glass front in flat daylight.
Accurate details — where the real place differs from the average image: open 24 hours; the store sign has a horizontal band of brand colors; a steamer of pork buns by the register.
From the sidewalk at about 1 m; the character peeking from behind a pillar at the storefront edge, raising one mitten hand; the store sign cut off at the top of the frame, only part of a color band visible.
People: one or two shoppers going in and out, backs turned, faces blurred.
An unpolished, candid smartphone snapshot taken by a tourist in Japan.
Season: early winter, people in coats. Time: midday, flat overcast light. Weather: dry, overcast.
Shot handheld with a phone's main camera (about 26mm equivalent), from about 1 m high.
Slightly tilted horizon, subject a little off-center, one edge awkwardly cut off.
Deep depth of field typical of phone cameras; mild noise in the shadows; the store interior slightly blown out; natural mixed color casts; no color grading, no HDR look, no cinematic lighting.
Ordinary details in the scene: drink cases stacked by the door, a red vending machine, parked bicycles, a bin for cans.
Any signs, labels or posters are small, distant, angled or out of focus. A short piece of text that renders correctly may stay readable; garbled pseudo-text is not acceptable.

[MUSE]
In the frame is the character from the reference image: a cream-beige fuzzy plush figure with a hood-like furry head, a smooth pale oval face, two small glossy black bead eyes, soft pink cheeks, a tiny curved line for a smile, rounded mitten-like arms with no fingers, short stubby legs and a pear-shaped body. It is about 1 m tall.
It peeks out from behind a pillar at the edge of the storefront, raising one mitten hand in a cheerful wave.
It keeps a matte felt plush texture; it is not a real animal, not realistic fur, not a person in a costume.
It is lit by the same light as the scene: flat daylight from the front, the side away from the store glass in soft shadow. It casts a soft contact shadow on the concrete sidewalk.

[AVOID]
No golden-hour glow unless stated, no light rays, no heavy background blur, no oversaturated colors, no logos or brand names, no fake Japanese characters, no fingers on the character, no open mouth, no people looking at the camera, no faces in sharp focus, no postcard-perfect symmetrical composition.
No store logo or name, no readable shelf labels or posters on the glass.
```

The result of this prompt is `examples/convenience-store-noon.webp` — judged in QA as the strongest combination in the pack (see the field notes, "What tested strongest").

Time-of-day presets:

- Morning: early morning, soft low sun, long cool shadows, a quiet, slightly hazy air. Suits: shrine approaches, shopping streets before opening, station platforms.
- Midday: midday, flat overcast light, or harsh midday sun with hard shadows. Suits: crowds at landmarks, eating while walking. Overcast midday is less likely to look fake than sunny midday.
- Night: night, lit by {a specific light source}, deep shadows, visible noise. Suits: alleys, izakaya, convenience stores, crossings.
- Golden evening light is the light AI makes most "artistic." Avoid it unless specified.
- For 3 images in one day, keep the same weather and vary the framing — "morning wide, midday medium, night close" — so they don't read as repetitions.

Muse action presets and cautions:

- **A peace sign causes breakage.** Making fingerless mitten hands do a peace sign makes the model grow fingers. If there is no official peace-sign depiction, substitute "raising one hand": raises one mitten hand in a cheerful wave. "no fingers" in the AVOID section is mandatory.
- Dango: holds up a skewer of three-colored dango, one dango already missing. Show that it has been eaten by "one already missing," not "in the middle of eating" (this prevents a mouth from being drawn).
- A warm can: holds a slim short Japanese drink can with both hands, label turned away, faint steam. "slim short Japanese" and the label direction prevent the can from becoming a Western type.
- Sitting: sits on the edge of a bench, legs dangling. The proportions change, so restate the height as "sitting height about 60 cm."
- Looking up: looks up at {the object}, seen slightly from behind. A diagonal rear view avoids face breakage.
- Waiting: stands at the curb waiting for the light. The most stable of the everyday actions.

### Variations in how Muse appears (2026-11-13, specified by the user)

Don't use the standard form — "standing full-body in the foreground" — every time. Mix in irregular appearances:

- Close-up: a close-up of the face (large, from the edge of the frame)
- Only the face emerging from behind something (e.g., peeking out from behind/beside a vending machine)
- Diagonal back view, or over-the-back view
- Small, in a corner of the frame

The size standard (about 1 m, fixed) does not change. Only the field of view and the way Muse appears change.

## 3. Adjustment points by place type

The overall picture: everyday places look fake through broken details (text, logos, the shapes of fixtures), and the "correct" shape is loosely defined (close enough passes). Their weakness is that they easily become "could be anywhere" images. The countermeasure is to blur the detail text and add traces of life specific to that place. Famous places look fake through symbolization (poster composition), structural breakage in buildings, and the handling of people — and the "correct" shape is strict (anyone who has seen the place can tell at a glance). The countermeasure is to abandon the full view and let a single key feature, shown partially, carry the place.

Everyday places:

- **Convenience store**: what breaks is the logo, the text on shelves, the notices on the glass. Shoot from outside the store, with the interior through the glass as the background. Two time presets work. Night: the bright interior glowing against the dark street. Midday — currently the strongest combination in QA — flat daylight, the interior visible through the glass, and the everyday clutter in front of the store (drink cases, a vending machine, parked bicycles) doing the place-work; Muse peeks from behind a pillar. Cut the logo at the edge of the frame or blur it. Leaving only the color band (green and blue, blue and white, etc.) conveys "that convenience store" without a brand name. Having a specific chain's logo drawn should also be avoided for rights reasons. Props: a steamed pork bun, an onigiri (in film packaging), a can from the hot shelf.
- **An alley with a vending machine**: works as in the prototype. The red "あったか〜い" ("hot") label on the buttons — show only the color, out of focus.
- **Yamanote Line platform**: what breaks is the station name sign (text) and the train's face and window rows. Keep the station sign out of frame. Convey the place with the yellow tactile paving, part of a platform door, a bench, and the sky on the track side. For the train, show only the blurred yellow-green stripe of its side while it arrives. People: commuters' backs, far away.
- **An ordinary izakaya**: what breaks is the text on red lanterns and the menu strips on the wall. Move in close on the tabletop. Place a draft beer mug, the small otoshi appetizer dish, a hand towel, and a chopstick wrapper around the main subject, and blur the walls. Lighting: warm tungsten, leaving the color cast in.
- **Don Quijote (Donki)**: the flood of handwritten POP cards is a breeding ground for text breakage. The penguin mascot touches character rights, so don't include it. The key is the flood itself, verbalized into six elements in the field notes: the ceiling as a display surface, zero blank space, giant price numbers and short shouted copy repeated as rhythm, red/black/yellow plus fluorescent white, maze-like aisles with changing genres, layers of multilingual POP. At this density, short copy that renders correctly raises realism; garbled product names and long text are the failure — blur those. The oppressive feeling of compressed displays stacked to the ceiling is the key to Donki-ness. Don't show the store name.
- **A tip common to everyday places**: because they easily become "could be anywhere" images, pin down the neighborhood with {AREA} and add one thing that carries that neighborhood's air (in an old downtown area, potted plants and a bathhouse chimney; in a suburb, a parking lot and utility poles).

Famous places:

- **Senso-ji**: what breaks is the text on Kaminarimon's giant lantern, the gate's structure, and the Nakamise signs. Avoid the frontal full view of Kaminarimon; choose one of: looking up from directly beneath the giant lantern (the carved dragon on its underside is visible, the lettering is not), standing Muse in the smoke of the incense burner in front of the main hall, or holding a ningyo-yaki cake on a Nakamise side street.
- **Shibuya Scramble Crossing**: what breaks is the faces, arms and legs of the crowd, and the text on building screens and signs. Shoot Muse waiting at the curb from a low position. Blur the crowd mid-crossing, and cut the signs at the top. At night or in the rain, overlapping umbrellas and smeared light hide almost all detail breakage.
- **Takeshita Street**: what breaks is garbled text — and a quiet, empty street, which is itself off-key here. The key features, read off real photos in QA (field notes, correction 10): the interlocking brick-pattern paving (not asphalt), the flower-motif entrance arch as the landmark, loud pink signage and a crepe stand's display case packed in densely, a gentle downhill slope, and a crowd of young visitors even in the morning. Shoot from under or just inside the arch, looking down the slope into the crowd; short, correctly rendered text may stay readable.
- **Kyoto temples and shrines**: Fushimi Inari's Senbon Torii — "the same thing repeated" — is what AI breaks most easily. The spacing of the pillars goes irregular and the donors' names bleed. Shoot diagonally through the tunnel with focus only on Muse and the gates blurred in the distance. The lettering is written only on the back side of the pillars (as seen facing uphill), so shooting facing uphill keeps the lettered sides mostly out of view. At Kiyomizu-dera, show Muse and the Kyoto cityscape over the railing rather than the full view of the stage. Moss gardens and stone-paved slopes have simple structures and rarely break.
- **Miyajima**: the great torii is so famous that errors in its shape (the number of pillars, whether it has supporting legs) are immediately apparent (it is a ryobu torii, with supporting legs in front of and behind the main pillars). Place the great torii small, in the distance, over the sea. Make the main subjects the deer and Muse in the foreground, or grilled oysters and momiji manju on the pier or the shopping street. Specifying high tide or low tide suddenly makes it feel real.

## 4. Meiji Jingu (an individual deep dive)

It works. The key is how you choose the key feature and the framing.

- The biggest pitfall is the color of the torii. Write "torii" and AI will almost certainly make it vermilion. Meiji Jingu's torii are Myojin-style gates of unpainted plain wood (Taiwan cypress). If you don't state it, the image becomes a different shrine in that instant.
  `a massive unpainted natural-wood (plain cypress) torii gate, weathered grey-brown wood, NOT vermilion, NOT red`
- What to shoot (in order of least likely to break): (1) The wide gravel approach through the forest. A simple structure that almost never breaks. Broom-swept lines in the gravel in the morning, dappled light, large tree trunks. The safest. (2) The base of a great torii pillar. The pillar's thickness conveys the scale, and cutting the top (the kasagi crossbeam) out of the frame lowers the risk of structural breakage. (3) The wall of donated sake barrels (komodaru) and the row of wine barrels. Popular with overseas visitors, but the kanji labels on the barrels break easily — shoot diagonally, out of focus, and show them as a row of colors. (4) The married couple camphor trees, the purification fountain, the ema plaque racks. Ema have text, so blur them at a distance or show their backs. (5) The main hall / worship hall. The most breakable. If used at all, show only the edge of the verdigris copper roof, pillars, and part of the gravel.
- Framing and subject placement: avoid frontal symmetry. Shoot diagonally from the edge of the approach, from a position where only one pillar of the torii enters the frame. Look up and cut the top. Placing Muse in the foreground and shooting from low, so the pillar exits through the top of the frame, conveys the scale and avoids having to draw the breakable kasagi and gakuzuka. A back view is also effective (Muse walking away down the approach, seen diagonally from behind, prevents face breakage and matches the meaning of the experience — "revisiting on your behalf"). Include only a few people, small and blurred, far down the approach. A completely empty approach looks fake.
- Cultural care: no peace signs and no eating or drinking in front of the worship hall. On the approach, bowing, looking up at the sky, and waving are safe. Don't have Muse drink water at the purification fountain (it reads as a breach of etiquette). Don't make the faces of shrine priests, shrine maidens, or wedding processions the main subject. Don't depict the inside of the worship hall (to avoid looking like a photo of a place where photography is prohibited).
- Prompt example (morning): the gravel approach, late autumn, soft early-morning light with dappled sun. At the right edge, only the base of a plain-wood great torii pillar, its top cut by the frame. Broom-swept lines, fallen leaves, a low wooden fence. Small, blurred worshippers in the distance. Muse stands on the gravel slightly left of center, looking up at the pillar (three-quarter back view). Light: soft morning light from the upper left, a warm sunlit patch on the head. Contact shadow present. (Summary here; the full text is in the original Opus answer.)

## 5. Getting the handwritten line in without breaking it

- **Recommended: generate only the photo, and composite the text in afterwards.** The most reliable approach, and stable as a mass-production system. Generate only the photo part (portrait orientation, the upper ~80%). For compositing, lay out the cream-colored paper band at the bottom and the handwritten line with a program (Pillow, or HTML-to-image conversion) in the same layout every time. Handwriting-style font candidates: Google Fonts' Caveat, Patrick Hand, Kalam (understood to be under commercial-use licenses, but check the license text before adopting). For a handwritten feel: rotate each word by ±1 degree, wobble the text baseline by ±1–2 px, add slight ink fade. Advantages: zero spelling errors, no regeneration needed to swap the line, and the band's color and size are uniform across all postcards.
- If you have the generator draw it: keep the line to about 6 words, using short, common words ("Still here, still warm." is a good length). Put it in quotes as "the exact text," with "nothing else written." Put the text on a plain paper band (it breaks more easily overlaid on the photo). Say "single line, centered" to prevent line breaks. Avoid apostrophes, dashes, and emoji. Generate several and pick the one with correct spelling.
  `On the plain cream paper band at the bottom, handwritten in black felt-tip pen, the exact text: "Still here, still warm." — single line, centered, nothing else written on the band.`
- How to write the line: don't include the place name (the photo speaks). Include the feel of the time of day (morning: "Morning again." / night: "Still here, still warm."). If the visitor has a memory of their own, a line that quietly answers it strengthens the feeling of "revisiting on your behalf."

## 6. How to spot failures (checklist)

If even one applies, redo it:

- Muse: fingers have grown / the hands are not mitten-shaped. The mouth is open, or there are teeth or a tongue. The shape of the eyes, cheeks, or head differs from the reference image. It looks like a realistic animal's fur, or like a costume (a person inside). The height is clearly off from the decided size.
- Compositing: no contact shadow at the feet, so Muse looks like it's floating. The direction or color of the light on Muse contradicts the background's light source.
- Background: there is readable (or nearly readable) Japanese-like gibberish text. A real brand's logo or mascot, or an existing character, appears. A torii's color differs from the real one, or the number or shape of pillars is wrong. People's faces or hands are melting, or are shown sharp and from the front.
- Culture: eating/drinking or a peace sign in front of a worship hall, drinking at a purification fountain, or other disrespect or breaches of etiquette. It looks like the inside of a place where photography is prohibited.
- The handwritten line (when drawn inside the image): even one difference in spelling, punctuation, or capitalization. Any text beyond what was specified.

Minor issues — allow them, judging by degree:

- Photo-likeness: the blur is too strong and it looks like a DSLR shot. The saturation is too high, or golden evening light or light rays have crept in uninvited. The composition is perfectly symmetrical and looks like a poster. Everything is uniformly over-detailed, or conversely it's too clean, with no traces of life.
- Place-likeness: is there exactly one key feature that makes someone who has been there think "ah, that place"? (Too many and it becomes a poster.) Do the season, weather, time, and light agree? At a famous place, has the crowd dropped to zero?
- Series (3 images in one day): does the light progress through morning, midday, night? Is the weather consistent as one day? Are all three the same composition and the same distance?

### Two separate pass conditions (added 2026-11-13 from the Kotonoha review)

- Is the image free of breakage? (the checklist above)
- **Can someone who has visited the place recognize it as that place?** — Even if piling up breakage-hiding treatments (cutting, blurring, distant views) succeeds, an image whose place cues have disappeared is not adopted into the pool. As reinforcement, attach a small place-name caption to each postcard (the name does not excuse inaccuracy).

### Allocating the imperfection (also added from the review)

- Don't apply every "unpolished" element (tilt, cropping, noise, low position, etc.) to every image. **Choose only 0–2 kinds per image.** If every photo has the same quirks, it reads as "clumsy AI photos, always clumsy in the same way." The ~1 m camera height is a reference for Muse's sense of size; it does not mean fixing every photo's shooting height (include variety too: looking up, table height, etc.).

Suggested approach: don't roll out to every place at once. Generate several images each, with the same fixed text, for one everyday place, one famous place, and Meiji Jingu × morning/midday/night — 9 images — and measure the yield against the checklist. Strengthen the AVOID section of the fixed text only for the items with poor yield (usually text, torii, and fingers). If the visitor has their own travel photos, using one as a background reference image can greatly raise a famous place's accuracy (but decide in advance how to handle other people's faces appearing in them).

## 7. Can famous sights be kept up "always"? (answer to the follow-up)

Conclusion: **it cannot be said that prompt craft alone can keep them up "always."** That said, most famous places hold up stably if they follow the types. How easily a place holds up is decided by what is remembered about it. If the memory is an experience or an atmosphere (a forest approach, a crowd, a bamboo grove), it held up comparatively reliably in this pack's QA. If the memory is the shape of the building itself (the great torii, the Golden Pavilion, the full view of Tokyo Tower), the risk that the shape drifts with each generation remains. The realistic answer, as a system, is to "decide in advance, for each famous place, a way of shooting it that is hard to break and still recognizable (a place card)" and to "have a rule for lowering the shot by one level when it fails." A real-photo reference image is the most effective single measure, but the conditions for using one are limited.

Why famous places look fake:

1. AI's image of a famous place is made of "the average of postcards." Because training photos skew toward front views, fine weather, and full views, an unspecified request produces the average image, and it feels like "a poster."
2. Exact shapes are demanded. Repetitions of the same part (Senbon Torii, a steel tower's lattice, rows of roof tiles), bilateral symmetry, pillar counts, and fixed proportions are what AI breaks most easily. In an everyday scene a drift still passes; at a famous place, anyone who has seen it can tell immediately.
3. The average image drifts from the real thing. Places get pulled toward type — torii are vermilion, castles are black, temples are gold (Meiji Jingu's plain wood → vermilion is the textbook case).
4. Text and crests are part of the famous place (the Kaminarimon lantern, plaques, signs). They break easily and also carry trademark issues.

A four-way classification of famous places:

- **Type A — atmosphere/experience**: the memory is the feeling of walking, the light, the crowds. Examples: the Meiji Jingu approach, the Arashiyama bamboo grove, the Dotonbori riverside, shopping streets, the Shibuya crossing. Ease of holding up: high. Specify the light and the crowd density correctly and it was the most stable type in this pack's QA.
- **Type B — recognizable by a part**: the memory is one distinctive part. Examples: the Kaminarimon giant lantern (looking up from below), inside the Senbon Torii, the railing of Kiyomizu's stage. Ease: medium to high. Shoot only the key part, from an angle that is hard to break.
- **Type C — the shape itself**: the memory is the whole building's shape. Examples: Miyajima's great torii, the Golden Pavilion, Tokyo Tower, Himeji Castle, a five-story pagoda. Ease: medium to low. Don't shoot the full view from the front; keep it small in a distant view, diagonal, or partial. A real-photo reference image helps most.
- **Type D — text/signage**: the memory is the sign or logo itself. Examples: the Dotonbori Glico sign, Shibuya 109. Ease: avoid. Don't draw them, for rights reasons too. Replace with a Type A shot of the same place.
- Type C is not unshootable. The basics: because making the building the main subject makes breakage conspicuous, make Muse the main subject and pull the building back to "just enough to tell where it is."

The place card (made once per famous place, 7 items): ① type (A–D) ② key feature (only one. Two or more and it becomes a tourist poster) ③ facts that differ from the average image (color, material, count, roof color, water level, how the season looks — write down the points where AI gets pulled toward the average) ④ angle (never the frontal full view. Cut the top / diagonal / looking up / small in a distant view / over Muse's back) ⑤ how to handle the breakable elements (text, repeated parts, symmetry, and how to let them escape) ⑥ crowd density (match the real crowding) ⑦ action restrictions (actions to avoid at religious sites and historic sites, places that must not be shown).

Slotting a card into the prompt: use the main template in §2 — there is only one template. The card's five variables go at the head of [PHOTO] in the order SPOT_DESCRIPTION → KEY_FEATURE → FACTS_AGAINST_STEREOTYPE → ANGLE_AND_CROP → PEOPLE, and the card's AVOID is appended after the template's common AVOID text. Resolve nested variables inside the card text ({AREA}, {TIDE}, {SEASON}) first. §2's worked example shows the fully substituted form.

Applying this to the main famous places:

- Meiji Jingu: type A (the torii is C). Key features: the gravel approach, the base of the plain-wood great torii pillar. Fact that differs: the torii is plain wood, not vermilion. Handling: cut the top of the torii at the top of the frame. The approach, over Muse's back. Don't use a full view of the worship hall.
- Senso-ji: type B. Key feature: the giant lantern from directly below. Fact that differs: an angle where the lantern's lettering is not shown. Handling: looking up. Blur the main hall through the incense burner's smoke.
- Fushimi Inari: type B. Key feature: inside the Senbon Torii. Fact that differs: the lettering is only on the back side of the pillars. Handling: shoot facing uphill. Blur the gates in the distance; focus only on Muse.
- Miyajima: type C. Key features: the great torii over the sea (small, in a distant view), a deer in the foreground. Facts that differ: it is a ryobu torii (with supporting legs); high tide or low tide. Handling: keep the torii small; the main subjects are the deer and Muse in the foreground.
- Kinkaku-ji (the Golden Pavilion): type C. Key feature: the pavilion across the pond. Fact that differs: the gold is only on the upper two stories; the first story is not gold. Handling: over Muse's back from in front of the pond fence; keep the pavilion small and don't place it front and center.
- Tokyo Tower: type C. Key feature: the red-and-white steel tower. Fact that differs: the steel lattice breaks easily. Handling: show only the upper half peeking between buildings, or blur it with night lights.
- Himeji Castle: type C. Key feature: the white keep. Fact that differs: white plaster (don't let it drift to a black castle). Handling: in a distant view, over a gate or stone wall. Foreground: the stone wall and gravel.
- Arashiyama bamboo grove: type A. Key feature: the bamboo path. Fact that differs: it is actually crowded. Handling: include a few people. Morning light.
- Dotonbori: type A (the signs are D). Key feature: the riverside promenade and the smear of neon. Fact that differs: don't draw the signs. Handling: at night, show the neon as blurred colored light.

Systems for getting closer to "always":

- A rule for lowering the shot by one level on failure: full view → (1) show the key feature partially (Type B) → (2) shrink the key feature into a distant view → (3) show a fragment → (4) drop the key feature and shoot only the place's atmosphere (Type A: the approach, the crowd, a famous food). Decide a count — "if the torii's shape doesn't match after 3 remakes, drop to (2)" — so that a postcard never fails to arrive. But the lowering has a floor: at every step, the result still has to pass §6's recognizability check — someone who has been there must be able to tell it is that place. If a lowered shot no longer reads as the place, don't ship it under that place's name; at most it is an unnamed neighborhood scene. A place-name caption does not rescue an unrecognizable image.
- Real-photo reference images (the most effective method): using the visitor's own travel photos as background references can greatly raise accuracy and strengthens the experiential meaning of "the place I photographed myself." Decide the handling of other people's faces in advance. If the operator prepares reference photos for each famous place, confirm permission to use them. Avoid using strangers' photos from the internet as references without permission. How faithfully the generation model can use a reference image is to be confirmed with prototypes.
- A first check for each famous place: once a place card is made, have someone who knows the place check only the first few images. Errors in "facts that differ from the average image" can't be spotted by someone who doesn't know. A checked card can be reused, so the effort is once per famous place.
- Summary: Type A was the most stable with the template alone in this QA. Type B is stable once the key feature and angle are fixed. For Type C, prompts alone cannot guarantee accuracy every time (combine: small in a distant view, Muse as the main subject, the lowering rule, real-photo references). Type D: don't draw it; replace with Type A.
- Additional offer from Opus: the place cards for about 20 major famous places can also be compiled into a table.
