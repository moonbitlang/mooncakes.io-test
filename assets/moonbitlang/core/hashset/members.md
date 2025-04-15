# Documentation
|Type|description|
|---|---|
|[T](#T)||

|Value|description|
|---|---|
|[add](#add)||
|[capacity](#capacity)||
|[clear](#clear)||
|[contains](#contains)||
|[difference](#difference)||
|[each](#each)||
|[eachi](#eachi)||
|[from\_array](#from_array)||
|[from\_iter](#from_iter)||
|[insert](#insert)||
|[intersection](#intersection)||
|[is\_empty](#is_empty)||
|[iter](#iter)||
|[new](#new)||
|[of](#of)||
|[remove](#remove)||
|[size](#size)||
|[symmetric\_difference](#symmetric_difference)||
|[to\_array](#to_array)||
|[union](#union)||

## T

```moonbit
:::source,moonbitlang/core/hashset/types.mbt,38:::type T[K]
```

 Mutable hash set, not thread safe.

 #### Example

 ```
 let set = @hashset.of([(3, "three"), (8, "eight"), (1, "one")])
 set.add((4, "four"))
 assert_eq!(set.contains((4, "four")), true)
 ```

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/hashset/hashset.mbt,321:::impl[K : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/hashset#T">T</a>[K]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/hashset/hashset.mbt,321:::fn output[K : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/hashset#T">T</a>[K], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/hashset/hashset.mbt,233:::impl[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for <a href="moonbitlang/core/hashset#T">T</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/hashset/hashset.mbt,233:::fn arbitrary[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>](size : Int, rs : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> <a href="moonbitlang/core/hashset#T">T</a>[X]
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### add
  ```moonbit
  :::source,moonbitlang/core/hashset/hashset.mbt,56:::fn <a href="moonbitlang/core/hashset#T">T</a>::add[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/hashset#T">T</a>[K], key : K) -> Unit
  ```
  > 
  >  Insert a key into hash set.
- #### capacity
  ```moonbit
  :::source,moonbitlang/core/hashset/hashset.mbt,139:::fn <a href="moonbitlang/core/hashset#T">T</a>::capacity[K](self : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> Int
  ```
  > 
  >  Get the capacity of the set.
- #### clear
  ```moonbit
  :::source,moonbitlang/core/hashset/hashset.mbt,169:::fn <a href="moonbitlang/core/hashset#T">T</a>::clear[K](self : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> Unit
  ```
  > 
  >  Clears the set, removing all keys. Keeps the allocated space.
- #### contains
  ```moonbit
  :::source,moonbitlang/core/hashset/hashset.mbt,93:::fn <a href="moonbitlang/core/hashset#T">T</a>::contains[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/hashset#T">T</a>[K], key : K) -> Bool
  ```
  > 
  >  Check if the hash set contains a key.
- #### difference
  ```moonbit
  :::source,moonbitlang/core/hashset/hashset.mbt,196:::fn <a href="moonbitlang/core/hashset#T">T</a>::difference[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/hashset#T">T</a>[K], other : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> <a href="moonbitlang/core/hashset#T">T</a>[K]
  ```
  > 
  >  Difference of two hash sets.
- #### each
  ```moonbit
  :::source,moonbitlang/core/hashset/hashset.mbt,151:::fn <a href="moonbitlang/core/hashset#T">T</a>::each[K](self : <a href="moonbitlang/core/hashset#T">T</a>[K], f : (K) -> Unit) -> Unit
  ```
  > 
  >  Iterate over all keys of the set.
- #### eachi
  ```moonbit
  :::source,moonbitlang/core/hashset/hashset.mbt,157:::fn <a href="moonbitlang/core/hashset#T">T</a>::eachi[K](self : <a href="moonbitlang/core/hashset#T">T</a>[K], f : (Int, K) -> Unit) -> Unit
  ```
  > 
  >  Iterate over all keys of the set, with index.
- #### from\_array
  ```moonbit
  :::source,moonbitlang/core/hashset/deprecated.mbt,25:::fn <a href="moonbitlang/core/hashset#T">T</a>::from_array[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](arr : <a href="moonbitlang/core/array#Array">Array</a>[K]) -> <a href="moonbitlang/core/hashset#T">T</a>[K]
  ```
  > 
- #### from\_iter
  ```moonbit
  :::source,moonbitlang/core/hashset/deprecated.mbt,39:::fn <a href="moonbitlang/core/hashset#T">T</a>::from_iter[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[K]) -> <a href="moonbitlang/core/hashset#T">T</a>[K]
  ```
  > 
- #### insert
  ```moonbit
  :::source,moonbitlang/core/hashset/hashset.mbt,50:::fn <a href="moonbitlang/core/hashset#T">T</a>::insert[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/hashset#T">T</a>[K], key : K) -> Unit
  ```
  > 
  >  Insert a key into hash set.
  > @alert unsafe "Panic if the hash set is full."
- #### intersection
  ```moonbit
  :::source,moonbitlang/core/hashset/hashset.mbt,188:::fn <a href="moonbitlang/core/hashset#T">T</a>::intersection[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/hashset#T">T</a>[K], other : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> <a href="moonbitlang/core/hashset#T">T</a>[K]
  ```
  > 
  >  Intersection of two hash sets.
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/hashset/hashset.mbt,145:::fn <a href="moonbitlang/core/hashset#T">T</a>::is_empty[K](self : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> Bool
  ```
  > 
  >  Check if the hash set is empty.
- #### iter
  ```moonbit
  :::source,moonbitlang/core/hashset/hashset.mbt,212:::fn <a href="moonbitlang/core/hashset#T">T</a>::iter[K](self : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[K]
  ```
  > 
- #### new
  ```moonbit
  :::source,moonbitlang/core/hashset/deprecated.mbt,18:::fn <a href="moonbitlang/core/hashset#T">T</a>::new[K](capacity~ : Int = ..) -> <a href="moonbitlang/core/hashset#T">T</a>[K]
  ```
  > 
- #### of
  ```moonbit
  :::source,moonbitlang/core/hashset/deprecated.mbt,32:::fn <a href="moonbitlang/core/hashset#T">T</a>::of[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[K]) -> <a href="moonbitlang/core/hashset#T">T</a>[K]
  ```
  > 
- #### remove
  ```moonbit
  :::source,moonbitlang/core/hashset/hashset.mbt,115:::fn <a href="moonbitlang/core/hashset#T">T</a>::remove[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/hashset#T">T</a>[K], key : K) -> Unit
  ```
  > 
  >  Remove a key from hash set.
- #### size
  ```moonbit
  :::source,moonbitlang/core/hashset/hashset.mbt,133:::fn <a href="moonbitlang/core/hashset#T">T</a>::size[K](self : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> Int
  ```
  > 
  >  Get the number of keys in the set.
- #### symmetric\_difference
  ```moonbit
  :::source,moonbitlang/core/hashset/hashset.mbt,204:::fn <a href="moonbitlang/core/hashset#T">T</a>::symmetric_difference[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/hashset#T">T</a>[K], other : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> <a href="moonbitlang/core/hashset#T">T</a>[K]
  ```
  > 
  >  Symmetric difference of two hash sets.
- #### to\_array
  ```moonbit
  :::source,moonbitlang/core/hashset/hashset.mbt,434:::fn <a href="moonbitlang/core/hashset#T">T</a>::to_array[K](self : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> <a href="moonbitlang/core/array#Array">Array</a>[K]
  ```
  > 
- #### union
  ```moonbit
  :::source,moonbitlang/core/hashset/hashset.mbt,179:::fn <a href="moonbitlang/core/hashset#T">T</a>::union[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/hashset#T">T</a>[K], other : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> <a href="moonbitlang/core/hashset#T">T</a>[K]
  ```
  > 
  >  Union of two hash sets.
  > @alert unsafe "Panic if the hash set is full."

## add

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,56:::fn add[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/hashset#T">T</a>[K], key : K) -> Unit
```

 Insert a key into hash set.

## capacity

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,139:::fn capacity[K](self : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> Int
```

 Get the capacity of the set.

## clear

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,169:::fn clear[K](self : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> Unit
```

 Clears the set, removing all keys. Keeps the allocated space.

## contains

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,93:::fn contains[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/hashset#T">T</a>[K], key : K) -> Bool
```

 Check if the hash set contains a key.

## difference

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,196:::fn difference[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/hashset#T">T</a>[K], other : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> <a href="moonbitlang/core/hashset#T">T</a>[K]
```

 Difference of two hash sets.

## each

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,151:::fn each[K](self : <a href="moonbitlang/core/hashset#T">T</a>[K], f : (K) -> Unit) -> Unit
```

 Iterate over all keys of the set.

## eachi

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,157:::fn eachi[K](self : <a href="moonbitlang/core/hashset#T">T</a>[K], f : (Int, K) -> Unit) -> Unit
```

 Iterate over all keys of the set, with index.

## from\_array

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,32:::fn from_array[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](arr : <a href="moonbitlang/core/array#Array">Array</a>[K]) -> <a href="moonbitlang/core/hashset#T">T</a>[K]
```

 Create new hash set from array.

## from\_iter

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,226:::fn from_iter[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[K]) -> <a href="moonbitlang/core/hashset#T">T</a>[K]
```


## insert

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,50:::fn insert[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/hashset#T">T</a>[K], key : K) -> Unit
```

 Insert a key into hash set.
@alert unsafe "Panic if the hash set is full."

## intersection

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,188:::fn intersection[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/hashset#T">T</a>[K], other : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> <a href="moonbitlang/core/hashset#T">T</a>[K]
```

 Intersection of two hash sets.

## is\_empty

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,145:::fn is_empty[K](self : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> Bool
```

 Check if the hash set is empty.

## iter

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,212:::fn iter[K](self : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[K]
```


## new

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,21:::fn new[K](capacity~ : Int = ..) -> <a href="moonbitlang/core/hashset#T">T</a>[K]
```

 Create new hash set.

## of

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,39:::fn of[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[K]) -> <a href="moonbitlang/core/hashset#T">T</a>[K]
```


## remove

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,115:::fn remove[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/hashset#T">T</a>[K], key : K) -> Unit
```

 Remove a key from hash set.

## size

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,133:::fn size[K](self : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> Int
```

 Get the number of keys in the set.

## symmetric\_difference

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,204:::fn symmetric_difference[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/hashset#T">T</a>[K], other : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> <a href="moonbitlang/core/hashset#T">T</a>[K]
```

 Symmetric difference of two hash sets.

## to\_array

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,434:::fn to_array[K](self : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> <a href="moonbitlang/core/array#Array">Array</a>[K]
```


## union

```moonbit
:::source,moonbitlang/core/hashset/hashset.mbt,179:::fn union[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/hashset#T">T</a>[K], other : <a href="moonbitlang/core/hashset#T">T</a>[K]) -> <a href="moonbitlang/core/hashset#T">T</a>[K]
```

 Union of two hash sets.
@alert unsafe "Panic if the hash set is full."
