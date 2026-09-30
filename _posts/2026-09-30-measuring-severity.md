---
layout: post
title: "Measuring Severity: What Error Rates Hide"
date: 2026-09-30 09:00:00+0200
description: "Two models with the same accuracy can fail in very different ways. A Grand Challenges paper at AXIOM 2026 argues that expert-labeled severity is a missing evaluation primitive, most urgent when comparing efficient models for clinical prediction."
author: Andy Man Yeung Tai
tags: evaluation-metrics clinical-ai efficiency
categories: research
featured: true
related_posts: false
---

Accuracy treats every error as equivalent. Two systems with identical accuracy are not truly equivalent if one makes mistakes that a competent expert would also make, whereas the other produces outputs that no human expert would accept. Current benchmarks cannot tell these two failure modes apart.

This is the starting point of my Grand Challenges submission to [AXIOM 2026](https://axiom-neurips2026.github.io/), *Foundations of Efficient Deep Learning*, a NeurIPS 2026 workshop, with Nico Kallenberg, Jens Kleesiek, and Michael Kamp. The paper argues that severity labels, expert judgments of the harm done by a particular wrong answer, are a missing evaluation primitive. ["Measuring Severity" is on OpenReview](https://openreview.net/forum?id=AFWMSe0WOT), accepted to the Grand Challenges track.

The proposal itself is compact. Define s_i(ŷ, y) = 1 where predicting ŷ on instance i when the truth is y is an error that experts judge harmful. Then a severe error rate

E = (1/N) Σᵢ 1[ŷᵢ ≠ yᵢ] · s_i(ŷᵢ, yᵢ)

is the fraction of all instances answered unacceptably. Reported as a pair with accuracy A, (A, E) says how often a model fails and how often it fails badly; the ratio E/(1−A) is the share of its mistakes that are severe.

Two existing approaches are special cases of this. Instance-level costs attach one value to each example; class-level cost matrices attach one value to each pair of labels. Neither can say that a given wrong answer is recoverable on one case and not on another.

The missing primitive is felt most strongly in efficiency research. Compression, quantization, and adaptive inference are selected and compared on accuracy, yet what a compressed model forgets is not random: errors concentrate on particular instances and classes [Hooker et al., 2019]. Without severity labels, choosing the cheaper model is a blind trade between compute and harm. Existing weights derived from annotator disagreement measure how contested a case is, not how much harm a wrong answer does, and the two can point in opposite directions.

Where costs are measurable they are used, as in fraud detection. Where cost is a judgment, evaluation has no input to run on. Direct severity annotation exists today only in radiology report generation. Our plan is to build a first instance in a clinical setting at a university hospital, combining three assets: a FHIR-based database spanning specialties, an annotation facility staffed by practicing clinicians and senior medical students, and access to documented incident records. One question we hope to answer is whether severity and case ambiguity correlate. The actionable region is their intersection, where the model makes the uncontested, severe errors.

We will present the argument in Paris on December 13. Comments and critique are welcome on [OpenReview](https://openreview.net/forum?id=AFWMSe0WOT).

## References

1. Bahnsen, A. C., Aouada, D., and Ottersten, B. (2015). Example-dependent cost-sensitive decision trees. *Expert Systems with Applications*, 42(19), 6609-6619.
2. Elkan, C. (2001). The foundations of cost-sensitive learning. *Proc. 17th International Joint Conference on Artificial Intelligence (IJCAI)*, 973-978.
3. Guan, H., Hou, P. C., Hong, P., Wang, L., Zhang, W., Du, X., Zhou, Z., and Zhou, L. (2025). A clinically-informed framework for evaluating vision-language models in radiology report generation. *AMIA Annual Symposium*.
4. Hooker, S., Courville, A., Clark, G., Dauphin, Y., and Frome, A. (2019). What do compressed deep neural networks forget? [arXiv:1911.05248](https://arxiv.org/abs/1911.05248).
5. Kang, K. and Mussmann, S. (2026). Instance-level costs for nuanced classifier evaluation. *Proc. 43rd International Conference on Machine Learning (ICML)*, PMLR 306.
6. Sayin, B., Casati, F., Passerini, A., Yang, J., and Chen, X. (2022). Rethinking and recomputing the value of ML models. [arXiv:2209.15157](https://arxiv.org/abs/2209.15157).
7. Yu, F., Endo, M., Krishnan, R., et al. (2023). Evaluating progress in automatic chest X-ray radiology report generation. *Patterns*, 4(9), 100802.
