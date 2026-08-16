# PlotProof — Internal Notes (NOT for submission)

Everything in this file was moved out of `cosmosphere.tex` or found during the alignment
review on 2026-08-16. The submitted PDF should contain none of it.

---

## 1. Blockers — resolve before 18 Sep 2026

| # | Blocker | Source |
|---|---------|--------|
| 1 | **Team has 2 members; exactly 3 are required.** Recruit a third (age 15–25, SMA/SMK or D3/D4/S1). | `RULES.MD` |
| 2 | **Official Proposal Idea Template not yet released** (README link is a placeholder). Submissions not following its mandatory anatomy are **disqualified**. Our content must be transplanted into it, not submitted as-is. The template is on the Devpost challenge page — *not* the compsphere.id team dashboard, which is Top-30/Phase-2 only. | `README.md` |
| 3 | Team name still a placeholder in title block and page footer. | — |
| 4 | Architecture diagram placeholder still in the document. | — |
| 5 | Two `\needcite{}` markers render in **red** in the PDF. They are visible deliberately. Resolve or delete. | — |
| 6 | Guidebook not yet downloaded/read (Step 1 of GET STARTED). May contain additional formatting rules. | `README.md` |

---

## 2. Claims that still need a real source

Criterion 1 (25%) explicitly requires claims "supported by valid data", so unsourced
numbers cost real marks.

- **~40% of Indonesia's oil palm area is independent smallholder.** Widely reported, but
  cite it properly — Indonesian Ministry of Agriculture (Direktorat Jenderal Perkebunan)
  statistics, or an RSPO/Chain Reaction Research report.
- **"Only a small fraction hold certification."** The earlier draft said "fewer than 1%".
  I could not verify that figure, so the wording was softened. Either source the exact
  number or keep it qualitative — do not assert 1% without a citation.
- **Field-agent cost per plot.** The business model rests on the spread between a field
  visit and an automated check. A sourced per-plot cost figure would make the Market
  section much stronger. Currently argued qualitatively on purpose.
- ~~WHO~~ — the earlier draft listed the **World Health Organization** as a source for
  palm oil statistics. Removed. Use: RSPO, Chain Reaction Research, WRI / Global Forest
  Watch, Indonesian Ministry of Agriculture, European Commission.

### Already verified (in the bibliography)
- EUDR application dates: **30 Dec 2026** large/medium operators, **30 Jun 2027**
  micro/small. Source: European Commission EUDR page.
- **31 Dec 2020** deforestation cutoff — Reg. (EU) 2023/1115 Art. 2(13).
- Geolocation: **six decimal digits**; polygons mandatory only **above 4 ha** —
  Art. 2(28). This legitimises phone-GPS capture for sub-hectare plots.
- Art. 4a(5) (Dec 2025 amendment): micro/small *primary* operators may substitute a
  postal address for geolocation. Pre-empted in §2.3 of the proposal.

---

## 3. Substantive changes made in the revision, and why

1. **Added the 31 Dec 2020 cutoff and restructured the solution around it.** The old draft
   never mentioned it. A 2026 photograph cannot prove what stood on the land in 2020, so
   the original mechanism did not address the actual legal test. Fix: the *verdict* is now
   satellite-archive-derived; the photo *disambiguates* sub-hectare alerts.
2. **Reframed "satellites can't see" → hybrid.** Planet NICFI (~4.8 m) and RADD/GLAD
   alerts exist; the old title overclaimed and the old body contradicted it two paragraphs
   later. New framing: satellites flag well, adjudicate poorly.
3. **Fixed the incentive problem.** Old draft paid the farmer on "verified submission"
   while the farmer benefits from a clean verdict. Now payment is explicitly for a
   *valid* submission, never a favourable one — so nobody is paid to lie.
4. **Removed the "cannot be edited after the fact" contradiction.** Line 71 of the old
   draft claimed metadata was uneditable; line 72 screened for GPS spoofing. Replaced with
   hardware-backed signing + trusted timestamp, described as tamper-*evident*.
5. **Added the challenge-response capture (nonce + random bearing in frame).** Defeats
   replay of stored/borrowed photos, which a plain upload flow cannot. This is the
   strongest single novelty in the build and the easiest to demo live.
6. **Added an anti-fraud table, a "Why This Requires Web3" section, and a risks section.**
   A judge will ask why this is not a Postgres table; the old draft had no answer.
7. **Added the business model.** Nothing funded the token reward. Now: buyers pay per
   verified plot, which is also the sustainability answer for criterion 4.
8. **Polygon Mumbai → Amoy.** Mumbai was deprecated in 2024.
9. **Bounded the AI claim.** "Lightweight AI model" implied training. Now stated as a
   pre-trained model applied zero-shot plus classical forensics — defensible in 24 h.
10. **Removed from the submitted PDF**: the judging-criteria alignment section (quoting the
    rubric percentages back at judges reads as writing-to-the-rubric), the open-items
    checklist (shows unfinished work), and the Phase 2 criteria note (judges know them).
11. **Dropped "12:00am WIB"** from the deadline line — unverified, and 12:00am on 18 Sep
    would effectively mean end of 17 Sep. Confirm the real cutoff time on Devpost.
12. **Dropped "(COMPSPHERE 11)"** from the running header — the "11" is not in any of our
    source documents. Restore if the guidebook confirms it.

---

## 4. Phase 1 judging map (kept out of the PDF on purpose)

| Criterion | Weight | Where the proposal earns it |
|---|---|---|
| Problem Relevance & Solution Fit | 25% | §2 — dated deadline, cited regulation text, the historical-cutoff problem named explicitly and then solved |
| Technical Architecture & Feasibility | 20% | §6–7 — layered stack, explicit 24 h envelope, pre-trained-not-trained model note |
| Innovation & Value Proposition | 30% | §3–5 — challenge-response capture, satellite/ground cross-check, pay-for-valid-not-clean, audit-and-slash. Contrasted against Koltiva and Unilever/SAP GreenToken |
| Market & Impact Viability | 15% | §8 — who pays, flat vs linear onboarding cost, seven-commodity expansion |
| Document Clarity & Structure | 10% | Must be transplanted into the official template (blocker 2) |

---

## 5. Rule compliance checklist

- [ ] **Zero-Code Integrity** — all MVP code written 10–11 Oct 2026 only. This repo currently
      holds documents only, which is fine; start the MVP in a **fresh public repo** created
      during the window so the commit audit is unambiguous.
- [ ] **AI Policy** — generative AI permitted only for brainstorming and grammar. Core
      system logic must be original. Applies to Phase 2: the contracts, verification
      service, and capture logic have to be written by the team. Proposal drafting and
      research assistance is within the allowed scope; implementation is not.
- [ ] **Public repo** stays public until judging is finalised.
- [ ] Ages 15–25, exactly 3 members, category: International Student.
- [ ] Phase 1 PDF ≤ 10 MB (watch the architecture diagram's file size).
- [ ] Phase 2: public repo link, ≤10 slides, optional live deployment for bonus points —
      deploy to Vercel/testnet, since deployed projects are explicitly preferred.

---

## 6. Open design decisions

- [ ] Exact satellite data source for the 2020 baseline lookup — Sentinel-2 via Copernicus
      / Google Earth Engine vs. Planet NICFI (registration lead time?) vs. pre-baked
      RADD alert tiles. **Decide before the marathon; API access is the likeliest 24 h
      blocker and is not code, so it can be arranged in advance.**
- [ ] Audit sampling rate and slash amount — needs to make fraud negative-EV. Worth a
      one-slide expected-value calculation for the pitch Q&A.
- [ ] Reward size: flat per plot vs. scaled by plot size or data quality.
- [ ] `m` and `n` for cooperative attestation (2-of-3 neighbours? 1 officer + 1 neighbour?).
- [ ] Role split: contracts + reward/slashing · capture app + on-device forensics ·
      verification service + dashboard + pitch. Third member's strength decides the split.
