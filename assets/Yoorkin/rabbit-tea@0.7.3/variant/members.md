# Documentation
|Type|description|
|---|---|
|[Variant](#Variant)||

## Variant

```moonbit
:::source,Yoorkin/rabbit-tea/variant/variant.mbt,2:::pub(all) enum Variant {
  Boolean(Bool)
  Integer(Int)
  Floating(Double)
  String(String)
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,Yoorkin/rabbit-tea/variant/variant.mbt,7:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for <a href="Yoorkin/rabbit-tea/variant#Variant">Variant</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/variant/variant.mbt,7:::fn compare(<a href="Yoorkin/rabbit-tea/variant#Variant">Variant</a>, <a href="Yoorkin/rabbit-tea/variant#Variant">Variant</a>) -> Int
    ```
    > automatically derived
- ```moonbit
  :::source,Yoorkin/rabbit-tea/variant/variant.mbt,7:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="Yoorkin/rabbit-tea/variant#Variant">Variant</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/variant/variant.mbt,7:::fn op_equal(<a href="Yoorkin/rabbit-tea/variant#Variant">Variant</a>, <a href="Yoorkin/rabbit-tea/variant#Variant">Variant</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,Yoorkin/rabbit-tea/variant/variant.mbt,7:::impl <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="Yoorkin/rabbit-tea/variant#Variant">Variant</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/variant/variant.mbt,7:::fn hash_combine(<a href="Yoorkin/rabbit-tea/variant#Variant">Variant</a>, <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,Yoorkin/rabbit-tea/variant/variant.mbt,7:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="Yoorkin/rabbit-tea/variant#Variant">Variant</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/variant/variant.mbt,7:::fn output(<a href="Yoorkin/rabbit-tea/variant#Variant">Variant</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
