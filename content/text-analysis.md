---
title: Text analysis
prev: network-analysis
next: conclusion
---

The text we have analysed is from the introductory paragraphs of each of the articles. We picked this text because we
wanted to capture the essence of the article without having to analyse all the available text. Some of these texts are
longer than others, but in general they all capture the essence of the article. 

Below is an excerpt of the introductory paragraphs from the article about US president Richard Nixon.

> Richard Milhous Nixon (January 9, 1913 - April 22, 1994) was the 37th president of the United States, serving from 
> 1969 to 1974. A member of the Republican Party, he previously served as a representative and senator from California 
> and was the 36th vice president from 1953 to 1961 under President Dwight D. Eisenhower. His five years in the 
> White House saw reduction of U.S. involvement in the Vietnam War, détente with the Soviet Union and China, the first 
> crewed Moon landings, and the establishment of the Environmental Protection Agency and Occupational Safety and 
> Health Administration. Nixon's second term ended early, when he became the only president to resign from office, as a 
> result of the Watergate scandal. Nixon was born into a poor family of Quakers in a small town in Southern California. 
> He graduated from Duke Law School in 1937, practiced law in California, then moved with his wife Pat to Washington in 
> 1942 to work for the federal government. After active duty in the Naval Reserve during World War II, he was elected to
> the House of Representatives in 1946. His work on the Alger Hiss case established his reputation as a leading 
> anti-Communist, which elevated him to national prominence, and in 1950, he was elected to the Senate. Nixon was the 
> running mate of Dwight D. Eisenhower, the Republican Party's presidential nominee in the 1952 election, and served for
> eight years as the vice president. He ran for president in 1960, narrowly lost to John F. Kennedy, then failed again 
> in a 1962 race for governor of California, after which it was widely believed that his political career was over. 
> However, in 1968, he made another run for the presidency and was elected, defeating Hubert Humphrey by less than one 
> percentage point in the popular vote, as well as defeating third party candidate George Wallace.


Each of these texts then represented one document in our corpus, where the corpus is the entire collection of documents, 
either from the full data set or from the communities found within the network. 

## *Preprocessing of text*
The first steps of any text-based task, is to pre-process the text and make it usable for the tasks one wants to use
the text for. For our approach, we wanted to have the text uniform in terms of capitalisation and to remove punctuation.
We also needed it to be one long string and not a list of strings. 

Instead of writing our own code for analysing the text, we made use of already written libraries for text analysis from
SKlearn. This way we knew that the code would be robust, and it made it easier to get the correct values for the 
analysis. As SKlearn already had methods for tf-idf vectorisation, we could use those and therefore focus more on the 
analysis than writing functioning code. The SKlearn functions combines the pre-processing of lowering the text, such 
that all letters are de-capitalised and the tokenization, where the texts are reduced to the individual terms which
appear in the text.

## *TF-IDF*
The method we used for understanding the text was TF-IDF vectorisation. TF-IDF is a method that uses two parts: 
> TF stands for Term Frequency and represents how often a term occurs in one document. 

> IDF stands for Inverse Document Frequency and represents the inverse of how many documents the term occurs in, in the
> entire corpus

> The final TF-IDF value is then arrived at by multiplying the TF value with the IDF value

This final TF-IDF value is then a numerical value that represents how important a term is across the entire corpus. 
This means that words that occur frequently in just a few documents will have a higher TF-IDF value and therefore count
as being more significant than words that occur less frequently. On the other hand, words that occur in only a few 
documents, but occur very frequently in these documents, will also be seen as significant to that document. 

Doing this we can get an understanding of which words are most defining for the documents, and also for the individual
communities that we have found in the network.

## *Top terms the dataset*
When looking at the entire data set, we can use TF-IDF to extract what the top terms for the data set are. As mentioned
these words will be the ones that are most important and indicative of the theme of the dataset.
The top 10 terms for the entire dataset are these following 10 terms

    soviet government party war president
    united states state new military

These top terms show us to some degree what this data set is about. We see that the two big players of the Cold War are
both captured in these top terms, namely the Soviet Union and the United States. This is generally encouraging, as this
shows that the methods that we have used to capture the important words actually encapsulates what is largely viewed as
the defining distinctions of participating world powers in the Cold War.

## *Top terms in Communities*
Within the communities in the network we have used TF-IDF to extract the top terms of each of these communities. For 
instance community 0, which is a community where the 3 most connected nodes are the articles about U.S. presidents
`Richard Nixon`, `Dwight Eisenhower` and `Harry Truman`, have the top 10 terms

    kennan, macarthur, eisenhower, gaulle, 
    reagan, bush, reza, hoover, wilson, carter

All of these terms are names of presidents or leaders, which tell us something about what the community is about. In the
case of community 0, the top terms reinforce the fact that this community has encapsulated the presidents of the western
world, especially the presidents of the US. Another observation to be made is that the term `gaulle` has been captured,
which references the French general and president `Charles le Gaulle`, which indicates that he is significant for these
articles, and by extension that he had some relevance to the people the articles are about.

Another community worth looking at is community 1, which consists of articles about leaders of the Soviet Union. The
top articles in this community are the articles about `Nikita Krushchev`, `mikhail Grobachev` and `Vladimir Lenin`. Here
we see the following top terms:

    putin, gorbachev, yeltsin, amin, andropov, 
    solzhenitsyn, taraki, kosygin, suslov, podgorny

Again it is very much the same picture as before. All of these top terms underlines what the community is about, namely
Soviet presidents and leaders; all people that played a significant role during the Cold War and in the events which 
occurred during the Cold War.

## *Word clouds*
Another way to visualise the differences in the words used in each community, is the word cloud. This is a simple method
for generating pleasing visuals of the words in a text, and gives an intuitive overview of what words are the most 
common in a given document. 

![](/images/wordclouds.png)

These word clouds are from made from the texts found in 9 of the communities in event and degree filtered subgraph. 
Above each word cloud is the 3 highest degree articles listed from each of the communities. What we see in these word
clouds is that there are some clear differences in the words that occur most frequently, but also that some words are
frequent in all 9 communities. This allows us to get insights into what the theme of the community is. For instance, the
first community (top left) contains words `Soviet`, `German`, `Germany`, `Russian` all 4 of which are very prominent, 
and the top article is the one about the Eastern Front during World War 2. From this we can infer that this community
contains articles about Germany, The Soviet Union and the Eastern Bloc in general. We can furthermore see that it is 
quite different from the word cloud from community 2 (top middle), which highlights words such as `Isreal`, `Isreali` 
and `British`, and seems to be more about the British Empire, Israel and events that occurred in relation to these
countries.

Throughout, we see that all the word clouds are quite different and that each of them include unique words which belong
only to that community. Another observation to be made, is that the word `Soviet` is prominent in almost all 
word clouds, indicating the huge relevance the Soviet Union had on the entire time period.