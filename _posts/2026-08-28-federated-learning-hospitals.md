---
layout: post
title: "Federated Learning for Hospitals: Models Without Moving Data"
date: 2026-08-28 12:00:00+0200
description: "The data problem in medical AI, and how we handle it at FLIP-IT: we train the model where the data already lives."
author: Andy Man Yeung Tai
tags: federated-learning medical-ai privacy
categories: research
featured: true
related_posts: false
---

When people hear I work on medical AI, the first question is usually: where does the data come from?

The honest answer is that it does not really come from anywhere. Patient data stays inside the hospital. Privacy law requires this, hospitals are careful with patient records, and they should be. The result is that most clinical models are trained on one hospital's data, and then do not work well anywhere else.

Federated learning is a simple fix. Instead of bringing data to the model, we bring the model to the data. Each hospital trains the model on its own computers, and only the model updates are sent back. No patient records ever leave. A central server combines the updates into one shared model, and this repeats for many rounds.

That is what we are building in FLIP-IT right now. We train models that predict chronic kidney disease risk across general practices, without any patient data leaving a practice. We run this on the Flower framework. I work on it with Prof. Jens Kleesiek and Dr. Moon Kim at IKIM, University Hospital Essen, and with Prof. Michael Kamp and his lab at TU Dortmund.

It sounds easy in one paragraph. In practice it is not. Each practice's data looks different from the next one, sending updates back and forth costs a lot of communication bandwidth, and even model updates can leak private information if you are careless. My side of the project is mostly about these three problems.

I will write up details as the project develops. If you work on similar things, I am happy to talk.

## References

1. McMahan, B., Moore, E., Ramage, D., Hampson, S., and Agüera y Arcas, B. (2017). Communication-efficient learning of deep networks from decentralized data. *AISTATS*. [arXiv:1602.05629](https://arxiv.org/abs/1602.05629)
2. Beutel, D. J., Topal, T., Mathur, A., Qiu, X., Fernandez-Marques, J., Gao, Y., Sani, L., Li, K. H., Parcollet, T., de Gusmão, P. P. B., and Lane, N. D. (2020). Flower: A friendly federated learning research framework. [arXiv:2007.14390](https://arxiv.org/abs/2007.14390)
3. Kairouz, P., McMahan, H. B., et al. (2021). Advances and open problems in federated learning. *Foundations and Trends in Machine Learning*, 14(1-2), 1-210. [doi:10.1561/2200000083](https://doi.org/10.1561/2200000083)
4. Tai, A. M. Y., Kazemi, A., Kim, J. J., Schmeckenbecher, J., Kitchin, V., Suen, J., Moro, R., and Krausz, R. M. (2025). Utilizing machine learning for early intervention and risk management in the opioid overdose crisis. *WIREs Computational Statistics*, 17(1), e70008. [doi:10.1002/wics.70008](https://doi.org/10.1002/wics.70008)
