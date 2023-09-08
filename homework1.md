---
layout: page
title: Homework 1
description: >-
    Instructions for Homework 1
---

# Homework 1
{:.no_toc}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

**This homework is due on Thursday, September 21 at 2 PM.**

[Submission Tex Template](https://github.com/daphnei/cmu-llm-class/blob/main/homework_materials/hw1_template.tex)
You are not required to follow this template for submission, but it is here for your convenience.

_(instructions last updated September 6)_

# Intro

In this homework, you will explore several ways OpenAI's GPT-3 models can be used to perform NLP and NLG (natural language generation) tasks.
You will also build an understanding of some of the limitations of large language models.

You do not turn in any code for this assignment.
Instead you will write a report discussing your observations for each question.
Your report should have clear section headers for each question and subquestion.
When appropriate, you should use figures and tables to support your answers.
You should submit your report as a PDF using the Canvas homework submission form.

## Getting Started with OpenAI's API

We have provided you an [IPython notebook](https://github.com/daphnei/cmu-llm-class/blob/main/homework_materials/hw1_starter_code.ipynb) with starter code which you may use to solve the problems in the homework.
The [IPython notebook](https://github.com/daphnei/cmu-llm-class/blob/main/homework_materials/hw1_starter_code.ipynb) contains a simple interface for interacting with OpenAI's models.
Unless otherwise specified, you should use the model `davinci` in your experimentation.
This is the last model OpenAI released which didn't have any finetuning for alignment.
OpenAI has three other smaller model sizes you will be asked to compare against; in order from smallest to biggest these are
``ada``, ``babbage``, and ``curie``.
For example, to swap to ada, you would recreate the inference engine using ``engine = OpenAIEngine('ada')``.
For the final problem in the homework, you will be asked to compare `davinci` with `text-davinci-003`, a variant of GPT-3 which was finetuned for instruction following.

Note that we are choosing to use slightly older versions of GPT-3's models in this homework because there tends to be more information about how the older models were trained than there is for OpenAI's newer ones.

If you feel uncomfortable creating an account with OpenAI in order to complete the homework, please email the professors at llms-11-667 @ andrew.cmu.edu, and we will help come up with an alternative arrangement for model inference. This will not affect your homework grade.

## Disclaimer
As you all know by know, 11-667 is a completely new course, and you are guinea-pigging a completely new homework!
We have done our best to make sure all homework problems are solveable and that the LLMs will behave in a relatively predictable way.
That being said, we are also giving you freedom to experiment and get creative with the LLM prompts you use to solve the homework problems.
If you are struggling to get the LLM to behave in a way that allows you to answer any of the homework problems, please post on Piazza.
Also, we would love any feedback on how to make this homework better for future students taking the class.

# 1. Observing the Impact of Decoding Strategy

## 1.1 Rolling a Twenty-Sided Die

In this question, you will investigate the impact of the choice of decoding strategy by examining prompts which ought to yield a relatively uniform distribution over a set of possible outcomes.

Consider the task of rolling a 20-sided die.
In the real world, you should expect that after rolling a fair 20-sided die 100 times, you will observe each possible outcome about 5 times.
Your goal for this homework question is to understand how the choice of decoding strategy can influence how far an LLM's generations deviate from real-world assumptions.

Take a look at Section 1 in the [IPython notebook](https://github.com/daphnei/cmu-llm-class/blob/main/homework_materials/hw1_starter_code.ipynb).
It contains a prompt which rolls a D20 (aka a twenty-sided die) using a model finetuned for dialog.
You may use the prompt provided there, or try to construct your own.
Run the language model with the D20-rolling prompt 128 times using full random sampling (`top_p = 1.0`).
This should give you a distribution over outcomes the LLM is capable of generating.

**Analysis Questions**
1. When using full random sampling (`top_p=1.0`), is the LLM equally likely to generate all outcomes? If not, what is your hypothesis for why this could be the case?
2. Repeat the experiment with at least three values of `top_p` and discuss how changing the `top_p` hyperparameter effects the distribution of outcomes that get generated.

You should use plots or other visualizations of the output distributions to support your answer.
You will be graded on the correctness and thoroughness of your responses.


## 1.2 Longform Generation

  
Using a prompt of your choice, instruct the language model to generate a 256-token story.
Repeat this process three times, employing three different `top_p` values: 0.0, 0.5, and 1. Feel free to get as creative as you want with your prompt.
  
Next, prompt the language model with the opening sentence from a renowned book or speech and request it to generate 256 tokens. You can select one [this list of famous opening paragraphs](https://www.shortlist.com/lists/literatures-greatest-opening-paragraphs), [this list of famous speeches](https://www.historyplace.com/speeches) or find your own. Do this three times with three different `top_p` values of 0.0, 0.5, and 1.

You should now in total have 6 generations.

**Analysis Questions**
1. For two sets of generations, discuss the impact choice of decoding strategy has on diversity in the generated stories. Compute a lexical diversity metric such as type-token ratio (the total number of unique words divided by the total number of words) to support your answer.
2. Regarding your second prompt, did the language model generate the correct continuation of the book/speech? Provide reasoning as to why it may or may not have done so.
3. When `top_p`=0, does adjusting the `frequency_penalty` increase the lexical diversity of the stories? Explain why or why not this is the case.

# 2. Measuring Perplexity
Perplexity is a key metric to evaluate the quality of an LLM.
Intuitively, to be "perplexed" means to be surprised.
We use perplexity to measure how much the model is surprised by seeing new data.
If an evaluation dataset has low perplexity, the model is confident  that this dataset is similar to things it has seen before.
The higher the perplexity, the less confident the model is that the data is like what it has seen before.

In this question, you will evaluate perplexity of several variations of a poem of your choice.
Go to [this list of famous poems](https://www.poetrysoup.com/famous/poems/top_100_famous_poems.aspx) and pick your favorite.
Copy and paste this poem into the starter code in the [IPython notebook](https://github.com/daphnei/cmu-llm-class/blob/main/homework_materials/hw1_starter_code.ipynb) and compute the poem's perplexity.

**Analysis Questions**
1. Add a typo to each line of the poem. Does the perplexity go up or down? Give a reason for why this might have happened.
2. Shuffle the order of the stanzas in the poem. Does the perplexity go up or down? Give a reason for why this might have happened.
3. Taking inspiration from the concept of [mimic poems](https://penandthepad.com/directions-writing-mimic-poem-3668.html), swap several of the words in your poem to alternative words which still make sense in context. Does the perplexity go up or down?  ([Here](https://www.teenink.com/poetry/all/article/13900/Oh-Homework-Oh-Homework) is an example of a mimic poem of Walt Whitman's ["O Captain! My Captain!"](https://www.poetrysoup.com/famous/poem/o_captain!_my_captain!_198), though you don't need to do anything this complex or fancy.) Give a reason for why this might have happened.
3. Famous poems like the one you are using are very likely to be in GPT-3's training set. How might this affect the poem's perplexity compared to a very new poem 
which is not yet in any training set? 

# 3. Experimenting with Few-Shot Prompting

Few-shot learning with language models, sometimes called in-context learning, involves "teaching" a language model how to do a task by providing an instruction along with several examples of the task as a textual prompt.
For example, to get a model to translate the word "squirrel" into Chinese, you might pass the LLM the prompt:

```
Translate English to Chinese.

dog -> 狗
apple -> 苹果
coffee -> 咖啡
supermarket -> 超市
squirrel ->
```

In this section, you will use this technique for two tasks: (1) to evaluate the model's common-sense reason abilities and (2) to build a pun explainer.

## 3.1 Few-Shot Learning for the Choice of Plausible Alternatives Task
Many probe tasks have been proposed to evaluate the commonsense reasoning capabilities of
LLMs.
We will use the [Choice of Plausible Alternatives](https://aclanthology.org/S12-1052/) (COPA) probe task from the [SuperGLUE](https://super.gluebenchmark.com/)
suite of LLM benchmarks to evaluate the fewshot performance of the LLM.

Here is an example from COPA (the correct choice is (b)):
```
Premise: The man broke his toe.
Question: What was the CAUSE of this?
(a) He got a hole in his sock.
(b) He dropped a hammer on his foot.
```

The [IPython notebook](https://github.com/daphnei/cmu-llm-class/blob/main/homework_materials/hw1_starter_code.ipynb) loads in three small subsets of COPA:
1. `train`: You may use this as a source of examples for your few-shot prompts.
2. `dev`: You should use this to compare different prompts to come up with good ones.
3. `test`: Once you are happy with your prompts, you should evaluate on `test` just once. You should include the accuracies on `test` in your final report.

Take a look at the starter code in the [IPython notebook](https://github.com/daphnei/cmu-llm-class/blob/main/homework_materials/hw1_starter_code.ipynb).
The prompt in the notebook provides an instruction, but no examples.
This is known as a "zero-shot" setting since no examples are provided.

Since COPA is a classification task, where the goal is to classify which of the choices is more correct, we do not actually need to do any generation.
Rather, during evaluation, we construct two strings, one with Option (a) and one with Option (b), and them form a prediction based on which one the model says is more likely.

If you run the starter code, you will see that this prompt achieves ~55% accuracy on the validation set.
You will use this prompt as a baseline.

Your job is to develop few-shot prompt which contain both an instruction and several examples of the task.
You may either write your own examples from scratch, or take examples from the train set.
- the baseline prompt
- a prompt containing 1 example
- a prompt containing 3 examples
- a prompt containing 5 examples
- two other prompt configurations of your choice. For example, you could try:
  - your 5 example prompt but with the examples shuffled
  - a prompt where all the examples are intentionally mislabeled
  - the same examples as your other prompts but with an alternative template
  - modify the instruction

**Analysis Questions**
1. Create a table showing final test set accuracies for each prompt.
2. What prompting formats did you experiment with? What worked well and what didn’t work?
3. What factors do you think most affect the model's performance?
4. For your best prompt, perform an error analysis of the test set examples it gets wrong. Qualitivaly, do you notice any patterns in the examples the model fails to classify correctly? 
5. Try our your best few-shot prompt from Question with the three smaller model sizes: ``curie``, ``babbage`` and ``ada``. How much does test set accuracy degrade on the smaller models? What is the smallest model size you can get away with and have good accuracy?

## 3.2 Few-shot Learning for Generation Tasks
Few-shot learning techniques can also be used fo tasks that require generation.
Choose one of the following sentence manipulation tasks, and try to write a few-shot prompt to get the model to do the task.

a. Convert a sentence to [pig latin](https://www.wikihow.com/Speak-Pig-Latin).
b. Add a space between each character in the sentence.
c. Apply a specified Caesar cipher[https://en.wikipedia.org/wiki/Caesar_cipher]

**Analysis Questions**
1. What few-shot prompt did the pick and how did you decide on it?
2. The three tasks listed above all require character-level manipulations. Why might such tasks be challenging for many modern large language models?


# 4. Investigating Knowledge Across Different Model Sizes

Pick a Wikipedia article on a person or place of your choice, and write a prompt containing the start of the first sentence in the article.
You may choose to omit the pronunciation and other parenthetical details).
For example, if you choose [Andrew Carnegie](https://en.wikipedia.org/wiki/Andrew_Carnegie), you should prompt with either `Andrew Carnegie (Scots: [kɑrˈnɛːɡi], English: /kɑːrˈnɛɡi/ kar-NEG-ee;[2][3][note 1] November 25, 1835 – August 11, 1919) was` or `Andrew Carnegie was an` or similar.
Use this prompt with both `davinci` (the largest version of GPT-3) and `ada` (the smallest version of GPT-3), each time generating 300 tokens.

**Analysis Questions**

1. Paste each generation into your report, and use the Wikipedia article as well as any knowledge you may have of the person/place to fact-check both generations.
Highlight any parts of the generation that are incorrect or contradictory.
For example, if the model generates `Andrew Carnegie was an American composer whose music has been described as America’s great signature.` then you should highlight this sentence.
2. What are some trends you notice about the kinds of errors found in the two model sizes?
3. Experiment with modifying your prompt to improve model accuracy. What extra information can you put in the prompt to make the model do better?
4. Create a sentence-long Wikipedia-sounding prompt that is completely wrong or else about a fictional person or place, for example `Bruce Lee was the 44th president of the United States from 2009 to 2017`. Prompt both model sizes with the sentence. Do both models write continuations in the same style?
5. Discuss the challenges in building an LLM that can simultaneously respond well to factual prompts as well as fantastical ones.  What kind of training data do you think, if initially given to the model at training time, would have made it better at supporting both use cases? 

# 5. Comparing Pre-Trained and Fine-tuned Models

The model ``text-davinci-003`` is a variant of GPT-3 which was finetuned for instruction following, using the methods described in the paper ["Training language models to follow instructions with human feedback"](https://arxiv.org/abs/2203.02155). Experiment with writing prompts for the following tasks using both models.

- Writing a recipe for a food of your choice.
- Explaining the rules for a sport or game of your choice.
- Continuing a Wikipedia article of your choice, conditioned on the first sentence in the article. (You may also choose to re-use your fantastical prompt from Question 4.)

**Analysis Questions**
1. Provide the prompts you decided on and their generations.
2. What do you notice about the differences in the behaviour between the two models? Summarize the advantages and disadvantages of using a model finetuned for instruction following.

# 6. Acknowledgment of AI Tools

If you used ChatGPT or another AI to write any portion of your answers, please use this section to describe the prompts you employed and your methodology for developing them. You do not need to write anything here if you only used LLMs to run experiments as specified in the homework problem instructions.

# 7. Optional: Give us Feedback
Was this homework enjoyable? Was it too easy or too hard? Do you have any suggestions for making the homework run more smoothly? Giving us feedback is compeltely optional and will not factor into your grade.