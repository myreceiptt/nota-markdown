---
description: >-
  This is the making-of record for the BGC ALPHA Simulator: an internal web application used to test ALPHA policy choices against BGC and iBLOOMING business data.
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# BGC ALPHA Simulator: Build Process and Author Contributions

> **Why this document exists.** This is the making-of record for the BGC ALPHA
> Simulator: an internal web application used to test ALPHA policy choices against
> BGC and iBLOOMING business data. It records how the project moved from early
> AI-assisted conversations to a working decision console, and distinguishes
> Fabio Kalandra's business and product decisions from AI-assisted implementation.
>
> **Method note.** This revision uses two kinds of evidence:
>
> - **Transcript evidence** comes from the local Codex rollout logs for this exact
>   workspace (`/Users/fabiomaulana/Documents/bgc simulator`), read in date order.
>   The earliest available project session is **16 March 2026**. The text below
>   quotes only short, relevant user instructions or carefully paraphrases them.
>   It does not reproduce raw chats or private material.
> - **Repository evidence** comes from git history, project specifications,
>   dictionaries, the `context/` pack, and deliverables. Statements marked
>   **(inferred from repo)** are reconstructions, not claims that a particular
>   conversation happened.
>
> Git names `unclekaldoteth` and `fabiokalandra` refer to Fabio Kalandra, the
> human author. Codex and, where used, Claude/ChatGPT are tools. They did not own
> the business decisions attributed to Fabio below.

---

## Ringkasan (Bahasa Indonesia)

Simulator ALPHA dibuat untuk membantu BGC dan iBLOOMING mengambil keputusan
kebijakan token secara lebih aman. Masalah awalnya bukan sekadar “membuat token”,
tetapi bagaimana menguji dampak aturan ALPHA terhadap data bisnis nyata: siapa yang
mendapat nilai, seberapa besar beban kas perusahaan, bagaimana risiko cash-out,
dan apakah hasilnya cukup adil serta bisa dijelaskan ke founder.

Pada 16 Maret 2026, Fabio meminta AI mempelajari dokumen bisnis, reward,
whitepaper, token flow, dan simulasi terlebih dahulu. Setelah itu Fabio menyetujui
bentuk produk sebagai **internal decision console dengan simulation engine nyata,
bukan dashboard saja**. Dari sana proyek berkembang menjadi aplikasi web dengan
data snapshot, skenario, proses simulasi, hasil, perbandingan, decision pack, dan
export laporan.

Kontribusi Fabio terlihat jelas di percakapan: ia menentukan tujuan produk,
meminta data tetap setia pada *understanding document* yang sudah final, meminta
data salah ditolak, membedakan actual dan forecast, meminta laporan yang mudah
dibaca founder, dan mengarahkan agar hasil simulasi dipakai untuk memfinalkan
whitepaper serta token flow. AI membantu menyusun dokumen, membuat pola kode
standar, dan mengimplementasikan perubahan. Namun arti bisnis BGC/iBLOOMING,
standar kejujuran data, dan keputusan produk tetap berasal dari Fabio.

---

## 1. What the simulator is

The BGC ALPHA Simulator is an **internal decision-support web app**. A permitted
user uploads a versioned business-data snapshot, selects or edits an ALPHA policy
scenario, runs a deterministic model, and reviews the money, distribution,
treasury, fairness, risk, and decision outputs. Completed runs can be compared and
exported for founder discussion.

It is deliberately not a public token product. The MVP does not deploy smart
contracts, operate wallets, execute cash-outs, or prove a public market price. Its
purpose is to make a Phase 1 internal policy decision evidence-based before any
larger Web3 commitment.

## 2. Chronological build narrative

### Phase A: learn the business before defining the product
**16 March 2026 | transcript evidence**

Fabio did not begin by asking for a generic token dashboard. His first request was
to create a PRD for “BGC Alpha coin use and distribution,” but only after the AI
had read the linked Living Doc, meeting notes, reward understanding document,
whitepaper draft, token-flow draft, and simulation document. He then asked what
the PRD would be based on. This established the project rule that the simulator
must start from BGC/iBLOOMING business semantics rather than invent a simplified
token model.

When the product form was discussed, Fabio expected a web app and explicitly
endorsed the sharper definition: **“an internal decision console backed by a real
simulation engine, not just a dashboard.”** This is the clearest first product
decision in the available record. It explains the later choice to build a full
data-to-decision workflow instead of a presentation-only interface.

The initial PRD and founder PRD preserve that framing: historical data is loaded,
policy variables are changed, a reproducible simulation is run, and founders use
the result to judge a pilot. The core scope and non-goals are documented in
`bgc-alpha-simulator-prd.md` and `bgc-alpha-simulator-prd-founder-v1.md`.

### Phase B: turn the concept into a buildable system
**16–17 March 2026 | transcript and repo evidence**

Fabio asked for a concrete stack and repository structure, then directed the work
to start with Milestones 0 and 1: bootstrap the monorepo and create the app/package
skeleton. The resulting proposal selected a TypeScript pnpm/Turborepo monorepo:
Next.js for the internal web app, PostgreSQL/Prisma for durable records, Zod for
shared input contracts, a TypeScript simulation engine, and a separate `pg-boss`
worker for long-running jobs.

This was a practical MVP choice, not a claim that those tools are the only valid
technology. The stack document explicitly rejects an early split into a separate
frontend, backend, and Python engine as unnecessary for a deterministic MVP
**(inferred from repo, supported by `bgc-alpha-simulator-tech-stack-and-repo-v1.md`)**.

Fabio also checked that the product could really run locally: he asked whether a
database was needed before `pnpm dev`, set up Docker, investigated worker errors,
and tested the sign-in and snapshot screens. This shows active author participation
in moving from a plan to a runnable app, rather than treating generated code as a
finished product.

The first implementation included access roles, snapshot ingestion/validation,
scenario persistence, queued execution, and result pages. Fabio then requested a
plain-English explanation of the actual flow and asked for a glossary after
reviewing scenario parameters. The later English and Indonesian dictionaries are
the durable result of that accessibility requirement.

### Phase C: make the model data-driven and usable in meetings
**17–31 March 2026 | transcript evidence**

After the first loop worked, Fabio chose the next problem: real historical data and
baseline-model encoding. He asked for a build plan, approved the first phase, and
then asked whether the system needed real data. When told the sample snapshot was
the limiting factor, he asked for a browser CSV uploader. This moved the project
away from demo-only inputs toward a proper snapshot lifecycle.

Fabio also shaped the product's communication layer. For a meeting he asked for a
short, understandable screen-by-screen explanation: sign in, upload and approve a
snapshot, configure a scenario, run the worker, review the result, and compare
runs. He then requested clearer overview content showing scenario results and
snapshotted data, not merely system status.

On 30–31 March, Fabio supplied and repeatedly checked new source CSV categories,
asked the AI to list the files it had read, and required the simulator to align
with all of them. He asked for baseline, conservative, growth, and stress
scenarios with milestones, plus a configuration that could produce green health,
ready milestones, and acceptable fairness. These are evidence that scenarios were
intended as business-policy experiments, not decorative presets.

### Phase D: deployment, run records, and presentable evidence
**2–4 April 2026 | transcript and git evidence**

Deployment exposed real production concerns: Fabio tested Vercel environment and
database failures, while the repository records fixes for Next.js detection,
Prisma generation, Postgres configuration, snapshot storage, Vercel Blob uploads,
and inline processing where a separate worker was unavailable. Git commits from
2–3 April provide the verifiable engineering chronology.

On 4 April Fabio identified a governance problem in the early product: rerunning
the identical scenario on the identical snapshot created duplicate result records
and polluted comparison. He proposed comparing the same scenario record plus the
same snapshot, suggested the `seedHash` approach, and asked that the existing
result be opened instead. He also asked for a dedicated **Result Ref** area where
each saved run can be opened directly.

That decision became the result-reference page and duplicate-run prevention in
commit `d1cf0d1` (4 April). The result is not just a technical optimisation. It
keeps the comparison screen auditable: a reference identifies a distinct,
reproducible policy/data combination rather than a duplicate click.

Fabio also set a report-quality standard. He required exports to include the full
Simulation Result, not only a text fragment, and insisted that a PDF actually be a
presentable PDF with readable cards, tables, and charts matching the web app. He
then applied the same requirement to Compare exports. This explains the later PDF
and compare-export work rather than treating it as cosmetic polish.

### Phase E: protect business meaning with a faithful data model
**18–29 April 2026 | transcript and git evidence**

This is the largest evolution in the project. Fabio challenged an important
shortcut: the repository had compressed the business into generic monthly fields
such as PC volume, SP reward basis, generic reward totals, cash-out, and sink
spend. He asked whether that meant the input no longer matched the understanding
document, then stated two requirements:

1. The data shape must be sufficient to represent the understanding document
   correctly.
2. Nothing in that understanding document, which was already final, should be
   changed or replaced.

He authorized implementation of `SIMULATOR_FAITHFUL_DATA_MODEL_SPEC.md`, requested
sample data over 24 months, and kept questioning whether the imported CSV was read
according to the real rules. This led to the canonical/full-detail model: members,
aliases, role history, business events, PC/SP ledgers, reward obligations, pool
ledgers, cash-outs, and qualification history can be retained, while monthly facts
are derived for simulation. Compatibility CSV remains supported, but it is not
presented as the only source of truth.

Fabio made the data-quality standard stricter in practice. When an audit naming
mismatch was found, he asked to close it. When offered a warning for a legacy field,
he approved changing it to an error so future CSVs must use the correct name. In a
later integrity review he agreed to start with snapshot/data integrity before
scenario math and compare. These choices explain the schema-drift handling,
fingerprints, validation issues, manifest/audit artifacts, accepted hybrid
snapshots, and archive lifecycle recorded in the 20–22 April commits.

### Phase F: broaden from historical replay to a controlled policy decision pack
**24 April–6 May 2026 | transcript and git evidence**

Fabio asked for a brutally honest challenge of the whitepaper and token flow against
the simulation document. This changed the simulator's role: it should not make a
whitepaper look complete just because a chart exists. It must show what the data
supports and what remains an assumption.

During the 26 April review, Fabio asked about the gap between historical data and
forecast data, then approved the staged extension: token-flow specification and
ledger, a forecast layer separated from actuals, Web3/tokenomics assumptions, and
a whitepaper evidence pack. The later implementation and documents keep these
boundaries visible. `Imported Data Only` and `Add Forecast` are intentionally
separate modes; actual ALPHA use and modeled ALPHA use are different measures.

Fabio also asked whether the simulator was sufficient to produce the token flow
and whitepaper, requested scenarios that balance treasury safety, fairness,
cash-out risk, growth support, and internal use, and asked what was limiting
internal use. This is why the product has a decision pack, cashflow-first compare
view, risk flags, token-flow outputs, and finalization documents rather than an
unsupported “best scenario” claim.

Git confirms the sequence: decision artifacts and hybrid snapshots (21 April),
decision-pack governance and cashflow delta (22 April), token-flow workflow and
finalization artifacts (27 April), token-price assumptions as evidence (28 April),
and clearer snapshot/data basis plus iBLOOMING sales-point and internal-credit
cashflow support (29–30 April).

### Phase G: calibration, labels, founder readability, and cleanup
**May–June 2026 | transcript and repo evidence**

Fabio continued testing real data rather than accepting an abstract engine. He
questioned pool-rate assumptions, the required `active_member` field, number
formats used in Indonesian data, zero values in treasury/distribution outputs, and
the meaning of actual versus modeled ALPHA use. He supplied a manually prepared
monthly file and asked that the engine accept common thousands separators while
remaining strict about meaning. These conversations led to monthly-import and
forecast-label improvements in commit `02458b5` (5 May).

For founder use, Fabio asked that a four-scenario comparison be concise and
decision-ready, not verbose. He later requested reports with more charts and
infographics because dense numbers were harder for some readers to use. The UI and
export guidance now consistently put company cashflow before ALPHA-policy metrics
and require visible data-quality and forecast labels.

On 15 May Fabio requested a reusable `context/` pack and an architecture flow
chart. The six context files now preserve product intent, architecture, UI rules,
code standards, AI workflow rules, and progress notes for future contributors.

The last committed work on 27 June removes dead code, fixes Node type support, and
synchronizes the lockfile. At the repository state reviewed on 12 July, the
documented next phase remains calibration and hardening: choose the active evidence
baseline, make imports reproducible, calibrate against observed totals, and obtain
founder sign-off. Uncommitted worktree files are not treated here as verified
historical milestones.

## 3. How AI was used

AI was a working partner, not an autonomous product owner.

- **Research and synthesis.** Fabio directed the AI to read the source material
  before writing the PRD, then used it to turn a large set of business documents
  into plans, dictionaries, screen explanations, decks, and founder-facing drafts.
- **Standard software scaffolding.** AI helped produce conventional patterns such
  as the monorepo layout, Next.js route/page shells, Prisma models, Zod validation,
  worker jobs, test fixtures, report renderers, and deployment fixes.
- **Iterative implementation and debugging.** Fabio tested local and deployed
  behavior, supplied errors and source files, asked direct questions, and requested
  fixes. The AI then inspected and changed code under those constraints.
- **Plain-language translation.** AI helped explain technical concepts such as a
  snapshot, worker, fingerprint, scenario parameter, and data contract to a
  non-engineer audience. Fabio repeatedly asked for wording that founders could
  understand quickly.

AI was useful for speed and standard patterns. It was not the source of truth for
BGC/iBLOOMING economics, policy legitimacy, or evidence quality. Those needed
human judgment and source documents.

## 4. Author contributions: Fabio Kalandra

The following items are direct author contributions supported by transcript
evidence. They are separated from AI-generated implementation detail.

| Fabio's contribution | Evidence in the transcripts | Why it matters |
|---|---|---|
| Defined the project problem as ALPHA use and distribution, grounded in the business documents. | 16 Mar: Fabio required the AI to read the Living Doc, meeting notes, reward understanding document, whitepaper, token flow, and simulation document before creating the PRD. | Prevented a generic crypto product from replacing the actual BGC/iBLOOMING problem. |
| Chose the product form. | 16 Mar: Fabio endorsed an “internal decision console backed by a real simulation engine, not just a dashboard.” | Set the direction for a data, model, and decision workflow. |
| Directed the MVP toward a real runnable application. | 16 Mar: Fabio initiated the monorepo milestones, database setup, local testing, and first implementation tickets. | Turned the concept into working software rather than a static proposal. |
| Required real-data ingestion and browser upload. | 17 Mar: after identifying the lack of real historical snapshots as the blocker, Fabio asked for browser CSV upload. | Made the simulator testable against evidence, not only samples. |
| Defined usable scenario thinking. | 30–31 Mar: Fabio asked for baseline, conservative, growth, and stress scenarios, milestones, and health/fairness checks. | Made the model useful for trade-off decisions. |
| Established reproducible run governance. | 4 Apr: Fabio identified duplicate scenario/snapshot runs, proposed checking the same scenario record plus snapshot, and required an existing result to open instead. | Protects result references and prevents misleading duplicate comparisons. |
| Set the founder-report standard. | 4 Apr and 3–6 May: Fabio required real, presentable PDF exports, web-consistent charts, concise comparison language, and later more visual reports. | Made technical outputs usable in founder discussions. |
| Protected the fixed business semantics. | 18 Apr: Fabio required enough data to represent the understanding document correctly and said it must never be changed or replaced. | This is the basis for the faithful/full-detail data model. |
| Chose strict data integrity over convenient acceptance. | 18–26 Apr: Fabio asked to close audit mismatches, approved turning a legacy warning into an error, and prioritized snapshot/data integrity. | Reduces the risk that a neat-looking result is based on invalid input. |
| Required honest boundaries between actual data, forecasts, and claims. | 24–26 Apr: Fabio requested an objective challenge of the whitepaper/token flow, asked how forecast data should work, and approved distinct actual/forecast and evidence layers. | Avoids presenting model assumptions as historical facts. |
| Kept company cashflow and token policy connected but distinct. | 26 Apr onwards: Fabio asked about treasury safety, fairness, cash-out risk, growth support, internal use, pool basis, and internal-credit meaning. | Supports the cashflow-first decision lens rather than treating ALPHA totals as the whole business. |
| Made future work easier to understand and continue. | 15 May: Fabio requested the reusable context pack and architecture diagram. | Captures project rules for later maintainers and study. |

## 5. What is reconstructed rather than directly witnessed

The transcripts provide strong evidence for the product framing, decisions, and
iteration above. They do **not** prove every low-level authorship detail. The
following are therefore inferred from repository evidence:

- Exactly which lines or components were typed manually by Fabio versus generated
  by an assistant.
- The precise private discussions that produced every business number in the
  baseline, scenario guardrail, and token-flow documents.
- The original creation dates of planning files before they entered the repository.
- Any conversation that occurred outside the available Codex logs, including prior
  ChatGPT or Claude chats that were not stored in this local session archive.

This limitation is intentional. It is better to label missing evidence than to
invent a conversation or overstate a contribution.

## 6. Evidence index

For a reviewer who wants to audit this narrative without reading raw chat logs:

- **Project transcripts:** local Codex sessions dated 16 March, 23–24 March,
  30–31 March, 2–4 April, 10 April, 18 April, 26 April, and 15 May 2026, filtered
  to the `bgc simulator` workspace. The 16 March session is the earliest available
  transcript for this project.
- **Git history:** `git log --all --stat --date=short`; committed milestones run
  from 2 April to 27 June 2026 under Fabio's identities above, with merge commits
  also recorded.
- **Product and implementation records:** `bgc-alpha-simulator-prd.md`,
  `bgc-alpha-simulator-prd-founder-v1.md`,
  `bgc-alpha-simulator-tech-stack-and-repo-v1.md`,
  `bgc-alpha-simulator-data-baseline-build-plan-v1.md`,
  `bgc-alpha-simulator-calibration-workflow-v1.md`,
  `SIMULATOR_FAITHFUL_DATA_MODEL_SPEC.md`, `COMPANY_CASHFLOW_LENS_SPEC.md`, the
  English/Indonesian dictionaries, `context/`, and `deliverables/final-docs/`.

*Updated 12 July 2026. This document summarizes evidence and deliberately omits
private data, raw credentials, and unnecessary transcript detail.*

---

P.S. Read this document freely for information and guidance. Do not redistribute or restate—no quotes, summaries, paraphrases, or derivatives—without prior written permission from [**Prof. NOTA**](https://nota.endhonesa.com/). Sharing the link is allowed. So, share the link, not the text. Do not discuss or re-tell the contents in any form—written, spoken, or recorded—without prior written permission.

---
