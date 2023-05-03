

# Structural generalization in semantic parsing

See Google Drive Folder for materials and additional explanation: [Folder](https://drive.google.com/drive/folders/1D_Glq-6y9L2bwmznGSRVevZx5nBbStwK?usp=share_link)

Please do not distribute materials beyond this hackathon, as this is work in progress to potentially be published. Thank you! 

## Objective
Prompt engineering to test the structural generalization abilities of GPT-x models with a semantic representation. 


## Background

Natural language is characterized by compositionality: the meaning of a complex expression is constructed from the meanings 
of its constituent parts. [COGS: A Compositional Generalization Challenge Based on Semantic Interpretation](https://aclanthology.org/2020.emnlp-main.731/)
(Kim & Linzen, 2020) introduced a semantic parsing dataset based on a fragment of English to facilitate the evaluation of the compositional abilities of language
processing architectures. 

The dataset distinguished two types of generalization (Figure 3 in COGS paper): 


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

See **Tips & Tricks** document in Google Drive for possible methods to do this!


## Dataset 

A yet-to-be-released dataset will be provided to those working on this task that extends the [COGS](https://github.com/najoungkim/COGS) dataset (Kim & Linzen, 2020). 

Find data in **Google Drive Folder** (linked at top).

The dataset contains natural English sentences and their mappings to a logical form, as well as splits for training and generalization on several categories of structural generalization. 
Participants will need to select specific generalization types to focus on.

### Example Input & Output

Include COGS logical form (see Figure 1 of COGS paper):


_Example input/prompt_: "Provide the correct mapping of the following sentence (_taken from gen set_) based on this/these example(s) (_taken from train set_)...
Feel free to produce an output more complex than anything you have output before!"

_Example output_: Sentence with mapping to COGS LF.


### Evaluation

Exact match on generalization sets. Compare to other models: [slide 7](https://docs.google.com/presentation/d/1vJ_VBitlqG9PUS7bYGL442i--PwA9-euRcJjzW4aVy4/edit?usp=sharing) 


