# Label Operations

Given the format of Blossom programs, assignments don't exist. 
Instead the label in the resultant graph of a rule will refer to the value in the initial graph of the rule, and will manipulate it in some way.
And this will be the new value of the label.

## Numeric Operations

Numerical operations with two values of the same type will return that type with one exception. An integer divided by an integer will return a rational. The `floor` and `ceil` functions exist to round down or up (respectively) from a real or rational to an integer.

Numerical operations with two values of different types will return a value of the type with the higher precedence. The order, from lowest to highest is (`integer`, `rational`, `real`).

  * `^` : Exponential
  * `/` : Division
  * `*` : Multiplication
  * `+` : Addition
  * `-` : Subtraction
  * `%` : Modulo

### Numeric Comparisons

  * `=`  : Equality
  * `!=` : Inequality
  * `>`  : Greater than
  * `>=` : Greater than or equal to
  * `<`  : Less than
  * `<=` : Less than or equal to
  
## String Operations

  * `*` : Repetition
  * `+` : Concatenation
  
### String Comparisons

  * `=`  : Equality
  * `!=` : Inequality
  * `^=` : Begins with
  * `$=` : Ends with
  * `~=` : Contains


## Boolean Operations

  * `&`, `and`, `∧` : And
  * `|`, `or`, `∨`  : Or
  * `!`, `not`, `¬` : Not
  * `^`, `xor`, `⊻` : Exclusive-or
  
### Boolean Comparisons

  * `=`  : Equality
  * `!=` : Inequality

# Rule Conditions

Rules can also be suffixed with a condition, using the where modifier. These conditions can use the inbuilt functions.

## Builtin Functions

  * `in(node_id)`                 : Returns an integer equal to the number of edges with the node specified by node_id as their target.
  * `out(node_id)`                : Returns an integer equal to the number of edges with the node specified by node_id as their source.
  * `edge(source_id, target_id)`  : Returns an integer equal to the number of edges from the node specified by source_id to the node specified be target_id.
  * `adj(node_1_id, node_2_id)`   : Returns an integer equal to the number of edges in either direction between the two nodes.
  * `edge?(source_id, target_id)` : Returns a boolean showing whether there is at least one edge from the source node to the target node.
  * `adj?(node_1_id, node_2_id)`  : Returns a boolean showing whether there is at least one edge in either direction between the nodes. This is also known as the nodes being adjacent.
