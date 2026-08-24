# PlotProof Hackathon Research Brief

Prepared for the Cosmosphere / HACKSPHERE proposal repo. This is planning and research only. Do not treat this as MVP source code.

## Core Thesis

PlotProof should not claim that phone photos or AI "replace satellites." That is too easy for judges to attack.

The sharper thesis is:

> Satellites are good at broad monitoring but weaker on fragmented smallholder plots. PlotProof combines satellite-era baseline evidence, farmer-side challenge-response capture, and blockchain anchoring so buyers can audit who submitted what, where, and when.

This makes the Web3 layer meaningful: not "blockchain because hackathon," but an evidence registry where later actors cannot quietly rewrite, delete, or hide farmer submissions.

## Evidence To Use

| Claim | Source support | Why it matters |
|---|---|---|
| EUDR applies from 30 Dec 2026 for large/medium operators and 30 Jun 2027 for micro/small operators. | European Commission EUDR page: https://environment.ec.europa.eu/topics/forests/deforestation/regulation-deforestation-free-products_en | Gives urgency and a real compliance deadline. |
| EUDR requires proof that products do not come from recently deforested land or cause forest degradation. | European Commission EUDR page, lines on operator/trader proof obligation. | Frames the actual legal problem. |
| Global oil-palm mapping is much stronger for industrial plantations than smallholders. | Descals et al. 2024, Earth System Science Data: https://essd.copernicus.org/articles/16/5111/2024/ | Supports the "smallholder verification gap" with peer-reviewed data. |
| Descals et al. report about 91% producer/user accuracy for industrial oil palm and about 71-72% for smallholders. | Same ESSD paper. | Strongest quantitative hook for the proposal. |
| Existing traceability systems still lean on mapping, surveying, field agents, training, and producer onboarding. | Koltiva EUDR palm oil page: https://www.koltiva.com/post/eudr-deforestation-regulation-addressing-solutions-in-the-palm-oil-supply-chain | Lets PlotProof position itself as lower-cost farmer-side evidence collection, not another enterprise dashboard. |
| Enterprise blockchain pilots already exist for palm oil traceability. | Unilever/SAP GreenToken pilot: https://www.unilever.com/news/press-and-media/press-releases/2022/sap-unilever-pilot-blockchain-technology-supporting-deforestationfree-palm-oil/ | Shows the market accepts blockchain traceability, but the first-mile evidence bottleneck remains. |
| Polygon Amoy is the current safer testnet choice than Mumbai. | Polygon Amoy announcement: https://polygon.technology/blog/introducing-the-amoy-testnet-for-polygon-pos | Avoids outdated Polygon Mumbai setup. |
| Pinata can upload files to IPFS using standard file uploads and returns content identifiers. | Pinata docs: https://docs.pinata.cloud/files/uploading-files | Good stretch goal for evidence storage. |
| MetaMask supports EVM dapp connections across browser/mobile. | MetaMask Connect docs: https://docs.metamask.io/metamask-connect/ | Useful for wallet connection in a 24-hour web MVP. |
| ethers v6 Contract objects support calling methods, querying logs, and listening to events. | ethers docs: https://docs.ethers.org/v6/api/contract/ | Good lightweight frontend chain integration. |

## Positioning Fixes

1. Replace "satellites can't see" with "satellites struggle to adjudicate smallholder plots."
2. Do not say metadata "cannot be edited." Say: "metadata is captured at submission time, checked for consistency, signed or hashed, and made tamper-evident once anchored."
3. Keep the AI claim modest. In 24 hours, ship deterministic checks plus maybe a pre-trained image embedding or perceptual hash. Do not promise custom model training.
4. Be honest that PlotProof addresses deforestation-free evidence, not the entire EUDR legality requirement. Land title / STDB documents are a future extension.
5. Treat IPFS as stretch. The must-have demo is on-chain hash + metadata + dashboard lookup.
6. Confirm event naming. The repo has HACKSPHERE 2026, COMPSPHERE 11, and the attached PDF says COMPSPHERE 12. Do not submit until this is reconciled with the official guidebook / Devpost page.
7. Confirm deadline wording. "18 Sep 2026, 12:00am WIB" likely means the end of 17 Sep in practical terms. Work to 17 Sep to avoid a timezone mistake.

## MVP Shape

The winning hackathon version should have five visible proofs:

| Proof | Demo action |
|---|---|
| Farmer can submit evidence | Upload/capture photo, location, plot ID, wallet address. |
| Bad evidence can be rejected | Demo duplicate image rejection or missing-location rejection. |
| Good evidence creates an immutable record | Show transaction hash on Polygon Amoy. |
| Farmer incentive exists | Show reward balance incrementing after a valid submission. |
| Buyer/regulator can audit | Search plot ID / QR code and see hash, coordinates, timestamp, submitter, status. |

## Recommended Architecture

| Layer | Recommendation | Reason |
|---|---|---|
| Frontend | Next.js or Vite React | Fastest web demo path, easy wallet integration. |
| Wallet | MetaMask, EIP-1193 / ethers v6 | Familiar to judges and fast to debug. |
| Chain | Polygon Amoy | Testnet, EVM-compatible, visible explorer. |
| Contract | One PlotRegistry contract | Keep it auditable in Q&A. |
| Backend | Small Node/Express or Next API route | Handles verification and optional IPFS signing. |
| Storage | On-chain hash required; IPFS optional | Avoid overloading the 24-hour build. |
| Verification | Rule-based checks first | More reliable than rushing a fake AI model. |
| AI stretch | CLIP/embedding similarity or lightweight image classifier | Only if the base flow is done early. |

## Suggested Verification Rules

These are requirements, not code:

1. Reject missing GPS or user-denied browser location.
2. Reject coordinates outside a configured Indonesia / target-region bounding box.
3. Reject duplicate photo evidence using perceptual hash similarity.
4. Reject repeated plot submissions from the same wallet unless marked as an update.
5. Store only scaled integer coordinates on-chain, not raw floating-point strings.
6. Hash photo bytes + metadata together so the record binds the image to location/time.
7. Emit a clear event when a plot is verified so the dashboard can query history.

## Proposal Improvement Notes

The attached PDF has strong research density, but it is too long and slightly overclaims. For Phase 1, compress around:

1. Problem: EUDR + smallholder mapping gap + field-agent cost bottleneck.
2. Solution: farmer-side challenge-response evidence + verification + on-chain audit trail.
3. Why Web3: tamper-evident public evidence registry, buyer auditability, reward ledger.
4. MVP: exactly what can be shown in 24 hours.
5. Impact: cheaper onboarding for smallholders, reusable for cocoa/coffee/rubber later.

Do not include internal rubrics, open TODOs, or unfinished placeholders in the final proposal.

