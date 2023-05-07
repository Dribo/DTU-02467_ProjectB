---
title: Wikipedia article interlinkage
layout: single 
next: network-analysis
---

##### How are the pages referenced in the Cold War article interlinked with each other?
*by Magnus A. Nielsen (s204072) & Philip J. F. Helsted (s204147)*

This webpage is accompanied by the following github repository, where data and the code used to perform the anlysis can
be found. Click [***this***](https://github.com/Dribo/DTU-02467_ProjectA) button to go the repository.

## Introduction and Motivation
Wikipedia is an enormous database of knowledge about everything and anything and history is definitely 
well-documented on Wikipedia. The time period of the Cold War, and the corresponding Wikipedia article, is an 
interesting piece both of and on history about a highly factionalized 
world divided in east and west and communism and capitalism. 
The most well-documented Wikipedia is the English Wikipedia, which raises the question of bias
in the way this conflict and its referenced works are described. Is there, for instance, differences in
the language used that cannot be explained by the difference in topic? This is one of the question we aim to answer
with this web-page.

## The Data
The data is available [***here***](data/wiki_english_with_tokens.csv)

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

    URL, TITLE, LIST OF REFERENCES, LIST OF PARAGRAPH TEXTS, 
    CATEGORIES, TYPE, TOKENS, UNIQUE TOKENS

Of these, the most
important ones are the list of references and the list of paragraphs. The list of references is the variable containing
the articles referenced, and is the one being used to build the network. The list of paragraphs is the first couple of
paragraphs from the article, and are used to build both the tokens and the unique tokens. These are also added as an 
attribute in the network, and used to explore the language of the articles.

## *The Network*
As mentioned, the network was constructed from the data set by using the list of references that was scraped for each 
of the articles. This was done by creating a node for each article, and creating an edge for each reference to the 
referenced article. The resulting full network had in total `857` nodes and `16216` edges. To simplify things a bit, we
decided to make the Network undirected as that allowed us to better detect and understand the communities found in the 
network. 

![](/images/basic-network.png)

## *Subgraphs*
To facilitate a deeper understanding of the network, we decided to create some subgraphs of the network. We had built
a heuristic for collecting the type of article, divided in person, event and none, and used this to assign each of the 
nodes in the network a type. We could then use this to filter away all nodes of different type, such that the nodes left
were the ones of the same type. This enabled us to look exclusively at both persons and events related to the Cold War,
in effect allowing us to zoom in on the parts that were the most relevant to us.

![](/images/basic-network-person.png)

> Subgraph with type 'person'

![](/images/basic-network-event.png)

> Subgraph with type 'event'

## *Community detection*
A way in which we wanted to explore the network and the underlying data, was to detect communities within the network.
Communities would tell us something about how the network was connected, and we hoped that it would show us a clear 
divide in, for instance, east and west, capitalism and communism and so on. What we found was that in the Person
subgraph, some clear communities appeared. We found communities of for instance U.S. presidents, Soviet presidents, 
East-Asian Leaders, all grouped quite neatly in communities. 

![](/images/basic-network-person-communities.png)

