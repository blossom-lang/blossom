(DISCLAIMER: These specifications are currently incomplete and are subject to change.)

# Blossom Specifications

Blossom has two main concepts: [**Graphs**](#blossom-graphs) and [**Graph Programs**](#blossom-graph-programs).

## Blossom Graphs

Blossom graphs are denoted with square brackets. An empty graph is represented like so: `[]`.
A blossom graph is a set of [**nodes**](#nodes), followed by a set of [**edges**](#edges). These two sets are separated with a vertical pipe (`|`).
So an alternative way of representing an empty graph would be this: `[|]`. If a graph has no edges, the vertical pipe is also not required, hence the first empty graph: `[]`.

### Nodes 

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

### Edges

An edge is defined by its source and target nodes. Edges are directed, and multiple edges can exist between the same two nodes. An edge is represented by an arrow (`->`) going from the ID of its source node to the ID of its target node. These are all valid graphs with edges.

```blsm
[ 1, 2 | 1->2 ]
```

```blsm
[ 
  1, 
  2 
| 
  1->2, 
  1->2, 
  2->1 
]
```

Nodes and edges are separated by commas (`,`), and a trailing comma after the last node/edge is permitted.

### Labels

Both nodes and edges can also have a **label**.
A label is enclosed in parentheses (`()`), and contains a single value, followed by an optional list of boolean flags.

This value can be one of the following types:

  * `boolean` : A boolean value, either TRUE or FALSE.
  * `integer` : An integer in the mathematical sense. i.e a whole number.
  * `rational` : A rational number. i.e a fraction.
  * `real` : A real number. i.e a decimal.
  * `string` : A string of characters. Blossom uses UTF-8 encoding for its strings.
  
The numerical types of Blossom follow a heirarchy. All integers are also rationals. And all rationals are also reals. Numbers can be freely implicitly cast in this direction.
There is also the special `any` type, which means the value's type is unknown.

```blsm
[ 1 (4) ]
```

## Blossom Graph Programs

A blossom program is made up of [**rule**](#rules) definitions and then declarations about their application. 
A rule is the most basic way blossom interacts with graphs. It's made up of an *match graph*, and a *resultant graph*. 
For a rule to be applied to a *host graph*, there must be some way to map the nodes and edges of the match graph to corresponding nodes and edges in the host graph.

### Rules

A rule defines a transformation from one (sub)graph into another. The application of a rule onto a graph attempts to find a match for the subgraph within this graph, and then attempts to transform this subgraph.

#### Label Operations

Numerical operations with two values of the same type will return that type with one exception. An integer divided by an integer will return a rational. The `floor` and `ceil` functions exist to round down or up (respectively) from a real or rational to an integer.

Numerical operations with two values of different types will return a value of the type with the higher precedence. The order, from lowest to highest is (`integer`, `rational`, `real`).
