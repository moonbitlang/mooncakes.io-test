# Documentation
|Type|description|
|---|---|
|[T](#T)||

|Value|description|
|---|---|
|[clear](#clear)||
|[copy](#copy)||
|[each](#each)||
|[eachi](#eachi)||
|[fold](#fold)||
|[from\_array](#from_array)||
|[from\_iter](#from_iter)||
|[is\_empty](#is_empty)||
|[iter](#iter)||
|[length](#length)||
|[new](#new)||
|[of](#of)||
|[peek](#peek)||
|[peek\_exn](#peek_exn)||
|[pop](#pop)||
|[pop\_exn](#pop_exn)||
|[push](#push)||
|[transfer](#transfer)||
|[unsafe\_peek](#unsafe_peek)||
|[unsafe\_pop](#unsafe_pop)||

## T

```moonbit
:::source,moonbitlang/core/queue/types.mbt,28:::type T[A]
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/queue/queue.mbt,51:::impl[A : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/queue#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/queue/queue.mbt,51:::fn output[A : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/queue#T">T</a>[A], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/queue/queue.mbt,465:::impl[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for <a href="moonbitlang/core/queue#T">T</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/queue/queue.mbt,465:::fn arbitrary[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>](size : Int, rs : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> <a href="moonbitlang/core/queue#T">T</a>[X]
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### clear
  ```moonbit
  :::source,moonbitlang/core/queue/queue.mbt,84:::fn <a href="moonbitlang/core/queue#T">T</a>::clear[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> Unit
  ```
  > 
  >  Clears the queue.
  > 
  >  #### Example
  >  ```
  >  let queue : @queue.T[Int] = @queue.of([1, 2, 3, 4])
  >  queue.clear()
  >  ```
- #### copy
  ```moonbit
  :::source,moonbitlang/core/queue/queue.mbt,286:::fn <a href="moonbitlang/core/queue#T">T</a>::copy[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> <a href="moonbitlang/core/queue#T">T</a>[A]
  ```
  > 
  >  Returns a copy of the queue.
  > 
  >  #### Example
  >  ```
  >  let queue : @queue.T[Int] = @queue.of([1, 2, 3, 4])
  >  let queue2 : @queue.T[Int] = queue.copy()
  >  assert_eq!(queue2.length(), 4)
  >  ```
- #### each
  ```moonbit
  :::source,moonbitlang/core/queue/queue.mbt,232:::fn <a href="moonbitlang/core/queue#T">T</a>::each[A](self : <a href="moonbitlang/core/queue#T">T</a>[A], f : (A) -> Unit) -> Unit
  ```
  > 
  >  Iterates over the queue.
  > 
  >  #### Example
  >  ```
  >  let queue : @queue.T[Int] = @queue.of([1, 2, 3, 4])
  >  let mut sum = 0
  >  queue.each(fn(x) { sum = sum + x })
  >  ```
- #### eachi
  ```moonbit
  :::source,moonbitlang/core/queue/queue.mbt,251:::fn <a href="moonbitlang/core/queue#T">T</a>::eachi[A](self : <a href="moonbitlang/core/queue#T">T</a>[A], f : (Int, A) -> Unit) -> Unit
  ```
  > 
  >  Iterates over the queue with index.
  > 
  >  #### Example
  >  ```
  >  let queue : @queue.T[Int] = @queue.of([1, 2, 3, 4])
  >  let mut sum = 0
  >  queue.eachi(fn(x, i) { sum = sum + x * i })
  >  ```
- #### fold
  ```moonbit
  :::source,moonbitlang/core/queue/queue.mbt,270:::fn <a href="moonbitlang/core/queue#T">T</a>::fold[A, B](self : <a href="moonbitlang/core/queue#T">T</a>[A], init~ : B, f : (B, A) -> B) -> B
  ```
  > 
  >  Folds over the queue.
  > 
  >  #### Example
  >  ```
  >  let queue : @queue.T[Int] = @queue.new()
  >  let sum = queue.fold(init=0, fn(acc, x) { acc + x })
  >  assert_eq!(sum, 0)
  >  ```
- #### from\_array
  ```moonbit
  :::source,moonbitlang/core/queue/deprecated.mbt,25:::fn <a href="moonbitlang/core/queue#T">T</a>::from_array[A](arr : <a href="moonbitlang/core/array#Array">Array</a>[A]) -> <a href="moonbitlang/core/queue#T">T</a>[A]
  ```
  > 
- #### from\_iter
  ```moonbit
  :::source,moonbitlang/core/queue/deprecated.mbt,32:::fn <a href="moonbitlang/core/queue#T">T</a>::from_iter[A](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]) -> <a href="moonbitlang/core/queue#T">T</a>[A]
  ```
  > 
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/queue/queue.mbt,110:::fn <a href="moonbitlang/core/queue#T">T</a>::is_empty[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> Bool
  ```
  > 
  >  Checks if the queue is empty.
  > 
  >  #### Example
  >  ```
  >  let queue : @queue.T[Int] = @queue.new()
  >  assert_true!(queue.is_empty())
  >  ```
- #### iter
  ```moonbit
  :::source,moonbitlang/core/queue/queue.mbt,348:::fn <a href="moonbitlang/core/queue#T">T</a>::iter[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
  ```
  > 
  >  Creates an iter from the queue.
  > 
  >  #### Example
  >  ```
  >  let queue : @queue.T[Int] = @queue.of([5, 6, 7, 8])
  >  let sum = queue.iter().fold(fn(x, y) { x + y }, init=0)
  >  assert_eq!(sum, 26)
  >  ```
- #### length
  ```moonbit
  :::source,moonbitlang/core/queue/queue.mbt,98:::fn <a href="moonbitlang/core/queue#T">T</a>::length[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> Int
  ```
  > 
  >  Get the length of the queue.
  > 
  >  #### Example
  >  ```
  >  let queue : @queue.T[Int] = @queue.new()
  >  assert_eq!(queue.length(), 0)
  >  ```
- #### new
  ```moonbit
  :::source,moonbitlang/core/queue/deprecated.mbt,18:::fn <a href="moonbitlang/core/queue#T">T</a>::new[A]() -> <a href="moonbitlang/core/queue#T">T</a>[A]
  ```
  > 
- #### of
  ```moonbit
  :::source,moonbitlang/core/queue/deprecated.mbt,39:::fn <a href="moonbitlang/core/queue#T">T</a>::of[A](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A]) -> <a href="moonbitlang/core/queue#T">T</a>[A]
  ```
  > 
- #### peek
  ```moonbit
  :::source,moonbitlang/core/queue/queue.mbt,169:::fn <a href="moonbitlang/core/queue#T">T</a>::peek[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> A?
  ```
  > 
  >  Peeks at the first value in the queue, which returns None if the queue is empty.
  > 
  >  #### Example
  >  ```
  >  let queue : @queue.T[Int] = @queue.of([1, 2, 3, 4])
  >  assert_eq!(queue.peek(), Some(1))
  >  ```
- #### peek\_exn
  ```moonbit
  :::source,moonbitlang/core/queue/queue.mbt,157:::fn <a href="moonbitlang/core/queue#T">T</a>::peek_exn[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> A
  ```
  > 
- #### pop
  ```moonbit
  :::source,moonbitlang/core/queue/queue.mbt,215:::fn <a href="moonbitlang/core/queue#T">T</a>::pop[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> A?
  ```
  > 
  >  Pops the first value from the queue, which returns None if the queue is empty.
  > 
  >  #### Example
  >  ```
  >  let queue : @queue.T[Int] = @queue.of([1, 2, 3, 4])
  >  assert_eq!(queue.pop(), Some(1))
  >  ```
- #### pop\_exn
  ```moonbit
  :::source,moonbitlang/core/queue/queue.mbt,203:::fn <a href="moonbitlang/core/queue#T">T</a>::pop_exn[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> A
  ```
  > 
- #### push
  ```moonbit
  :::source,moonbitlang/core/queue/queue.mbt,122:::fn <a href="moonbitlang/core/queue#T">T</a>::push[A](self : <a href="moonbitlang/core/queue#T">T</a>[A], x : A) -> Unit
  ```
  > 
  >  Adds a value to the queue.
  > 
  >  #### Example
  >  ```
  >  let queue : @queue.T[Int] = @queue.new()
  >  queue.push(1)
  >  ```
- #### transfer
  ```moonbit
  :::source,moonbitlang/core/queue/queue.mbt,320:::fn <a href="moonbitlang/core/queue#T">T</a>::transfer[A](self : <a href="moonbitlang/core/queue#T">T</a>[A], dst : <a href="moonbitlang/core/queue#T">T</a>[A]) -> Unit
  ```
  > 
  >  Transfers all elements from one queue to another.
  > 
  >  Adds all of the elements of source to the end of destination, then clears source.
  > 
  >  #### Example
  >  ```
  >  let dst : @queue.T[Int] = @queue.new()
  >  let src : @queue.T[Int] = @queue.of([5, 6, 7, 8])
  >  src.transfer(dst)
  >  ```
- #### unsafe\_peek
  ```moonbit
  :::source,moonbitlang/core/queue/queue.mbt,147:::fn <a href="moonbitlang/core/queue#T">T</a>::unsafe_peek[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> A
  ```
  > 
  >  Peeks at the first value in the queue.
  > 
  >  #### Example
  >  ```
  >  let queue : @queue.T[Int] = @queue.of([1, 2, 3, 4])
  >  assert_eq!(queue.unsafe_peek(), 1)
  >  ```
  >  @alert unsafe "Panics if the queue is empty."
- #### unsafe\_pop
  ```moonbit
  :::source,moonbitlang/core/queue/queue.mbt,185:::fn <a href="moonbitlang/core/queue#T">T</a>::unsafe_pop[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> A
  ```
  > 
  >  Pops the first value from the queue.
  > 
  >  #### Example
  >  ```
  >  let queue : @queue.T[Int] = @queue.of([1, 2, 3, 4])
  >  assert_eq!(queue.unsafe_pop(), 1)
  >  ```
  >  @alert unsafe "Panics if the queue is empty."

## clear

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,84:::fn clear[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> Unit
```

 Clears the queue.

 #### Example
 ```
 let queue : @queue.T[Int] = @queue.of([1, 2, 3, 4])
 queue.clear()
 ```

## copy

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,286:::fn copy[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> <a href="moonbitlang/core/queue#T">T</a>[A]
```

 Returns a copy of the queue.

 #### Example
 ```
 let queue : @queue.T[Int] = @queue.of([1, 2, 3, 4])
 let queue2 : @queue.T[Int] = queue.copy()
 assert_eq!(queue2.length(), 4)
 ```

## each

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,232:::fn each[A](self : <a href="moonbitlang/core/queue#T">T</a>[A], f : (A) -> Unit) -> Unit
```

 Iterates over the queue.

 #### Example
 ```
 let queue : @queue.T[Int] = @queue.of([1, 2, 3, 4])
 let mut sum = 0
 queue.each(fn(x) { sum = sum + x })
 ```

## eachi

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,251:::fn eachi[A](self : <a href="moonbitlang/core/queue#T">T</a>[A], f : (Int, A) -> Unit) -> Unit
```

 Iterates over the queue with index.

 #### Example
 ```
 let queue : @queue.T[Int] = @queue.of([1, 2, 3, 4])
 let mut sum = 0
 queue.eachi(fn(x, i) { sum = sum + x * i })
 ```

## fold

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,270:::fn fold[A, B](self : <a href="moonbitlang/core/queue#T">T</a>[A], init~ : B, f : (B, A) -> B) -> B
```

 Folds over the queue.

 #### Example
 ```
 let queue : @queue.T[Int] = @queue.new()
 let sum = queue.fold(init=0, fn(acc, x) { acc + x })
 assert_eq!(sum, 0)
 ```

## from\_array

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,36:::fn from_array[A](arr : <a href="moonbitlang/core/array#Array">Array</a>[A]) -> <a href="moonbitlang/core/queue#T">T</a>[A]
```

 Creates a new queue from an array.

 #### Example
 ```
 let array = Array::makei(3, fn(idx) { idx + 1 })
 let queue : @queue.T[Int] = @queue.from_array(array)
 assert_eq!(queue.length(), 3)
 ```

## from\_iter

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,370:::fn from_iter[A](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]) -> <a href="moonbitlang/core/queue#T">T</a>[A]
```

 Creates a new queue from an iter.

 #### Example
 ```
 let queue : @queue.T[Int] = @queue.from_iter(Iter::empty())
 assert_eq!(queue.length(), 0)
 ```

## is\_empty

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,110:::fn is_empty[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> Bool
```

 Checks if the queue is empty.

 #### Example
 ```
 let queue : @queue.T[Int] = @queue.new()
 assert_true!(queue.is_empty())
 ```

## iter

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,348:::fn iter[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
```

 Creates an iter from the queue.

 #### Example
 ```
 let queue : @queue.T[Int] = @queue.of([5, 6, 7, 8])
 let sum = queue.iter().fold(fn(x, y) { x + y }, init=0)
 assert_eq!(sum, 26)
 ```

## length

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,98:::fn length[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> Int
```

 Get the length of the queue.

 #### Example
 ```
 let queue : @queue.T[Int] = @queue.new()
 assert_eq!(queue.length(), 0)
 ```

## new

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,23:::fn new[A]() -> <a href="moonbitlang/core/queue#T">T</a>[A]
```

 Creates a new empty queue.

 #### Example
 ```
 let queue : @queue.T[Int] = @queue.new()
 assert_eq!(queue.length(), 0)
 ```

## of

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,384:::fn of[A](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A]) -> <a href="moonbitlang/core/queue#T">T</a>[A]
```

 Creates a new queue from a FixedArray.

 #### Example
 ```
 let queue : @queue.T[Int] = @queue.of([1, 2, 3, 4])
 assert_eq!(queue.length(), 4)
 ```

## peek

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,169:::fn peek[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> A?
```

 Peeks at the first value in the queue, which returns None if the queue is empty.

 #### Example
 ```
 let queue : @queue.T[Int] = @queue.of([1, 2, 3, 4])
 assert_eq!(queue.peek(), Some(1))
 ```

## peek\_exn

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,157:::fn peek_exn[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> A
```


## pop

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,215:::fn pop[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> A?
```

 Pops the first value from the queue, which returns None if the queue is empty.

 #### Example
 ```
 let queue : @queue.T[Int] = @queue.of([1, 2, 3, 4])
 assert_eq!(queue.pop(), Some(1))
 ```

## pop\_exn

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,203:::fn pop_exn[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> A
```


## push

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,122:::fn push[A](self : <a href="moonbitlang/core/queue#T">T</a>[A], x : A) -> Unit
```

 Adds a value to the queue.

 #### Example
 ```
 let queue : @queue.T[Int] = @queue.new()
 queue.push(1)
 ```

## transfer

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,320:::fn transfer[A](self : <a href="moonbitlang/core/queue#T">T</a>[A], dst : <a href="moonbitlang/core/queue#T">T</a>[A]) -> Unit
```

 Transfers all elements from one queue to another.

 Adds all of the elements of source to the end of destination, then clears source.

 #### Example
 ```
 let dst : @queue.T[Int] = @queue.new()
 let src : @queue.T[Int] = @queue.of([5, 6, 7, 8])
 src.transfer(dst)
 ```

## unsafe\_peek

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,147:::fn unsafe_peek[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> A
```

 Peeks at the first value in the queue.

 #### Example
 ```
 let queue : @queue.T[Int] = @queue.of([1, 2, 3, 4])
 assert_eq!(queue.unsafe_peek(), 1)
 ```
 @alert unsafe "Panics if the queue is empty."

## unsafe\_pop

```moonbit
:::source,moonbitlang/core/queue/queue.mbt,185:::fn unsafe_pop[A](self : <a href="moonbitlang/core/queue#T">T</a>[A]) -> A
```

 Pops the first value from the queue.

 #### Example
 ```
 let queue : @queue.T[Int] = @queue.of([1, 2, 3, 4])
 assert_eq!(queue.unsafe_pop(), 1)
 ```
 @alert unsafe "Panics if the queue is empty."
