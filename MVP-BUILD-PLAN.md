# PlotProof MVP Build Plan

This plan is designed for the 24-hour coding window. Because the rules say all MVP code must be written during the marathon, this file is intentionally limited to architecture, requirements, and execution order.

## Build Goal

Build a live Web3 MVP that proves this flow:

1. Farmer submits plot evidence.
2. Verification layer accepts or rejects it.
3. Accepted evidence is anchored on Polygon Amoy.
4. Farmer reward balance increases.
5. Buyer/regulator dashboard can audit the record by plot ID or QR.

## Non-Negotiable Demo

By judging time, the team must be able to show:

| Feature | Acceptance criterion |
|---|---|
| Wallet connection | User connects MetaMask and sees address/network. |
| Evidence capture | User uploads a photo and records browser geolocation or a controlled demo coordinate. |
| Verification pass | A valid sample creates a verification result. |
| Verification fail | Duplicate or missing-location sample is rejected before chain write. |
| On-chain write | A transaction appears on Polygon Amoy explorer. |
| Reward balance | Submitting wallet's reward count/balance visibly increases. |
| Dashboard lookup | Plot ID shows submitter, hash, coordinates, timestamp, and status. |

## Team Split

| Role | Owner | Deliverables |
|---|---|---|
| Smart contract + tests | Member 1 | PlotRegistry, event design, deployment script, explorer link. |
| Frontend capture + wallet | Member 2 | Submit page, MetaMask connection, form validation, transaction call. |
| Verification + dashboard + pitch | Member 3 | Rule checks, duplicate detection, dashboard lookup, slides/demo script. |

If the third member is weaker technically, give them dashboard + pitch + demo data while the stronger two handle contract and capture.

## Fresh Repo Rule

Use a fresh public repository created only when the coding window starts. Keep this existing repo as proposal/planning material.

Before the coding window, it is safe to prepare:

1. Accounts: MetaMask, Polygon faucet, Pinata, Vercel.
2. Test wallet funding.
3. UI wireframes.
4. Architecture diagram.
5. Research citations.
6. Sample photos for demo.
7. Environment setup notes.

Do not prepare source code, contract templates, app boilerplate, or copied implementation files before the official start if the final rules preserve Zero-Code Integrity.

## Contract Requirements

One contract is enough for the MVP.

Required behavior:

1. Store plot record by plot ID.
2. Store submitter wallet.
3. Store evidence hash.
4. Store scaled latitude and longitude.
5. Store timestamp / block timestamp.
6. Store status.
7. Increment reward balance after accepted submission.
8. Emit event on successful verification.
9. Prevent overwriting existing plot records unless an explicit update method is created.

Avoid full ERC-20 unless the base demo is finished early. A simple internal reward balance is easier to defend and less likely to break.

## Verification Requirements

Start deterministic:

1. Metadata/location present.
2. Coordinates inside accepted target region.
3. Photo hash not already used.
4. Perceptual hash not too similar to previous photo.
5. Evidence hash binds photo + metadata.

Stretch:

1. IPFS upload and CID anchoring.
2. Random challenge phrase or direction shown before capture.
3. Tiny image classifier / embedding similarity check.
4. Cooperative attestation from another wallet.

## UI Pages

| Page | Purpose |
|---|---|
| `/` | Simple role choice: Farmer, Buyer/Regulator. |
| `/submit` | Farmer capture/upload, GPS, verification result, submit to chain. |
| `/dashboard` | Search plot ID, show chain record and reward status. |
| `/demo` | Pre-seeded records and fail/pass demo buttons. |

## 24-Hour Timeline

| Time | Target |
|---|---|
| 0-2h | Fresh repo, stack setup, contract skeleton, frontend skeleton. |
| 2-5h | Contract storage, events, tests, deploy to Amoy. |
| 5-8h | Wallet connect, network switch/check, read/write contract calls. |
| 8-11h | Submit form, file hashing, geolocation, basic verification. |
| 11-14h | Dashboard lookup and event/history display. |
| 14-16h | Duplicate rejection and reward balance display. |
| 16-18h | Seed demo data, Vercel deploy, verify explorer links. |
| 18-20h | Polish UI, error states, empty states, mobile check. |
| 20-22h | Slides, architecture diagram, Q&A defenses. |
| 22-24h | Full rehearsal, backup video, final repo cleanup. |

## Demo Script

1. Open dashboard first and show existing verified plots.
2. Explain the problem in one sentence: "Smallholders need affordable proof, but field-agent verification does not scale."
3. Switch to farmer submission.
4. Upload valid sample, show pass result, submit to Amoy.
5. Click explorer transaction.
6. Return to dashboard and search plot ID.
7. Show reward balance changed.
8. Upload duplicate sample and show rejection.
9. Close with why this needs Web3: public, tamper-evident evidence history plus farmer incentives.

## Q&A Defense Points

| Judge question | Answer direction |
|---|---|
| Why blockchain? | Because buyers/regulators need an audit trail that no single exporter can rewrite after the shipment is challenged. |
| Is the AI real? | The MVP uses reliable deterministic checks; production can add stronger models. We avoided fake training in 24 hours. |
| Can farmers spoof GPS? | The MVP detects basic inconsistencies; production adds signed capture, challenge-response, cooperative attestation, and audit sampling. |
| Does this solve all EUDR? | No. It solves deforestation evidence. Land legality documents are a future module. |
| Why not Koltiva? | Existing platforms still depend on mapping/surveying/field-agent onboarding. PlotProof makes farmer-side evidence cheap enough to scale. |

