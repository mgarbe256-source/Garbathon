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
| Scene 3 | https://d2ol7oe51mr4n9.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/a5fd59f1-78be-4658-b187-d83b0434bba4.mp4 | Golf course scene. **Current final** — fixed two issues: (1) the group composite had everyone squished (aspect-ratio distortion from the compositing step), rebuilt with uniform per-person scaling; (2) Cindy's dialogue expressions were too extreme, regenerated with a calmer/more restrained performance prompt. Soul `109038a8-af80-46fd-b663-11dddd1334d9` (informally "Cindy-3") remains her correct identity throughout. |

## Revision history (Scene 3, golf course)

1. `5a3106ff-f5ef-438f-9c98-bf8778fd5dec` — original 4-clip assembly (wan2_7 voice-converted dialogue)
2. `5ad30173-ee1f-40f2-a20b-6ffdd7b0e916` — re-ran Cindy's voice_change conversion (2nd pass)
3. `fd169628-acf9-40f0-b82e-aba3edb7f3b2` — switched Cindy to direct clone TTS (seed_audio), but 4s video duration truncated the audio, cutting off her last words
4. `c9579552-9b5a-4a0f-90eb-9073056c8c11` — fixed by regenerating at 6s duration so the full TTS line (5.06s) fits without truncation
5. `2b3b4a4b-81df-4268-96f1-a51a8a8a990d` — **current final** — added whoosh-of-air sound to teleport-in and raven teleport-out (both were silent `kling3_0` generations). Uses soul `109038a8...`, the user-confirmed correct Cindy identity.
6. `72a2e75f-b041-4e57-88a6-78cb177836b2` — **mistake, reverted.** Misread user feedback as "wrong soul used" and swapped Cindy to the `Cindy-3` *reference element* (a single photo, id `012604f1-e131-4498-a149-79853edda1e1`) instead of the correct trained Soul. User confirmed afterward that soul `109038a8...` ("A" in the comparison sheet, already in use) was right all along, and that "Cindy-3" refers to a named Soul, not that reference element. Do not reuse `012604f1...` as Cindy's identity.
7. `a5fd59f1-78be-4658-b187-d83b0434bba4` — **current final** — the actual issues with the golf scene turned out to be (a) the group composite had visibly squished people (the original manual PIL compositing script apparently stretched aspect ratio per-person), fixed by rebuilding with a single uniform scale factor per person (no independent x/y stretch); (b) Cindy's dialogue close-up had overly extreme facial expressions, fixed by regenerating with a calmer/more restrained performance prompt (same close-up source image and same clone-voice audio, only the `wan2_7` prompt changed). Both teleport clips were regenerated using the un-squished, re-harmonized composite as their endpoint image.

**Naming note:** the user refers to Cindy's correct identity informally as "Cindy-3." This maps to soul_id `109038a8-af80-46fd-b663-11dddd1334d9` — NOT the reference element of the same name (`012604f1-e131-4498-a149-79853edda1e1`), which is a different, unrelated asset. Use the soul_id for any future Cindy generation.

## Revision history (Scene 2, kitchen)

1. `fa3a320e-ad62-4ae6-ba5f-58832a3e1d62` — original assembly; teleport-in and teleport-out both silent (`kling3_0` generated with `sound: "off"`)
2. `0e130563-94f6-4fa3-a4f5-df624920ab26` — **current final** — regenerated both teleport clips with `sound: "on"` and a whoosh-of-air audio prompt, spliced around the original (untouched) dialogue segment

## Experiments / alternates (not scene finals)

Not part of the numbered scene sequence — side comparisons kept here so the links
aren't lost, same as everything else.

| What | Link | Notes |
|---|---|---|
| Seedance 2.0 take on Scene 2's teleport-out | https://d2ol7oe51mr4n9.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/f4cc1a7a-5777-44fe-8554-f3af563c58af.mp4 | Same kitchen source image and teleport-out premise as Scene 2, rendered by `seedance_2_0` instead of `kling3_0`, using its own native audio generation instead of a manual whoosh-sound prompt trick. For comparison only — Scene 2's actual final still uses the `kling3_0` version above. |
