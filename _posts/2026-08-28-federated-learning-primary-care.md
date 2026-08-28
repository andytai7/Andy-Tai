---
layout: post
title: "Federated Learning for Primary Care: Training Models Without Moving Data"
date: 2026-08-28 12:00:00+0200
description: "Most medical AI is built in hospitals. FLIP-IT deliberately targets primary care: we train models inside general practices, where routine data actually lives."
author: Andy Man Yeung Tai
tags: federated-learning medical-ai privacy
categories: research
featured: true
related_posts: false
---

Most medical AI starts in a hospital. That is the wrong place to start.

In Germany, as in most health systems, routine medicine happens in small general practices. That is where patients go first, where chronic diseases are managed over years, and where early warning signs appear long before anyone is admitted to a hospital. But almost every published medical AI model is trained on hospital data, simply because hospitals are big, centralized, and easier for researchers to access. The result is models optimized for the sickest minority of patients, applied to the routine majority.

I work on the opposite approach. [FLIP-IT](https://www.flipit-research.network/) (Federated Learning in Practice Networks) is building an infrastructure for decentralized training of medical AI models directly in the outpatient practice network: general practices across North Rhine-Westphalia. The project is co-funded by the European Union and the state of North Rhine-Westphalia (Ministry of Economic Affairs, Industry, Climate Action and Energy).

The core mechanism is federated learning. Instead of moving data to the model, we move the model to the data. Each practice trains a copy of the model on its own patient records; only the model updates come back; a server aggregates them into one shared model; and this repeats for many rounds. No patient record ever leaves the practice. This is what the project calls privacy by design: the data stays on local systems not as an afterthought, but as the architecture.

Why go to this trouble? Three reasons:

1. **The data is where the patients are.** Practice records capture the full trajectory of routine care, not just acute hospital episodes. For chronic diseases, that longitudinal view is the signal that matters.
2. **Generalization.** A model trained across many independent practices learns from genuinely diverse populations and record-keeping styles, instead of one hospital's quirks.
3. **Consent and compliance.** Keeping data in the practice sidesteps most of the data-transfer problem, but it requires its own legal and technical groundwork, which is a research question in its own right.

Concretely, FLIP-IT develops AI models for the early detection of complications in chronic diseases such as diabetes, COPD, and coronary heart disease, trained across this practice network. The work is organized into three work packages: **LEGAL** (privacy-compliant contract frameworks and guidelines for federated learning in outpatient care), **DATA** (the data infrastructure and quality side), and **NETWORK** (the federated training platform itself). Partners: [IKIM](https://ikim.uk-essen.de/) at University Medicine Essen, [docport GmbH](https://www.docport.de/), [Flower Labs](https://flower.ai/), and the physician associations [KVWL](https://www.kvwl.de/) and [KVNO](https://www.kvno.de/). We build on the Flower framework. I work on it with Prof. Jens Kleesiek and Dr. Moon Kim at IKIM, with project lead Dr. Nicolas Conze, and with Prof. Michael Kamp and his lab at TU Dortmund.

Simple to say, hard to do. Every practice's data looks different, the practices are small sites with modest compute and bandwidth, and even model updates can leak information if you are careless. Most of my working time goes to these three problems.

If you run a practice and want to join, or want to propose a study on the infrastructure, the project website has dedicated entry points for both: [flipit-research.network](https://www.flipit-research.network/). I will write up technical details as results come in. If you work on the same problems, I am happy to talk.

## References

1. FLIP-IT: Federated Learning in Practice Networks (project consortium, IKIM). [flipit-research.network](https://www.flipit-research.network/)
2. McMahan, B., Moore, E., Ramage, D., Hampson, S., and Agüera y Arcas, B. (2017). Communication-efficient learning of deep networks from decentralized data. *AISTATS*. [arXiv:1602.05629](https://arxiv.org/abs/1602.05629)
3. Beutel, D. J., Topal, T., Mathur, A., et al. (2020). Flower: A friendly federated learning research framework. [arXiv:2007.14390](https://arxiv.org/abs/2007.14390)
4. Kairouz, P., McMahan, H. B., et al. (2021). Advances and open problems in federated learning. *Foundations and Trends in Machine Learning*, 14(1-2), 1-210. [doi:10.1561/2200000083](https://doi.org/10.1561/2200000083)
5. Tai, A. M. Y., Kazemi, A., Kim, J. J., Schmeckenbecher, J., Kitchin, V., Suen, J., Moro, R., and Krausz, R. M. (2025). Utilizing machine learning for early intervention and risk management in the opioid overdose crisis. *WIREs Computational Statistics*, 17(1), e70008. [doi:10.1002/wics.70008](https://doi.org/10.1002/wics.70008)
