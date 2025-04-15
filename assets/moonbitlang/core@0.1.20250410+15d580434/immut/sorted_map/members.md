# Documentation
|Type|description|
|---|---|
|[T](#T)||

|Value|description|
|---|---|
|[add](#add)||
|[contains](#contains)||
|[each](#each)||
|[eachi](#eachi)||
|[elems](#elems)||
|[filter](#filter)||
|[filter\_with\_key](#filter_with_key)||
|[fold](#fold)||
|[foldl\_with\_key](#foldl_with_key)||
|[foldr\_with\_key](#foldr_with_key)||
|[from\_array](#from_array)||
|[from\_iter](#from_iter)||
|[from\_json](#from_json)||
|[insert](#insert)||
|[is\_empty](#is_empty)||
|[iter](#iter)||
|[iter2](#iter2)||
|[keys](#keys)||
|[lookup](#lookup)||
|[map](#map)||
|[map\_with\_key](#map_with_key)||
|[new](#new)| Create an empty map.|
|[of](#of)||
|[op\_get](#op_get)||
|[remove](#remove)||
|[singleton](#singleton)||
|[size](#size)||
|[to\_array](#to_array)||
|[to\_json](#to_json)||

## T

```moonbit
:::source,moonbitlang/core/immut/sorted_map/types.mbt,35:::type T[K, V]
```

 Immutable map, consists of key-value pairs.

 #### Example

 ```
 let map1 = @sorted_map.of([(3, "three"), (8, "eight"), (1, "one")])
 let map2 = map1.add(2, "two").remove(3)
 assert_eq!(map2.lookup(2), Some("two"))
 let map3 = map2.add(2, "updated")
 assert_eq!(map2.lookup(3), None)
 assert_eq!(map3.lookup(3), None)
 assert_eq!(map3.lookup(2), Some("updated"))
 ```

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/traits_impl.mbt,35:::impl[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/sorted_map/traits_impl.mbt,35:::fn compare[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], other : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/traits_impl.mbt,16:::impl[K, V] <a href="moonbitlang/core/builtin#Default">Default</a> for <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/sorted_map/traits_impl.mbt,16:::fn default[K, V]() -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/traits_impl.mbt,21:::impl[K : <a href="moonbitlang/core/builtin#Eq">Eq</a>, V : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/sorted_map/traits_impl.mbt,21:::fn op_equal[K : <a href="moonbitlang/core/builtin#Eq">Eq</a>, V : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], other : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/traits_impl.mbt,59:::impl[K : <a href="moonbitlang/core/builtin#Hash">Hash</a>, V : <a href="moonbitlang/core/builtin#Hash">Hash</a>] <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/sorted_map/traits_impl.mbt,59:::fn hash_combine[K : <a href="moonbitlang/core/builtin#Hash">Hash</a>, V : <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/traits_impl.mbt,66:::impl[K : <a href="moonbitlang/core/builtin#Show">Show</a>, V : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/sorted_map/traits_impl.mbt,66:::fn output[K : <a href="moonbitlang/core/builtin#Show">Show</a>, V : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/traits_impl.mbt,71:::impl[K : <a href="moonbitlang/core/builtin#Show">Show</a>, V : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/sorted_map/traits_impl.mbt,71:::fn to_json[K : <a href="moonbitlang/core/builtin#Show">Show</a>, V : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/traits_impl.mbt,80:::impl[V : <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a>] <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="moonbitlang/core/immut/sorted_map#T">T</a>[String, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/sorted_map/traits_impl.mbt,80:::fn from_json[V : <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a>](json : <a href="moonbitlang/core/json#Json">Json</a>, path : <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[String, V]!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/traits_impl.mbt,51:::impl[K : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/sorted_map/traits_impl.mbt,54:::fn arbitrary[K : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>](size : Int, rs : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### add
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/map.mbt,19:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::add[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], key : K, value : V) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
  ```
  > 
  >  Create a new map with a key-value pair inserted.
  > O(log n).
  > 
- #### contains
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/utils.mbt,36:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::contains[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], key : K) -> Bool
  ```
  > 
  >  Check if the map contains a key.
  > O(log n).
- #### each
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/utils.mbt,98:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::each[K, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], f : (K, V) -> Unit) -> Unit
  ```
  > 
  >  Iterate over the key-value pairs in the map.
- #### eachi
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/utils.mbt,111:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::eachi[K, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], f : (Int, K, V) -> Unit) -> Unit
  ```
  > 
  >  Iterate over the key-value pairs with index.
- #### elems
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/utils.mbt,264:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::elems[K, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/array#Array">Array</a>[V]
  ```
  > 
  >  Return all elements of the map in the ascending order of their keys.
- #### empty
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/utils.mbt,18:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::empty[K, V]() -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
  ```
  >  Create an empty map.
- #### filter
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/map.mbt,96:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::filter[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], pred : (V) -> Bool) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
  ```
  > 
  >  Filter values that satisfy the predicate
- #### filter\_with\_key
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/map.mbt,102:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::filter_with_key[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], pred : (K, V) -> Bool) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
  ```
  > 
  >  Filter key-value pairs that satisfy the predicate
- #### fold
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/utils.mbt,149:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::fold[K, V, A](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], init~ : A, f : (A, V) -> A) -> A
  ```
  > 
  >  Fold the values in the map.
  > O(n).
- #### foldl\_with\_key
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/utils.mbt,174:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::foldl_with_key[K, V, A](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], f : (A, K, V) -> A, init~ : A) -> A
  ```
  > 
  >  Pre-order fold.
  > O(n).
- #### foldr\_with\_key
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/utils.mbt,156:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::foldr_with_key[K, V, A](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], f : (A, K, V) -> A, init~ : A) -> A
  ```
  > 
  >  Post-order fold.
  > O(n).
- #### from\_array
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/deprecated.mbt,42:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::from_array[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](array : <a href="moonbitlang/core/array#Array">Array</a>[(K, V)]) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
  ```
  > 
- #### from\_iter
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/deprecated.mbt,49:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::from_iter[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[(K, V)]) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
  ```
  > 
- #### from\_json
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/deprecated.mbt,63:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::from_json[V : <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a>](json : <a href="moonbitlang/core/json#Json">Json</a>) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[String, V]!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
  ```
  > 
- #### insert
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/deprecated.mbt,21:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::insert[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], key : K, value : V) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
  ```
  > 
  >  Create a new map with a key-value pair inserted.
  > O(log n).
  > 
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/utils.mbt,62:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::is_empty[K, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]) -> Bool
  ```
  > 
- #### iter
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/utils.mbt,214:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::iter[K, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[(K, V)]
  ```
  > 
- #### iter2
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/utils.mbt,233:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::iter2[K, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[K, V]
  ```
  > 
- #### keys
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/utils.mbt,258:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::keys[K, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/array#Array">Array</a>[K]
  ```
  > 
  >  Return all keys of the map in ascending order.
- #### lookup
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/utils.mbt,75:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::lookup[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], key : K) -> V?
  ```
  > 
  >  Get the value associated with a key.
  > O(log n).
- #### map
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/utils.mbt,128:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::map[K, X, Y](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, X], f : (X) -> Y) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, Y]
  ```
  > 
  >  Ts over the values in the map.
- #### map\_with\_key
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/utils.mbt,138:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::map_with_key[K, X, Y](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, X], f : (K, X) -> Y) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, Y]
  ```
  > 
  >  Maps over the key-value pairs in the map.
- #### new
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/deprecated.mbt,28:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::new[K, V]() -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
  ```
  > 
- #### of
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/deprecated.mbt,56:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::of[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](array : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[(K, V)]) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
  ```
  > 
- #### op\_get
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/utils.mbt,92:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::op_get[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], key : K) -> V?
  ```
  > 
- #### remove
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/map.mbt,78:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::remove[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], key : K) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
  ```
  > 
  >  Create a new map with a key-value pair removed. O(log n).
  > If the key is not a member or map, the original map is returned.
- #### singleton
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/deprecated.mbt,35:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::singleton[K, V](key : K, value : V) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
  ```
  > 
- #### size
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/utils.mbt,54:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::size[K, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]) -> Int
  ```
  > 
  >  Get the number of key-value pairs in the map.
- #### to\_array
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/map.mbt,119:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::to_array[K, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/array#Array">Array</a>[(K, V)]
  ```
  > 
  >  Convert to an array of key-value pairs.
- #### to\_json
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_map/utils.mbt,279:::fn <a href="moonbitlang/core/immut/sorted_map#T">T</a>::to_json[K : <a href="moonbitlang/core/builtin#Show">Show</a>, V : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/json#Json">Json</a>
  ```
  > 

## add

```moonbit
:::source,moonbitlang/core/immut/sorted_map/map.mbt,19:::fn add[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], key : K, value : V) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
```

 Create a new map with a key-value pair inserted.
O(log n).


## contains

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,36:::fn contains[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], key : K) -> Bool
```

 Check if the map contains a key.
O(log n).

## each

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,98:::fn each[K, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], f : (K, V) -> Unit) -> Unit
```

 Iterate over the key-value pairs in the map.

## eachi

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,111:::fn eachi[K, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], f : (Int, K, V) -> Unit) -> Unit
```

 Iterate over the key-value pairs with index.

## elems

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,264:::fn elems[K, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/array#Array">Array</a>[V]
```

 Return all elements of the map in the ascending order of their keys.

## filter

```moonbit
:::source,moonbitlang/core/immut/sorted_map/map.mbt,96:::fn filter[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], pred : (V) -> Bool) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
```

 Filter values that satisfy the predicate

## filter\_with\_key

```moonbit
:::source,moonbitlang/core/immut/sorted_map/map.mbt,102:::fn filter_with_key[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], pred : (K, V) -> Bool) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
```

 Filter key-value pairs that satisfy the predicate

## fold

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,149:::fn fold[K, V, A](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], init~ : A, f : (A, V) -> A) -> A
```

 Fold the values in the map.
O(n).

## foldl\_with\_key

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,174:::fn foldl_with_key[K, V, A](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], f : (A, K, V) -> A, init~ : A) -> A
```

 Pre-order fold.
O(n).

## foldr\_with\_key

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,156:::fn foldr_with_key[K, V, A](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], f : (A, K, V) -> A, init~ : A) -> A
```

 Post-order fold.
O(n).

## from\_array

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,204:::fn from_array[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](array : <a href="moonbitlang/core/array#Array">Array</a>[(K, V)]) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
```

 Build a map from an array of key-value pairs.
O(n\*log n).

## from\_iter

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,252:::fn from_iter[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[(K, V)]) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
```


## from\_json

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,284:::fn from_json[V : <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a>](json : <a href="moonbitlang/core/json#Json">Json</a>) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[String, V]!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
```


## insert

```moonbit
:::source,moonbitlang/core/immut/sorted_map/deprecated.mbt,21:::fn insert[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], key : K, value : V) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
```

 Create a new map with a key-value pair inserted.
O(log n).


## is\_empty

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,62:::fn is_empty[K, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]) -> Bool
```


## iter

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,214:::fn iter[K, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[(K, V)]
```


## iter2

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,233:::fn iter2[K, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[K, V]
```


## keys

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,258:::fn keys[K, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/array#Array">Array</a>[K]
```

 Return all keys of the map in ascending order.

## lookup

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,75:::fn lookup[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], key : K) -> V?
```

 Get the value associated with a key.
O(log n).

## map

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,128:::fn map[K, X, Y](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, X], f : (X) -> Y) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, Y]
```

 Ts over the values in the map.

## map\_with\_key

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,138:::fn map_with_key[K, X, Y](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, X], f : (K, X) -> Y) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, Y]
```

 Maps over the key-value pairs in the map.

## new

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,23:::fn new[K, V]() -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
```
 Create an empty map.

## of

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,269:::fn of[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](array : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[(K, V)]) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
```


## op\_get

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,92:::fn op_get[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], key : K) -> V?
```


## remove

```moonbit
:::source,moonbitlang/core/immut/sorted_map/map.mbt,78:::fn remove[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V], key : K) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
```

 Create a new map with a key-value pair removed. O(log n).
If the key is not a member or map, the original map is returned.

## singleton

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,29:::fn singleton[K, V](key : K, value : V) -> <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]
```

 Create a map with a single key-value pair.

## size

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,54:::fn size[K, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]) -> Int
```

 Get the number of key-value pairs in the map.

## to\_array

```moonbit
:::source,moonbitlang/core/immut/sorted_map/map.mbt,119:::fn to_array[K, V](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/array#Array">Array</a>[(K, V)]
```

 Convert to an array of key-value pairs.

## to\_json

```moonbit
:::source,moonbitlang/core/immut/sorted_map/utils.mbt,279:::fn to_json[K : <a href="moonbitlang/core/builtin#Show">Show</a>, V : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : <a href="moonbitlang/core/immut/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/json#Json">Json</a>
```

