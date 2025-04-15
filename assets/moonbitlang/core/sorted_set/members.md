# Documentation
|Type|description|
|---|---|
|[T](#T)||

|Value|description|
|---|---|
|[add](#add)||
|[contains](#contains)||
|[copy](#copy)||
|[deep\_clone](#deep_clone)||
|[diff](#diff)||
|[difference](#difference)||
|[disjoint](#disjoint)||
|[each](#each)||
|[eachi](#eachi)||
|[from\_array](#from_array)||
|[from\_iter](#from_iter)||
|[intersect](#intersect)||
|[intersection](#intersection)||
|[is\_empty](#is_empty)||
|[iter](#iter)||
|[new](#new)||
|[of](#of)| @alert deprecated "Use @sorted\_set.from\_array instead"|
|[range](#range)||
|[remove](#remove)||
|[singleton](#singleton)||
|[size](#size)||
|[subset](#subset)||
|[to\_array](#to_array)||
|[union](#union)||

## T

```moonbit
:::source,moonbitlang/core/sorted_set/types.mbt,20:::type T[V]
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,319:::impl[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/sorted_set#T">T</a>[V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/sorted_set/set.mbt,319:::fn op_equal[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], other : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,418:::impl[V : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/sorted_set#T">T</a>[V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/sorted_set/set.mbt,418:::fn output[V : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
    >  Converts the set to string.
- ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,426:::impl[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for <a href="moonbitlang/core/sorted_set#T">T</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/sorted_set/set.mbt,426:::fn arbitrary[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](size : Int, rs : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> <a href="moonbitlang/core/sorted_set#T">T</a>[X]
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### add
  ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,105:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::add[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], value : V) -> Unit
  ```
  > 
- #### contains
  ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,135:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::contains[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], value : V) -> Bool
  ```
  > 
  >  Return if a value is contained in the set.
- #### copy
  ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,63:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::copy[V](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
  ```
  > 
  >  Returns a shallow copy of the MutableSet.
  >  
  >  It is just copying the tree structure, not the values.
  >  
- #### deep\_clone
  ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,54:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::deep_clone[V](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
  ```
  > 
  >  It is just copying the tree structure, not the values.
  > It requires a Clone trait on T, which we don't have yet.
  > 
- #### diff
  ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,270:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::diff[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], src : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
  ```
  > 
  >  Returns the difference of two sets.
  >  
- #### difference
  ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,278:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::difference[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], src : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
  ```
  > 
  >  Returns the difference of two sets.
- #### disjoint
  ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,310:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::disjoint[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], src : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> Bool
  ```
  > 
  >  Returns if two sets are disjoint.
- #### each
  ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,337:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::each[V](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], f : (V) -> Unit) -> Unit
  ```
  > 
  >  Iterates the set.
- #### eachi
  ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,351:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::eachi[V](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], f : (Int, V) -> Unit) -> Unit
  ```
  > 
  >  Iterates the set with index.
- #### from\_iter
  ```moonbit
  :::source,moonbitlang/core/sorted_set/deprecated.mbt,18:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::from_iter[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[V]) -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
  ```
  > 
- #### intersect
  ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,288:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::intersect[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], src : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
  ```
  > 
  >  Returns the intersection of two sets.
- #### intersection
  ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,294:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::intersection[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], src : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
  ```
  > 
  >  Returns the intersection of two sets.
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,325:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::is_empty[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> Bool
  ```
  > 
  >  Returns if MutableSet is empty.
- #### iter
  ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,384:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::iter[V](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[V]
  ```
  > 
  >  Returns a iterator.
- #### range
  ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,451:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::range[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], low : V, high : V) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[V]
  ```
  > 
- #### remove
  ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,116:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::remove[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], value : V) -> Unit
  ```
  > 
- #### size
  ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,331:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::size[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> Int
  ```
  > 
  >  Returns the number of elements in the MutableSet.
- #### subset
  ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,302:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::subset[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], src : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> Bool
  ```
  > 
  >  Returns if a set is a subset of another set.
- #### to\_array
  ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,361:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::to_array[V](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> <a href="moonbitlang/core/array#Array">Array</a>[V]
  ```
  > 
  >  Converts the set to an array.
- #### union
  ```moonbit
  :::source,moonbitlang/core/sorted_set/set.mbt,153:::fn <a href="moonbitlang/core/sorted_set#T">T</a>::union[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], src : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
  ```
  > 
  >  Returns the union of two sets.

## add

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,105:::fn add[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], value : V) -> Unit
```


## contains

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,135:::fn contains[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], value : V) -> Bool
```

 Return if a value is contained in the set.

## copy

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,63:::fn copy[V](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
```

 Returns a shallow copy of the MutableSet.
 
 It is just copying the tree structure, not the values.
 

## deep\_clone

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,54:::fn deep_clone[V](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
```

 It is just copying the tree structure, not the values.
It requires a Clone trait on T, which we don't have yet.


## diff

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,270:::fn diff[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], src : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
```

 Returns the difference of two sets.
 

## difference

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,278:::fn difference[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], src : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
```

 Returns the difference of two sets.

## disjoint

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,310:::fn disjoint[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], src : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> Bool
```

 Returns if two sets are disjoint.

## each

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,337:::fn each[V](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], f : (V) -> Unit) -> Unit
```

 Iterates the set.

## eachi

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,351:::fn eachi[V](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], f : (Int, V) -> Unit) -> Unit
```

 Iterates the set with index.

## from\_array

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,31:::fn from_array[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](array : <a href="moonbitlang/core/array#Array">Array</a>[V]) -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
```

 Initialize an set from an array.

## from\_iter

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,410:::fn from_iter[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[V]) -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
```


## intersect

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,288:::fn intersect[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], src : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
```

 Returns the intersection of two sets.

## intersection

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,294:::fn intersection[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], src : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
```

 Returns the intersection of two sets.

## is\_empty

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,325:::fn is_empty[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> Bool
```

 Returns if MutableSet is empty.

## iter

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,384:::fn iter[V](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[V]
```

 Returns a iterator.

## new

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,19:::fn new[V]() -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
```

 Construct a empty set.

## of

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,40:::fn of[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](array : <a href="moonbitlang/core/array#Array">Array</a>[V]) -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
```
 @alert deprecated "Use @sorted\_set.from\_array instead"

## range

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,451:::fn range[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], low : V, high : V) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[V]
```


## remove

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,116:::fn remove[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], value : V) -> Unit
```


## singleton

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,25:::fn singleton[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](value : V) -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
```

 Returns the one-value set containing only `value`.

## size

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,331:::fn size[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> Int
```

 Returns the number of elements in the MutableSet.

## subset

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,302:::fn subset[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], src : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> Bool
```

 Returns if a set is a subset of another set.

## to\_array

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,361:::fn to_array[V](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> <a href="moonbitlang/core/array#Array">Array</a>[V]
```

 Converts the set to an array.

## union

```moonbit
:::source,moonbitlang/core/sorted_set/set.mbt,153:::fn union[V : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/sorted_set#T">T</a>[V], src : <a href="moonbitlang/core/sorted_set#T">T</a>[V]) -> <a href="moonbitlang/core/sorted_set#T">T</a>[V]
```

 Returns the union of two sets.
