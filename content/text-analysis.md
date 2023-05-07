---
title: Text analysis
prev: network-analysis
next: conclusion
---

# Text Analysis
The text we have analysed is from the introductory paragraphs of each of the articles. We picked this text because we
wanted to capture the essence of the article without having to analyse all the available text. 

> Example of introductory paragraph


Each of these texts then represented one document in our corpus, where the corpus is the entire collection of documents, 
either from the full data set or from the communities found within the network. 

## Preprocessing of text
The first steps of any text-based task, is to pre-process the text and make it usable for the tasks one wants to use
the text for. For our approach, we wanted to have the text uniform in terms of capitalisation and to remove punctuation.
We also needed it to be one long string and not a list of strings. 

Instead of writing our own code for analysing the text, we made use of already written libraries for text analysis from
SKlearn. This way we knew that the code would be robust, and it made it easier to get the correct values for the 
analysis. As SKlearn already had methods for tf-idf vectorisation, we could use those and therefore focus more on the 
analysis than writing functioning code. The SKlearn functions combines the pre-processing of lowering the text, such 
that all letters are de-capitalised and the tokenization, where the texts are reduced to the individual terms which
appear in the text.

## TF-IDF
The method we used for understanding the text was TF-IDF vectorisation. TF-IDF is a method that uses two parts: 
> TF stands for Term Frequency and represents how often a term occurs in one document. 

> IDF stands for Inverse Document Frequency and represents the inverse of how many documents the term occurs in, in the
> entire corpus

> The final TF-IDF value is then arrived at by multiplying the TF value with the IDF value

This final TF-IDF value is then a numerical value that represents how important a term is across the entire corpus. 
This means that words that occur frequently in just a few documents will have a higher TF-IDF value, and as such count 
as being more significant. 
