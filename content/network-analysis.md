---
title: Network Description and Analysis
prev: Wikipedia article interlinkage
next: network-analysis
---

For the research questions of this project, a graph is a suitable representation of the data. It allows us to describe each wikipedia page as a node, and a reference as a link to another node. 

## Attributes

The data we have collected for each page is added as attributes to the nodes in the graph, so we can easily analyse data on the graph after applying methods that filter and group nodes. The attributes we add to each node are shown below

| Attribute            | Data format                        | Source                                                                           |
|----------------------|------------------------------------|----------------------------------------------------------------------------------|
| TYPE                 | Either 'person', 'event' or 'none' | We use a list of selected keywords for each type and scan categories for these   |
| LIST_PARAGRAPH_TEXTS | List of strings                    | From the data we collected                                                       |
| FLAT_TEXT            | String                             | We flatten the string array to allow easier use for tokenizers and wordcloud     |
| CATEGORIES           | List of strings                    | We take the wikipedia categories section which we scraped during data collection |
| TITLE                | String                             | The title of the corresponding wikipedia page   <br/>                            |
> Figure showing each attributes and how we obtain the value

## Directed vs Undirected

The data from wikipedia contains links from one page to another. This inherently makes a directed graph a viable option. In this case we decide to go forward with a simplified graph which is undirected. This is because the methods we intend to use, for example the community algorithm, does not work on directed graphs. 

## Subgraphs created

Using the attributes in our nodes we experimented with subsets. We filtered based on type to get insights on this specific group. Another filter that proved useful was discarding nodes based on number of connections. Removing nodes with few edges and very high amounts of edges made a less interconnected graph which was more suitable for finding communities. We found subgraphs that were more readable in a visualization than the full graph. A few examples of graphs we found are shown below, we included communities for clarity, but we will go more into detail on these later

![](/images/full-graph.png)

> The full graph is highly interconnected and the found communities are scattered, this makes it difficult to get insight. For example, United States and the Soviet Union are both included in the same community.

![](/images/subgraph-event.png)

> When we chose to only include nodes with type 'event', we see communities based on geography and politics, which in our opinion makes for a better distinction. However, the high amount of interlinkage still obscures these groups and the visualization is quite chaotic to look at

![](/images/subgraph-event-degree-filter.png)

> The final step of adding a filter on degree gives a smaller, yet more meaningfully grouped graph. We now see communities based on Japan and east europe also, while larger pages such as world war II are omitted. This likely makes for a more insightful analysis, that sheds light on a more historically accurate categorization of events.

# Analysis

## Assortativity

Assortativity is a metric that quantifies how much node has in common with neighbors. We compute this metric for degree on both the full graph and the subgraph. For the full graph we also compute assortativity with respect to the type attribute, to see whether wikipedia articles about events tend to refer to other events, and the same for type.

For degree, the full graph gets a value of -0.13 and for the subgraph 0.01. For the full graph, larger articles tend to refer to smaller ones. In the subgraph, such distinction is negligible. For the type attribute, the full graph gets assortativity 0.05. 

In general, the wikipedia pages don't tend to have clear groups in terms of person or event. Therefore we will proceed using a filter on such type, since this is unlikely to separate naturally in the following community analysis.

## Distribution of degrees

The data from wikipedia contains pages with a very large amount of references, but also pages with few or none. To better understand how this might impact the graph, we plot the distribution of node degrees.

![](/images/degree-distribution-fullgraph.png)

> Degree distribution of full graph

Explanation: Looking at the degree distributions of the full graph, we see a few outliers with large amounts of edges. The mean degree is 36.5. 

![](/images/degree-distribution.png)

> Degree distribution of subgraph with event and degree filter

Explanation: In the subgraph that we intend to use for community text analysis, we see a much more even distribution, with a mean degree of 9.7.

## Modularity and communities

The subgraph has a much lower mean degree, which could provide higher modularity and therefore communities, which are more separate, which is a good thing if we want to look at them separately for further analysis. The purpose of this section is to validate or invalidate this claim.

To measure how well the communities are divised, we compute modularity for the three aforementioned graphs. In technical terms, modularity quantifies how interlinked the communities are compared to a graph where edges are randomized. The value is between -0.5, representing complete non-modular clustering, and 1, meaning fully modular partitions within the graph (no edges across communities).

The community detecting algorithm we use is Louvain, which optimizes for modularity. This algorithm first finds clusters locally, then iteratively combining clusters until the next step leads to a decrease in modularity. Trying all possible combinations would get the best result in theory, but this is computationally impractical. Hence, the aforementioned heuristic is used.

For modularity we initially find a value of the entire graph at 0.36. Filtering for event only gives 0.46 which is an improvement. Finally, we find 0.60 after thresholding node degrees. Therefore, the subgraph with event- and degree filtering is the one we proceed with for text analysis.