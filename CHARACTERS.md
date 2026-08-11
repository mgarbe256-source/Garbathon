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

## Voices

Custom voice clones (`voice_type: element`) are capped at 3 slots on this account,
already full: Steve, Debbie, Cindy-2. No delete-voice tool is available to me, so
per user decision on 2026-08-11, Richard and Ilana use stock **preset** voices
instead of clones for now (skip cloning; revisit later if a slot opens up or the
plan is upgraded). Two clean single-speaker audio clips were already extracted
from their shared conversation recording and confirmed as media (Ilana's clip
`dee2d57b-cff9-4135-b66c-6cb76bf249a9`, ~32.5s; Richard's clip
`7d7f8167-66cb-4bd7-9f13-f9faf5bbb9d4`, ~50.7s) in case cloning is revisited later.

| Character | Voice | voice_id | voice_type |
|---|---|---|---|
| Steve | Steve (clone) | `4554f8fb-4340-452f-902e-c00936d9b476` | element |
| Debbie | Debbie (clone) | `4035a2e6-5c8d-475f-81a5-7a5affb9ccb8` | element |
| Cindy | Cindy-2 (clone) | `62792e14-4627-42b2-8f45-d18c82116987` | element |
| Richard | Archie (preset) | `bd072316-f77c-588b-b6e5-e46b9b03d008` | preset |
| Ilana | Helena (preset) | `3c2b83c0-2e0a-5ae8-998a-a5fe71b7eccd` | preset |
