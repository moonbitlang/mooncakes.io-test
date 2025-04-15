# Documentation
|Type|description|
|---|---|
|[T](#T)||

|Value|description|
|---|---|
|[add](#add)||
|[contains](#contains)||
|[each](#each)||
|[from\_array](#from_array)||
|[from\_iter](#from_iter)||
|[is\_empty](#is_empty)||
|[iter](#iter)||
|[new](#new)||
|[of](#of)||
|[remove](#remove)||
|[size](#size)||
|[union](#union)||

## T

```moonbit
:::source,moonbitlang/core/immut/hashset/types.mbt,25:::type T[A]
```

 An immutable hash set data structure

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/immut/hashset/HAMT.mbt,261:::impl[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/immut/hashset#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/hashset/HAMT.mbt,261:::fn op_equal[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/hashset#T">T</a>[A], other : <a href="moonbitlang/core/immut/hashset#T">T</a>[A]) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/hashset/HAMT.mbt,256:::impl[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>] <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="moonbitlang/core/immut/hashset#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/hashset/HAMT.mbt,256:::fn hash_combine[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : <a href="moonbitlang/core/immut/hashset#T">T</a>[A], hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/hashset/HAMT.mbt,229:::impl[A : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/immut/hashset#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/hashset/HAMT.mbt,229:::fn output[A : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/immut/hashset#T">T</a>[A], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/hashset/HAMT.mbt,273:::impl[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for <a href="moonbitlang/core/immut/hashset#T">T</a>[K]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/hashset/HAMT.mbt,273:::fn arbitrary[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>](size : Int, rs : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> <a href="moonbitlang/core/immut/hashset#T">T</a>[K]
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### add
  ```moonbit
  :::source,moonbitlang/core/immut/hashset/HAMT.mbt,115:::fn <a href="moonbitlang/core/immut/hashset#T">T</a>::add[A : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : <a href="moonbitlang/core/immut/hashset#T">T</a>[A], key : A) -> <a href="moonbitlang/core/immut/hashset#T">T</a>[A]
  ```
  > 
  >  Add a key to the hashset.
- #### contains
  ```moonbit
  :::source,moonbitlang/core/immut/hashset/HAMT.mbt,44:::fn <a href="moonbitlang/core/immut/hashset#T">T</a>::contains[A : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : <a href="moonbitlang/core/immut/hashset#T">T</a>[A], key : A) -> Bool
  ```
  > 
  >  Lookup a value from the hash set
- #### each
  ```moonbit
  :::source,moonbitlang/core/immut/hashset/HAMT.mbt,203:::fn <a href="moonbitlang/core/immut/hashset#T">T</a>::each[A](self : <a href="moonbitlang/core/immut/hashset#T">T</a>[A], f : (A) -> Unit) -> Unit
  ```
  > 
  >  Iterate through the elements in a hash set
- #### from\_array
  ```moonbit
  :::source,moonbitlang/core/immut/hashset/deprecated.mbt,32:::fn <a href="moonbitlang/core/immut/hashset#T">T</a>::from_array[A : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>](arr : <a href="moonbitlang/core/array#Array">Array</a>[A]) -> <a href="moonbitlang/core/immut/hashset#T">T</a>[A]
  ```
  > 
- #### from\_iter
  ```moonbit
  :::source,moonbitlang/core/immut/hashset/deprecated.mbt,25:::fn <a href="moonbitlang/core/immut/hashset#T">T</a>::from_iter[A : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]) -> <a href="moonbitlang/core/immut/hashset#T">T</a>[A]
  ```
  > 
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/immut/hashset/HAMT.mbt,197:::fn <a href="moonbitlang/core/immut/hashset#T">T</a>::is_empty[A](self : <a href="moonbitlang/core/immut/hashset#T">T</a>[A]) -> Bool
  ```
  > 
  >  Returns true if the hash set is empty.
- #### iter
  ```moonbit
  :::source,moonbitlang/core/immut/hashset/HAMT.mbt,214:::fn <a href="moonbitlang/core/immut/hashset#T">T</a>::iter[A](self : <a href="moonbitlang/core/immut/hashset#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
  ```
  > 
  >  Converted to Iter
- #### new
  ```moonbit
  :::source,moonbitlang/core/immut/hashset/deprecated.mbt,18:::fn <a href="moonbitlang/core/immut/hashset#T">T</a>::new[A]() -> <a href="moonbitlang/core/immut/hashset#T">T</a>[A]
  ```
  > 
- #### of
  ```moonbit
  :::source,moonbitlang/core/immut/hashset/deprecated.mbt,39:::fn <a href="moonbitlang/core/immut/hashset#T">T</a>::of[A : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A]) -> <a href="moonbitlang/core/immut/hashset#T">T</a>[A]
  ```
  > 
- #### remove
  ```moonbit
  :::source,moonbitlang/core/immut/hashset/HAMT.mbt,121:::fn <a href="moonbitlang/core/immut/hashset#T">T</a>::remove[A : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : <a href="moonbitlang/core/immut/hashset#T">T</a>[A], key : A) -> <a href="moonbitlang/core/immut/hashset#T">T</a>[A]
  ```
  > 
  >  Remove an element from a set
- #### size
  ```moonbit
  :::source,moonbitlang/core/immut/hashset/HAMT.mbt,165:::fn <a href="moonbitlang/core/immut/hashset#T">T</a>::size[A](self : <a href="moonbitlang/core/immut/hashset#T">T</a>[A]) -> Int
  ```
  > 
  >  Calculate the size of a set.
  > 
  >  WARNING: this operation is `O(N)` in set size
- #### union
  ```moonbit
  :::source,moonbitlang/core/immut/hashset/HAMT.mbt,183:::fn <a href="moonbitlang/core/immut/hashset#T">T</a>::union[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : <a href="moonbitlang/core/immut/hashset#T">T</a>[K], other : <a href="moonbitlang/core/immut/hashset#T">T</a>[K]) -> <a href="moonbitlang/core/immut/hashset#T">T</a>[K]
  ```
  > 
  >  Union two hashsets

## add

```moonbit
:::source,moonbitlang/core/immut/hashset/HAMT.mbt,115:::fn add[A : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : <a href="moonbitlang/core/immut/hashset#T">T</a>[A], key : A) -> <a href="moonbitlang/core/immut/hashset#T">T</a>[A]
```

 Add a key to the hashset.

## contains

```moonbit
:::source,moonbitlang/core/immut/hashset/HAMT.mbt,44:::fn contains[A : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : <a href="moonbitlang/core/immut/hashset#T">T</a>[A], key : A) -> Bool
```

 Lookup a value from the hash set

## each

```moonbit
:::source,moonbitlang/core/immut/hashset/HAMT.mbt,203:::fn each[A](self : <a href="moonbitlang/core/immut/hashset#T">T</a>[A], f : (A) -> Unit) -> Unit
```

 Iterate through the elements in a hash set

## from\_array

```moonbit
:::source,moonbitlang/core/immut/hashset/HAMT.mbt,234:::fn from_array[A : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>](arr : <a href="moonbitlang/core/array#Array">Array</a>[A]) -> <a href="moonbitlang/core/immut/hashset#T">T</a>[A]
```


## from\_iter

```moonbit
:::source,moonbitlang/core/immut/hashset/HAMT.mbt,224:::fn from_iter[A : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]) -> <a href="moonbitlang/core/immut/hashset#T">T</a>[A]
```


## is\_empty

```moonbit
:::source,moonbitlang/core/immut/hashset/HAMT.mbt,197:::fn is_empty[A](self : <a href="moonbitlang/core/immut/hashset#T">T</a>[A]) -> Bool
```

 Returns true if the hash set is empty.

## iter

```moonbit
:::source,moonbitlang/core/immut/hashset/HAMT.mbt,214:::fn iter[A](self : <a href="moonbitlang/core/immut/hashset#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
```

 Converted to Iter

## new

```moonbit
:::source,moonbitlang/core/immut/hashset/HAMT.mbt,38:::fn new[A]() -> <a href="moonbitlang/core/immut/hashset#T">T</a>[A]
```


## of

```moonbit
:::source,moonbitlang/core/immut/hashset/HAMT.mbt,245:::fn of[A : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A]) -> <a href="moonbitlang/core/immut/hashset#T">T</a>[A]
```


## remove

```moonbit
:::source,moonbitlang/core/immut/hashset/HAMT.mbt,121:::fn remove[A : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : <a href="moonbitlang/core/immut/hashset#T">T</a>[A], key : A) -> <a href="moonbitlang/core/immut/hashset#T">T</a>[A]
```

 Remove an element from a set

## size

```moonbit
:::source,moonbitlang/core/immut/hashset/HAMT.mbt,165:::fn size[A](self : <a href="moonbitlang/core/immut/hashset#T">T</a>[A]) -> Int
```

 Calculate the size of a set.

 WARNING: this operation is `O(N)` in set size

## union

```moonbit
:::source,moonbitlang/core/immut/hashset/HAMT.mbt,183:::fn union[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : <a href="moonbitlang/core/immut/hashset#T">T</a>[K], other : <a href="moonbitlang/core/immut/hashset#T">T</a>[K]) -> <a href="moonbitlang/core/immut/hashset#T">T</a>[K]
```

 Union two hashsets
