# Extracting and Generating biographical facts from Wikipedia Articles

Biographies are texts that explain the lives of notable people, where did they live, who did they meet, why are they important, etcetera. The "problem" is that important factual information might get lost among the minor events or stilistic approach that the unstructured biographical text contains.

We are interested in using LLMs to query for the most relevant set of events that characterised a person's life as well as their basic biographical information that can help historians situate this person in the right context. This biographical information can be an open set of properties. Some of the most common properties are:
- Date of Birth
- Date of Death
- Place of Birth
- Place of Death
- Family Relations
- Places they visited
- Occupation(s)
- Organizations where they participated 
- ...

In short, we would like to extract structured information from free text in the form of truples (Subject, Property, Object). Take for example the following text:

> Matthijs Musson (1593 in Antwerp – 3 November 1678) was a painter and art dealer based in Antwerp, who played an important role in popularizing artists of the 17th-century Antwerp school by marketing them throughout Europe. Matthijs Musson was born in Antwerp as the son of Robert Musson, an innkeeper. Matthijs is possibly a pupil in the workshop of Rubens and becomes a master in the Antwerp Guild of Saint Luke in 1622.

From such pasagge we would like to extract structured triples with the most salient information such as:

- (Matthijs Musson, place of birth, Antwerp)
- (Matthijs Musson, place of death, Antwerp)
- (Matthijs Musson, date of birth, 1593)
- (Matthijs Musson, date of death, 3 November 1678)
- (Matthijs Musson, child of, Robert Musson)
- (Matthijs Musson, occupation, painter)
- (Matthijs Musson, occupation, art dealer)
- (Matthijs Musson, influenced by, Rubens)
- (Matthijs Musson, worked at, Antwerp Guild of Saint Luke)
- ...


## Research questions

- Text to Triples: Can we use LLMs to extract specific structured information from text?
- Triples to Text: Can we use LLMs to generate textual information from a list of triples?
- How can we prompt LLMs to generate synthetic training data to improve performance on one or both tasks?
 
 
## Data

We prepared a toy dataset consisting of 75 Wikipedia biographical articles (Download it [here](https://drive.google.com/file/d/18Udfb0ljMvT-Deqt3EwYNtE0o0b0wj8t/view?usp=share_link)). Each file also contains triples found in Wikidata that correspond to structured information of the same person described in Wikipedia. This way we have access to both structured and textual information. 

We can use the dataset for experimentation and evaluation, for example: 
- Use the known Wikidata triples to test the accuracy of the information extracted from free text.
- Use the Wikipedia text to compare the generated LLM text from triples as input.


More ideas related to this topic are appreciated!
   