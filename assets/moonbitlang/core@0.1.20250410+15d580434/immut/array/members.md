# Documentation
|Type|description|
|---|---|
|[T](#T)||

|Value|description|
|---|---|
|[concat](#concat)||
|[copy](#copy)||
|[each](#each)||
|[eachi](#eachi)||
|[fold](#fold)||
|[fold\_left](#fold_left)||
|[fold\_right](#fold_right)||
|[from\_array](#from_array)||
|[from\_iter](#from_iter)||
|[is\_empty](#is_empty)||
|[iter](#iter)||
|[length](#length)||
|[make](#make)||
|[makei](#makei)||
|[map](#map)||
|[new](#new)||
|[of](#of)||
|[op\_get](#op_get)||
|[push](#push)||
|[rev\_fold](#rev_fold)||
|[set](#set)||
|[to\_array](#to_array)||

## T

```moonbit
:::source,moonbitlang/core/immut/array/types.mbt,20:::type T[A]
```

 Invariants:
 - `shift` = tree height \* `num_bits`. When it is 0, we are at the leaf level.
 - `size` = the number of elements in the tree.
 - `shift` is not used when `tree` is `Empty`.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,191:::impl[A] <a href="moonbitlang/core/builtin#Add">Add</a> for <a href="moonbitlang/core/immut/array#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/array/array.mbt,191:::fn op_add[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], other : <a href="moonbitlang/core/immut/array#T">T</a>[A]) -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
    ```
    > 
    >  Concat two arrays.
- ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,317:::impl[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/immut/array#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/array/array.mbt,317:::fn op_equal[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], other : <a href="moonbitlang/core/immut/array#T">T</a>[A]) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,310:::impl[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>] <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="moonbitlang/core/immut/array#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/array/array.mbt,310:::fn hash_combine[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,322:::impl[A : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/immut/array#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/array/array.mbt,322:::fn output[A : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,302:::impl[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for <a href="moonbitlang/core/immut/array#T">T</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/array/array.mbt,302:::fn arbitrary[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>](size : Int, rs : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> <a href="moonbitlang/core/immut/array#T">T</a>[X]
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### concat
  ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,172:::fn <a href="moonbitlang/core/immut/array#T">T</a>::concat[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], other : <a href="moonbitlang/core/immut/array#T">T</a>[A]) -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
  ```
  > 
  >  Given two trees, concatenate them into a new tree.
- #### copy
  ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,50:::fn <a href="moonbitlang/core/immut/array#T">T</a>::copy[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A]) -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
  ```
  > 
  >  Physically copy the array.
  > Since it is an immutable data structure,
  > it is rarely the case that you would need this function.
  >  
- #### each
  ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,215:::fn <a href="moonbitlang/core/immut/array#T">T</a>::each[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], f : (A) -> Unit) -> Unit
  ```
  > 
  >  Iterate over the array.
  > 
  >  #### Example
  >  ```
  >  let arr = []
  >  let v = @array.of([1, 2, 3, 4, 5])
  >  v.each(fn(e) { arr.push(e) })
  >  assert_eq!(arr, [1, 2, 3, 4, 5])
  >  ```
- #### eachi
  ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,229:::fn <a href="moonbitlang/core/immut/array#T">T</a>::eachi[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], f : (Int, A) -> Unit) -> Unit
  ```
  > 
  >  Iterate over the array with index.
  > 
  >  #### Example
  >  ```
  >  let arr = []
  >  let v = @array.of([1, 2, 3, 4, 5])
  >  v.eachi(fn(i, e) { arr.push(i * e) })
  >  assert_eq!(arr, [0, 2, 6, 12, 20])
  >  ```
- #### fold
  ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,241:::fn <a href="moonbitlang/core/immut/array#T">T</a>::fold[A, B](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], init~ : B, f : (B, A) -> B) -> B
  ```
  > 
  >  Fold the array.
  > 
  >  #### Example
  >  ```
  >  let v = @array.of([1, 2, 3, 4, 5])
  >  assert_eq!(v.fold(fn(a, b) { a + b }, init=0), 15)
  >  ```
- #### fold\_left
  ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,267:::fn <a href="moonbitlang/core/immut/array#T">T</a>::fold_left[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], f : (A, A) -> A, init~ : A) -> A
  ```
  > 
  >  Fold the array from left to right.
  > 
  >  #### Example
  >  ```
  >  let v = @array.of([1, 2, 3, 4, 5])
  >  assert_eq!(v.fold(fn(a, b) { a + b }, init=0), 15)
  >  ```
- #### fold\_right
  ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,281:::fn <a href="moonbitlang/core/immut/array#T">T</a>::fold_right[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], f : (A, A) -> A, init~ : A) -> A
  ```
  > 
  >  Fold the array from right to left.
  > 
  >  #### Example
  >  ```
  >  let v = @array.of([1, 2, 3, 4, 5])
  >  assert_eq!(v.rev_fold(fn(a, b) { a + b }, init=0), 15)
  >  ```
- #### from\_array
  ```moonbit
  :::source,moonbitlang/core/immut/array/deprecated.mbt,32:::fn <a href="moonbitlang/core/immut/array#T">T</a>::from_array[A](arr : <a href="moonbitlang/core/array#Array">Array</a>[A]) -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
  ```
  > 
- #### from\_iter
  ```moonbit
  :::source,moonbitlang/core/immut/array/deprecated.mbt,25:::fn <a href="moonbitlang/core/immut/array#T">T</a>::from_iter[A](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]) -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
  ```
  > 
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,106:::fn <a href="moonbitlang/core/immut/array#T">T</a>::is_empty[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A]) -> Bool
  ```
  > 
- #### iter
  ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,201:::fn <a href="moonbitlang/core/immut/array#T">T</a>::iter[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
  ```
  > 
  >  Return an iterator over the array.
- #### length
  ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,111:::fn <a href="moonbitlang/core/immut/array#T">T</a>::length[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A]) -> Int
  ```
  > 
- #### make
  ```moonbit
  :::source,moonbitlang/core/immut/array/deprecated.mbt,39:::fn <a href="moonbitlang/core/immut/array#T">T</a>::make[A](len : Int, value : A) -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
  ```
  > 
- #### makei
  ```moonbit
  :::source,moonbitlang/core/immut/array/deprecated.mbt,46:::fn <a href="moonbitlang/core/immut/array#T">T</a>::makei[A](len : Int, f : (Int) -> A) -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
  ```
  > 
- #### map
  ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,293:::fn <a href="moonbitlang/core/immut/array#T">T</a>::map[A, B](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], f : (A) -> B) -> <a href="moonbitlang/core/immut/array#T">T</a>[B]
  ```
  > 
  >  Map a function over the array.
  > 
  >  #### Example
  >  ```
  >  let v = @array.of([1, 2, 3, 4, 5])
  >  assert_eq!(v.map(fn(e) { e * 2 }), @array.of([2, 4, 6, 8, 10]))
  >  ```
- #### new
  ```moonbit
  :::source,moonbitlang/core/immut/array/deprecated.mbt,18:::fn <a href="moonbitlang/core/immut/array#T">T</a>::new[A]() -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
  ```
  > 
- #### of
  ```moonbit
  :::source,moonbitlang/core/immut/array/deprecated.mbt,53:::fn <a href="moonbitlang/core/immut/array#T">T</a>::of[A](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A]) -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
  ```
  > 
- #### op\_get
  ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,127:::fn <a href="moonbitlang/core/immut/array#T">T</a>::op_get[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], index : Int) -> A
  ```
  > 
  >  Get a value at the given index.
  > 
  >  #### Examples
  >  ```
  >  let v = @array.of([1, 2, 3, 4, 5])
  >  assert_eq!(v[0], 1)
  >  ```
- #### push
  ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,165:::fn <a href="moonbitlang/core/immut/array#T">T</a>::push[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], value : A) -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
  ```
  > 
  >  Push a value to the end of the array.
  > 
  >  #### Example
  >  ```
  >  let v = @array.of([1, 2, 3])
  >  assert_eq!(v.push(4), @array.of([1, 2, 3, 4]))
  >  ```
- #### rev\_fold
  ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,253:::fn <a href="moonbitlang/core/immut/array#T">T</a>::rev_fold[A, B](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], init~ : B, f : (B, A) -> B) -> B
  ```
  > 
  >  Fold the array in reverse order.
  > 
  >  #### Example
  >  ```
  >  let v = @array.of([1, 2, 3, 4, 5])
  >  assert_eq!(v.rev_fold(fn(a, b) { a + b }, init=0), 15)
  >  ```
- #### set
  ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,149:::fn <a href="moonbitlang/core/immut/array#T">T</a>::set[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], index : Int, value : A) -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
  ```
  > 
  >  Set a value at the given index (immutable).
  > 
  >  #### Example
  >  ```
  >  let v = @array.of([1, 2, 3, 4, 5])
  >  assert_eq!(v.set(1, 10), @array.of([1, 10, 3, 4, 5]))
  >  ```
- #### to\_array
  ```moonbit
  :::source,moonbitlang/core/immut/array/array.mbt,91:::fn <a href="moonbitlang/core/immut/array#T">T</a>::to_array[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A]) -> <a href="moonbitlang/core/array#Array">Array</a>[A]
  ```
  > 

## concat

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,172:::fn concat[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], other : <a href="moonbitlang/core/immut/array#T">T</a>[A]) -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
```

 Given two trees, concatenate them into a new tree.

## copy

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,50:::fn copy[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A]) -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
```

 Physically copy the array.
Since it is an immutable data structure,
it is rarely the case that you would need this function.
 

## each

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,215:::fn each[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], f : (A) -> Unit) -> Unit
```

 Iterate over the array.

 #### Example
 ```
 let arr = []
 let v = @array.of([1, 2, 3, 4, 5])
 v.each(fn(e) { arr.push(e) })
 assert_eq!(arr, [1, 2, 3, 4, 5])
 ```

## eachi

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,229:::fn eachi[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], f : (Int, A) -> Unit) -> Unit
```

 Iterate over the array with index.

 #### Example
 ```
 let arr = []
 let v = @array.of([1, 2, 3, 4, 5])
 v.eachi(fn(i, e) { arr.push(i * e) })
 assert_eq!(arr, [0, 2, 6, 12, 20])
 ```

## fold

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,241:::fn fold[A, B](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], init~ : B, f : (B, A) -> B) -> B
```

 Fold the array.

 #### Example
 ```
 let v = @array.of([1, 2, 3, 4, 5])
 assert_eq!(v.fold(fn(a, b) { a + b }, init=0), 15)
 ```

## fold\_left

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,267:::fn fold_left[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], f : (A, A) -> A, init~ : A) -> A
```

 Fold the array from left to right.

 #### Example
 ```
 let v = @array.of([1, 2, 3, 4, 5])
 assert_eq!(v.fold(fn(a, b) { a + b }, init=0), 15)
 ```

## fold\_right

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,281:::fn fold_right[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], f : (A, A) -> A, init~ : A) -> A
```

 Fold the array from right to left.

 #### Example
 ```
 let v = @array.of([1, 2, 3, 4, 5])
 assert_eq!(v.rev_fold(fn(a, b) { a + b }, init=0), 15)
 ```

## from\_array

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,77:::fn from_array[A](arr : <a href="moonbitlang/core/array#Array">Array</a>[A]) -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
```

 Create a persistent array from an array.
 
 #### Example
 ```
 let v = @array.of([1, 2, 3])
 assert_eq!(v, @array.from_array([1, 2, 3]))
 ```

## from\_iter

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,82:::fn from_iter[A](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]) -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
```


## is\_empty

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,106:::fn is_empty[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A]) -> Bool
```


## iter

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,201:::fn iter[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
```

 Return an iterator over the array.

## length

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,111:::fn length[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A]) -> Int
```


## make

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,27:::fn make[A](len : Int, value : A) -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
```

 Create a persistent array with a given length and value.

## makei

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,33:::fn makei[A](len : Int, f : (Int) -> A) -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
```

 Create a persistent array with a given length and a function to generate values.

## map

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,293:::fn map[A, B](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], f : (A) -> B) -> <a href="moonbitlang/core/immut/array#T">T</a>[B]
```

 Map a function over the array.

 #### Example
 ```
 let v = @array.of([1, 2, 3, 4, 5])
 assert_eq!(v.map(fn(e) { e * 2 }), @array.of([2, 4, 6, 8, 10]))
 ```

## new

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,21:::fn new[A]() -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
```

 Return a new empty array

## of

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,39:::fn of[A](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A]) -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
```

 Convert a FixedArray to an @immut/array.

## op\_get

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,127:::fn op_get[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], index : Int) -> A
```

 Get a value at the given index.

 #### Examples
 ```
 let v = @array.of([1, 2, 3, 4, 5])
 assert_eq!(v[0], 1)
 ```

## push

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,165:::fn push[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], value : A) -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
```

 Push a value to the end of the array.

 #### Example
 ```
 let v = @array.of([1, 2, 3])
 assert_eq!(v.push(4), @array.of([1, 2, 3, 4]))
 ```

## rev\_fold

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,253:::fn rev_fold[A, B](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], init~ : B, f : (B, A) -> B) -> B
```

 Fold the array in reverse order.

 #### Example
 ```
 let v = @array.of([1, 2, 3, 4, 5])
 assert_eq!(v.rev_fold(fn(a, b) { a + b }, init=0), 15)
 ```

## set

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,149:::fn set[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A], index : Int, value : A) -> <a href="moonbitlang/core/immut/array#T">T</a>[A]
```

 Set a value at the given index (immutable).

 #### Example
 ```
 let v = @array.of([1, 2, 3, 4, 5])
 assert_eq!(v.set(1, 10), @array.of([1, 10, 3, 4, 5]))
 ```

## to\_array

```moonbit
:::source,moonbitlang/core/immut/array/array.mbt,91:::fn to_array[A](self : <a href="moonbitlang/core/immut/array#T">T</a>[A]) -> <a href="moonbitlang/core/array#Array">Array</a>[A]
```

