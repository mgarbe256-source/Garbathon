# Scene Links

Direct links to the final assembled scene videos for the Higgsfield short. These are
uploaded media assets (built by concatenating individual generated clips with ffmpeg,
then uploaded to Higgsfield) — they are **not** Higgsfield generations, so they won't
appear in a generation history/gallery. Bookmark this file, or use the links directly.

## Confirmed scenes

| Scene | Link | Notes |
|---|---|---|
| Kitchen scene | https://d2ol7oe51mr4n9.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/fa3a320e-ad62-4ae6-ba5f-58832a3e1d62.mp4 | Confirmed as the final upload in this scene's revision cluster (verified against generation history timestamps). **Not yet visually confirmed by the user.** Numbering (Scene 1 vs Scene 2) unresolved — see below. |
| Golf course scene | https://d2ol7oe51mr4n9.cloudfront.net/user_3HZ3Ovx0vMaLGvw3wYJo7Ezbkwx/c9579552-9b5a-4a0f-90eb-9073056c8c11.mp4 | **Confirmed final.** Teleport-in, 4 dialogue close-ups, raven teleport-out. Cindy's line uses direct clone TTS (seed_audio). |

## Open question: scene numbering

Searched the full video generation history back to its start (no earlier results) —
the only multi-clip productions featuring Steve, Michael, Cindy, and Debbie together
are the kitchen scene and the golf course scene. A third candidate (four friends
walking down a country road, raven-transitioning to an Italian restaurant) was
confirmed by the user to be **just a test**, not a real scene, and is excluded here.

So either:
- The kitchen scene is actually "Scene 1" and the golf course is "Scene 2", or
- A true Scene 1 hasn't been produced yet.

Update this file once the user clarifies.

## Revision history (golf course scene)

For reference, in case a later revision needs to roll back or reuse an intermediate:

1. `5a3106ff-f5ef-438f-9c98-bf8778fd5dec` — original 4-clip assembly (wan2_7 voice-converted dialogue)
2. `5ad30173-ee1f-40f2-a20b-6ffdd7b0e916` — re-ran Cindy's voice_change conversion (2nd pass)
3. `fd169628-acf9-40f0-b82e-aba3edb7f3b2` — switched Cindy to direct clone TTS (seed_audio), but 4s video duration truncated the audio, cutting off her last words
4. `c9579552-9b5a-4a0f-90eb-9073056c8c11` — **current final** — fixed by regenerating at 6s duration so the full TTS line (5.06s) fits without truncation
