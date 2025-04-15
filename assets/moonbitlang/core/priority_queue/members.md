# Documentation
|Type|description|
|---|---|
|[T](#T)||

|Value|description|
|---|---|
|[clear](#clear)||
|[copy](#copy)||
|[from\_array](#from_array)||
|[from\_iter](#from_iter)||
|[is\_empty](#is_empty)||
|[iter](#iter)||
|[length](#length)||
|[new](#new)||
|[of](#of)||
|[peek](#peek)||
|[pop](#pop)||
|[push](#push)||
|[to\_array](#to_array)||
|[unsafe\_pop](#unsafe_pop)||

## T

```moonbit
:::source,moonbitlang/core/priority_queue/types.mbt,22:::type T[A]
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/priority_queue/priority_queue.mbt,271:::impl[A : <a href="moonbitlang/core/builtin#Show">Show</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/priority_queue#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/priority_queue/priority_queue.mbt,271:::fn output[A : <a href="moonbitlang/core/builtin#Show">Show</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/priority_queue/priority_queue.mbt,276:::impl[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for <a href="moonbitlang/core/priority_queue#T">T</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/priority_queue/priority_queue.mbt,276:::fn arbitrary[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](size : Int, rs : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> <a href="moonbitlang/core/priority_queue#T">T</a>[X]
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### clear
  ```moonbit
  :::source,moonbitlang/core/priority_queue/priority_queue.mbt,229:::fn <a href="moonbitlang/core/priority_queue#T">T</a>::clear[A](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A]) -> Unit
  ```
  > 
  >  Clears the queue.
  > 
  >  #### Example
  >  ```
  >  let queue = @priority_queue.of([1, 2, 3, 4])
  >  queue.clear()
  >  assert_eq!(queue.length(), 0)
  >  ```
- #### copy
  ```moonbit
  :::source,moonbitlang/core/priority_queue/priority_queue.mbt,69:::fn <a href="moonbitlang/core/priority_queue#T">T</a>::copy[A](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A]) -> <a href="moonbitlang/core/priority_queue#T">T</a>[A]
  ```
  > 
  >  Return a copy of the queue.
  > 
  >  #### Example
  >  ```
  >  let queue = @priority_queue.of([1, 2, 3, 4])
  >  let queue2 = @priority_queue.copy(queue)
  >  assert_eq!(queue2.length(), 4)
  >  ```
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/priority_queue/priority_queue.mbt,242:::fn <a href="moonbitlang/core/priority_queue#T">T</a>::is_empty[A](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A]) -> Bool
  ```
  > 
  >  Checks if the priority queue is empty.
  > 
  >  #### Example
  >  ```
  >  let queue : @priority_queue.T[Int] = @priority_queue.new()
  >  assert_eq!(queue.is_empty(), true)
  >  ```
- #### iter
  ```moonbit
  :::source,moonbitlang/core/priority_queue/priority_queue.mbt,94:::fn <a href="moonbitlang/core/priority_queue#T">T</a>::iter[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
  ```
  > 
- #### length
  ```moonbit
  :::source,moonbitlang/core/priority_queue/priority_queue.mbt,146:::fn <a href="moonbitlang/core/priority_queue#T">T</a>::length[A](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A]) -> Int
  ```
  > 
- #### peek
  ```moonbit
  :::source,moonbitlang/core/priority_queue/priority_queue.mbt,213:::fn <a href="moonbitlang/core/priority_queue#T">T</a>::peek[A](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A]) -> A?
  ```
  > 
  >  Peeks at the first value in the priority queue, which returns None if the priority queue is empty.
  > 
  >  #### Example
  >  ```
  >  let queue = @priority_queue.of([1, 2, 3, 4])
  >  let first = queue.peek() // Some(4)
  >  assert_eq!(first, Some(4))
  >  ```
- #### pop
  ```moonbit
  :::source,moonbitlang/core/priority_queue/priority_queue.mbt,178:::fn <a href="moonbitlang/core/priority_queue#T">T</a>::pop[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A]) -> A?
  ```
  > 
  >  Pops the first value from the priority queue, which returns None if the queue is empty.
  > 
  >  #### Example
  >  ```
  >  let queue = @priority_queue.of([1, 2, 3, 4])
  >  let first = queue.pop() // Some(4)
  >  assert_eq!(first, Some(4))
  >  assert_eq!(queue.length(), 3)
  >  ```
- #### push
  ```moonbit
  :::source,moonbitlang/core/priority_queue/priority_queue.mbt,199:::fn <a href="moonbitlang/core/priority_queue#T">T</a>::push[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A], value : A) -> Unit
  ```
  > 
  >  Adds a value to the priority queue.
  > 
  >  #### Example
  >  ```
  >  let queue = @priority_queue.new()
  >  queue.push(1)
  >  assert_eq!(queue.length(), 1)
  >  ```
- #### to\_array
  ```moonbit
  :::source,moonbitlang/core/priority_queue/priority_queue.mbt,75:::fn <a href="moonbitlang/core/priority_queue#T">T</a>::to_array[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A]) -> <a href="moonbitlang/core/array#Array">Array</a>[A]
  ```
  > 
- #### unsafe\_pop
  ```moonbit
  :::source,moonbitlang/core/priority_queue/priority_queue.mbt,160:::fn <a href="moonbitlang/core/priority_queue#T">T</a>::unsafe_pop[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A]) -> Unit
  ```
  > 
  >  Pops the first value from the priority queue.
  > 
  >  #### Example
  >  ```
  >  let queue = @priority_queue.of([1, 2, 3, 4])
  >  queue.unsafe_pop()
  >  assert_eq!(queue.length(), 3)
  >  ```
  >  @alert unsafe "Panic if the queue is empty."

## clear

```moonbit
:::source,moonbitlang/core/priority_queue/priority_queue.mbt,229:::fn clear[A](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A]) -> Unit
```

 Clears the queue.

 #### Example
 ```
 let queue = @priority_queue.of([1, 2, 3, 4])
 queue.clear()
 assert_eq!(queue.length(), 0)
 ```

## copy

```moonbit
:::source,moonbitlang/core/priority_queue/priority_queue.mbt,69:::fn copy[A](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A]) -> <a href="moonbitlang/core/priority_queue#T">T</a>[A]
```

 Return a copy of the queue.

 #### Example
 ```
 let queue = @priority_queue.of([1, 2, 3, 4])
 let queue2 = @priority_queue.copy(queue)
 assert_eq!(queue2.length(), 4)
 ```

## from\_array

```moonbit
:::source,moonbitlang/core/priority_queue/priority_queue.mbt,35:::fn from_array[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](arr : <a href="moonbitlang/core/array#Array">Array</a>[A]) -> <a href="moonbitlang/core/priority_queue#T">T</a>[A]
```

 Creates a new priority queue from an array.

 #### Example
 ```
 let queue = @priority_queue.of([1, 2, 3, 4, 5])
 assert_eq!(queue.length(), 5)
 ```

## from\_iter

```moonbit
:::source,moonbitlang/core/priority_queue/priority_queue.mbt,108:::fn from_iter[K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[K]) -> <a href="moonbitlang/core/priority_queue#T">T</a>[K]
```


## is\_empty

```moonbit
:::source,moonbitlang/core/priority_queue/priority_queue.mbt,242:::fn is_empty[A](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A]) -> Bool
```

 Checks if the priority queue is empty.

 #### Example
 ```
 let queue : @priority_queue.T[Int] = @priority_queue.new()
 assert_eq!(queue.is_empty(), true)
 ```

## iter

```moonbit
:::source,moonbitlang/core/priority_queue/priority_queue.mbt,94:::fn iter[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
```


## length

```moonbit
:::source,moonbitlang/core/priority_queue/priority_queue.mbt,146:::fn length[A](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A]) -> Int
```


## new

```moonbit
:::source,moonbitlang/core/priority_queue/priority_queue.mbt,23:::fn new[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>]() -> <a href="moonbitlang/core/priority_queue#T">T</a>[A]
```

 Creates a new empty priority queue.

 #### Example
 ```
 let queue : @priority_queue.T[Int] = @priority_queue.new()
 assert_eq!(queue.length(), 0)
 ```

## of

```moonbit
:::source,moonbitlang/core/priority_queue/priority_queue.mbt,247:::fn of[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A]) -> <a href="moonbitlang/core/priority_queue#T">T</a>[A]
```


## peek

```moonbit
:::source,moonbitlang/core/priority_queue/priority_queue.mbt,213:::fn peek[A](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A]) -> A?
```

 Peeks at the first value in the priority queue, which returns None if the priority queue is empty.

 #### Example
 ```
 let queue = @priority_queue.of([1, 2, 3, 4])
 let first = queue.peek() // Some(4)
 assert_eq!(first, Some(4))
 ```

## pop

```moonbit
:::source,moonbitlang/core/priority_queue/priority_queue.mbt,178:::fn pop[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A]) -> A?
```

 Pops the first value from the priority queue, which returns None if the queue is empty.

 #### Example
 ```
 let queue = @priority_queue.of([1, 2, 3, 4])
 let first = queue.pop() // Some(4)
 assert_eq!(first, Some(4))
 assert_eq!(queue.length(), 3)
 ```

## push

```moonbit
:::source,moonbitlang/core/priority_queue/priority_queue.mbt,199:::fn push[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A], value : A) -> Unit
```

 Adds a value to the priority queue.

 #### Example
 ```
 let queue = @priority_queue.new()
 queue.push(1)
 assert_eq!(queue.length(), 1)
 ```

## to\_array

```moonbit
:::source,moonbitlang/core/priority_queue/priority_queue.mbt,75:::fn to_array[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A]) -> <a href="moonbitlang/core/array#Array">Array</a>[A]
```


## unsafe\_pop

```moonbit
:::source,moonbitlang/core/priority_queue/priority_queue.mbt,160:::fn unsafe_pop[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/priority_queue#T">T</a>[A]) -> Unit
```

 Pops the first value from the priority queue.

 #### Example
 ```
 let queue = @priority_queue.of([1, 2, 3, 4])
 queue.unsafe_pop()
 assert_eq!(queue.length(), 3)
 ```
 @alert unsafe "Panic if the queue is empty."
