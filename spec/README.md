# Blossom Specifications (Incomplete)

Blossom has two main concepts: **Graphs** and **Graph Programs**.

## Blossom Graphs

Blossom graphs are denoted with square brackets. An empty graph is represented like so: `[]`.
A blossom graph is a set of nodes, followed by a set of edges. These two sets are separated with a vertical pipe (`|`).
So an alternative way of representing an empty graph would be this: `[|]`.

A node is represented with a unique (within the graph) numerical identifier. 
The two code blocks below represent the same graph, illustrating that blossom doesn't care about whitespace, or trailing commas.
This is a graph with three unlabled nodes, and no edges.

```blsm
[1, 2, 3]
```


```blsm
[
  1, 
  2, 
  3,
]
```

An edge is defined by its source and target nodes.

## Blossom Graph Programs

A blossom program is made up of **rule** definitions and then declarations about their application. 
A rule is the most basic way blossom interacts with graphs. It's made up of an *match graph*, and a *resultant graph*. 
For a rule to be applied to a *host graph*, there must be some way to map the nodes and edges of the match graph to corresponding nodes and edges in the host graph.

