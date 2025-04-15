# Documentation
|Type|description|
|---|---|
|[Bitset](#Bitset)||
|[T](#T)||

|Value|description|
|---|---|
|[copy](#copy)||
|[get](#get)||
|[length](#length)||
|[new](#new)||
|[set](#set)||
|[union](#union)||

## Bitset

```moonbit
:::source,moonbitlang/ulex/lib/util/bitset/bitset.mbt,5:::type Bitset
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/bitset/bitset.mbt,8:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/bitset/bitset.mbt,8:::fn op_equal(<a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>, <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/bitset/bitset.mbt,51:::impl <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/bitset/bitset.mbt,51:::fn hash_combine(self : <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>, hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/bitset/bitset.mbt,56:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/bitset/bitset.mbt,56:::fn output(self : <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### copy
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/bitset/bitset.mbt,16:::fn <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>::copy(self : <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>) -> <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>
  ```
  > 
- #### get
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/bitset/bitset.mbt,21:::fn <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>::get(self : <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>, index : Int) -> Bool
  ```
  > 
- #### length
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/bitset/bitset.mbt,46:::fn <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>::length(self : <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>) -> Int
  ```
  > 
- #### set
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/bitset/bitset.mbt,26:::fn <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>::set(self : <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>, index : Int, value : Bool) -> Unit
  ```
  > 
- #### union
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/bitset/bitset.mbt,32:::fn <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>::union(self : <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>, other : <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>) -> <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>
  ```
  > 

## T

```moonbit
:::source,moonbitlang/ulex/lib/util/bitset/bitset.mbt,2:::type T = <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>
```


## copy

```moonbit
:::source,moonbitlang/ulex/lib/util/bitset/bitset.mbt,16:::fn copy(self : <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>) -> <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>
```


## get

```moonbit
:::source,moonbitlang/ulex/lib/util/bitset/bitset.mbt,21:::fn get(self : <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>, index : Int) -> Bool
```


## length

```moonbit
:::source,moonbitlang/ulex/lib/util/bitset/bitset.mbt,46:::fn length(self : <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>) -> Int
```


## new

```moonbit
:::source,moonbitlang/ulex/lib/util/bitset/bitset.mbt,11:::fn new(len : Int) -> <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>
```


## set

```moonbit
:::source,moonbitlang/ulex/lib/util/bitset/bitset.mbt,26:::fn set(self : <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>, index : Int, value : Bool) -> Unit
```


## union

```moonbit
:::source,moonbitlang/ulex/lib/util/bitset/bitset.mbt,32:::fn union(self : <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>, other : <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>) -> <a href="moonbitlang/ulex/lib/util/bitset#Bitset">Bitset</a>
```

