# Documentation
|Type|description|
|---|---|
|[T](#T)||

|Value|description|
|---|---|
|[add](#add)||
|[clear](#clear)||
|[contains](#contains)||
|[each](#each)||
|[eachi](#eachi)||
|[from\_array](#from_array)| Creates a sorted map from a array of key-value pairs.|
|[from\_iter](#from_iter)||
|[get](#get)||
|[is\_empty](#is_empty)||
|[iter](#iter)||
|[iter2](#iter2)||
|[keys](#keys)||
|[new](#new)||
|[of](#of)||
|[op\_get](#op_get)||
|[op\_set](#op_set)||
|[range](#range)|Returns a new array of key-value pairs that are within the specified range \[low, high).|
|[remove](#remove)||
|[size](#size)||
|[to\_array](#to_array)||
|[values](#values)||

## T

```moonbit
:::source,moonbitlang/core/sorted_map/types.mbt,25:::type T[K, V]
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/sorted_map/map.mbt,26:::impl[K : <a href="moonbitlang/core/builtin#Eq">Eq</a>, V : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/sorted_map/map.mbt,26:::fn op_equal[K : <a href="moonbitlang/core/builtin#Eq">Eq</a>, V : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], other : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/sorted_map/utils.mbt,64:::impl[K : <a href="moonbitlang/core/builtin#Show">Show</a>, V : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/sorted_map/utils.mbt,64:::fn output[K : <a href="moonbitlang/core/builtin#Show">Show</a>, V : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/sorted_map/map.mbt,241:::impl[K : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/sorted_map/map.mbt,244:::fn arbitrary[K : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>](size : Int, rs : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### add
  ```moonbit
  :::source,moonbitlang/core/sorted_map/map.mbt,53:::fn <a href="moonbitlang/core/sorted_map#T">T</a>::add[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], key : K, value : V) -> Unit
  ```
  > 
  >  Inserts a key-value pair.
- #### clear
  ```moonbit
  :::source,moonbitlang/core/sorted_map/map.mbt,118:::fn <a href="moonbitlang/core/sorted_map#T">T</a>::clear[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]) -> Unit
  ```
  > 
  >  Clears the map.
- #### contains
  ```moonbit
  :::source,moonbitlang/core/sorted_map/map.mbt,97:::fn <a href="moonbitlang/core/sorted_map#T">T</a>::contains[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], key : K) -> Bool
  ```
  > 
  >  Checks if map contains a key-value pair.
- #### each
  ```moonbit
  :::source,moonbitlang/core/sorted_map/map.mbt,125:::fn <a href="moonbitlang/core/sorted_map#T">T</a>::each[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], f : (K, V) -> Unit) -> Unit
  ```
  > 
  >  Iterates the map.
- #### eachi
  ```moonbit
  :::source,moonbitlang/core/sorted_map/map.mbt,143:::fn <a href="moonbitlang/core/sorted_map#T">T</a>::eachi[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], f : (Int, K, V) -> Unit) -> Unit
  ```
  > 
  >  Iterates the map with index.
- #### from\_iter
  ```moonbit
  :::source,moonbitlang/core/sorted_map/deprecated.mbt,18:::fn <a href="moonbitlang/core/sorted_map#T">T</a>::from_iter[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[(K, V)]) -> <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]
  ```
  > 
- #### get
  ```moonbit
  :::source,moonbitlang/core/sorted_map/map.mbt,79:::fn <a href="moonbitlang/core/sorted_map#T">T</a>::get[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], key : K) -> V?
  ```
  > 
  >  Gets a value by a key.
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/sorted_map/map.mbt,106:::fn <a href="moonbitlang/core/sorted_map#T">T</a>::is_empty[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]) -> Bool
  ```
  > 
  >  Returns true if map is empty.
- #### iter
  ```moonbit
  :::source,moonbitlang/core/sorted_map/map.mbt,186:::fn <a href="moonbitlang/core/sorted_map#T">T</a>::iter[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[(K, V)]
  ```
  > 
- #### iter2
  ```moonbit
  :::source,moonbitlang/core/sorted_map/map.mbt,210:::fn <a href="moonbitlang/core/sorted_map#T">T</a>::iter2[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[K, V]
  ```
  > 
- #### keys
  ```moonbit
  :::source,moonbitlang/core/sorted_map/map.mbt,163:::fn <a href="moonbitlang/core/sorted_map#T">T</a>::keys[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/array#Array">Array</a>[K]
  ```
  > 
  >  Returns all keys in the map.
- #### op\_get
  ```moonbit
  :::source,moonbitlang/core/sorted_map/map.mbt,21:::fn <a href="moonbitlang/core/sorted_map#T">T</a>::op_get[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], key : K) -> V?
  ```
  > 
- #### op\_set
  ```moonbit
  :::source,moonbitlang/core/sorted_map/map.mbt,16:::fn <a href="moonbitlang/core/sorted_map#T">T</a>::op_set[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], key : K, value : V) -> Unit
  ```
  > 
- #### range
  ```moonbit
  :::source,moonbitlang/core/sorted_map/map.mbt,249:::fn <a href="moonbitlang/core/sorted_map#T">T</a>::range[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], low : K, high : K) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[K, V]
  ```
  > Returns a new array of key-value pairs that are within the specified range \[low, high).
- #### remove
  ```moonbit
  :::source,moonbitlang/core/sorted_map/map.mbt,65:::fn <a href="moonbitlang/core/sorted_map#T">T</a>::remove[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], key : K) -> Unit
  ```
  > 
  >  Removes a key-value pair.
- #### size
  ```moonbit
  :::source,moonbitlang/core/sorted_map/map.mbt,112:::fn <a href="moonbitlang/core/sorted_map#T">T</a>::size[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]) -> Int
  ```
  > 
  >  Returns the count of key-value pairs in the map.
- #### to\_array
  ```moonbit
  :::source,moonbitlang/core/sorted_map/map.mbt,179:::fn <a href="moonbitlang/core/sorted_map#T">T</a>::to_array[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/array#Array">Array</a>[(K, V)]
  ```
  > 
  >  Converts the map to an array.
- #### values
  ```moonbit
  :::source,moonbitlang/core/sorted_map/map.mbt,171:::fn <a href="moonbitlang/core/sorted_map#T">T</a>::values[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/array#Array">Array</a>[V]
  ```
  > 
  >  Returns all values in the map.

## add

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,53:::fn add[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], key : K, value : V) -> Unit
```

 Inserts a key-value pair.

## clear

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,118:::fn clear[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]) -> Unit
```

 Clears the map.

## contains

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,97:::fn contains[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], key : K) -> Bool
```

 Checks if map contains a key-value pair.

## each

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,125:::fn each[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], f : (K, V) -> Unit) -> Unit
```

 Iterates the map.

## eachi

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,143:::fn eachi[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], f : (Int, K, V) -> Unit) -> Unit
```

 Iterates the map with index.

## from\_array

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,45:::fn from_array[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](entries : <a href="moonbitlang/core/array#Array">Array</a>[(K, V)]) -> <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]
```
 Creates a sorted map from a array of key-value pairs.

## from\_iter

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,234:::fn from_iter[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[(K, V)]) -> <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]
```


## get

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,79:::fn get[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], key : K) -> V?
```

 Gets a value by a key.

## is\_empty

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,106:::fn is_empty[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]) -> Bool
```

 Returns true if map is empty.

## iter

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,186:::fn iter[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[(K, V)]
```


## iter2

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,210:::fn iter2[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[K, V]
```


## keys

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,163:::fn keys[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/array#Array">Array</a>[K]
```

 Returns all keys in the map.

## new

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,32:::fn new[K, V]() -> <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]
```

 Returns a new sorted map.

## of

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,38:::fn of[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](entries : <a href="moonbitlang/core/array#Array">Array</a>[(K, V)]) -> <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]
```


## op\_get

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,21:::fn op_get[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], key : K) -> V?
```


## op\_set

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,16:::fn op_set[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], key : K, value : V) -> Unit
```


## range

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,249:::fn range[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], low : K, high : K) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[K, V]
```
Returns a new array of key-value pairs that are within the specified range \[low, high).

## remove

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,65:::fn remove[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V], key : K) -> Unit
```

 Removes a key-value pair.

## size

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,112:::fn size[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]) -> Int
```

 Returns the count of key-value pairs in the map.

## to\_array

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,179:::fn to_array[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/array#Array">Array</a>[(K, V)]
```

 Converts the map to an array.

## values

```moonbit
:::source,moonbitlang/core/sorted_map/map.mbt,171:::fn values[K, V](self : <a href="moonbitlang/core/sorted_map#T">T</a>[K, V]) -> <a href="moonbitlang/core/array#Array">Array</a>[V]
```

 Returns all values in the map.
