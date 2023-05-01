+++
title = "Toxic language"
hascode = true
date = Date(2023, 4, 11)
+++

# Toxic language Detection
We formulated two prompt engineering challenges to do with toxic language detection.
The first concerns the detection of *explicit* toxicity, the second detection and explanation of *implicit* toxicity.


## Challenge 1 - Explicit Toxicity
Prompt Engineering for the detection of toxic spans, target spans, and target group from an explicit toxic text.

### Task Description
Create a prompt to identify: 
1. Toxic spans and tokens: words that make the text toxic
2. Target spans and tokens: words that make reference to the group addressed in the toxic text
3. Target group: a group of people targeted in the toxic text

#### Example Input
Dad should have told the muzrat to fuck off and went in anyway

#### Expected Output
```
Toxic tokens: [muzrat, fuck, off] 
Toxic spans: [1, 1, 1, 1, 1, 0, 1, 0, 0, 1, 1, 1, 1]
Target span: [muzrat]    
Targeting spans: [0, 0, 0, 0, 1, 1, 0, 0, 0, 0, 0, 0, 0]
Target group: Islam
*************************************************************
```
Please note that 0 refers to the corresponding non-toxic/non-targeting token while 1 refers to the corresponding toxic/targeting token. 

### References
1. Mathew, B., Saha, P., Yimam, S. M., Biemann, C., Goyal, P., & Mukherjee, A. (2021, May). Hatexplain: A benchmark dataset for explainable hate speech detection. In Proceedings of the AAAI Conference on Artificial Intelligence (Vol. 35, No. 17, pp. 14867-14875).
2. Barbarestani, B., Maks, I., & Vossen, P. (2022, October). Annotating Targets of Toxic Language at the Span Level. In Proceedings of the Third Workshop on Threat, Aggression and Cyberbullying (TRAC 2022) (pp. 43-51).
3. https://github.com/cltl/Target-Spans-Detection

### Data
- [training](https://drive.google.com/file/d/15XNhpVGcDnWKnjYY8cp_vNNp_vGkERlx/view?usp=share_link)
- [Development](https://drive.google.com/file/d/1fG9hGIeaOFq7e5yPdopTNJl8RX1Wbx5N/view?usp=share_link)
- [test](https://drive.google.com/file/d/1fG9hGIeaOFq7e5yPdopTNJl8RX1Wbx5N/view?usp=share_link)

### Models
ChatGPT or  Koala

### Evaluation
Comparison to the gold data

### Example of the prompt
```
Given the sentence '{}' tokenized as '{}', output the target group, targeting tokens, and toxic tokens. The target group should be one of the following: {}.\n output the targeting tokens and toxic tokens in the sentence. For the targeting tokens, output both the words and a list of 0's and 1's indicating whether each word is a targeting token. For the toxic tokens, output both the words and a list of 0's and 1's indicating whether each word is a toxic token. Targeting tokens refer to the words or subwords in the sentence that are used to refer to a specific target, in this case, human beings. All words or subwords referring to the target should be included as targeting tokens, regardless of how many times they appear in the sentence. Toxic tokens refer to the words or subwords in the sentence that are considered to be harmful or offensive. These words may include profanity, insults, slurs, or any language that could be considered inappropriate or hurtful. Note that the specific criteria used to label words as toxic may vary depending on the context and the specific task. target group for the given text with respect to toxic language. Target group refers to a specific group of people who are being targeted for their identity in an offensive and harmful way. This may include groups that are marginalized, oppressed, or discriminated against based on their race, ethnicity, religion, gender identity, sexual orientation, or other personal characteristics. Here are a few examples:\
**Input 1:**\
Sentence: You Bangladeshi guys are f***ing gangsta.\
Tokens: [You, Bangladeshi, guys, are, f***ing, gangsta]\
**Output 1:**\
Target group: Asian\
Targeting Tokens: [You, Bangladeshi, guys]\
Targeting Tokens (0's and 1's): [1, 1, 1, 0, 0, 0]\
Toxic Tokens: [f***ing, gangsta]\
Toxic Tokens (0's and 1's): [0, 0, 0, 0, 1, 1] \
**Input 2:**\
Sentence: Just because we don't let groups of creepy Moroccan rapists into the club doesn't make us racist\
Tokens: [Just, because, we, don\'t, let, groups, of, creepy, Moroccan, rapists, into, the, club, doesn\'t, make, us, racist]\
**Output 2:**\
Target group: African\
Targeting Tokens: [creepy, Moroccan, rapists]\
Targeting Tokens (0's and 1's): [0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0]\
Toxic Tokens: [creepy, rapists]\
Toxic Tokens (0's and 1's): [0, 0, 0, 0, 0, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 0, 0]\
**Input 3:**\
Sentence: They do no shit other than going to the mosque\
Tokens: [They, do, no, shit, other, than, going, to, the, mosque]\
**Output 3:**\
Target group: Islam\
Targeting Tokens: [They]\
Targeting Tokens (0's and 1's): [1, 0, 0, 0, 0, 0, 0, 0, 0, 0]\
Toxic Tokens: [shit]\
Toxic Tokens (0's and 1's): [0, 0, 0, 1, 0, 0, 0, 0, 0, 0]\
**Input 4:**\
Sentence: Fuck the ignorant assholes from America UK and all other countries who try and soil the wonderful ties between all democratic nations\
Tokens: [Fuck, the, ignorant, assholes, from, America, UK, and, all, other, countries, who, try, and, soil, the, wonderful, ties, between, all, democratic, nations]\
**Output 4:**\
Target group: Other\
Targeting Tokens: [the, ignorant, assholes, from, America, UK, all, other, countries]\
Targeting Tokens (0's and 1's): [0, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]\
Toxic Tokens: [Fuck, ignorant, assholes]\
Toxic Tokens (0's and 1's): [1, 0, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]\
**Input 5:**\
Sentence: You spics are worthless\
Tokens: [You, spics, are, worthless]\
**Output 5:**\
Target group: Hispanic\
Targeting Tokens: [You, spics]\
Targeting Tokens (0's and 1's): [1, 1, 0, 0]\
Toxic Tokens: [spics, worthless]\
Toxic Tokens (0's and 1's): [0, 1, 0, 1]\
**Input 6:**\
Sentence: He is a stupid Muslim\
Tokens: [He, is, a, stupid, Muslim]\
**Output 6:**\
Target group: Islam\
Targeting Tokens: [He, a, stupid, Muslim]\
Targeting Tokens (0's and 1's): [1, 0, 1, 1, 1]\
Toxic Tokens: [stupid]\
Toxic Tokens (0's and 1's): [0, 0, 0, 1, 0]\
**Input 7:**\
Sentence: He is stupid and the stupid should be fired.\
Tokens: [He, is, stupid, The, stupid, should, be, fired]\
**Output 7:**\
Target group: Other\
Targeting Tokens: [He, the, stupid]\
Targeting Tokens (0's and 1's): [1, 0, 0, 0, 1, 1, 0, 0, 0]\
Toxic Tokens: [stupid, stupid]\
Toxic Tokens (0's and 1's): [0, 0, 1, 0, 0, 1, 0, 0, 0]\
**Input 8:**\
Sentence: You can never escape these hoes\
Tokens: [You, can, never, escape, these, hoes]\
**Output 8:**\
Target group: Women\
Targeting Tokens: [these, hoes]\
Targeting Tokens (0's and 1's): [0, 0, 0, 0, 1, 1]\
Toxic Tokens: [hoes]\
Toxic Tokens (0's and 1's): [0, 0, 0, 0, 0, 1]\
**Input 9:**\
Sentence: Tell that bitch call me back\
Tokens: [Tell, that, bitch, call, me, back]\
**Output 9:**\
Target group: Women\
Targeting Tokens: [that, bitch]\
Targeting Tokens (0's and 1's): [0, 1, 1, 0, 0, 0]\
Toxic Tokens: [bitch]\
Toxic Tokens (0's and 1's): [0, 0, 1, 0, 0, 0]\
**Input 10:**\
Sentence: You should really get out of bed faster than that slut\
Tokens: [You, should, really, get, out, of, bed, faster, than, that, slut]\
**Output 10:**\
Target group: Women\
Targeting Tokens: [that, slut]\
Targeting Tokens (0's and 1's): [0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1]\
Toxic Tokens: [slut]\
Toxic Tokens (0's and 1's): [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1]\
**Input 11:**\
Sentence: She is such a whore\
Tokens: [She, is, such, a, whore]\
**Output 11:**\
Target group: Women\
Targeting Tokens: [She, a, whore]\
Targeting Tokens (0's and 1's): [1, 0, 0, 1, 1]\
Toxic Tokens: [whore]\
Toxic Tokens (0's and 1's): [0, 0, 0, 0, 1]\
```
Note that the sizes of the targeting tokens and toxic tokens lists should be exactly the same as the list of tokens, with each element in the targeting and toxic tokens lists corresponding to a single token in the list of tokens. Please ensure that the tokenization process used to generate the list of tokens is consistent with the criteria used to label the targeting and toxic tokens.


## Challenge 2 - Implicit Toxicity

|                 | Prompt Engineering for prediction of implied statement in an implicit toxic comment                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------|
| Description     | From a given implicitly toxic text generate the statement that is implied.                                                      |
| Example Input   | “yes you are fine in a white majority country. how is mexico doing these days? people come here because you couldn’t build it.“ |
| Expected Output | Implied Statement: mexicans are incompetent                                                                                     |
| Reference       | Latent Hatred (ElSherief et al., 2021)                                                                                        |
| Dataset         | https://drive.google.com/file/d/1mLihcKXwzKJDntH7-RLxIR3msDZu_zHi/view?usp=share_link                                           |
| Model(s)        | Any LLM usable for prompting (e.g. ChatGPT, Koala)                                                                              |
| Evaluation      | Average and maximum BLEU and ROUGE scores between generated implied statement and reference implied statements.                 |
