# Documentation
|Type|description|
|---|---|
|[Unit](#Unit)||

|Value|description|
|---|---|
|[default](#default)||
|[to\_string](#to_string)||

## default

```moonbit
:::source,moonbitlang/core/unit/unit.mbt,40:::fn default() -> Unit
```

 same as `Unit::default`

## to\_string

```moonbit
:::source,moonbitlang/core/unit/unit.mbt,16:::fn to_string(self : Unit) -> String
```


## Unit


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/unit/unit.mbt,45:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for Unit
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/unit/unit.mbt,45:::fn compare(_self : Unit, _other : Unit) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/unit/unit.mbt,34:::impl <a href="moonbitlang/core/builtin#Default">Default</a> for Unit
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/unit/unit.mbt,34:::fn default() -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/unit/unit.mbt,22:::impl <a href="moonbitlang/core/builtin#Hash">Hash</a> for Unit
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/unit/unit.mbt,22:::fn hash(self : Unit) -> Int
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/core/unit/unit.mbt,28:::fn hash_combine(self : Unit, hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### to\_string
  ```moonbit
  :::source,moonbitlang/core/unit/unit.mbt,16:::fn <a href="moonbitlang/core/unit#Unit">Unit</a>::to_string(self : Unit) -> String
  ```
  > 
