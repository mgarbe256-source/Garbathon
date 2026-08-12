# Scene Links

Direct links to the final assembled scene videos for the Higgsfield short. These are
uploaded media assets (built by concatenating individual generated clips with ffmpeg,
then uploaded to Higgsfield) — they are **not** Higgsfield generations, so they won't
appear in a generation history/gallery. Bookmark this file, or use the links directly.

**Standing practice (per user instruction, 2026-08-11):** this file is the living
record of every scene's current final version. It gets updated immediately whenever
a scene changes — no separate request needed each time.

Confirmed correct by the user on 2026-08-11 — this is the real numbering.

| Scene | Link | Notes |
|---|---|---|
| Scene 1 | https://d2ol7oe51mr4n9.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/6fc59d66-bba7-4e20-b3e2-56846fbdbcdd.mp4 | Confirmed correct by user. Teleport-out reportedly has a good sound effect already. |
| Scene 2 | https://d2ol7oe51mr4n9.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/0e130563-94f6-4fa3-a4f5-df624920ab26.mp4 | Kitchen scene. **Current final** — teleport-in and teleport-out were both silent; regenerated both with a whoosh-of-air sound effect and spliced back around the untouched original dialogue segment. Original (silent teleports) version: `fa3a320e-ad62-4ae6-ba5f-58832a3e1d62`. |
| Scene 3 | https://d2ol7oe51mr4n9.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/84a34caf-a7c7-41d9-9cb3-950a9260495d.mp4 | Golf course scene. **Current final** — rebuilt both teleport clips from scratch using a new technique (reverse-generation for the exit, see revision 10 below) to get natural motion without the squish. **Not yet visually confirmed by the user.** Soul `109038a8-af80-46fd-b663-11dddd1334d9` (informally "Cindy-3") remains her correct identity throughout. |
| Scene 4 | *in progress — see revision history below* | Marriott Pinnacle hotel arrival, Vancouver. Teleport-in, costume-transformation, and sky-burst clips built; dialogue clips still pending user's recorded audio. Not yet assembled into a full scene. |

## Revision history (Scene 3, golf course)

1. `5a3106ff-f5ef-438f-9c98-bf8778fd5dec` — original 4-clip assembly (wan2_7 voice-converted dialogue)
2. `5ad30173-ee1f-40f2-a20b-6ffdd7b0e916` — re-ran Cindy's voice_change conversion (2nd pass)
3. `fd169628-acf9-40f0-b82e-aba3edb7f3b2` — switched Cindy to direct clone TTS (seed_audio), but 4s video duration truncated the audio, cutting off her last words
4. `c9579552-9b5a-4a0f-90eb-9073056c8c11` — fixed by regenerating at 6s duration so the full TTS line (5.06s) fits without truncation
5. `2b3b4a4b-81df-4268-96f1-a51a8a8a990d` — **current final** — added whoosh-of-air sound to teleport-in and raven teleport-out (both were silent `kling3_0` generations). Uses soul `109038a8...`, the user-confirmed correct Cindy identity.
6. `72a2e75f-b041-4e57-88a6-78cb177836b2` — **mistake, reverted.** Misread user feedback as "wrong soul used" and swapped Cindy to the `Cindy-3` *reference element* (a single photo, id `012604f1-e131-4498-a149-79853edda1e1`) instead of the correct trained Soul. User confirmed afterward that soul `109038a8...` ("A" in the comparison sheet, already in use) was right all along, and that "Cindy-3" refers to a named Soul, not that reference element. Do not reuse `012604f1...` as Cindy's identity.
7. `a5fd59f1-78be-4658-b187-d83b0434bba4` — the group composite had visibly squished people (the original manual PIL compositing script apparently stretched aspect ratio per-person), fixed by rebuilding with a single uniform scale factor per person (no independent x/y stretch). Cindy's dialogue close-up had overly extreme facial expressions, fixed by regenerating with a calmer/more restrained performance prompt. Both teleport clips regenerated using the un-squished, re-harmonized composite as their endpoint image.
8. `547b5ff8-3aa3-468b-b6f1-d4a52eea1e59` — v7 still squished the group during the raven teleport-out (kling3_0 re-renders the source image each generation, reintroducing distortion even from a correct input) and Cindy's calmer prompt had accidentally dropped lip-sync guidance, leaving her mouth static. Fixed by (a) extracting the literal last frame of the teleport-in clip and using it as the teleport-out's start_image — guarantees the vanish starts from what's already correctly on screen instead of a fresh re-render, (b) adding "clear synchronized lip sync matching the audio" back into Cindy's prompt alongside the restrained-performance language. **Side effect discovered later:** the frozen-frame trick killed all natural motion in the teleport-out (and by comparison made teleport-in look flat too) — see revision 9.
9. `c8ff77e7-be13-4ca2-bc31-7ff5e3d7c8d2` — **failed experiment, reverted.** Attempted to restore natural motion by feeding the actual corrected composite (not a frozen frame) as start/end image for both teleport clips, plus natural-motion language in the prompts. Result was worse on both axes: the squish came back (confirms feeding the live composite to kling3_0 for regeneration is what causes squishing, independent of which composite image is used), and added narrative language like "friends chatting" in the prompt appears to have bled into kling3_0's native audio generation, producing nonsensical ambient sound. Do not reuse this approach as-is. Reverted final back to v8 (`547b5ff8...`).

**Open problem (as of v9):** getting natural motion (glancing, breathing, weight shifts) into the golf scene's teleport clips without kling3_0 either (a) squishing everyone when it regenerates from a composite image, or (b) picking up unwanted audio from narrative prompt language. The frozen-frame trick (v8) avoids squish by sacrificing all motion.

10. `84a34caf-a7c7-41d9-9cb3-950a9260495d` — **current final** — user asked for a full redo with a new prompt approach. Key observation: teleport-IN (empty start_image → populated end_image) has never squished across any revision; only teleport-OUT (populated start_image → empty end_image) squishes. This suggests kling3_0 holds the *end* image faithfully but takes liberties with a complex populated *start* image during heavy motion (the raven swirl). New technique: generate the raven effect in the *reliable* direction — empty→populated, ravens gathering then bursting apart to reveal the group, same structural pattern as the smoke teleport-in — then reverse the clip (video+audio, `ffmpeg -vf reverse -af areverse`) to get the actual vanish (populated→ravens→empty) for use as the teleport-out. Both new prompts use concrete physical motion cues (weight shifts, head turns, hand/grip adjustments, breeze) instead of narrative/social language (avoiding the "friends chatting" audio-bleed problem from v9), with the "Audio:" instruction kept short and separate. Not yet visually confirmed on either motion or squish.

**Naming note:** the user refers to Cindy's correct identity informally as "Cindy-3." This maps to soul_id `109038a8-af80-46fd-b663-11dddd1334d9` — NOT the reference element of the same name (`012604f1-e131-4498-a149-79853edda1e1`), which is a different, unrelated asset. Use the soul_id for any future Cindy generation.

## Revision history (Scene 4, hotel arrival)

1. `fb823e46-b721-4574-b3e8-13ab50de5f7a` — teleport-in clip. https://d8j0ntlcm91z4.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/hf_20260811_221539_fb823e46-b721-4574-b3e8-13ab50de5f7a.mp4 — Steve, Debbie, Michael, and Cindy (Cindy-2 soul) arrive via raven-flock teleport in front of the Marriott Pinnacle, looking around surprised at their west-coast-casual/flashy-gay outfits. Built with `kling3_0`, empty→populated direction (start_image `93d53018-583f-4514-aad4-bffc76b1cab9`, end_image `8b11387a-8a66-4d85-b965-0058bfa6f98d`, both 16:9 via `outpaint_image`), continuing the raven transition from the end of Scene 3. **Confirmed good by the user.**
2. Superhero costume reference image `e64d4229-fa03-4c6e-95f9-e2e36295a1b1` — https://d8j0ntlcm91z4.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/hf_20260812_000634_e64d4229-fa03-4c6e-95f9-e2e36295a1b1.png — `nano_banana_2` edit of the hotel-arrival composite (`8b11387a...`), changing only clothing to superhero tights/capes (Debbie and Cindy slim but busty), faces/poses/background locked. **Confirmed good by the user.**
3. `4f562be7-0111-4672-8e4f-558973587fd4` — transformation clip. https://d8j0ntlcm91z4.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/hf_20260812_001554_4f562be7-0111-4672-8e4f-558973587fd4.mp4 — group throws hands up, flash of light, reveals superhero costumes. `kling3_0`, start_image `8b11387a...` (hotel-arrival pose) → end_image `e64d4229...` (superhero costumes), 16:9, 6s, native audio (whoosh building to heroic chime). Not yet visually confirmed by the user.
4. `e13a9862-6c07-404b-99db-9318e6b2036c` — **not used in Scene 4 — reserved for Scene 5.** First sky-effect attempt (nod-pose group, light descends and lands, reversed to ascend). User confirmed the underlying "light from the sky, land in front of the hotel" effect is good but wants it saved for Scene 5's teleport instead of used here.
5. `95cccd62-489f-4b4d-aa77-6f96948e3b6a` and `d75d5982-2bb8-43e6-aef7-91342802f75d` — **not used in Scene 4 — reserved for Scene 5.** Raw "descend and land" clips (light streak descends from the sky, resolves into the group landing), built as the reliable empty→populated half of the reverse-generation technique. `95cccd62` lands in a nod pose (paired with `e64d4229` costume image); `d75d5982` lands in the "look up, one arm raised" launch pose (paired with new pose image `a3cee483-2d28-4dba-ac65-931e47f4339a`, itself a `nano_banana_2` edit of `e64d4229` changing only the pose). Both are landing motion — kept here as raw material for Scene 5, not reversed for Scene 4.
6. `b10f6c68-c951-42e0-af73-6e384bfda0fc` — **current Scene 4 ending clip.** https://d2ol7oe51mr4n9.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/b10f6c68-c951-42e0-af73-6e384bfda0fc.mp4 — the group looks up, raises one hand to the sky, then blasts off upward and vanishes. Built by reversing `d75d5982` (video+audio, `ffmpeg -vf reverse -af areverse`) so the "look up, hand raised" landing pose becomes the launch starting point and the descent motion plays backward as a takeoff. Not yet visually confirmed by the user.

**Script (confirmed 2026-08-12):**
- Cindy: "I don't see him anywhere."
- Debbie: "I thought for sure he would be here. He is always here!"
- Steve: "I feel like we have looked everywhere. Where else can he be?"
- Michael: "Wait, of course, I know where he is. It is going to be a long trip so we need to change clothes."
- Ending: cut back to the group in their hotel-arrival pose/framing, they throw up their hands, a flash of light transforms them into superhero costumes (tights and capes; Debbie and Cindy slim but busty), they look up, raise one hand to the sky, then blast off upward with matching audio. **Transformation clip (3) and blast-off clip (6) built.**

**Dialogue audio (voice-converted, ready for lip-synced video generation):**
- Cindy: `56f9787a-4aec-48b0-add7-076ac9506680` — user's recorded line run through `voice_change` with Cindy-2's clone voice (`62792e14-4627-42b2-8f45-d18c82116987`), preserving the user's original timing/emotion.
- Debbie: `a4980c4a-31c4-453f-99c5-a7b18dbb999e` — same technique, Debbie's clone voice (`4035a2e6-5c8d-475f-81a5-7a5affb9ccb8`).
- Steve: `df896333-2d09-4b9f-a537-bb5cd55789bc` — same technique, Steve's clone voice (`4554f8fb-4340-452f-902e-c00936d9b476`).
- Michael: `05ee7afa-29f9-42e4-8b87-456950c1ed25` — user's own recorded line, unconverted (Michael is the user's own likeness/voice).
- Technique: each line was wrapped in a silent placeholder video (`ffmpeg -f lavfi color=black` + the audio), run through `voice_change` (video-based, preserves timing/performance unlike text-to-speech), then the converted audio track was extracted back out via `ffmpeg -vn`.

**Dialogue video clips — attempt 1 (wrong, not used):** `9ce73ad5...`, `062f5a74...`, `caf50359...`, `11163362...` — all four wrongly used the wide 4-person group composite as start_image instead of an individual close-up. Superseded by attempt 2 below; do not use.

**Dialogue video clips — attempt 2 (wrong, not used):** `edfff56d...`, `b904e71a...`, `19032942...`, `44282a09...` — close-up framing was right, but `nano_banana_pro` cropping individual people out of the 4-person group composite lost/scrambled facial identity (user reported the "Debbie" clip actually showed Cindy) and `wan2_7` produced static, non-moving mouths on these degraded source images. Superseded by attempt 3 below; do not use.

**Dialogue video clips — attempt 3:** built via close-ups generated directly from each character's trained Soul (`soul_2` + soul_id) instead of cropping the group photo.
8. Debbie — `a99efb3b-4793-4fa2-87b1-fb2d3e70cab9` — https://d8j0ntlcm91z4.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/hf_20260812_015343_a99efb3b-4793-4fa2-87b1-fb2d3e70cab9.mp4 — **CONFIRMED GOOD by user.** Close-up source `100dfd02...` (soul `52c6956c...`).
9. Steve — `2bab12ce-653f-4a95-9b02-525b60512ed0` — https://d8j0ntlcm91z4.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/hf_20260812_015343_2bab12ce-653f-4a95-9b02-525b60512ed0.mp4 — **CONFIRMED GOOD by user.** Close-up source `1a52b6cd...` (soul `00ee0321...`).
7. Cindy — `fd106e02-fa90-4405-aa21-f0dfbae27f3c` — **WRONG, not used.** User reported face still not good and mouth not lip-synced to the audio despite Soul generation. Superseded by attempt 4 below.
10. Michael — `503dbe1a-2576-4a4d-b041-bfb2a6ac031e` — **WRONG, not used — serious failure.** Soul generation (soul `1d71accb...`) rendered Michael as a different person of a different race entirely, despite using his correct, established soul_id. Superseded by attempt 4 below.

**Dialogue video clips — attempt 4 (wrong, not used):** Cindy `66e125ad...`, Michael `12733092...` — used elements Cindy-Confirmed and Michael-Arborist. User reported both still wrong. Superseded by attempt 5 below.

**Dialogue video clips — attempt 5 (wrong, not used):** Cindy `5932622f...`, Michael `46743959...`. Per user's explicit instruction, used elements **Cindy-2-Ref** and **Michael1** — Michael's face was acceptable this time ("will do") but his outfit and background were generic/random instead of matching the actual scene (root cause: the `nsfw`-moderation dodge forced a plain "standing outdoors" prompt with no scene-specific detail). Cindy's face was still wrong. Superseded by attempt 6 below.

**Dialogue video clips — attempt 6 (Cindy + Michael only, current):**
7. Cindy — `322e01df-0e90-4346-9c54-30443561293c` — https://d8j0ntlcm91z4.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/hf_20260812_023047_322e01df-0e90-4346-9c54-30443561293c.mp4
10. Michael — `429fe422-50bd-49e8-949c-b0118b0edb8e` — https://d8j0ntlcm91z4.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/hf_20260812_023047_429fe422-50bd-49e8-949c-b0118b0edb8e.mp4

Fixed differently for each: **Michael** — kept his accepted face (element Michael1) but fixed continuity by editing his actual group-photo crop (`1ffe23d3...`, correct flashy outfit + real hotel background from this scene) with `nano_banana_pro`, "change only his face to match <<<Michael1>>>", instead of generating a fresh portrait from scratch (result: `d5cc8e79...`). **Cindy** — the old Cindy Soul used in Scene 3 (`109038a8...`) no longer exists in the workspace ("Character not found"), so instead of guessing another named asset, extracted an actual frame of her confirmed Scene 3 dialogue close-up directly from the real Scene 3 video (`84a34caf...` at 10s) via `ffmpeg`, uploaded it, and saved it as a new reference element **Cindy-Scene3-True** (`d414403b-db95-4959-b654-be9638f5d450`) — ground truth rather than a named guess. Applied the same "edit face onto the real crop" technique as Michael: `nano_banana_pro` on her group-photo crop (`719972ac...`) with "edit this photo so the woman's face matches <<<Cindy-Scene3-True>>>, keep clothing/pose/background the same" (result: `abdf5ed2...`; first attempt at this edit failed outright, second hung indefinitely and was abandoned, third succeeded).

**Dialogue video clips — attempt 6 outcome:** user reported the "Cindy-Scene3-True" frame was actually **Debbie's** face, not Cindy's — the Scene 3 video frame itself was mislabeled/wrong (consistent with Cindy's soul degrading after being confirmed correct on 2026-08-11, per CHARACTERS.md). User also flagged that Steve's and Debbie's attempt-3 clips (pure Soul generation, no real photo/background anchor) had generic outfits/backgrounds not matching the actual scene. User then posted an actual real reference photo of herself (a tree-arborist safety-uniform photo) to settle Cindy's identity definitively.

**Dialogue video clips — attempt 7 (current, all four):**
7. Cindy — `06265e36-200c-45b8-a876-9ae8a726d7e5` — https://d8j0ntlcm91z4.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/hf_20260812_025934_06265e36-200c-45b8-a876-9ae8a726d7e5.mp4
8. Debbie — `abec782c-5307-4463-b043-fcafcb2ef31c` — https://d8j0ntlcm91z4.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/hf_20260812_025934_abec782c-5307-4463-b043-fcafcb2ef31c.mp4
9. Steve — `95118cc7-0829-4d62-acfc-6a8dad639bc7` — https://d8j0ntlcm91z4.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/hf_20260812_025934_95118cc7-0829-4d62-acfc-6a8dad639bc7.mp4
10. Michael — `429fe422-50bd-49e8-949c-b0118b0edb8e` — unchanged from attempt 6 (not flagged wrong this round).

User's pasted photo uploaded and saved as new reference element **Cindy-Real-UserConfirmed** (`fc0f0579-4380-4d07-b02b-d77e647e1d6f`) — the actual ground truth. This also confirmed the naming of the pre-existing "-Arborist" reference elements (Cindy-Arborist, Debbie-Arborist, Steve-Arborist, Michael-Arborist, created 2026-08-09): they are a matched set of real confirmed photos from the same tree-arborist photoshoot, one per character — the correct identity anchors for this whole cast. All three fixed the same way: `nano_banana_pro` edited each character's real group-photo crop (correct outfit + hotel background) to swap in the correct face — Cindy via Cindy-Real-UserConfirmed (crop `719972ac...` → `661ec101...`), Steve via **Steve-Arborist** (`17067706-b952-4945-9101-752b7f4505b2`, crop `caf62d1a...` → `5325e3cc...`), Debbie via **Debbie-Arborist** (`24deec5c-9272-4c4b-b013-7060400235fe`, crop `2b6c8bde...` → `74a0d9d7...`). Not yet visually confirmed by the user.

**Scene 4 dialogue — final set to use:** Cindy `06265e36...` (attempt 7), Debbie `abec782c...` (attempt 7), Steve `95118cc7...` (attempt 7), Michael `429fe422...` (attempt 6).

**Going forward, use these confirmed real-photo identity anchors for any future Cindy/Debbie/Steve/Michael face-fix work:** Cindy-Real-UserConfirmed (`fc0f0579-4380-4d07-b02b-d77e647e1d6f`), Debbie-Arborist (`24deec5c-9272-4c4b-b013-7060400235fe`), Steve-Arborist (`17067706-b952-4945-9101-752b7f4505b2`), Michael-Arborist (`cd90f8bb-0a64-4f6f-8f5b-d1c486b632ab`) or Michael1 (`dc054a58-467c-4599-8ad7-0d25a0b56235`). Prefer editing an existing correctly-composed scene image (real outfit/background) with "change only the face to match <<<element>>>" over generating a fresh portrait from scratch.

**Scene 4 status:** all component clips built (teleport-in, 4 dialogue, transformation, blast-off) — not yet assembled into one final sequence.
- User will record reference audio (for emotion/intonation) before the four dialogue clips are generated.

## Revision history (Scene 2, kitchen)

1. `fa3a320e-ad62-4ae6-ba5f-58832a3e1d62` — original assembly; teleport-in and teleport-out both silent (`kling3_0` generated with `sound: "off"`)
2. `0e130563-94f6-4fa3-a4f5-df624920ab26` — **current final** — regenerated both teleport clips with `sound: "on"` and a whoosh-of-air audio prompt, spliced around the original (untouched) dialogue segment

## Title / graphic assets

Non-scene assets kept for later use in the final edit.

| What | File | Notes |
|---|---|---|
| "Where's Richard?" title card | `title-images/wheres-richard-title.png` | User-made in Gemini (not Higgsfield), since repeated Higgsfield attempts (`soul_2`, `nano_banana_flash`, `seedream_v4_5`) kept either cropping Richard, losing his likeness entirely when Ilana was added as a second reference element, or replacing him with a generic Waldo. User supplied this finished version directly on 2026-08-11 — saved as-is, to be used as a title/intro card later in the edit. |

## Experiments / alternates (not scene finals)

Not part of the numbered scene sequence — side comparisons kept here so the links
aren't lost, same as everything else.

| What | Link | Notes |
|---|---|---|
| Seedance 2.0 take on Scene 2's teleport-out | https://d2ol7oe51mr4n9.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/f4cc1a7a-5777-44fe-8554-f3af563c58af.mp4 | Same kitchen source image and teleport-out premise as Scene 2, rendered by `seedance_2_0` instead of `kling3_0`, using its own native audio generation instead of a manual whoosh-sound prompt trick. For comparison only — Scene 2's actual final still uses the `kling3_0` version above. |
