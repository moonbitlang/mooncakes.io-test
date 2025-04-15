# Documentation
|Type|description|
|---|---|
|[DotGraph](#DotGraph)||
|[Edge](#Edge)||
|[NodeType](#NodeType)||

|Value|description|
|---|---|
|[add\_edge](#add_edge)||

## DotGraph

```moonbit
:::source,moonbitlang/ulex/lib/tests/dot.mbt,11:::pub(all) struct DotGraph {
  edges : <a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/ulex/lib/tests#Edge">Edge</a>]
  nodes : <a href="moonbitlang/core/builtin#Map">Map</a>[Int, (<a href="moonbitlang/ulex/lib/tests#NodeType">NodeType</a>, String?)]
  name : String
}
```


#### mooncakes-io-method-mark-Methods
- #### add\_edge
  ```moonbit
  :::source,moonbitlang/ulex/lib/tests/dot.mbt,23:::fn <a href="moonbitlang/ulex/lib/tests#DotGraph">DotGraph</a>::add_edge(self : <a href="moonbitlang/ulex/lib/tests#DotGraph">DotGraph</a>, from~ : Int, to~ : Int, edge_info? : String) -> Unit
  ```
  > 
- #### new
  ```moonbit
  :::source,moonbitlang/ulex/lib/tests/dot.mbt,18:::fn <a href="moonbitlang/ulex/lib/tests#DotGraph">DotGraph</a>::new(name~ : String = ..) -> <a href="moonbitlang/ulex/lib/tests#DotGraph">DotGraph</a>
  ```
  > 

## Edge

```moonbit
:::source,moonbitlang/ulex/lib/tests/dot.mbt,2:::type Edge
```


## NodeType

```moonbit
:::source,moonbitlang/ulex/lib/tests/dot.mbt,5:::type NodeType
```


## add\_edge

```moonbit
:::source,moonbitlang/ulex/lib/tests/dot.mbt,23:::fn add_edge(self : <a href="moonbitlang/ulex/lib/tests#DotGraph">DotGraph</a>, from~ : Int, to~ : Int, edge_info? : String) -> Unit
```

