---
layout: page
title: "Machine Learning for Overdose Risk Prediction (RAMP)"
description: "Overdose risk prediction models for clinical decision support, funded by Health Canada (RAMP project)"
img: assets/img/project_1_banner.png
importance: 2
category: research
related_publications: true
---

The opioid overdose crisis in British Columbia has claimed over 17,000 lives since 2016. Care for people at risk is still often fragmented and reactive. Millions of health records hold patterns that conventional statistical methods cannot detect, clinicians need risk estimates at the point of care rather than retrospective analyses, and uniform interventions do not account for individual risk profiles.

As Co-Investigator on the **Risk Assessment and Management Platform (RAMP)**, a $1,407,790 Health Canada Substance Use and Addictions Program project (2019-2024), I developed the machine learning models at RAMP's core, using the **BC Provincial Overdose Cohort** (2015-2019, N = 36,679 individuals):

- **Data engineering:** Processing multi-source health records, handling missing data, and addressing severe class imbalance
- **Model development:** Random Forest, XGBoost, and Support Vector Machine classifiers over 48 clinical features
- **Performance:** 91.12% AUROC for general overdose prediction, above the benchmarks reported in related work.

**Interactive demonstration:** the overdose risk classifier is deployed as a [live web application](https://andytai7-odclassifiers.hf.space).

<iframe src="https://andytai7-odclassifiers.hf.space" frameborder="0" width="100%" height="450"></iframe>

## Key findings

- **Protective factors:** Opioid Agonist Therapy (OAT) consistently reduced overdose mortality
- **Risk factors:** Polysubstance use, co-occurring mental health disorders (particularly depression), and cardiovascular conditions significantly elevated risk
- **Interaction effects:** The combination of OAT adherence and mental health status is informative on its own, which suggests that treatment planning has to consider both together

## Outcomes and next steps

Health Canada SUAP funding concluded in 2024 with the validated prediction platform and the clinical decision support architecture delivered. The next steps I see for this work are causal inference for treatment optimization, real-time multimodal data integration (wearables, patient-reported outcomes, and social determinants), algorithmic fairness across demographic groups, and implementation science for clinical translation.

The [dissertation and related publications](/Andy-Tai/publications/) provide the background for this work: our systematic reviews and meta-analyses covered machine learning for opioid-related outcomes in more than 50 studies.
