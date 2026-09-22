---
layout: post
title: "How I Got Here: From the Lab Bench to Hospital Data"
date: 2026-09-22 09:00:00+0200
description: A long answer to a short question. Basketball, a bad first year, optogenetics at SickKids, the overdose crisis, ten courses at UBC, and why I moved to Essen.
author: Andy Man Yeung Tai
tags: career mental-health machine-learning teaching
categories: personal
giscus_comments: false
related_posts: false
toc:
  sidebar: left
---

People sometimes ask how a neuroscience student ended up building machine learning tools inside a German hospital. The short answer is that I kept following the question that interested me most. The longer answer is below. It is more personal than most of what I write here, but it explains why I work the way I do.

## A slow start

I grew up in Vancouver and, for a long time, I did not feel that I fit in anywhere. Sport and science were where I felt most at home. I swam and played basketball at the provincial level in high school, and I gave up music to go further in sport.

In grade 10, on my high school basketball team, I was the target of harassment by older teammates. I left that year determined never to feel so powerless again. For a while that turned into an all-or-nothing drive that did not serve me well. I trained harder than anyone, chose my university by where I could make the team, and made the varsity basketball team at the University of Toronto.

Then I nearly failed my first year. Success on the court had not fixed what was underneath, and I had stopped paying attention to almost everything else. Rebuilding from there taught me more than any early success had. It also taught me that steady effort beats intensity, a lesson I still have to relearn from time to time.

## Finding research

Research is where I found my footing.

In Sheena Josselyn's lab at SickKids, I studied the amygdala with optogenetics and operant conditioning. I learned molecular biology from Dr. Brandon Walters and learned to handle animals, perfuse, slice and image brains from PhD student Alex Jacob. It was my first real contact with how much about the brain is still unknown, and it made me want a career in research.

At the same time, in Roger McIntyre's Mood Disorders Psychopharmacology Unit at Toronto Western Hospital, I worked with machine learning specialist Dr. Alcides Albuquerque on a review of big data and machine learning in psychiatry. It became my first first-author paper, in *Artificial Intelligence in Medicine* (2019). More importantly, it showed me that I could contribute to medicine through data and not only at the bench.

I was also volunteering during these years. At Toronto Western I worked with elderly patients in the Hospital Elder Life Program, my first time in a clinical setting. Earlier, with a student group, I had helped build a school in the Maasai Mara in Kenya from materials we fundraised for. Both experiences stayed with me as reminders of who research is ultimately for.

## The overdose crisis

In 2018 I moved back to Vancouver. After a short stint in Clare Beasley's lab at BC Children's Hospital, classifying microglia in brain tissue from people with bipolar disorder and schizophrenia, I joined Michael Krausz's Addiction and Concurrent Disorders Group at UBC. That is where I found the research I wanted to do.

I worked on WalkAlong, a youth mental health platform, and on RAMP, the Risk Assessment and Management Platform, funded by Health Canada's Substance Use and Addictions Program, on which I became a Co-Investigator. My PhD in Neuroscience used the BC Provincial Overdose Cohort (2015 to 2019, 36,679 people) to predict overdose risk from routine administrative and clinical data. The best models reached 91.12 per cent AUROC for general overdose prediction.

The result I remember most is not the number. It is a pattern I saw again and again. A clinician asks a question, and it takes months of extraction, cleaning and statistics before an answer comes back, even though the data were there all along. By the time the answer arrives, the question has often moved on.

During my PhD I also spent three months at the University of Sydney's Brain and Mind Centre, with Ian Hickie and Frank Iorfino's digital mental health team. They taught me to think about where a prediction fits into a person's care, not just whether it is accurate. That collaboration later became our 2026 paper on artificial intelligence in youth mental health.

## Teaching

From 2024 to 2026 I was a Postdoctoral Teaching and Learning Fellow in UBC's Master of Data Science and Department of Statistics. I taught 10 courses to more than 550 students, from probability and databases to data visualization and science communication, and I co-wrote *The Regression Cookbook*, an open textbook that teaches statistics and machine learning side by side in Python and R.

Teaching changed how I do research. Students do not let you hide behind jargon, so I learned to define terms before using them and to put the uncertainty next to every estimate. I also supervised capstone teams working with partners such as BC Children's Hospital and the Vaccine Evaluation Center; one of those projects became a paper in *Engineering Applications of Artificial Intelligence*.

My own first year at university taught me how easily a capable student can fall behind without anyone noticing. That is a large part of why I care about mentoring. I founded Building Blocks, a peer-mentoring nonprofit, in 2019 and still run it, and I now mentor students from undergraduate to PhD level.

## Moving to Essen

In July 2026 I moved to Germany to join the Institute for Artificial Intelligence in Medicine (IKIM) at University Hospital Essen. I work on FLIP-IT, a project that trains prediction models for chronic kidney disease inside general practices, so that patient data never leave the practice. The project brings together clinical AI with Jens Kleesiek and learning theory with Michael Kamp at the Lamarr Institute and TU Dortmund. (I wrote about FLIP-IT in [an earlier post](/Andy-Tai/blog/2026/federated-learning-primary-care/).)

Essen was the right place for a simple reason. The hospital runs its own FHIR data platform and its own compute, and it treats data protection as part of the engineering rather than as paperwork. That makes it possible to build methods on real data under real governance.

## What I have learned

A few things have stayed constant across all of this.

- **Report plainly.** Clinicians have little time. Give them the number, the uncertainty, and what did not work.
- **Measure, do not assume.** If a method can be wrong, find out how often before anyone relies on it.
- **Work across disciplines.** Almost everything I have done well, I have done in teams where people with different training catch different mistakes.
- **Steady beats intense.** It took me a bad first year to learn it, and it has served me better than talent or drive ever did.

If any of this overlaps with what you work on, I would be glad to hear from you.
