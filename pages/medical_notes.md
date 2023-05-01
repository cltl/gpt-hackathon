+++
title = "Medical notes"
hascode = false
date = Date(2023, 4, 11)
+++

# Medical notes

## Background
[A-PROOF](https://cltl.github.io/a-proof-project/), a collaboration between CLTL & AUMC, develop a tool to automatically classify patients' functioning categories and levels based on medical notes written by medical professionals. 

Each note could contain multiple sentences; each sentence could contain multiple categories. 9 categories were chosen from [ICF code](https://www.who.int/standards/classifications/international-classification-of-functioning-disability-and-health) to use for labeling. 

## Existing Datasets & Model Performance

3 researches were done:
- the initial research trained the model with 7,683 notes
- subsequent researches fine-tuned the model with 2,039 and 510 notes, respectively

Subsequent researches tried to improve the model's generalization ability on notes from different medical domains (covid patients of secondary care notes vs primary care notes vs cancer patients notes). Neither performance exceed the initial research. 

## Goal

Augment the training dataset by adding synthetic data from generative model to the current data sets, and fine-tune the model for better performance.


## Current status

Synthetic data (medical notes) have been generated successfully using gpt-3.5-turbo, with under-satisfactory quality for some categories and levels.


## Task
Generate synthetic data (medical notes) that matches the categories and levels specified.

- improve prompt for error-prone notes of specific categories & levels
- Data quality comparison between different models, such as text-davinci-003, llama, or alpaca, etc.


