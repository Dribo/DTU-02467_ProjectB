---
title: Graph Description and Analysis
prev: Wikipedia article interlinkage
next: network-analysis
---

To answer some of the research questions of this project, a graph is a suitable representation of the data. It allows us to describe each wikipedia page as a node, and a reference as a link to another node. 

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

Nam commodo lorem quis tortor euismod, ut ultrices orci aliquet. Sed eget dui nec sem ullamcorper convallis id nec ante. Aliquam ultricies a massa quis semper. Donec suscipit augue ut sagittis hendrerit. Aliquam erat volutpat. Proin aliquet maximus nibh, id aliquet justo maximus at. Sed accumsan ante id aliquam pellentesque. 

![](/images/dtu-logo.png)

Aliquam nec hendrerit quam. Suspendisse maximus eros sollicitudin, accumsan turpis eu, blandit nulla. Nunc lorem elit, molestie at libero gravida, placerat consectetur ante. Sed tincidunt viverra tellus a vehicula.


1. Lorem ipsum dolor sit amet
1. Lorem ipsum dolor sit amet
1. Lorem ipsum dolor sit amet

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam blandit lobortis turpis. Praesent porttitor, turpis eu posuere molestie, sem dolor scelerisque sapien, eu aliquet ante felis ac metus. Pellentesque semper ultricies urna. Aenean auctor, turpis ut convallis ultrices, eros tellus bibendum risus, eu varius velit ante et diam. 

* Lorem ipsum dolor sit amet
* Lorem ipsum dolor sit amet
* Lorem ipsum dolor sit amet

In suscipit lorem orci, eu placerat nibh dignissim ut. Nullam consequat nisl dui, in ornare risus porttitor sed. Integer vitae nibh semper purus ultrices rutrum. Pellentesque non diam ornare, imperdiet elit a, tempus lacus. Suspendisse viverra euismod dapibus.

Suspendisse non tellus faucibus, dapibus leo at, elementum magna. Fusce quis ante ex. In non ex eleifend, luctus risus quis, dapibus velit. Nulla facilisi. Integer iaculis arcu at fermentum varius. Donec auctor dolor non dolor pulvinar luctus. Mauris vestibulum lacinia nisl, a dictum erat molestie sed. Vivamus vel blandit turpis, nec sollicitudin massa. Nunc velit eros, tristique elementum congue eget, auctor dictum tellus. 

Quisque iaculis, sem quis imperdiet faucibus, nunc lorem feugiat purus, vestibulum condimentum turpis turpis ut ante. Donec vestibulum lectus ut ullamcorper condimentum. Curabitur fermentum nulla vitae arcu sollicitudin pulvinar.

<img src="/images/dtu-logo.png" width="200" />

Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia curae; Suspendisse eu tellus ut erat porttitor luctus. Vivamus aliquam auctor massa, in auctor orci. Ut quis enim ut lorem consectetur blandit dictum eu mauris.