# Documentation
|Type|description|
|---|---|
|[T](#T)||

|Value|description|
|---|---|
|[array](#array)||
|[enums](#enums)||
|[integer](#integer)||
|[object](#object)||
|[string](#string)||

## T

```moonbit
:::source,peter-jerry-ye/mcp-server/schema/schema.mbt,16:::type T
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,peter-jerry-ye/mcp-server/schema/schema.mbt,91:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="peter-jerry-ye/mcp-server/schema#T">T</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/mcp-server/schema/schema.mbt,91:::fn to_json(self : <a href="peter-jerry-ye/mcp-server/schema#T">T</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### to\_json
  ```moonbit
  :::source,peter-jerry-ye/mcp-server/schema/schema.mbt,58:::fn <a href="peter-jerry-ye/mcp-server/schema#T">T</a>::to_json(self : <a href="peter-jerry-ye/mcp-server/schema#T">T</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
  ```
  > 
- #### verify
  ```moonbit
  :::source,peter-jerry-ye/mcp-server/schema/schema.mbt,96:::fn <a href="peter-jerry-ye/mcp-server/schema#T">T</a>::verify(self : <a href="peter-jerry-ye/mcp-server/schema#T">T</a>, json : <a href="moonbitlang/core/json#Json">Json</a>) -> Bool
  ```
  > 

## array

```moonbit
:::source,peter-jerry-ye/mcp-server/schema/schema.mbt,53:::fn array(schema : <a href="peter-jerry-ye/mcp-server/schema#T">T</a>) -> <a href="peter-jerry-ye/mcp-server/schema#T">T</a>
```


## enums

```moonbit
:::source,peter-jerry-ye/mcp-server/schema/schema.mbt,48:::fn enums(values : <a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/core/json#Json">Json</a>]) -> <a href="peter-jerry-ye/mcp-server/schema#T">T</a>
```


## integer

```moonbit
:::source,peter-jerry-ye/mcp-server/schema/schema.mbt,29:::fn integer() -> <a href="peter-jerry-ye/mcp-server/schema#T">T</a>
```


## object

```moonbit
:::source,peter-jerry-ye/mcp-server/schema/schema.mbt,39:::fn object(object : <a href="moonbitlang/core/builtin#Map">Map</a>[String, <a href="peter-jerry-ye/mcp-server/schema#T">T</a>], additionalProperties~ : Bool = .., required? : <a href="moonbitlang/core/array#Array">Array</a>[String]) -> <a href="peter-jerry-ye/mcp-server/schema#T">T</a>
```


## string

```moonbit
:::source,peter-jerry-ye/mcp-server/schema/schema.mbt,34:::fn string() -> <a href="peter-jerry-ye/mcp-server/schema#T">T</a>
```

