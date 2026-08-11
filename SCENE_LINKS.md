# Scene Links

Direct links to the final assembled scene videos for the Higgsfield short. These are
uploaded media assets (built by concatenating individual generated clips with ffmpeg,
then uploaded to Higgsfield) — they are **not** Higgsfield generations, so they won't
appear in a generation history/gallery. Bookmark this file, or use the links directly.

Confirmed correct by the user on 2026-08-11 — this is the real numbering.

| Scene | Link | Notes |
|---|---|---|
| Scene 1 | https://d2ol7oe51mr4n9.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/6fc59d66-bba7-4e20-b3e2-56846fbdbcdd.mp4 | Confirmed correct by user. Teleport-out reportedly has a good sound effect already. |
| Scene 2 | https://d2ol7oe51mr4n9.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/0e130563-94f6-4fa3-a4f5-df624920ab26.mp4 | Kitchen scene. **Current final** — teleport-in and teleport-out were both silent; regenerated both with a whoosh-of-air sound effect and spliced back around the untouched original dialogue segment. Original (silent teleports) version: `fa3a320e-ad62-4ae6-ba5f-58832a3e1d62`. |
| Scene 3 | https://d2ol7oe51mr4n9.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/2b3b4a4b-81df-4268-96f1-a51a8a8a990d.mp4 | Golf course scene. Teleport-in and raven teleport-out have whoosh-of-air sound added (this was originally done under the mistaken belief it was "Scene 2" — it's actually Scene 3, but the sound fix is a valid improvement regardless). Original silent version: `c9579552-9b5a-4a0f-90eb-9073056c8c11`. |

## Revision history (Scene 3, golf course)

1. `5a3106ff-f5ef-438f-9c98-bf8778fd5dec` — original 4-clip assembly (wan2_7 voice-converted dialogue)
2. `5ad30173-ee1f-40f2-a20b-6ffdd7b0e916` — re-ran Cindy's voice_change conversion (2nd pass)
3. `fd169628-acf9-40f0-b82e-aba3edb7f3b2` — switched Cindy to direct clone TTS (seed_audio), but 4s video duration truncated the audio, cutting off her last words
4. `c9579552-9b5a-4a0f-90eb-9073056c8c11` — fixed by regenerating at 6s duration so the full TTS line (5.06s) fits without truncation
5. `2b3b4a4b-81df-4268-96f1-a51a8a8a990d` — **current final** — added whoosh-of-air sound to teleport-in and raven teleport-out (both were silent `kling3_0` generations)

## Revision history (Scene 2, kitchen)

1. `fa3a320e-ad62-4ae6-ba5f-58832a3e1d62` — original assembly; teleport-in and teleport-out both silent (`kling3_0` generated with `sound: "off"`)
2. `0e130563-94f6-4fa3-a4f5-df624920ab26` — **current final** — regenerated both teleport clips with `sound: "on"` and a whoosh-of-air audio prompt, spliced around the original (untouched) dialogue segment
