---
title: Motivation and Introduction
layout: single 
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
The data that have been used for this project, was obtained by web-scraping some articles on Wikipedia. The first 
article that was scraped, and therefore used as a starting point, was the article about the Cold War. 
From there all references to other Wikipedia articles present in the body-text were collected and each of these were
in-turn scraped for references. This resulted in a collection of articles all of which were referenced on the Cold War, 
and for each of these we had the articles they themselves referenced. Apart from the references, we also collected the 
first few paragraphs of text, and the categories of the articles. The text was collected as a way to explore the 
language used in the articles and the categories were collected to assign a label of person or event to each of the 
articles.

This resulted in a data-collection of 859 rows, where each row represents a reference from the Cold War article. In
total the amount of data summed to be approximately 40 MB of text data. Each row are described by 7 variables: 
URL, TITLE, LIST OF REFERENCES, LIST OF PARAGRAPH TEXTS, CATEGORIES, TYPE, TOKENS and UNIQUE TOKENS. Of these, the most
important ones are the list of references and the list of paragraphs. The list of references is the variable containing
the articles referenced, and is the one being used to build the network. The list of paragraphs is the first couple of
paragraphs from the article, and are used to build both the tokens and the unique tokens. These are also added as an 
attribute in the network, and used to explore the language of the articles.


### Sample rows from the data-frame? 


## The Network
As mentioned, the network was constructed from the data set by using the list of references that was scraped for each 
of the articles. This was done by creating a node for each article, and creating an edge for each reference to the 
referenced article. 

