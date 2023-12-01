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

This homework is due on Thursday Nov 30 2023 at 2pm.

# November 27 Update

The starter code, assignment file and latex template have been updated.
Here is a summary of the main changes:
   - Added `generate.py` to the starter code. **You will need to complete this file for Question 5.0 in the assignment.**
   - **The expected submission format has changed** (see assigment file for details).
   - Updated latex template to match the latest assignment file.


# Starter Code and Assignment File

The starter code for this homework is available [here](homework_materials/hw3_starter_code.zip).  
The assignment file is available [here](homework_materials/hw3.pdf).  
The latex template for this assignment is available [here](homework_materials/hw3_latex_template.zip).

# Preparation: Setting up AWS

To complete this homework, you will need access to GPU resources for training models.

The TAs have compiled step-by-step setup instructions with screenshots here: [AWS setup guide](https://docs.google.com/presentation/d/1Tw_klO84R9G7CZ3cINAKgy4BfdNm-8dlnRXSBIVD_3A/edit?usp=sharing)

# Submission

For homework 3, we will be using **Gradescope** for code and written answers and **Canvas** for model checkpoints and data. Please use the link from the Canvas coursepage.  
Two assignments have been created on Gradescope: `Homework 3 - PDF` and `Homework 3 - Code`.  

`Homework 3 - PDF` will be manually graded by the instructors.  
Please submit your a pdf file `[andrew-id].pdf` with answers to the written questions, and annotate the locations of each question's solution in your PDF.

`Homework 3 - Code` contains an autograder that will grade your code with the same unit tests provided in the homework.  
We will be evaluating code in Section 4 of the assignment through the autograder in Gradescope, but you should submit all the code that you used to complete the assignment.

For the autograder unit tests, please submit the following files on Gradescope with these **exact filenames**. Do not place your files in a directory, as the tests will not run properly.
- `cleaning.py`
- `tokenization.py`

We will also be manually grading and inspecting other parts of your code. To make manual grading possible, please submit the following (also on Gradescope):
- `model.py` (if using your HW2 code, include the implementation of your model)
- `config.yaml` (if using your HW2 code, include the config file to load your model)
- `generate.py`
- `test_other.py` (your custom test cases for Q3.3.4)
- `other_scripts.zip` (optional, but if other scripts are used, please zip and include a README indicating which scripts correspond to each question)

Since Gradescope has a 100MB size limit, we will submit model checkpoints and code through Canvas: `Homework 3 - Model Checkpoints and Data`.  Please submit these files to Canvas, with these exact filenames:
- `cleaned_data.arrow.zip`
- `model-original.pt` (weights from your model trained on uncleaned data)
- `model-clean.pt` (weights from your model trained on cleaned data)
