---
layout: post
title: "Federated Learning for Primary Care: Training Models Without Moving Data"
date: 2026-08-28 12:00:00+0200
description: "Why we are building FLIP-IT around general practices, not hospitals: we train the model where the data already lives."
author: Andy Man Yeung Tai
tags: federated-learning medical-ai privacy
categories: research
featured: true
related_posts: false
---

When people hear I work on medical AI, they usually ask where the training data comes from.

My honest answer: it does not come from anywhere. It stays in the doctor's office where it was collected. In Germany most routine care happens in small general practices, and their patient records sit behind strict privacy rules. That is a good thing. But it also means most medical AI models are trained at one site, and then work poorly anywhere else.

Federated learning is a simple fix. Instead of moving data to the model, we move the model to the data. Each practice trains a copy on its own patients, and only the model updates come back. A server averages the updates into one shared model, and this repeats for many rounds. No patient record ever leaves the practice.

That is exactly what I am building right now: FLIP-IT (Federated Learning in Practice Networks), a research infrastructure for medical AI in primary care in North Rhine-Westphalia, co-funded by the EU and the state. We train models that predict complications early for chronic diseases (chronic kidney disease, diabetes, COPD, coronary heart disease) across general practices. Partners: IKIM at University Hospital Essen, docport GmbH, Flower Labs, and the physician associations KVWL and KVNO. We run this on the Flower framework. I work on it with Prof. Jens Kleesiek and Dr. Moon Kim at IKIM, and with Prof. Michael Kamp and his lab at TU Dortmund.

Simple to say, hard to do. Every practice's data looks different, bandwidth between practices is limited, and even model updates can leak information if you are careless. Most of my working time goes to these three problems.

I will write up details as the results come in. If you work on the same problems, I am happy to talk.

## References

1. FLIP-IT project website (project consortium, IKIM). [flipit-research.network](https://www.flipit-research.network/)
2. McMahan, B., Moore, E., Ramage, D., Hampson, S., and Agüera y Arcas, B. (2017). Communication-efficient learning of deep networks from decentralized data. *AISTATS*. [arXiv:1602.05629](https://arxiv.org/abs/1602.05629)
3. Beutel, D. J., Topal, T., Mathur, A., et al. (2020). Flower: A friendly federated learning research framework. [arXiv:2007.14390](https://arxiv.org/abs/2007.14390)
4. Kairouz, P., McMahan, H. B., et al. (2021). Advances and open problems in federated learning. *Foundations and Trends in Machine Learning*, 14(1-2), 1-210. [doi:10.1561/2200000083](https://doi.org/10.1561/2200000083)
5. Tai, A. M. Y., Kazemi, A., Kim, J. J., Schmeckenbecher, J., Kitchin, V., Suen, J., Moro, R., and Krausz, R. M. (2025). Utilizing machine learning for early intervention and risk management in the opioid overdose crisis. *WIREs Computational Statistics*, 17(1), e70008. [doi:10.1002/wics.70008](https://doi.org/10.1002/wics.70008)
