+++
title = "Historic Dutch "
hascode = false
date = Date(2023, 4, 11)
+++

# Historical Dutch 
The Dutch East India Company (VOC) produced a wealth of texts about their activity in Asia in the seventeenth and eighteenth centuries. 
These texts are estimated to twenty-five million pages, and while many of them have been digitalized, research in these documents is still largely constrained by word-match searches.

The [Globalise](https://globalise.huygens.knaw.nl/) project that is run by the Huygens Institute of Dutch History and associated partners, among which the CLTL, aims at making these texts more accessible to the general public and at providing historians with advanced research tools.

The role of the CLTL in this project is to extract entities and events from these texts, so as to support research on trade notably, and political relations. Many of these texts report on ship voyages, like the following excerpt, taken from a General Letter of the 6th of January, 1628[^1]:

> Tsedert onsen Jongsten (hiernevens in copie gaande) met de schepen Frederick Hendrik, Hollandia, 't Wapen van Delff, 's landts Hollandia, ende de Galias den 12en November passato in compagnie van Batavia gescheyden ende den 15en ditto door de Strate Sunda geraeckt, sijn hier, Godtloff, den 17en ende den 21en van Teyouhan ende Jappan successive wel aengecomen 't jacht Erasmus ende 't schip de Vreede, t'samen geladen 810 picol rouwe Chineesche syde ende 332 picol coper.

which can be translated as:

> Since our latest message (here in copy) left with the ships Frederick Hendrik Hollandia, 't Wapen van Delff, 's landts Hollandia, and the Galias on the 12th of November last year together with Batavia and came through the Sunda Strait on the 15th of the same month, did arrive, God bless, on the 17th and the 21th from Taiwan and Japan successively the clipper Erasmus and the ship de Vreede, together loaded with 810 picul raw Chinese silk and 332 picul copper.

We are curious to see how we can prompt the newest generative LLMs to help with event and entity detection, or even to directly answer historical research questions.
 
## Tasks

1. Annotation task: prompt an LLM to annotate entities and events in a text, for instance by bracketing entities and event predicates with a predefined label set. 
    - Could the result be used for pre-annotations?
    - Are some types of entities or events harder to detect?
2. Infer quantities of trade and transport: evaluating the LLMs’ ability to quantify events and entities
    - you might for instance ask how many ships travelled on the 12th of November, or how many ships left Taiwan in November.
3. Listings: can you use LLMs to extract listings relating to voyages or people? We are interested in linking entities and events in relation to texts, and much of this information could be represented as tabular data.
    - you could have the model list all voyages, mentioning the ships travelling in each voyage, their departure and arrival dates, traject and cargo
    - or list people and attributes (origin, denomination, social status, etc.)
4. Essay questions: use LLMs to answer broader questions about the texts, for instance
    - what does this text tell us about relations between polities, whether local or European?
   

## Resources

Data will be provided on the day of the workshop. 

## Research questions

- How do LLMs fare with less salient entities?
- Can we use LLMs to reduce annotation costs/work (for creating training data for entity/event linking)?
- How can LLMs be used to make historical research more accessible?
 
[^1]: National Archive, The Hague, The Netherlands, 1.04.02 (Archive of the VOC), inventory no. 1092, folio 1, r.
