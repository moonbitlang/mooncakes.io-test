# Documentation
|Type|description|
|---|---|
|[T](#T)||

|Value|description|
|---|---|
|[from\_array](#from_array)||
|[is\_empty](#is_empty)||
|[iter](#iter)||
|[length](#length)||
|[new](#new)||
|[of](#of)||
|[peek](#peek)||
|[pop](#pop)||
|[pop\_exn](#pop_exn)||
|[push](#push)||
|[to\_array](#to_array)||
|[unsafe\_pop](#unsafe_pop)||

## T

```moonbit
:::source,moonbitlang/core/immut/priority_queue/types.mbt,16:::type T[A]
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,352:::impl[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,352:::fn op_equal[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A], other : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,357:::impl[A : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,357:::fn hash_combine[A : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A], hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,335:::impl[A : <a href="moonbitlang/core/builtin#Show">Show</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,335:::fn output[A : <a href="moonbitlang/core/builtin#Show">Show</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,344:::impl[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for <a href="moonbitlang/core/immut/priority_queue#T">T</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,344:::fn arbitrary[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](size : Int, rs : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> <a href="moonbitlang/core/immut/priority_queue#T">T</a>[X]
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### from\_array
  ```moonbit
  :::source,moonbitlang/core/immut/priority_queue/deprecated.mbt,25:::fn <a href="moonbitlang/core/immut/priority_queue#T">T</a>::from_array[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](arr : <a href="moonbitlang/core/array#Array">Array</a>[A]) -> <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]
  ```
  > 
- #### from\_iter
  ```moonbit
  :::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,78:::fn <a href="moonbitlang/core/immut/priority_queue#T">T</a>::from_iter[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]) -> <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]
  ```
  > 
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,308:::fn <a href="moonbitlang/core/immut/priority_queue#T">T</a>::is_empty[A](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]) -> Bool
  ```
  > 
  >  Checks if the immutable priority queue is empty.
  > 
  >  #### Example
  >  ```
  >  let queue = @priority_queue.new()
  >  assert_eq!(queue.is_empty(), true)
  >  assert_eq!(queue.push(1).is_empty(), false)
  >  ```
- #### iter
  ```moonbit
  :::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,64:::fn <a href="moonbitlang/core/immut/priority_queue#T">T</a>::iter[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
  ```
  > 
- #### length
  ```moonbit
  :::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,321:::fn <a href="moonbitlang/core/immut/priority_queue#T">T</a>::length[A](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]) -> Int
  ```
  > 
  >  Return the length of the immutable priority queue.
  > 
  >  #### Example
  >  ```
  >  let queue = @priority_queue.new()
  >  assert_eq!(queue.length(), 0)
  >  assert_eq!(queue.push(1).length(), 1)
  >  ```
- #### new
  ```moonbit
  :::source,moonbitlang/core/immut/priority_queue/deprecated.mbt,18:::fn <a href="moonbitlang/core/immut/priority_queue#T">T</a>::new[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>]() -> <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]
  ```
  > 
- #### of
  ```moonbit
  :::source,moonbitlang/core/immut/priority_queue/deprecated.mbt,32:::fn <a href="moonbitlang/core/immut/priority_queue#T">T</a>::of[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A]) -> <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]
  ```
  > 
- #### peek
  ```moonbit
  :::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,291:::fn <a href="moonbitlang/core/immut/priority_queue#T">T</a>::peek[A](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]) -> A?
  ```
  > 
  >  Peeks at the first value in the immutable priority queue, which returns None if the immutable priority queue is empty.
  > 
  >  #### Example
  >  ```
  >  let queue = @priority_queue.of([1, 2, 3, 4])
  >  assert_eq!(queue.peek(), Some(4))
  >  ```
- #### pop
  ```moonbit
  :::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,91:::fn <a href="moonbitlang/core/immut/priority_queue#T">T</a>::pop[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]) -> <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]?
  ```
  > 
  >  Pops the first value from the immutable priority queue, which returns None if the queue is empty.
  > 
  >  #### Example
  >  ```
  >  let queue = @priority_queue.of([1, 2, 3, 4])
  >  let first = queue.pop()
  >  assert_eq!(first, Some(@priority_queue.of([1, 2, 3])))
  >  ```
- #### pop\_exn
  ```moonbit
  :::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,213:::fn <a href="moonbitlang/core/immut/priority_queue#T">T</a>::pop_exn[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]) -> <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]
  ```
  > 
- #### push
  ```moonbit
  :::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,225:::fn <a href="moonbitlang/core/immut/priority_queue#T">T</a>::push[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A], value : A) -> <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]
  ```
  > 
  >  Adds a value to the immutable priority queue.
  > 
  >  #### Example
  >  ```
  >  let queue = @priority_queue.new()
  >  assert_eq!(queue.push(1).length(), 1)
  >  ```
- #### to\_array
  ```moonbit
  :::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,44:::fn <a href="moonbitlang/core/immut/priority_queue#T">T</a>::to_array[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]) -> <a href="moonbitlang/core/array#Array">Array</a>[A]
  ```
  > 
- #### unsafe\_pop
  ```moonbit
  :::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,198:::fn <a href="moonbitlang/core/immut/priority_queue#T">T</a>::unsafe_pop[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]) -> <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]
  ```
  > 
  >  Pops the first value from the immutable priority queue.
  > 
  >  @alert unsafe "Panics if the queue is empty."
  >  #### Example
  >  ```
  >  let queue = @priority_queue.of([1, 2, 3, 4])
  >  let first = queue.unsafe_pop()
  >  assert_eq!(first, @priority_queue.of([1, 2, 3]))
  >  ```

## from\_array

```moonbit
:::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,35:::fn from_array[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](array : <a href="moonbitlang/core/array#Array">Array</a>[A]) -> <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]
```

 Creates a new immutable priority queue from an array.

 #### Example
 ```
 let queue = @priority_queue.of([1, 2, 3, 4, 5])
 assert_eq!(queue.length(), 5)
 ```

## is\_empty

```moonbit
:::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,308:::fn is_empty[A](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]) -> Bool
```

 Checks if the immutable priority queue is empty.

 #### Example
 ```
 let queue = @priority_queue.new()
 assert_eq!(queue.is_empty(), true)
 assert_eq!(queue.push(1).is_empty(), false)
 ```

## iter

```moonbit
:::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,64:::fn iter[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
```


## length

```moonbit
:::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,321:::fn length[A](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]) -> Int
```

 Return the length of the immutable priority queue.

 #### Example
 ```
 let queue = @priority_queue.new()
 assert_eq!(queue.length(), 0)
 assert_eq!(queue.push(1).length(), 1)
 ```

## new

```moonbit
:::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,23:::fn new[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>]() -> <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]
```

 Creates a new empty immutable priority queue.

 #### Example
 ```
 let queue = @priority_queue.new()
 assert_eq!(queue.push(1).length(), 1)
 ```

## of

```moonbit
:::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,326:::fn of[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A]) -> <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]
```


## peek

```moonbit
:::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,291:::fn peek[A](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]) -> A?
```

 Peeks at the first value in the immutable priority queue, which returns None if the immutable priority queue is empty.

 #### Example
 ```
 let queue = @priority_queue.of([1, 2, 3, 4])
 assert_eq!(queue.peek(), Some(4))
 ```

## pop

```moonbit
:::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,91:::fn pop[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]) -> <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]?
```

 Pops the first value from the immutable priority queue, which returns None if the queue is empty.

 #### Example
 ```
 let queue = @priority_queue.of([1, 2, 3, 4])
 let first = queue.pop()
 assert_eq!(first, Some(@priority_queue.of([1, 2, 3])))
 ```

## pop\_exn

```moonbit
:::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,213:::fn pop_exn[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]) -> <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]
```


## push

```moonbit
:::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,225:::fn push[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A], value : A) -> <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]
```

 Adds a value to the immutable priority queue.

 #### Example
 ```
 let queue = @priority_queue.new()
 assert_eq!(queue.push(1).length(), 1)
 ```

## to\_array

```moonbit
:::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,44:::fn to_array[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]) -> <a href="moonbitlang/core/array#Array">Array</a>[A]
```


## unsafe\_pop

```moonbit
:::source,moonbitlang/core/immut/priority_queue/priority_queue.mbt,198:::fn unsafe_pop[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]) -> <a href="moonbitlang/core/immut/priority_queue#T">T</a>[A]
```

 Pops the first value from the immutable priority queue.

 @alert unsafe "Panics if the queue is empty."
 #### Example
 ```
 let queue = @priority_queue.of([1, 2, 3, 4])
 let first = queue.unsafe_pop()
 assert_eq!(first, @priority_queue.of([1, 2, 3]))
 ```
