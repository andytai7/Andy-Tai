---
layout: page
title: "Machine Learning for Overdose Risk Prediction (RAMP)"
description: "Health Canada-funded clinical decision support for the opioid overdose crisis"
img: assets/img/project_1_banner.png
importance: 2
category: research
related_publications: true
---

The opioid overdose crisis in British Columbia has claimed **over 17,000 lives since 2016**. Care remains fragmented and reactive: millions of health records contain subtle patterns that conventional statistical methods cannot detect, clinicians need immediate risk assessments rather than retrospective analyses, and one-size-fits-all interventions fail to address individual risk profiles.

As Co-Investigator on the **Risk Assessment and Management Platform (RAMP)**, a **$1,407,790 Health Canada Substance Use and Addictions Program project (2019-2024)**, I developed the machine learning models at RAMP's core, using the **BC Provincial Overdose Cohort** (2015-2019, N = 36,679 individuals):

- **Data engineering:** Processing multi-source health records, handling missing data, and addressing severe class imbalance
- **Model development:** Random Forest, XGBoost, and Support Vector Machine classifiers over 48 clinical features
- **Performance:** **88.77% accuracy** and **91.12% AUROC** for general overdose prediction, substantially outperforming literature benchmarks

**Interactive demonstration:** the overdose risk classifier is deployed as a [live web application](https://andytai7-odclassifiers.hf.space).

<iframe src="https://andytai7-odclassifiers.hf.space" frameborder="0" width="100%" height="450"></iframe>

## Key findings

- **Protective factors:** Opioid Agonist Therapy (OAT) consistently reduced overdose mortality
- **Risk factors:** Polysubstance use, co-occurring mental health disorders (particularly depression), and cardiovascular conditions significantly elevated risk
- **Novel insights:** Interactions between OAT adherence and mental health status reveal complex patterns requiring personalized intervention strategies

## Outcomes and next steps

The Health Canada SUAP funding concluded in 2024 after delivering the validated prediction platform and clinical decision support architecture. Future directions include **causal inference** for treatment optimization, **real-time multimodal data integration** (wearables, patient-reported outcomes, social determinants), **algorithmic fairness** across demographic groups, and **implementation science** for clinical translation.

My [dissertation and related publications](/Andy-Tai/publications/) establish the methodological foundations: systematic reviews and meta-analyses of ML for opioid-related outcomes across 50+ studies.
