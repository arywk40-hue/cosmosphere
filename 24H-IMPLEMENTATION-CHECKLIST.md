# 24-Hour Implementation Checklist

Use this only when the official coding window begins. Keep the team honest: AI may be allowed for brainstorming and grammar, but the core system logic must be written by the team if the current rules remain unchanged.

## Before Start

Allowed preparation:

- Confirm exact event name and proposal template.
- Recruit exactly 3 eligible members.
- Fund demo wallet with Amoy testnet token.
- Create Pinata, Vercel, and MetaMask accounts.
- Prepare sample photos and a backup demo video plan.
- Decide team roles.
- Decide final MVP scope.

Do not create source code before the start.

## Hour 0 Checklist

- Create fresh public GitHub repo.
- Add README with project name, team members, and hackathon notice.
- Choose stack: React/Vite or Next.js, Solidity, Hardhat, ethers.
- Create project folders during the official window.
- Commit immediately so the audit trail shows the start point.

## Smart Contract Track

- Create PlotRegistry.
- Define Plot struct.
- Define submit function.
- Define get function.
- Define reward balance mapping.
- Define verified event.
- Add overwrite protection.
- Add tests for valid submit, duplicate plot ID, reward increment, and lookup.
- Deploy to Polygon Amoy.
- Save contract address and explorer link.

## Frontend Track

- Add wallet connect.
- Add network detection / Amoy warning.
- Add farmer submit page.
- Add file upload.
- Add browser location handling.
- Add verification result component.
- Add contract write.
- Add transaction status and explorer link.
- Add responsive dashboard page.

## Verification Track

- Compute cryptographic hash of photo + metadata.
- Compute duplicate key / perceptual hash.
- Check location exists.
- Check coordinates are inside target region.
- Check plot ID is not empty.
- Block chain write when verification fails.
- Store demo verification history locally or through backend.
- Add clear reasons for rejection.

## Dashboard Track

- Search by plot ID.
- Read contract record.
- Show wallet, coordinates, evidence hash, timestamp, reward status.
- Add QR or shareable plot link if time permits.
- Seed 2-3 demo records.
- Keep a visible empty state and error state.

## Stretch Only After Base Demo Works

- IPFS upload.
- QR generation.
- Challenge-response phrase or random bearing.
- Cooperative attestation.
- AI image embedding / classifier.
- Multi-plot cooperative dashboard.

## Final Two Hours

- Run full demo three times.
- Deploy live app.
- Check on another laptop/phone.
- Check explorer links.
- Record backup video.
- Freeze changes except emergency fixes.
- Write final README with setup, contract address, demo URL, and screenshots.

## Submission Package

- Public repo link.
- Live deployment link.
- Contract address.
- 10-slide deck.
- 2-minute demo video backup.
- Short README explaining the exact MVP boundaries.

