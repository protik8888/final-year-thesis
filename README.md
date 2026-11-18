# Enhancing AI-Generated Text Detection Using Entropy-Based Active Learning for Hybrid Human-AI Content

Final Year Design Project (B.Sc. in CSE), Department of Computer Science and Engineering, United International University.

## Overview

LLMs now write text that is hard to tell apart from human writing, and most detectors fail on *hybrid* text: AI output that has been paraphrased or edited by a human. This project tackles that problem with an entropy-based active learning framework for four-class detection:

- **HW**: Human-Written
- **AW**: AI-Written
- **AWP**: AI-Written, Paraphrased
- **AWH**: AI-Written, Human-Edited

## Approach

- Built a balanced four-class dataset of academic abstracts (8,000 samples, 2,000 per class).
- Fine-tuned three transformer backbones: RoBERTa-base, DeBERTa-v3-base, and DistilBERT.
- At each active learning round, the model scores an unlabeled pool by normalized predictive entropy, and the top 10% most uncertain samples are added to training. Compared against a random-sampling baseline over 15 rounds and 3 seeds.

## Key Results

| Model | Entropy AL (Macro F1) | Random (Macro F1) |
|---|---|---|
| DistilBERT | **0.955** | 0.921 |
| DeBERTa-v3-base | 0.951 | 0.909 |
| RoBERTa-base | 0.924 (0.947 at round 20) | 0.927 |

- Entropy-based active learning matched or exceeded the full-data baseline (~0.95 Macro F1) using well under half of the labeled samples, while random sampling stayed below it.
- AW and AWH are the hardest classes to separate; HW is classified almost perfectly.

## Limitations

The labeling step is simulated (ground-truth labels stand in for live human annotators), and the RoBERTa round-20 result rests on two of three seeds.

## Authors

Shadab Yasar, Koushik Kumar Roy, Abdullah Al Khobaer, Nusrat Islam Choa, Rifat Sumaiya Porag, MD Jannatul Nayeem

**Supervision:** Md. Tarek Hasan (advisor).
Here is the initial paper(https://drive.google.com/file/d/1Itp_lgtNJd9Q8Nz9kD2iG5X8CVLyAM5G/view?usp=drive_link)
