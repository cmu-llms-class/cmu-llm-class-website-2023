---
layout: page
title: Homework 2
description: >-
    Instructions for Homework 2
---

# Homework 2
{:.no_toc}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

This homework is due on Tuesday, October 24th at 2 PM.

# Starter Code and Assignment File

The starter code for this homework is available [here](homework_materials/hw2_starter_code.zip).  
The assignment file is available [here](homework_materials/hw2.pdf).  
The latex template for this assignment is available [here](homework_materials/hw2_latex_template.zip).

# Preparation: Setting up AWS

To complete this homework, you will need access to GPU resources for training models.

The TAs have compiled step-by-step setup instructions with screenshots here: [AWS setup guide](https://docs.google.com/presentation/d/1Tw_klO84R9G7CZ3cINAKgy4BfdNm-8dlnRXSBIVD_3A/edit?usp=sharing)

**Note: Question 1, Question 2.1-4 and Question 3.1 can be done without GPU access. We suggest that you start the assignment early while waiting for AWS credits.**

# Submission

For homework 2, we will be using **Gradescope**. Please use the link from the Canvas coursepage.  
Two assignments have been created on Gradescope: `Homework 2 - PDF` and `Homework 2 - Code and Checkpoints`.  

`Homework 2 - PDF` will be manually graded by the instructors.  
Please submit your a pdf file `[andrew-id].pdf` with answers to the written questions, and annotate the locations of each question's solution in your PDF.

`Homework 2 - Code and Checkpoints` contains an autograder that will grade your code with the same unit tests provided in the homework.  
We will also be downloading your model checkpoint `model.pt` and configuration `config.yaml` for perplexity testing.  
The results of these tests will not be made visible until grades are released.  
Please submit the following files, with these **exact filenames**:
- `model.py`
- `train.py`
- `generate.py`
- `classify.py`
- `utils.py`
- `model.pt` (weights from your trained model in Question 2.6.)
- `config.yaml` (configuration file for your trained model in Question 2.6.)

Note: Since many students are having trouble with submitting their model checkpoints on Gradescope with the 100MB size limit, there is a Canvas assignment for this: `Homework 2 - Model Checkpoint`.  
If your model checkpoint exceeds 100MB, please submit your `model.pt` and `config.yaml` file on Canvas.  
If your model checkpoint is below 100MB, you can still submit `model.pt` and `config.yaml` on Gradescope.  
