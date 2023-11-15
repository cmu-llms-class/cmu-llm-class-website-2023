---
layout: page
title: Homework 3
description: >-
    Instructions for Homework 3
---

# Homework 3
{:.no_toc}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

This homework is due on Nov 30 2023.

# Starter Code and Assignment File

The starter code for this homework is available [here](homework_materials/hw3_starter_code.zip).  
The assignment file is available [here](homework_materials/hw3.pdf).  
The latex template for this assignment is available [here](homework_materials/hw3_latex_template.zip).

# Preparation: Setting up AWS

To complete this homework, you will need access to GPU resources for training models.

The TAs have compiled step-by-step setup instructions with screenshots here: [AWS setup guide](https://docs.google.com/presentation/d/1Tw_klO84R9G7CZ3cINAKgy4BfdNm-8dlnRXSBIVD_3A/edit?usp=sharing)

# Submission

For homework 3, we will be using **Gradescope**. Please use the link from the Canvas coursepage.  
Two assignments have been created on Gradescope: `Homework 3 - PDF` and `Homework 3 - Code and Checkpoints`.  

`Homework 3 - PDF` will be manually graded by the instructors.  
Please submit your a pdf file `[andrew-id].pdf` with answers to the written questions, and annotate the locations of each question's solution in your PDF.

`Homework 3 - Code and Checkpoints` contains an autograder that will grade your code with the same unit tests provided in the homework.  
We will be evaluating code in Section 4 of the assignment through the autograder in Gradescope, but you should submit all the code that you used to complete the assignment.
The results of these tests will not be made visible until grades are released.  

Please submit the following files, with these **exact filenames**:
- `cleaning.py`
- `cleaned_data.arrow`
- `other_scripts.zip` (please zip all other scripts you used, with a README indicating which scripts correspond to each question.)
- `model-original.pt` (weights from your model trained on uncleaned data)
- `model-clean.pt` (weights from your model trained on cleaned data)

Please use [this script](https://gist.github.com/Y0mingZhang/e65783e6c92d448ac94062a7f8951a50) to check that your submission format is correct. 

Note: Since many students are having trouble with submitting their model checkpoints on Gradescope with the 100MB size limit, there is a Canvas assignment for this: `Homework 2 - Model Checkpoint`.  
If your model checkpoint exceeds 100MB, please submit your `model-original.pt` and `model-clean.pt` file on Canvas.  
If your model checkpoint is below 100MB, you can still submit `model-original.pt` and `model-clean.pt` on Gradescope.  
