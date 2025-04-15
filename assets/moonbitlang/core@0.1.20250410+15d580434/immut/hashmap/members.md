# Documentation
|Type|description|
|---|---|
|[T](#T)||

|Value|description|
|---|---|
|[add](#add)||
|[each](#each)||
|[find](#find)||
|[from\_array](#from_array)||
|[from\_iter](#from_iter)||
|[iter](#iter)||
|[iter2](#iter2)||
|[new](#new)||
|[of](#of)||
|[op\_get](#op_get)||
|[remove](#remove)||
|[size](#size)||
|[union](#union)||

## T

```moonbit
:::source,moonbitlang/core/immut/hashmap/types.mbt,25:::type T[K, V]
```

 An immutable hash-map data structure

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/immut/hashmap/HAMT.mbt,292:::impl[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/hashmap/HAMT.mbt,292:::fn op_equal[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V], other : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/hashmap/HAMT.mbt,307:::impl[K : <a href="moonbitlang/core/builtin#Hash">Hash</a>, V : <a href="moonbitlang/core/builtin#Hash">Hash</a>] <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/hashmap/HAMT.mbt,307:::fn hash_combine[K : <a href="moonbitlang/core/builtin#Hash">Hash</a>, V : <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V], hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/hashmap/HAMT.mbt,257:::impl[K : <a href="moonbitlang/core/builtin#Show">Show</a>, V : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/hashmap/HAMT.mbt,257:::fn output[K : <a href="moonbitlang/core/builtin#Show">Show</a>, V : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/hashmap/HAMT.mbt,273:::impl[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, V : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/hashmap/HAMT.mbt,276:::fn arbitrary[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, V : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>](size : Int, rs : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### add
  ```moonbit
  :::source,moonbitlang/core/immut/hashmap/HAMT.mbt,131:::fn <a href="moonbitlang/core/immut/hashmap#T">T</a>::add[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V], key : K, value : V) -> <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]
  ```
  > 
  >  Add a key-value pair to the hashmap.
  > 
  >  If a pair with the same key already exists, the old one is replaced
- #### each
  ```moonbit
  :::source,moonbitlang/core/immut/hashmap/HAMT.mbt,219:::fn <a href="moonbitlang/core/immut/hashmap#T">T</a>::each[K, V](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V], f : (K, V) -> Unit) -> Unit
  ```
  > 
  >  Iterate through the elements in a hash map
- #### find
  ```moonbit
  :::source,moonbitlang/core/immut/hashmap/HAMT.mbt,44:::fn <a href="moonbitlang/core/immut/hashmap#T">T</a>::find[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V], key : K) -> V?
  ```
  > 
  >  Lookup a key from a hash map
- #### from\_array
  ```moonbit
  :::source,moonbitlang/core/immut/hashmap/deprecated.mbt,32:::fn <a href="moonbitlang/core/immut/hashmap#T">T</a>::from_array[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V](arr : <a href="moonbitlang/core/array#Array">Array</a>[(K, V)]) -> <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]
  ```
  > 
- #### from\_iter
  ```moonbit
  :::source,moonbitlang/core/immut/hashmap/deprecated.mbt,25:::fn <a href="moonbitlang/core/immut/hashmap#T">T</a>::from_iter[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[(K, V)]) -> <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]
  ```
  > 
- #### iter
  ```moonbit
  :::source,moonbitlang/core/immut/hashmap/HAMT.mbt,230:::fn <a href="moonbitlang/core/immut/hashmap#T">T</a>::iter[K, V](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[(K, V)]
  ```
  > 
  >  Converted to Iter
- #### iter2
  ```moonbit
  :::source,moonbitlang/core/immut/hashmap/HAMT.mbt,240:::fn <a href="moonbitlang/core/immut/hashmap#T">T</a>::iter2[K, V](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[K, V]
  ```
  > 
- #### new
  ```moonbit
  :::source,moonbitlang/core/immut/hashmap/deprecated.mbt,18:::fn <a href="moonbitlang/core/immut/hashmap#T">T</a>::new[K, V]() -> <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]
  ```
  > 
- #### of
  ```moonbit
  :::source,moonbitlang/core/immut/hashmap/deprecated.mbt,39:::fn <a href="moonbitlang/core/immut/hashmap#T">T</a>::of[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[(K, V)]) -> <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]
  ```
  > 
- #### op\_get
  ```moonbit
  :::source,moonbitlang/core/immut/hashmap/HAMT.mbt,64:::fn <a href="moonbitlang/core/immut/hashmap#T">T</a>::op_get[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V], key : K) -> V?
  ```
  > 
- #### remove
  ```moonbit
  :::source,moonbitlang/core/immut/hashmap/HAMT.mbt,137:::fn <a href="moonbitlang/core/immut/hashmap#T">T</a>::remove[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V], key : K) -> <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]
  ```
  > 
  >  Remove an element from a map
- #### size
  ```moonbit
  :::source,moonbitlang/core/immut/hashmap/HAMT.mbt,181:::fn <a href="moonbitlang/core/immut/hashmap#T">T</a>::size[K, V](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]) -> Int
  ```
  > 
  >  Calculate the size of a map.
  > 
  >  WARNING: this operation is `O(N)` in map size
- #### union
  ```moonbit
  :::source,moonbitlang/core/immut/hashmap/HAMT.mbt,199:::fn <a href="moonbitlang/core/immut/hashmap#T">T</a>::union[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V], other : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]) -> <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]
  ```
  > 
  >  Union two hashmaps

## add

```moonbit
:::source,moonbitlang/core/immut/hashmap/HAMT.mbt,131:::fn add[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V], key : K, value : V) -> <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]
```

 Add a key-value pair to the hashmap.

 If a pair with the same key already exists, the old one is replaced

## each

```moonbit
:::source,moonbitlang/core/immut/hashmap/HAMT.mbt,219:::fn each[K, V](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V], f : (K, V) -> Unit) -> Unit
```

 Iterate through the elements in a hash map

## find

```moonbit
:::source,moonbitlang/core/immut/hashmap/HAMT.mbt,44:::fn find[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V], key : K) -> V?
```

 Lookup a key from a hash map

## from\_array

```moonbit
:::source,moonbitlang/core/immut/hashmap/HAMT.mbt,262:::fn from_array[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V](arr : <a href="moonbitlang/core/array#Array">Array</a>[(K, V)]) -> <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]
```


## from\_iter

```moonbit
:::source,moonbitlang/core/immut/hashmap/HAMT.mbt,252:::fn from_iter[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[(K, V)]) -> <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]
```


## iter

```moonbit
:::source,moonbitlang/core/immut/hashmap/HAMT.mbt,230:::fn iter[K, V](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[(K, V)]
```

 Converted to Iter

## iter2

```moonbit
:::source,moonbitlang/core/immut/hashmap/HAMT.mbt,240:::fn iter2[K, V](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[K, V]
```


## new

```moonbit
:::source,moonbitlang/core/immut/hashmap/HAMT.mbt,38:::fn new[K, V]() -> <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]
```


## of

```moonbit
:::source,moonbitlang/core/immut/hashmap/HAMT.mbt,281:::fn of[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[(K, V)]) -> <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]
```


## op\_get

```moonbit
:::source,moonbitlang/core/immut/hashmap/HAMT.mbt,64:::fn op_get[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V], key : K) -> V?
```


## remove

```moonbit
:::source,moonbitlang/core/immut/hashmap/HAMT.mbt,137:::fn remove[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V], key : K) -> <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]
```

 Remove an element from a map

## size

```moonbit
:::source,moonbitlang/core/immut/hashmap/HAMT.mbt,181:::fn size[K, V](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]) -> Int
```

 Calculate the size of a map.

 WARNING: this operation is `O(N)` in map size

## union

```moonbit
:::source,moonbitlang/core/immut/hashmap/HAMT.mbt,199:::fn union[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V](self : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V], other : <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]) -> <a href="moonbitlang/core/immut/hashmap#T">T</a>[K, V]
```

 Union two hashmaps
