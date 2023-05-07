---
title: Motivation
prev: 
next: Data description
---

# Wikipedia article interlinkage
##### How are the pages referenced in the Cold War article interlinked with each other?
*by Magnus A. Nielsen (s204072) & Philip J. F. Helsted (s204147)*

## Introduction and Motivation
Wikipedia is an enormous database of knowledge about everything and anything and history is definitely 
well-documented on Wikipedia. The time period of the Cold War, and the corresponding Wikipedia article, is an 
interesting piece both of and on history about a highly factionalized 
world divided in east and west and communism and capitalism. 
The most well-documented Wikipedia is the English Wikipedia, which raises the question of bias
in the way this conflict and its referenced works are described. Is there for instance a notable difference in the 
sentiment of articles about the Eastern bloc compared to articles about the Western bloc? Or are there differences in
the language used that cannot be explained by the difference in topic? These are the kinds of questions we are trying
to answer with this webpage.

## The Data
The data that have been used for this project, was obtained by web-scraping some articles on Wikipedia. THe first that
was scraped, and therefore used as a starting point, was the article about the Cold War. From there all references to 
other Wikipedia articles present in the body-text were collected and each of these were in-turn scraped for references.
This resulted in a collection of articles all of which were referenced on the Cold War, and for each of these we had the
articles they themselves referenced. Apart from the references, we also collected the first few paragraphs of text, and
the categories of the articles. The text was collected as a way to explore the language used in the articles
and the categories were collected to assign a label of person or event to each of the articles.




## Something about graphs
On wikipedia, articles contain references to other articles whenever a subject has a Wikipedia article written about it.
This means that Wikipedia is interlinked through articles that reference each other, and can therefore be modelled as a 
network graph where edges are the 
