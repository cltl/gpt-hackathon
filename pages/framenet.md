+++
title = "Framenet"
hascode = false
date = Date(2023, 4, 11)
+++

# Framenet: Event co-reference task
News articles often report on incidents (e.g. a terrorist attack or a natural disaster). Different articles may report on the same incident, but approach it from different perspectives. For instance, an article may have been written right after the event occurred, several weeks after the incident occurred (when new information is uncovered or follow-up events occur) or even years after the event (reflecting on its implications). There is a high degree of linguistic variation in how such events are expressed in text. It is very difficult for automatic systems to recognize if two texts are about the same incident or not (i.e. perform event coreference).

In the course of the Dutch FrameNet project, we have collected texts about real-world incidents using information about incidents from Wikidata and Wikipedia. Through these resources, we were able to compile corpora of news articles that all report on the same incident. The incidents can further be categorized in event types (e.g. mass shooting, royal wedding, etc.). This approach provides us with a challenging event-coreference dataset; we have texts reporting on the same incident written at different times after the event (and potentially containing a high degree of variation in referring to the same incident) and texts about different incidents of the same type, thus potentially containing a high degree of similar expressions and even ambiguity.
Many of our texts have manually been annotated in terms of semantic roles (as represented in FrameNet). In contrast to traditional SRL, we annotate frames on the level of the entire document instead of on the level of sentences. In addition, we capture information about whether a frame expresses information about target incident we are focusing on.

For this hackathon, we propose a binary event-coreference task containing three subtasks:
* Subtask 1: Are the two texts about the same incident? (gold: structured data information - target incidents)
* Subtask 2: Provide an explanation of your answer giving evidence from the text (gold: frame annotations)
* Subtask 3: Perform event linking: Name the incident or incidents the texts are about (gold: structured data information - target incidents)

Subtask 3 may seem particularly unrealistic for "a humble language model". However, given that models are being trained on virtually all data on the internet, it could be interesting to explore how much of this information the model captures and how reliably it can use it.

The data will be made available soon.


