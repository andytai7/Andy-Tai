---
layout: page
title: "Federated Learning for Medical Data (FLIP-IT)"
description: "Privacy-preserving machine learning across primary care practices, IKIM, University Hospital Essen"
img: assets/img/Flipit-process.png
importance: 1
category: research
---

My current research at the **Institute for Artificial Intelligence in Medicine (IKIM)**, University Hospital Essen, is the **FLIP-IT** project: **Federated Learning in Practice Networks**. FLIP-IT builds an infrastructure for decentralized training of medical AI models directly in the outpatient practice network, general practices across North Rhine-Westphalia. The project is co-funded by the European Union and the state of North Rhine-Westphalia. Project site: [flipit-research.network](https://www.flipit-research.network/).

## Privacy by design

Most medical AI is built by centralizing patient data. FLIP-IT does the opposite: instead of moving the data to the model, we move the model to the data. Patient records stay on local systems at each practice, and the data never leaves the building.

The concrete guarantee is the **FLIP-IT deployment standard: patient-level DP-SGD with SecAgg+**. Every practice trains locally with differentially private stochastic gradient descent, and across rounds an **RDP accountant** tracks the composition of training against the privacy budget. Privacy is not tuned per clinic by hand: a rule-based server agent inventories the active SuperNodes and each practice's dataset size N, enforces one fixed global privacy target (ε, δ) for everyone, and runs the privacy calculator in reverse to derive a per-clinic plan, that clinic's own batch size and noise multiplier σ, which is dispatched to its SuperNode inside a Flower ConfigRecord. Large, mid-size, and small practices all receive the same ε guarantee regardless of size.

On the way back, secure aggregation closes the last gap: the SuperLink's SecAgg+ unmasking opens only the practice-weighted sum of updates, so the server never sees an individual clinic's update.

{% include figure.liquid loading="eager" path="assets/img/Flipit-privacy.png" title="FLIP-IT privacy design" class="img-fluid rounded z-depth-1" %}

<div class="caption">
    The FLIP-IT deployment standard: patient-level DP-SGD with SecAgg+. One global (ε, δ) target, a per-clinic noise and batch plan from the RDP accountant, and only the practice-weighted sum ever visible server-side.
</div>

## The end-to-end process

Training runs in rounds, but the full pipeline runs from practice onboarding to the consultation, in six stages:

1. **Join (one time, with practice IT).** The practice generates a private P-384 key pair; practice IT installs one Flower SuperNode pointed at the practice's own FHIR server, and the cohort is validated locally with our `ckd-fhir-extract` tool, which prints full exclusion accounting. On the consortium side, the admin runs the SuperLink with TLS and key-based admission and registers each practice's public key (`flwr supernode register`). Only registered practices can ever join a run, and any practice can be withdrawn.
2. **Data and census.** Inside the practice, the Tomedo practice software exports nightly into the practice's own PostgreSQL / FHIR server; `extract_features.sql` builds the canonical 16-column feature contract as a pseudonymised extract, with no names, no identifiers, and no patient ID column. In round zero, each practice reports only its patient count N; the server agent enforces the agreed global (ε, δ) target and inverts the privacy accountant into each clinic's own (batch size, σ) plan.
3. **Federated rounds.** Roughly ten rounds per cycle: each SuperNode receives the current global model, trains locally on its own cohort using DP-SGD under its own (batch, σ) plan, and returns a SecAgg+ masked update. The SuperLink unmasks only the weighted sum, applies FedAvg to produce the next global model, and every round logs global and worst-practice AUROC and sensitivity, so no small practice is hidden inside an average.
4. **Approval.** A governance gate before anything ships: global and worst-practice metrics must clear the agreed floor, a membership-inference leakage audit is re-run on the final model, and clinical review (docport / IKIM / RUB) plus legal review (Jorzig & Partner) decide on release.
5. **Deploy, with continuous oversight.** The approved model is exported as a JSON artifact paired with the practice-local scaler and delivered onto the practice machine, so scoring runs fully on-site with no server connection needed at consultation time. Every run stays logged at the SuperLink (rounds, ε spend, dual-level metrics); a practice can pause or leave at any time, its key is unregistered, and no data was ever held centrally. Later rounds refresh the model as cohorts evolve.
6. **Consult.** At the point of care the clinician opens the local form, enters routine features, and gets P(CKD stage ≥ 3) with the practice's calibrated flag. High-risk patients are offered early diagnostics and guideline follow-up. The score informs the consultation; the doctor decides.

What a practice actually sees: a one-time agreement to join plus an install sheet for IT; no change to daily work during training; and, afterwards, the CKD risk score simply showing up as routine decision support in the consultation.

{% include figure.liquid loading="eager" path="assets/img/Flipit-process.png" title="FLIP-IT federated training process" class="img-fluid rounded z-depth-1" %}

<div class="caption">
    The FLIP-IT pipeline end to end: six stages from practice onboarding to the consultation. Green boxes run inside the practice trust boundary, blue boxes at the central consortium.
</div>

## Work packages

- **LEGAL:** privacy-compliant contract frameworks and guidelines for federated learning in outpatient care
- **DATA:** data infrastructure and data quality across the participating practices
- **NETWORK:** the federated training platform itself

## My work

Within FLIP-IT I build federated chronic kidney disease risk prediction across general practice clinics using the [Flower](https://flower.ai/) framework, as part of the project's broader aim: validated AI models for the early detection of complications in chronic diseases such as diabetes, COPD, and coronary heart disease. Supervised by Prof. Michael Kamp (Lamarr Institute / TU Dortmund University), with Prof. Jens Kleesiek (IKIM), Dr. Moon Kim (IKIM), and Dr. Nicolas Conze as project lead. Consortium partners: IKIM, [docport](https://www.docport.de/), [Flower Labs](https://flower.ai/), and the associations of statutory health insurance physicians of Westphalia-Lippe ([KVWL](https://www.kvwl.de/)) and North Rhine ([KVNO](https://www.kvno.de/)).
