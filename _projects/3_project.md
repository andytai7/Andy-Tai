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

Most medical AI is built by centralizing patient data. FLIP-IT does the opposite: instead of moving the data to the model, we move the model to the data. Patient records stay on local systems at each practice.

{% include figure.liquid loading="eager" path="assets/img/Flipit-privacy.png" title="FLIP-IT privacy design" class="img-fluid rounded z-depth-1" %}

<div class="caption">
    Privacy by design in FLIP-IT: patient data never leaves the practice.
</div>

## The federated training process

Training runs in rounds. Each practice trains a copy of the model on its own patient records. Only the model updates come back, a server aggregates them into one shared model, and the cycle repeats. No patient record is ever transferred.

{% include figure.liquid loading="eager" path="assets/img/Flipit-process.png" title="FLIP-IT federated training process" class="img-fluid rounded z-depth-1" %}

<div class="caption">
    One round of federated training across the practice network.
</div>

## Work packages

- **LEGAL:** privacy-compliant contract frameworks and guidelines for federated learning in outpatient care
- **DATA:** data infrastructure and data quality across the participating practices
- **NETWORK:** the federated training platform itself

## My work

Within FLIP-IT I build **federated chronic kidney disease risk prediction across general practice clinics** using the [Flower](https://flower.ai/) framework, as part of the project's broader aim: validated AI models for the early detection of complications in chronic diseases such as diabetes, COPD, and coronary heart disease. Collaboration with Prof. Jens Kleesiek (IKIM), Prof. Michael Kamp (Lamarr Institute / TU Dortmund), and Dr. Moon Kim (IKIM), with Dr. Nicolas Conze as project lead. Consortium partners: IKIM, [docport](https://www.docport.de/), [Flower Labs](https://flower.ai/), and the associations of statutory health insurance physicians of Westphalia-Lippe ([KVWL](https://www.kvwl.de/)) and North Rhine ([KVNO](https://www.kvno.de/)).
