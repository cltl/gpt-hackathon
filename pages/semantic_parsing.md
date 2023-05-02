

# Structural generalization in semantic parsing

## Objective
Prompt engineering to test the structural generalization abilities of GPT-x models with a semantic representation. 


## Background

Natural language is characterized by compositionality: the meaning of a complex expression is constructed from the meanings 
of its constituent parts. [COGS: A Compositional Generalization Challenge Based on Semantic Interpretation](https://aclanthology.org/2020.emnlp-main.731/)
(Kim & Linzen, 2020) introduced a semantic parsing dataset based on a fragment of English to facilitate the evaluation of the compositional abilities of language
processing architectures. 

The dataset distinguished two types of generalization (Figure 3 in COGS paper): 

<img width="310" alt="Screenshot 2023-05-02 at 18 38 09" src="https://user-images.githubusercontent.com/25965256/235729547-6ad90522-4f34-4445-bf91-094310419d84.png">


(i) **_Lexical generalization_** involves recombining
known grammatical structures with words that were not observed in these particular structures in training. For example, “subject
to object” generalization tests how well a model that only sees a common noun (e.g. “hedgehog”)
in training can interpret that noun as an object in the generalization test-set. 

(ii) **_Structural generalization_** involves
generalizing to linguistic structures that were not
seen in training, or combining two novel structures to form a new structure. An example is “PP recursion”, where training
instances contain prepositional phrases of depth up
to two and generalization instances have PPs of depth 3–12. 

Semantic parsers have been shown to struggle primarily with structural generalization tasks ([Yao & Koller, 2022](https://aclanthology.org/2022.emnlp-main.337/)).
Large language models additionally show a performance ceiling of 80-90% exact match ([Qiu et al., 2022](https://aclanthology.org/2022.emnlp-main.624.pdf)), which hints that the cases they struggle with are also structural. 

## Task Description

Create a prompt to test the structural generalization abilities of GPT-x models via semantic parsing. 

_Recommended method_: explore prompting with GPT 3.5, and extend to GPT-4 (if compute and funds allow). 

## Dataset 

A yet-to-be-released dataset will be provided to those working on this task that extends the [COGS](https://github.com/najoungkim/COGS) dataset (Kim & Linzen, 2020).

The dataset contains natural English sentences and their mappings to a logical form, as well as splits for training and generalization on several categories of structural generalization. 
Participants will need to select specific generalization types to focus on.

### Example Input & Output

Include COGS logical form (see Figure 1 of COGS paper):

<img width="288" alt="Screenshot 2023-05-02 at 18 37 40" src="https://user-images.githubusercontent.com/25965256/235729884-2de87d13-e8fe-4235-a39e-d540bd5905d1.png">

_Example input/prompt_: "Provide the correct mapping of the following sentence (_taken from gen set_) based on this/these example(s) (_taken from train set_)...
Feel free to produce an output more complex than anything you have output before!"

_Example output_: Sentence with mapping to COGS LF.


### Evaluation

Exact match on generalization sets. Compare to other models: 


<img width="321" alt="Screenshot 2023-05-02 at 18 35 51" src="https://user-images.githubusercontent.com/25965256/235729123-7c5503be-a7b6-4c37-acc6-7d6fe11288d7.png">

