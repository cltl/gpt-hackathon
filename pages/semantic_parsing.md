

# Structural generalization in semantic parsing

See Google Drive Folder for materials and additional explanation: [Folder](https://drive.google.com/drive/folders/1D_Glq-6y9L2bwmznGSRVevZx5nBbStwK?usp=share_link)

Please do not distribute materials beyond this hackathon, as this is work in progress to potentially be published. Thank you! 

## Objective
Prompt engineering to test the structural generalization abilities of GPT-x models with a semantic representation. 


## Background & Research Question

Natural language is characterized by compositionality: the meaning of a complex expression is constructed from the meanings 
of its constituent parts. Compositionality helps explain why humans can produce and understand linguistic expressions they have never encountered. The question we investigate with this task is: **can language models generalize in the same ways as humans?** 

[COGS: A Compositional Generalization Challenge Based on Semantic Interpretation](https://aclanthology.org/2020.emnlp-main.731/)
(Kim & Linzen, 2020) introduced a semantic parsing dataset based on a fragment of English to evaluate the compositional abilities of language
processing architectures. The dataset distinguishes two types of generalization (Figure 3 in COGS paper): 

(i) **_Lexical generalization_** involves recombining
known grammatical structures with words that were not observed in these particular structures in training. For example, “object
to subject” generalization tests how well a model that only sees a common noun (e.g. “hedgehog”)
in object position at training can interpret that noun in subject position at test time.

(ii) **_Structural generalization_** involves
generalizing to linguistic structures that were not
seen in training, or combining two novel structures to form a new structure. An example is “PP recursion”, where training
instances contain prepositional phrases of depth up
to two, and generalization instances have PPs of depth 3–12. 

Semantic parsers have been shown to struggle primarily with structural generalization tasks unless they have explicit representations of structure ([Yao & Koller, 2022](https://aclanthology.org/2022.emnlp-main.337/)).
Large language models additionally show a performance ceiling of 80-90% exact match ([Qiu et al., 2022](https://aclanthology.org/2022.emnlp-main.624.pdf)), which hints that the cases they struggle with are also structural and not lexical. 

## Task Description

Develop and tune prompts to test the structural generalization abilities of GPT-x models via semantic parsing. 

See **Prompting Tips & Tricks** document in Google Drive for an outline of methods to do this, as well as Jupyter notebooks with examples!


## Dataset 

A yet-to-be-released dataset (dubbed 'SLOG') will be provided to those working on this task. SLOG extends the [COGS](https://github.com/najoungkim/COGS) dataset and introduces new structural generalization cases of (long-distance) extraction and recursion.

Find data in **Google Drive Folder** (linked at top).

The dataset contains natural English sentences and their mappings to COGS logical form, as well as splits for training and generalization on several categories of structural generalization. 
Participants will need to select specific generalization types to focus on.

### Example Input & Output

Include COGS logical form (see Figure 1 of COGS paper):


**_Example input/prompt_**: "Provide the correct mapping of the following sentence (_taken from gen set_) based on this/these example(s) (_taken from train set_)...
Feel free to produce an output more complex than anything you have output before!"

**_Example output_**: English sentence with mapping to COGS LF.


### Evaluation

Exact match accuracy on generalization sets. Existing semantic parser performance for reference: [slide 7](https://docs.google.com/presentation/d/1vJ_VBitlqG9PUS7bYGL442i--PwA9-euRcJjzW4aVy4/edit?usp=sharing) 


