# Characters

Trained Soul identities for the Higgsfield short, so IDs aren't lost. Update
whenever a new character finishes training or an identity gets corrected.

| Character | Soul ID | Status | Notes |
|---|---|---|---|
| Steve | `00ee0321-aa17-465f-af73-8507c1ad5e78` | ready | |
| Michael | `1d71accb-3594-43c9-be37-556f21f25d63` | ready | User's own voice/likeness |
| Debbie | `52c6956c-3305-434c-85f2-3e678bba971e` | ready | |
| Cindy (old) | `109038a8-af80-46fd-b663-11dddd1334d9` | ready, **retired** | Confirmed correct on 2026-08-11, but degraded afterward — repeatedly failed to render her face accurately in Scene 3/4 edits despite fixes. Superseded by Cindy-2 below. Do not use going forward. Two other stale "Cindy" souls also exist (`13532858-be71-47fd-b701-72f332854350`, `70ecfd95-8c7a-4daf-b7f8-7618cc2650d8`) — do not use either. |
| **Cindy-2** | `d0bd9737-57ea-437f-8e48-a519a79f5ffc` | ready | Fresh retrain from 10 new real reference photos, replacing the old Cindy soul above after repeated identity/rendering failures. **Use this one for all future Cindy generations.** |
| Richard | `c7939841-5005-4bda-81c7-51c422b98261` | ready | New character — the person Steve/Debbie/Cindy were searching for at the golf course in Scene 3, revealed to be a birthday surprise. Trained from 8 real reference photos. Personality/role not yet specified by user. Voice: preset **Archie** (`bd072316-f77c-588b-b6e5-e46b9b03d008`, voice_type `preset`) — see Voices section below. |
| Ilana | `ce6b3565-15bd-4a9a-b771-c89808173c58` | **training** (started 2026-08-11) | Second new character — Richard's wife. Trained from 5 real reference photos (minimum for Soul training; consider adding more later if identity accuracy needs improvement). Personality/role not yet specified by user. Voice: preset **Helena** (`3c2b83c0-2e0a-5ae8-998a-a5fe71b7eccd`, voice_type `preset`) — see Voices section below. |

## Reliable face-fix identity anchors (as of 2026-08-12)

Soul-based generation (`soul_2` + soul_id) has repeatedly failed for close-up
face fixes in this project — most severely, it once rendered Michael as a
different person of a different race entirely despite using his correct
soul_id. **Do not rely on Soul generation alone for identity-critical shots.**

The reliable technique instead: take an already-correct scene image (right
outfit/background) and edit *only the face* with `nano_banana_pro`, embedding
one of these confirmed-real reference elements as `<<<element_id>>>` in the
prompt (e.g. "change only her face to match <<<id>>>, keep clothing/pose/
background unchanged"):

| Character | Reference element | Element ID |
|---|---|---|
| Cindy | ~~Cindy-Real-UserConfirmed~~ **Cindy-Portrait-2** | ~~`fc0f0579-4380-4d07-b02b-d77e647e1d6f`~~ **`ce1b165a-339a-43f3-9b98-7608d8c23e97`** |
| Debbie | Debbie-Arborist | `24deec5c-9272-4c4b-b013-7060400235fe` |
| Steve | Steve-Arborist | `17067706-b952-4945-9101-752b7f4505b2` |
| Michael | Michael-Arborist | `cd90f8bb-0a64-4f6f-8f5b-d1c486b632ab` (or Michael1: `dc054a58-467c-4599-8ad7-0d25a0b56235`) |

The "-Arborist" elements (all four, created 2026-08-09) are a matched set of
real confirmed photos from the same tree-arborist photoshoot — one per
character. Cindy's own Arborist photo proved unreliable in practice (still
produced Debbie's face once), so her element was replaced with a fresh photo
the user posted directly and confirmed on 2026-08-12; the other three
Arborist elements remain the current best anchors for Debbie/Steve/Michael.
Do not blindly extract a face from a previously-generated scene video as a
"ground truth" reference — those can themselves be wrong (this happened once:
a Scene 3 video frame believed to be Cindy's confirmed face turned out to
actually be Debbie's).

## Voices

Custom voice clones (`voice_type: element`) are capped at 3 slots on this account,
full: Steve, Debbie, Cindy-Voice-2. No delete-voice tool is available to me — when
a slot needed freeing on 2026-08-12 (Cindy's original clone had stopped sounding
like her), the user deleted the old clone directly in the Higgsfield app. Per user
decision on 2026-08-11, Richard and Ilana use stock **preset** voices instead of
clones for now (skip cloning; revisit later if a slot opens up or the plan is
upgraded). Two clean single-speaker audio clips were already extracted from their
shared conversation recording and confirmed as media (Ilana's clip
`dee2d57b-cff9-4135-b66c-6cb76bf249a9`, ~32.5s; Richard's clip
`7d7f8167-66cb-4bd7-9f13-f9faf5bbb9d4`, ~50.7s) in case cloning is revisited later.

| Character | Voice | voice_id | voice_type |
|---|---|---|---|
| Steve | Steve (clone) | `4554f8fb-4340-452f-902e-c00936d9b476` | element |
| Debbie | Debbie (clone) | `4035a2e6-5c8d-475f-81a5-7a5affb9ccb8` | element |
| Cindy | ~~Cindy-2~~ **Cindy-Voice-2** (clone) | ~~`62792e14-4627-42b2-8f45-d18c82116987`~~ **`28d6f3c4-28cb-4a88-aa66-468312e60d27`** | element |
| Richard | Archie (preset) | `bd072316-f77c-588b-b6e5-e46b9b03d008` | preset |
| Ilana | Helena (preset) | `3c2b83c0-2e0a-5ae8-998a-a5fe71b7eccd` | preset |

**2026-08-12:** the original Cindy-2 voice clone stopped producing audio that
sounded like her (root cause unknown — same voice_id, same technique that worked
for Steve/Debbie). User provided a fresh source video (`IMG_3580.mov`, 16.6s
clean single-speaker audio) to re-clone from. Old clone deleted by the user in
the Higgsfield app to free the capped slot; new clone **Cindy-Voice-2**
(`28d6f3c4-28cb-4a88-aa66-468312e60d27`) created from that video and confirmed
`completed`/`is_audio_eligible`. **Use this voice_id for all future Cindy
generations — the old `62792e14...` id no longer exists.**

## Cindy Soul retrain — in progress (2026-08-12)

Even with the voice fixed, Cindy's face in the Scene 4 dialogue close-up
remained wrong, and using her real confirmed photo directly as `start_image`
also broke lip-sync (mouth not moving with audio). User supplied two new
reference images (a close-up portrait and a 5-view turnaround sheet,
recovered from the session transcript, staged via GitHub, cropped into 5
individual angle images in the Higgsfield sandbox) to retrain the Cindy Soul
from scratch.

All 6 images are uploaded and confirmed in the Higgsfield media library:

| Image | media_id |
|---|---|
| Portrait | `dfe5147e-f885-48c6-8754-b1fa6b2a418c` |
| Turnaround angle 0 | `e56780dd-95b8-4862-ae2c-920dae922a8d` |
| Turnaround angle 1 | `6bcfdd37-297d-43f3-95d3-0256a0392731` |
| Turnaround angle 2 | `90960a73-cfbf-4fce-95f9-b0c476f58331` |
| Turnaround angle 3 | `3ee4041c-7f8a-4cea-8083-39af40af39ca` |
| Turnaround angle 4 | `25cb850e-7d99-4ab4-9da6-d23b7d543541` |

`show_characters(action='train', ...)` failed repeatedly ("Something went
wrong") on 2026-08-12/13 across 8 attempts with varied inputs (media_id array,
https URL array, `medias` array, different character names, fewer images) —
while `list`, `balance`, and `media_confirm` all worked normally in between.
This points to a transient outage in the Soul-training endpoint itself, not
a problem with the images. If it needs to be retried later,
`show_characters(action='train', name=..., images=[the 6 media_ids above])`
is ready to go with no re-upload needed.

**Resolved 2026-08-13 via a different mechanism — bypassed Soul training
entirely.** Created a single-image reference **element** from the portrait
instead: **Cindy-Portrait-2** (`ce1b165a-339a-43f3-9b98-7608d8c23e97`,
`show_reference_elements` action=create, source media
`dfe5147e-f885-48c6-8754-b1fa6b2a418c`). Used the established "identity onto
real crop" technique — `nano_banana_pro` editing Cindy's already-correct
scene image with `<<<Cindy-Portrait-2>>>` embedded — to produce a fresh,
evenly-lit close-up, then animated that with `wan2_7`. This fixed both the
face identity and the lip-sync problem that persisted even when using
Cindy's raw real photo directly (root cause of the lip-sync failure was
likely animation-model sensitivity to the photo's lighting/angle, not
identity). **User confirmed: "face and lip-sync look good."**
**Cindy-Portrait-2 is now the primary identity anchor for Cindy** — supersedes
Cindy-Real-UserConfirmed (`fc0f0579-4380-4d07-b02b-d77e647e1d6f`) in the
table below, which repeatedly failed to produce a correct likeness.
