# Documentation
|Type|description|
|---|---|
|[DFA](#DFA)||
|[Input](#Input)||
|[NFA](#NFA)||
|[NFANode](#NFANode)||
|[TagAction](#TagAction)||

## DFA

```moonbit
:::source,moonbitlang/ulex/lib/automaton/dfa.mbt,68:::pub(all) struct DFA {
  graph : <a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/core/array#Array">Array</a>[(<a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">@moonbitlang/ulex/lib/util/eof_char_set.EofCharSet</a>, (Int, <a href="moonbitlang/ulex/lib/automaton#TagAction">TagAction</a>))]]
  end_nodes : <a href="moonbitlang/core/builtin#Map">Map</a>[Int, (Int, <a href="moonbitlang/core/array#Array">Array</a>[((Int, Int), (Int, Int))])]
  code_blocks : <a href="moonbitlang/core/array#Array">Array</a>[String]
  captures : <a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/core/array#Array">Array</a>[(String, <a href="moonbitlang/ulex/lib/type#VarType">@moonbitlang/ulex/lib/type.VarType</a>)]]
  start_action : <a href="moonbitlang/ulex/lib/automaton#TagAction">TagAction</a>
  node_count : Int
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/ulex/lib/automaton/dfa.mbt,76:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/ulex/lib/automaton#DFA">DFA</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/automaton/dfa.mbt,76:::fn output(<a href="moonbitlang/ulex/lib/automaton#DFA">DFA</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### from\_rule
  ```moonbit
  :::source,moonbitlang/ulex/lib/automaton/dfa.mbt,287:::fn <a href="moonbitlang/ulex/lib/automaton#DFA">DFA</a>::from_rule(rule : <a href="moonbitlang/ulex/lib/type#Rule">@moonbitlang/ulex/lib/type.Rule</a>) -> <a href="moonbitlang/ulex/lib/automaton#DFA">DFA</a>
  ```
  > 

## Input

```moonbit
:::source,moonbitlang/ulex/lib/automaton/nfa.mbt,2:::pub(all) enum Input {
  Eps
  EChar(<a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">@moonbitlang/ulex/lib/util/eof_char_set.EofCharSet</a>)
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/ulex/lib/automaton/nfa.mbt,5:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/ulex/lib/automaton#Input">Input</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/automaton/nfa.mbt,5:::fn op_equal(<a href="moonbitlang/ulex/lib/automaton#Input">Input</a>, <a href="moonbitlang/ulex/lib/automaton#Input">Input</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,moonbitlang/ulex/lib/automaton/nfa.mbt,5:::impl <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="moonbitlang/ulex/lib/automaton#Input">Input</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/automaton/nfa.mbt,5:::fn hash_combine(<a href="moonbitlang/ulex/lib/automaton#Input">Input</a>, <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,moonbitlang/ulex/lib/automaton/nfa.mbt,5:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/ulex/lib/automaton#Input">Input</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/automaton/nfa.mbt,5:::fn output(<a href="moonbitlang/ulex/lib/automaton#Input">Input</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## NFA

```moonbit
:::source,moonbitlang/ulex/lib/automaton/nfa.mbt,11:::pub(all) struct NFA {
  graph : <a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/ulex/lib/automaton#NFANode">NFANode</a>]
  end_nodes : <a href="moonbitlang/core/builtin#Map">Map</a>[Int, Int]
  code_blocks : <a href="moonbitlang/core/array#Array">Array</a>[String]
  captures : <a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/core/array#Array">Array</a>[((String, <a href="moonbitlang/ulex/lib/type#VarType">@moonbitlang/ulex/lib/type.VarType</a>), (Int, Int))]]
  node_count : Int
  tag_count : Int
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/ulex/lib/automaton/nfa.mbt,18:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/ulex/lib/automaton#NFA">NFA</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/automaton/nfa.mbt,18:::fn output(<a href="moonbitlang/ulex/lib/automaton#NFA">NFA</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### from\_rule
  ```moonbit
  :::source,moonbitlang/ulex/lib/automaton/nfa.mbt,55:::fn <a href="moonbitlang/ulex/lib/automaton#NFA">NFA</a>::from_rule(rule : <a href="moonbitlang/ulex/lib/type#Rule">@moonbitlang/ulex/lib/type.Rule</a>) -> <a href="moonbitlang/ulex/lib/automaton#NFA">NFA</a>
  ```
  > 

## NFANode

```moonbit
:::source,moonbitlang/ulex/lib/automaton/nfa.mbt,21:::pub(all) struct NFANode {
  num : Int
  eps : <a href="moonbitlang/core/immut/sorted_set#T">@moonbitlang/core/immut/sorted_set.T</a>[(<a href="moonbitlang/ulex/lib/automaton#NFANode">NFANode</a>, Int?)]
  trans : <a href="moonbitlang/core/array#Array">Array</a>[(<a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">@moonbitlang/ulex/lib/util/eof_char_set.EofCharSet</a>, (<a href="moonbitlang/ulex/lib/automaton#NFANode">NFANode</a>, Int?))]
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/ulex/lib/automaton/nfa.mbt,33:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for <a href="moonbitlang/ulex/lib/automaton#NFANode">NFANode</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/automaton/nfa.mbt,33:::fn compare(self : <a href="moonbitlang/ulex/lib/automaton#NFANode">NFANode</a>, other : <a href="moonbitlang/ulex/lib/automaton#NFANode">NFANode</a>) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/ulex/lib/automaton/nfa.mbt,28:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/ulex/lib/automaton#NFANode">NFANode</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/automaton/nfa.mbt,28:::fn op_equal(self : <a href="moonbitlang/ulex/lib/automaton#NFANode">NFANode</a>, other : <a href="moonbitlang/ulex/lib/automaton#NFANode">NFANode</a>) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/ulex/lib/automaton/nfa.mbt,38:::impl <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="moonbitlang/ulex/lib/automaton#NFANode">NFANode</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/automaton/nfa.mbt,38:::fn hash_combine(self : <a href="moonbitlang/ulex/lib/automaton#NFANode">NFANode</a>, hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/ulex/lib/automaton/nfa.mbt,25:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/ulex/lib/automaton#NFANode">NFANode</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/automaton/nfa.mbt,25:::fn output(<a href="moonbitlang/ulex/lib/automaton#NFANode">NFANode</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## TagAction

```moonbit
:::source,moonbitlang/ulex/lib/automaton/dfa.mbt,5:::pub(all) type TagAction <a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/core/array#Array">Array</a>[Int]]
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/ulex/lib/automaton/dfa.mbt,5:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/ulex/lib/automaton#TagAction">TagAction</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/automaton/dfa.mbt,5:::fn output(<a href="moonbitlang/ulex/lib/automaton#TagAction">TagAction</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
