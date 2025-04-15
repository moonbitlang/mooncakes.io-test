# Documentation
|Type|description|
|---|---|
|[View](#View)||
|[ArrayView](#ArrayView)||
|[Array](#Array)||
|[FixedArray](#FixedArray)||

|Value|description|
|---|---|
|[copy](#copy)||
|[filter\_map](#filter_map)||
|[join](#join)||
|[last](#last)||
|[push\_iter](#push_iter)||
|[shuffle](#shuffle)||
|[shuffle\_in\_place](#shuffle_in_place)||
|[sort](#sort)||
|[sort\_by](#sort_by)||
|[sort\_by\_key](#sort_by_key)||

## View

```moonbit
:::source,moonbitlang/core/array/view.mbt,27:::type View[T] = <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T]
```


 A `@array.View` represents a view into a section of an array without copying the data.

 #### Example

 ```moonbit
 let arr = [1, 2, 3, 4, 5]
 let view = arr[1:4]  // Creates a view of elements at indices 1,2,3
 assert_eq!(view[0], 2)
 assert_eq!(view.length(), 3)
 ```

## copy

```moonbit
:::source,moonbitlang/core/array/array_nonjs.mbt,35:::fn copy[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> <a href="moonbitlang/core/array#Array">Array</a>[T]
```

 Creates and returns a new array with a copy of all elements from the input
array.

 Parameters:

 * `array` : The array to be copied.

 Returns a new array containing all elements from the original array.

 Example:

 ```moonbit
 test "copy" {
   let original = [1, 2, 3]
   let copied = original.copy()
   inspect!(copied, content="[1, 2, 3]")
   inspect!(physical_equal(original, copied), content="false")
 }
 ```

## filter\_map

```moonbit
:::source,moonbitlang/core/array/array.mbt,150:::fn filter_map[A, B](self : <a href="moonbitlang/core/array#Array">Array</a>[A], f : (A) -> B?) -> <a href="moonbitlang/core/array#Array">Array</a>[B]
```

 Returns a new array containing the elements of the original array that satisfy the given predicate.
 
 #### Arguments
 
 * `self` - The array to filter.
 * `f` - The predicate function.
 
 #### Returns
 

## join

```moonbit
:::source,moonbitlang/core/array/array.mbt,198:::fn join(self : <a href="moonbitlang/core/array#Array">Array</a>[String], separator : String) -> String
```


## last

```moonbit
:::source,moonbitlang/core/array/array.mbt,181:::fn last[A](self : <a href="moonbitlang/core/array#Array">Array</a>[A]) -> A?
```

 Returns the last element of the array, or `None` if the array is empty.

 Parameters:

 * `array` : The array to get the last element from.

 Returns an optional value containing the last element of the array. The
result is `None` if the array is empty, or `Some(x)` where `x` is the last
element of the array.

 Example:

 ```moonbit
 test "last" {
   let arr = [1, 2, 3]
   inspect!(arr.last(), content="Some(3)")
   let empty : Array[Int] = []
   inspect!(empty.last(), content="None")
 }
 ```

## push\_iter

```moonbit
:::source,moonbitlang/core/array/array.mbt,51:::fn push_iter[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]) -> Unit
```

 Adds all elements from an iterator to the end of the array.

 This function iterates over each element in the provided iterator
and adds them to the array using the `push` method.

 #### Example
 ```
 let u = [1, 2, 3]
 let v = [4, 5, 6]
 u.push_iter(v.iter())
 assert_eq!(u, [1, 2, 3, 4, 5, 6])
 ```

## shuffle

```moonbit
:::source,moonbitlang/core/array/array.mbt,134:::fn shuffle[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], rand~ : (Int) -> Int) -> <a href="moonbitlang/core/array#Array">Array</a>[T]
```

 Shuffle the array using Knuth shuffle
 
 To use this function, you need to provide a rand function, which takes an integer as it upper bound
and returns an integer.
*rand n* is expected to returns a uniformly distribution integer between 0 and n - 1
 #### Example
 
 ```
 let arr = [1, 2, 3, 4, 5]
 fn rand(upper : Int) -> Int {
   let rng = @random.new()
   rng.int(limit=upper)
 }
 let _shuffled = Array::shuffle(arr, rand=rand)
 ```

## shuffle\_in\_place

```moonbit
:::source,moonbitlang/core/array/array.mbt,108:::fn shuffle_in_place[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], rand~ : (Int) -> Int) -> Unit
```

 Shuffle the array using Knuth shuffle
 
 To use this function, you need to provide a rand function, which takes an integer as it upper bound
and returns an integer.
*rand n* is expected to returns a uniformly distribution integer between 0 and n - 1
 #### Example
 
 ```
 let arr = [1, 2, 3, 4, 5]
 fn rand(upper : Int) -> Int {
   let rng = @random.new()
   rng.int(limit=upper)
 }
 Array::shuffle_in_place(arr, rand=rand)
 ```

## sort

```moonbit
:::source,moonbitlang/core/array/sort.mbt,27:::fn sort[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> Unit
```

 Sorts the array in place.

 It's an in-place, unstable sort(it will reorder equal elements). The time complexity is O(n log n) in the worst case.

 #### Example

 ```
 let arr = [5, 4, 3, 2, 1]
 arr.sort()
 assert_eq!(arr, [1, 2, 3, 4, 5])
 ```

## sort\_by

```moonbit
:::source,moonbitlang/core/array/sort_by.mbt,48:::fn sort_by[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], cmp : (T, T) -> Int) -> Unit
```

 Sorts the array with a custom comparison function.

 It's an in-place, unstable sort(it will reorder equal elements). The time complexity is O(n log n) in the worst case.

 #### Example

 ```
 let arr = [5, 3, 2, 4, 1]
 arr.sort_by(fn (a, b) { a - b })
 assert_eq!(arr, [1, 2, 3, 4, 5])
 ```

## sort\_by\_key

```moonbit
:::source,moonbitlang/core/array/sort_by.mbt,27:::fn sort_by_key[T, K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#Array">Array</a>[T], map : (T) -> K) -> Unit
```

 Sorts the array with a key extraction function.

 It's an in-place, unstable sort(it will reorder equal elements). The time complexity is O(n log n) in the worst case.

 #### Example

 ```
 let arr = [5, 3, 2, 4, 1]
 arr.sort_by_key(fn (x) {-x})
 assert_eq!(arr, [5, 4, 3, 2, 1])
 ```

## ArrayView


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/array/view.mbt,366:::impl[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/array/view.mbt,366:::fn compare[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T], other : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T]) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/array/view.mbt,352:::impl[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/array/view.mbt,352:::fn op_equal[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T], other : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T]) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/array/view.mbt,347:::impl[X : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/array/view.mbt,347:::fn output[X : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[X], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### all
  ```moonbit
  :::source,moonbitlang/core/array/view.mbt,105:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::all[T](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T], f : (T) -> Bool) -> Bool
  ```
  > 
  >  Checks if all elements in the array view match the condition.
  >  
  >  #### Example
  >  
  >  ```
  >  let v = [1, 4, 6, 8, 9]
  >  assert_false!(v[:].all(fn(elem) { elem % 2 == 0 }))
  >  assert_true!(v[1:4].all(fn(elem) { elem % 2 == 0 }))
  >  ```
- #### any
  ```moonbit
  :::source,moonbitlang/core/array/view.mbt,124:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::any[T](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T], f : (T) -> Bool) -> Bool
  ```
  > 
  >  Check if any of the elements in the array view match the condition.
  > 
  >  #### Example
  > 
  >  ```
  >  let v = [1, 2, 3, 4, 5][:]
  >  assert_true!(v.any(fn(ele) { ele < 6 }))
  >  assert_false!(v.any(fn(ele) { ele < 1 }))
  >  ```
- #### contains
  ```moonbit
  :::source,moonbitlang/core/array/view.mbt,154:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::contains[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T], value : T) -> Bool
  ```
  > 
  >  Checks whether the array view contains a specific element by comparing each
  > element with the target value using the equality operator.
  > 
  >  Parameters:
  > 
  >  * `view` : The array view to search in.
  >  * `target` : The value to search for in the array view.
  > 
  >  Returns a boolean value indicating whether the target value exists in the
  > array view.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "array_view/contains" {
  >    let arr = [1, 2, 3, 4, 5][:]
  >    inspect!(arr.contains(3), content="true")
  >    inspect!(arr.contains(6), content="false")
  >  }
  >  ```
- #### each
  ```moonbit
  :::source,moonbitlang/core/array/view.mbt,72:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::each[T](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T], f : (T) -> Unit) -> Unit
  ```
  > 
  >  Iterates over each element in the array view and applies a function to it.
  > 
  >  Parameters:
  > 
  >  * `self` : The array view to iterate over.
  >  * `function` : A function that takes an element of type `T` and returns
  >    nothing. This function will be applied to each element in the array view.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "array_view/each" {
  >    let arr = [1, 2, 3][:]
  >    let mut sum = 0
  >    arr.each(fn(x) { sum = sum + x })
  >    inspect!(sum, content="6")
  >  }
  >  ```
- #### eachi
  ```moonbit
  :::source,moonbitlang/core/array/view.mbt,89:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::eachi[T](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T], f : (Int, T) -> Unit) -> Unit
  ```
  > 
  >  Iterates over the elements of the array view with index.
  > 
  >  #### Example
  >  
  >  ```
  >  let v = [3, 4, 5][:]
  >  let mut sum = 0
  >  v.eachi(fn (i, x) { sum = sum + x + i })
  >  assert_eq!(sum, 15)
  >  ```
- #### filter
  ```moonbit
  :::source,moonbitlang/core/array/view.mbt,336:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::filter[T](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T], f : (T) -> Bool) -> <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  >  Filters the array view with a predicate function.
  > 
  >  #### Example
  >  ```
  >  let arr = [1, 2, 3, 4, 5, 6]
  >  let v = arr[2:].filter(fn (x) { x % 2 == 0 })
  >  assert_eq!(v, [4, 6])
  >  ```
- #### fold
  ```moonbit
  :::source,moonbitlang/core/array/view.mbt,204:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::fold[A, B](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[A], init~ : B, f : (B, A) -> B) -> B
  ```
  > 
  >  Fold out values from an View according to certain rules.
  > 
  >  #### Example
  >  ```
  >  let sum = [1, 2, 3, 4, 5][:].fold(init=0, fn { sum, elem => sum + elem })
  >  assert_eq!(sum, 15)
  >  ```
- #### foldi
  ```moonbit
  :::source,moonbitlang/core/array/view.mbt,236:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::foldi[A, B](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[A], init~ : B, f : (Int, B, A) -> B) -> B
  ```
  > 
  >  Fold out values from an View according to certain rules with index.
  > 
  >  #### Example
  >  ```
  >  let sum = [1, 2, 3, 4, 5][:].foldi(init=0, fn { index, sum, _elem => sum + index })
  >  assert_eq!(sum, 10)
  >  ```
- #### iter
  ```moonbit
  :::source,moonbitlang/core/array/view.mbt,185:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::iter[A](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[A]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
  ```
  > 
  >  Returns an iterator that yields each element of the array view in sequence
  > from start to end.
  > 
  >  Parameters:
  > 
  >  * `array_view` : The array view to iterate over.
  > 
  >  Returns an iterator that yields elements of type `A` from the array view.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "View::iter" {
  >    let arr = [1, 2, 3]
  >    let view = arr[1:]
  >    let mut sum = 0
  >    view.iter().each(fn(x) { sum = sum + x })
  >    inspect!(sum, content="5")
  >  }
  >  ```
- #### map
  ```moonbit
  :::source,moonbitlang/core/array/view.mbt,274:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::map[T, U](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T], f : (T) -> U) -> <a href="moonbitlang/core/array#Array">Array</a>[U]
  ```
  > 
  >  Maps a function over the elements of the array view.
  > 
  >  #### Example
  >  ```
  >  let v = [3, 4, 5]
  >  let v2 = v[1:].map(fn (x) {x + 1})
  >  assert_eq!(v2, [5, 6])
  >  ```
- #### map\_inplace
  ```moonbit
  :::source,moonbitlang/core/array/view.mbt,290:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::map_inplace[T](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T], f : (T) -> T) -> Unit
  ```
  > 
  >  Maps a function over the elements of the array view in place.
  > 
  >  #### Example
  >  ```
  >  let v = [3, 4, 5]
  >  v[1:].map_inplace(fn (x) {x + 1})
  >  assert_eq!(v, [3, 5, 6])
  >  ```
- #### mapi
  ```moonbit
  :::source,moonbitlang/core/array/view.mbt,305:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::mapi[T, U](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T], f : (Int, T) -> U) -> <a href="moonbitlang/core/array#Array">Array</a>[U]
  ```
  > 
  >  Maps a function over the elements of the array view with index.
  > 
  >  #### Example
  >  ```
  >  let v = [3, 4, 5]
  >  let v2 = v[1:].mapi(fn (i, x) {x + i})
  >  assert_eq!(v2, [4, 6])
  >  ```
- #### mapi\_inplace
  ```moonbit
  :::source,moonbitlang/core/array/view.mbt,321:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::mapi_inplace[T](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T], f : (Int, T) -> T) -> Unit
  ```
  > 
  >  Maps a function over the elements of the array view with index in place.
  > 
  >  #### Example
  >  ```
  >  let v = [3, 4, 5]
  >  v[1:].mapi_inplace(fn (i, x) {x + i})
  >  assert_eq!(v, [3, 4, 6])
  >  ```
- #### rev\_fold
  ```moonbit
  :::source,moonbitlang/core/array/view.mbt,220:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::rev_fold[A, B](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[A], init~ : B, f : (B, A) -> B) -> B
  ```
  > 
  >  Fold out values from an View according to certain rules in reversed turn.
  > 
  >  #### Example
  >  ```
  >  let sum = [1, 2, 3, 4, 5][:].rev_fold(init=0, fn { sum, elem => sum + elem })
  >  assert_eq!(sum, 15)
  >  ```
- #### rev\_foldi
  ```moonbit
  :::source,moonbitlang/core/array/view.mbt,252:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::rev_foldi[A, B](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[A], init~ : B, f : (Int, B, A) -> B) -> B
  ```
  > 
  >  Fold out values from an View according to certain rules in reversed turn with index.
  > 
  >  #### Example
  >  ```
  >  let sum = [1, 2, 3, 4, 5][:].rev_foldi(init=0, fn { index, sum, _elem => sum + index })
  >  assert_eq!(sum, 10)
  >  ```
- #### rev\_inplace
  ```moonbit
  :::source,moonbitlang/core/array/view.mbt,45:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::rev_inplace[T](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T]) -> Unit
  ```
  > 
  >  Reverses the elements in the array view in place.
  > 
  >  Parameters:
  > 
  >  * `self` : The array view whose elements are to be reversed.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "rev_inplace" {
  >    let arr = [1, 2, 3, 4, 5]
  >    arr[:].rev_inplace()
  >    inspect!(arr, content="[5, 4, 3, 2, 1]")
  >  }
  >  ```

## Array


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/array/array.mbt,189:::impl[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for <a href="moonbitlang/core/array#Array">Array</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/array/array.mbt,189:::fn arbitrary[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>](size : Int, rs : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[X]
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### copy
  ```moonbit
  :::source,moonbitlang/core/array/array_nonjs.mbt,35:::fn <a href="moonbitlang/core/array#Array">Array</a>::copy[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  >  Creates and returns a new array with a copy of all elements from the input
  > array.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to be copied.
  > 
  >  Returns a new array containing all elements from the original array.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "copy" {
  >    let original = [1, 2, 3]
  >    let copied = original.copy()
  >    inspect!(copied, content="[1, 2, 3]")
  >    inspect!(physical_equal(original, copied), content="false")
  >  }
  >  ```
- #### filter\_map
  ```moonbit
  :::source,moonbitlang/core/array/array.mbt,150:::fn <a href="moonbitlang/core/array#Array">Array</a>::filter_map[A, B](self : <a href="moonbitlang/core/array#Array">Array</a>[A], f : (A) -> B?) -> <a href="moonbitlang/core/array#Array">Array</a>[B]
  ```
  > 
  >  Returns a new array containing the elements of the original array that satisfy the given predicate.
  >  
  >  #### Arguments
  >  
  >  * `self` - The array to filter.
  >  * `f` - The predicate function.
  >  
  >  #### Returns
  >  
- #### from\_iter
  ```moonbit
  :::source,moonbitlang/core/array/array.mbt,34:::fn <a href="moonbitlang/core/array#Array">Array</a>::from_iter[T](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]) -> <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  >  Creates a new array containing all elements from an iterator.
  > 
  >  Parameters:
  > 
  >  * `iterator` : An iterator containing elements of type `T`.
  > 
  >  Returns a new array containing all elements from the iterator in the same
  > order.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::from_iter" {
  >    let iter = Iter::singleton(42)
  >    let arr = Array::from_iter(iter)
  >    inspect!(arr, content="[42]")
  >  }
  >  ```
- #### join
  ```moonbit
  :::source,moonbitlang/core/array/array.mbt,198:::fn <a href="moonbitlang/core/array#Array">Array</a>::join(self : <a href="moonbitlang/core/array#Array">Array</a>[String], separator : String) -> String
  ```
  > 
- #### last
  ```moonbit
  :::source,moonbitlang/core/array/array.mbt,181:::fn <a href="moonbitlang/core/array#Array">Array</a>::last[A](self : <a href="moonbitlang/core/array#Array">Array</a>[A]) -> A?
  ```
  > 
  >  Returns the last element of the array, or `None` if the array is empty.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to get the last element from.
  > 
  >  Returns an optional value containing the last element of the array. The
  > result is `None` if the array is empty, or `Some(x)` where `x` is the last
  > element of the array.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "last" {
  >    let arr = [1, 2, 3]
  >    inspect!(arr.last(), content="Some(3)")
  >    let empty : Array[Int] = []
  >    inspect!(empty.last(), content="None")
  >  }
  >  ```
- #### makei
  ```moonbit
  :::source,moonbitlang/core/array/array.mbt,80:::fn <a href="moonbitlang/core/array#Array">Array</a>::makei[T](length : Int, value : (Int) -> T) -> <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  >  Creates a new array of the specified length, where each element is
  > initialized using an index-based initialization function.
  > 
  >  Parameters:
  > 
  >  * `length` : The length of the new array. If `length` is less than or equal
  >    to 0, returns an empty array.
  >  * `initializer` : A function that takes an index (starting from 0) and
  >    returns a value of type `T`. This function is called for each index to
  >    initialize the corresponding element.
  > 
  >  Returns a new array of type `Array[T]` with the specified length, where each
  > element is initialized using the provided function.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::makei" {
  >    let arr = Array::makei(3, fn(i) { i * 2 })
  >    inspect!(arr, content="[0, 2, 4]")
  >  }
  >  ```
- #### push\_iter
  ```moonbit
  :::source,moonbitlang/core/array/array.mbt,51:::fn <a href="moonbitlang/core/array#Array">Array</a>::push_iter[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]) -> Unit
  ```
  > 
  >  Adds all elements from an iterator to the end of the array.
  > 
  >  This function iterates over each element in the provided iterator
  > and adds them to the array using the `push` method.
  > 
  >  #### Example
  >  ```
  >  let u = [1, 2, 3]
  >  let v = [4, 5, 6]
  >  u.push_iter(v.iter())
  >  assert_eq!(u, [1, 2, 3, 4, 5, 6])
  >  ```
- #### shuffle
  ```moonbit
  :::source,moonbitlang/core/array/array.mbt,134:::fn <a href="moonbitlang/core/array#Array">Array</a>::shuffle[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], rand~ : (Int) -> Int) -> <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  >  Shuffle the array using Knuth shuffle
  >  
  >  To use this function, you need to provide a rand function, which takes an integer as it upper bound
  > and returns an integer.
  > *rand n* is expected to returns a uniformly distribution integer between 0 and n - 1
  >  #### Example
  >  
  >  ```
  >  let arr = [1, 2, 3, 4, 5]
  >  fn rand(upper : Int) -> Int {
  >    let rng = @random.new()
  >    rng.int(limit=upper)
  >  }
  >  let _shuffled = Array::shuffle(arr, rand=rand)
  >  ```
- #### shuffle\_in\_place
  ```moonbit
  :::source,moonbitlang/core/array/array.mbt,108:::fn <a href="moonbitlang/core/array#Array">Array</a>::shuffle_in_place[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], rand~ : (Int) -> Int) -> Unit
  ```
  > 
  >  Shuffle the array using Knuth shuffle
  >  
  >  To use this function, you need to provide a rand function, which takes an integer as it upper bound
  > and returns an integer.
  > *rand n* is expected to returns a uniformly distribution integer between 0 and n - 1
  >  #### Example
  >  
  >  ```
  >  let arr = [1, 2, 3, 4, 5]
  >  fn rand(upper : Int) -> Int {
  >    let rng = @random.new()
  >    rng.int(limit=upper)
  >  }
  >  Array::shuffle_in_place(arr, rand=rand)
  >  ```
- #### sort
  ```moonbit
  :::source,moonbitlang/core/array/sort.mbt,27:::fn <a href="moonbitlang/core/array#Array">Array</a>::sort[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> Unit
  ```
  > 
  >  Sorts the array in place.
  > 
  >  It's an in-place, unstable sort(it will reorder equal elements). The time complexity is O(n log n) in the worst case.
  > 
  >  #### Example
  > 
  >  ```
  >  let arr = [5, 4, 3, 2, 1]
  >  arr.sort()
  >  assert_eq!(arr, [1, 2, 3, 4, 5])
  >  ```
- #### sort\_by
  ```moonbit
  :::source,moonbitlang/core/array/sort_by.mbt,48:::fn <a href="moonbitlang/core/array#Array">Array</a>::sort_by[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], cmp : (T, T) -> Int) -> Unit
  ```
  > 
  >  Sorts the array with a custom comparison function.
  > 
  >  It's an in-place, unstable sort(it will reorder equal elements). The time complexity is O(n log n) in the worst case.
  > 
  >  #### Example
  > 
  >  ```
  >  let arr = [5, 3, 2, 4, 1]
  >  arr.sort_by(fn (a, b) { a - b })
  >  assert_eq!(arr, [1, 2, 3, 4, 5])
  >  ```
- #### sort\_by\_key
  ```moonbit
  :::source,moonbitlang/core/array/sort_by.mbt,27:::fn <a href="moonbitlang/core/array#Array">Array</a>::sort_by_key[T, K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#Array">Array</a>[T], map : (T) -> K) -> Unit
  ```
  > 
  >  Sorts the array with a key extraction function.
  > 
  >  It's an in-place, unstable sort(it will reorder equal elements). The time complexity is O(n log n) in the worst case.
  > 
  >  #### Example
  > 
  >  ```
  >  let arr = [5, 3, 2, 4, 1]
  >  arr.sort_by_key(fn (x) {-x})
  >  assert_eq!(arr, [5, 4, 3, 2, 1])
  >  ```

## FixedArray


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,1085:::impl[T] <a href="moonbitlang/core/builtin#Add">Add</a> for <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/array/fixedarray.mbt,1085:::fn op_add[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], other : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]) -> <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]
    ```
    > 
    >  Concatenates two arrays and returns a new array containing all elements from
    > both arrays in order.
    > 
    >  Parameters:
    > 
    >  * `self` : The first array to concatenate.
    >  * `other` : The second array to concatenate.
    > 
    >  Returns a new array that contains all elements from the first array followed
    > by all elements from the second array. The returned array is independent of
    > both input arrays.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "op_add" {
    >    let arr1 : FixedArray[Int] = [1, 2, 3]
    >    let arr2 : FixedArray[Int] = [4, 5, 6]
    >    inspect!(arr1 + arr2, content="[1, 2, 3, 4, 5, 6]")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,1044:::impl[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/array/fixedarray.mbt,1044:::fn compare[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], other : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]) -> Int
    ```
    > 
    >  Compares two fixed arrays lexicographically based on their elements. First
    > compares the lengths of the arrays, then compares elements pairwise until a
    > difference is found or all elements have been compared.
    > 
    >  Parameters:
    > 
    >  * `self` : The first fixed array to compare.
    >  * `other` : The second fixed array to compare.
    > 
    >  Returns an integer that indicates the relative order:
    > 
    >  * A negative value if `self` is less than `other`
    >  * Zero if `self` equals `other`
    >  * A positive value if `self` is greater than `other`
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "FixedArray::compare" {
    >    let arr1 = [1, 2, 3]
    >    let arr2 = [1, 2, 4]
    >    let arr3 = [1, 2]
    >    inspect!(arr1.compare(arr2), content="-1") // arr1 < arr2
    >    inspect!(arr2.compare(arr1), content="1") // arr2 > arr1
    >    inspect!(arr1.compare(arr3), content="1") // arr1 > arr3 (longer)
    >    inspect!(arr1.compare(arr1), content="0") // arr1 = arr1
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,963:::impl[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/array/fixedarray.mbt,963:::fn op_equal[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], that : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]) -> Bool
    ```
    > 
    >  Checks if two fixed arrays are equal.
    > 
    >  Two arrays are considered equal if they have the same length and all
    > corresponding elements are equal. The elements in the arrays must implement
    > the `Eq` trait.
    > 
    >  Parameters:
    > 
    >  * `self` : The first fixed array to compare.
    >  * `other` : The second fixed array to compare.
    > 
    >  Returns `true` if the arrays are equal, `false` otherwise.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "FixedArray::op_equal" {
    >    let arr1 : FixedArray[Int] = [1, 2, 3]
    >    let arr2 : FixedArray[Int] = [1, 2, 3]
    >    let arr3 : FixedArray[Int] = [1, 2, 4]
    >    inspect!(arr1 == arr2, content="true")
    >    inspect!(arr1 == arr3, content="false")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,979:::impl[T : <a href="moonbitlang/core/builtin#Hash">Hash</a>] <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/array/fixedarray.mbt,979:::fn hash_combine[T : <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,1229:::impl[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/array/fixedarray.mbt,1229:::fn arbitrary[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>](size : Int, rs : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[X]
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### all
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,685:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::all[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], f : (T) -> Bool) -> Bool
  ```
  > 
  >  Check if all the elements in the array match the condition.
  > 
  >  #### Example
  > 
  >  ```
  >  let arr: FixedArray[Int] = [1, 2, 3, 4, 5]
  >  assert_true!(arr.all(fn(ele) { ele < 6 }))
  >  assert_false!(arr.all(fn(ele) { ele < 5 }))
  >  ```
- #### any
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,721:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::any[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], f : (T) -> Bool) -> Bool
  ```
  > 
  >  Check if any of the elements in the array match the condition.
  > 
  >  #### Example
  > 
  >  ```
  >  let arr: FixedArray[Int] = [1, 2, 3, 4, 5]
  >  assert_true!(arr.any(fn(ele) { ele < 6 }))
  >  assert_true!(arr.any(fn(ele) { ele < 5 }))
  >  ```
- #### blit\_from\_bytesview
  ```moonbit
  :::source,moonbitlang/core/array/blit.mbt,82:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::blit_from_bytesview(self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Byte], bytes_offset : Int, src : <a href="moonbitlang/core/bytes#View">@moonbitlang/core/bytes.View</a>) -> Unit
  ```
  > 
  >  Copy bytes from a @bytes.View into a fixed array of bytes.
  > 
  >  Parameters:
  > 
  >  * `self` : The destination fixed array of bytes.
  >  * `bytes_offset` : The starting position in the destination array where bytes will be copied.
  >  * `src` : The source View to copy from.
  > 
  >  Throws a panic if:
  >  * `bytes_offset` is negative
  >  * The destination array is too small to hold all bytes from the source View
  > 
  >  Example:
  > 
  >  ```moonbit
  >   let arr = FixedArray::make(4, b'\x00')
  >   let view = b"\x01\x02\x03"[1:]
  >   arr.blit_from_bytesview(1, view)
  >   inspect!(arr, content="[b'\\x00', b'\\x02', b'\\x03', b'\\x00']")
  >  ```
- #### contains
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,808:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::contains[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], value : T) -> Bool
  ```
  > 
  >  Checks if the array contains an element.
  > 
  >  #### Example
  >  ```
  >  let arr: FixedArray[Int] = [3, 4, 5]
  >  assert_true!(arr.contains(3))
  >  ```
- #### copy
  ```moonbit
  :::source,moonbitlang/core/array/blit.mbt,36:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::copy[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]) -> <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]
  ```
  > 
  >  Creates a new array that is a copy of the original array.
  > 
  >  Parameters:
  > 
  >  * `self` : The array to be copied. The type of elements in the array must be
  >    `T`.
  > 
  >  Returns a new array containing all elements from the original array in the
  > same order.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "copy" {
  >    let original = [1, 2, 3]
  >    let copied = original.copy()
  >    inspect!(copied, content="[1, 2, 3]")
  >    inspect!(physical_equal(original, copied), content="false")
  >  }
  >  ```
- #### each
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,32:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::each[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], f : (T) -> Unit) -> Unit
  ```
  > 
  >  Iterates over each element.
  > 
  >  #### Arguments
  > 
  >  - `self`: The array to iterate over.
  >  - `f`: The function to apply to each element.
  > 
  >  #### Example
  > 
  >  ```
  >  let arr = []
  >  [1, 2, 3, 4, 5].each(fn(x){ arr.push(x) })
  >  assert_eq!(arr, [1, 2, 3, 4, 5])
  >  ```
  >  TODO: change the intrinsic to match the function name
- #### eachi
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,83:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::eachi[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], f : (Int, T) -> Unit) -> Unit
  ```
  > 
  >  Iterates over the array with index.
  > 
  >  #### Arguments
  > 
  >  - `self`: The array to iterate over.
  >  - `f`: A function that takes an `Int` representing the index and a `T` representing the element of the array, and returns `Unit`.
  > 
  >  #### Example
  > 
  >  ```
  >  let arr = []
  >  [1, 2, 3, 4, 5].eachi(fn(index, elem){
  >    arr.push((index, elem))
  >  })
  >  assert_eq!(arr, [(0, 1), (1, 2), (2, 3), (3, 4), (4, 5)])
  >  ```
- #### ends\_with
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,892:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::ends_with[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], suffix : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]) -> Bool
  ```
  > 
  >  Check if the array ends with a given suffix.
  > 
  >  #### Example
  >  ```
  >  let v: FixedArray[Int] = [3, 4, 5]
  >  assert_true!(v.ends_with([5]))
  >  ```
- #### fold
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,399:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::fold[A, B](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A], init~ : B, f : (B, A) -> B) -> B
  ```
  > 
  >  Fold out values from an array according to certain rules.
  > 
  >  #### Example
  >  ```
  >  let sum = [1, 2, 3, 4, 5].fold(init=0, fn { sum, elem => sum + elem })
  >  assert_eq!(sum, 15)
  >  ```
- #### foldi
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,465:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::foldi[A, B](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A], init~ : B, f : (Int, B, A) -> B) -> B
  ```
  > 
  >  Fold out values from an array according to certain rules with index.
  > 
  >  #### Example
  >  ```
  >  let sum = [1, 2, 3, 4, 5].foldi(init=0, fn { index, sum, _elem => sum + index })
  >  assert_eq!(sum, 10)
  >  ```
- #### from\_array
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,381:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::from_array[T](array : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]
  ```
  > 
  >  Creates a new fixed-size array from a dynamic array. The resulting fixed
  > array will have the same length and elements as the input array.
  > 
  >  Parameters:
  > 
  >  * `array` : A dynamic array containing elements of type `T` that will be
  >    converted to a fixed array.
  > 
  >  Returns a new fixed array containing the same elements as the input array.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "FixedArray::from_array" {
  >    let dynamic_array = [1, 2, 3, 4, 5]
  >    let fixed_array = FixedArray::from_array(dynamic_array)
  >    inspect!(fixed_array, content="[1, 2, 3, 4, 5]")
  >  }
  >  ```
- #### from\_iter
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,1165:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::from_iter[T](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]) -> <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]
  ```
  > 
  >  Creates a new fixed array from an iterator.
  > 
  >  Parameters:
  > 
  >  * `iterator` : An iterator of type `Iter[T]` from which elements will be
  >    collected into a fixed array.
  > 
  >  Returns a new fixed array containing all elements from the iterator.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "FixedArray::from_iter" {
  >    let arr = [1, 2, 3]
  >    let fixed_arr = FixedArray::from_iter(arr.iter())
  >    inspect!(fixed_arr, content="[1, 2, 3]")
  >  }
  >  ```
- #### is\_sorted
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray_sort.mbt,529:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::is_sorted[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]) -> Bool
  ```
  > 
  >  Checks if the elements in the array are sorted in ascending order according
  > to their natural ordering.
  > 
  >  Parameters:
  > 
  >  * `array` : A fixed array of type `T`, where `T` must implement the `Compare`
  >    trait.
  > 
  >  Returns `true` if the array is sorted in ascending order, `false` otherwise.
  > An empty array or an array with a single element is considered sorted.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "FixedArray::is_sorted" {
  >    let sorted : FixedArray[Int] = [1, 2, 3, 4, 5]
  >    let unsorted : FixedArray[Int] = [5, 4, 3, 2, 1]
  >    inspect!(FixedArray::is_sorted(sorted), content="true")
  >    inspect!(FixedArray::is_sorted(unsorted), content="false")
  >  }
  >  ```
- #### last
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,1189:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::last[A](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A]) -> A?
  ```
  > 
  >  Returns the last element of a fixed array if it exists.
  > 
  >  Parameters:
  > 
  >  * `self` : The fixed array to get the last element from.
  > 
  >  Returns `Some(element)` containing the last element if the array is not
  > empty, or `None` if the array is empty.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "FixedArray::last" {
  >    let array : FixedArray[Int] = [1, 2, 3]
  >    inspect!(array.last(), content="Some(3)")
  >    let empty : FixedArray[Int] = []
  >    inspect!(empty.last(), content="None")
  >  }
  >  ```
- #### makei
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,336:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::makei[T](length : Int, value : (Int) -> T) -> <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]
  ```
  > 
  >  Creates a new fixed-size array of the specified length, where each element is
  > initialized using a function that maps indices to values.
  > 
  >  Parameters:
  > 
  >  * `length` : The length of the array to create. If `length` is less than or
  >    equal to 0, returns an empty array.
  >  * `initializer` : A function that takes an index (from 0 to `length - 1`) and
  >    returns a value of type `T` for that position.
  > 
  >  Returns a new fixed array containing the values produced by applying the
  > initializer function to each index.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "FixedArray::makei" {
  >    let arr = FixedArray::makei(3, fn(i) { i * 2 })
  >    inspect!(arr, content="[0, 2, 4]")
  >  }
  >  ```
- #### map
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,239:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::map[T, U](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], f : (T) -> U) -> <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[U]
  ```
  > 
  >  Applies a function to each element of the array and returns a new array with the results.
  > 
  >  #### Example
  > 
  >  ```
  >  let arr = [1, 2, 3, 4, 5]
  >  let doubled = arr.map(fn(x){ x * 2 })
  >  assert_eq!(doubled, [2, 4, 6, 8, 10])
  >  ```
- #### mapi
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,274:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::mapi[T, U](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], f : (Int, T) -> U) -> <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[U]
  ```
  > 
  >  Maps a function over the elements of the arr with index.
  > 
  >  #### Example
  >  ```
  >  let arr = [3, 4, 5]
  >  let added = arr.mapi(fn (i, x) { x + i })
  >  assert_eq!(added, [3, 5, 7])
  >  ```
- #### rev
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,575:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::rev[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]) -> <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]
  ```
  > 
  >  Returns a new array containing all elements in reverse order. The original
  > array remains unchanged.
  > 
  >  Parameters:
  > 
  >  * `self` : The array to be reversed.
  > 
  >  Returns a new array with the same elements but in reverse order.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "FixedArray::rev" {
  >    let arr : FixedArray[Int] = [1, 2, 3, 4, 5]
  >    inspect!(arr.rev(), content="[5, 4, 3, 2, 1]")
  >    // Original array remains unchanged
  >    inspect!(arr, content="[1, 2, 3, 4, 5]")
  >  }
  >  ```
- #### rev\_each
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,132:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::rev_each[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], f : (T) -> Unit) -> Unit
  ```
  > 
  >  Iterates over each element in reversed turn.
  > 
  >  #### Arguments
  > 
  >  - `self`: The array to iterate over.
  >  - `f`: The function to apply to each element.
  > 
  >  #### Example
  > 
  >  ```
  >  let arr = []
  >  [1, 2, 3, 4, 5].rev_each(fn(x){ arr.push(x) })
  >  assert_eq!(arr, [5, 4, 3, 2, 1])
  >  ```
- #### rev\_eachi
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,183:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::rev_eachi[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], f : (Int, T) -> Unit) -> Unit
  ```
  > 
  >  Iterates over the array with index in reversed turn.
  > 
  >  #### Arguments
  > 
  >  - `self`: The array to iterate over.
  >  - `f`: A function that takes an `Int` representing the index and a `T` representing the element of the array, and returns `Unit`.
  > 
  >  #### Example
  > 
  >  ```
  >  let arr = []
  >  [1, 2, 3, 4, 5].rev_eachi(fn(index, elem){
  >    arr.push((index, elem))
  >  })
  >  assert_eq!(arr, [(0, 5), (1, 4), (2, 3), (3, 2), (4, 1)])
  >  ```
- #### rev\_fold
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,431:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::rev_fold[A, B](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A], init~ : B, f : (B, A) -> B) -> B
  ```
  > 
  >  Fold out values from an array according to certain rules in reversed turn.
  > 
  >  #### Example
  >  ```
  >  let sum = [1, 2, 3, 4, 5].rev_fold(init=0, fn { sum, elem => sum + elem })
  >  assert_eq!(sum, 15)
  >  ```
- #### rev\_foldi
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,500:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::rev_foldi[A, B](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A], init~ : B, f : (Int, B, A) -> B) -> B
  ```
  > 
  >  Fold out values from an array according to certain rules in reversed turn with index.
  > 
  >  #### Example
  >  ```
  >  let sum = [1, 2, 3, 4, 5].rev_foldi(init=0, fn { index, sum, _elem => sum + index })
  >  assert_eq!(sum, 10)
  >  ```
- #### rev\_inplace
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,545:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::rev_inplace[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]) -> Unit
  ```
  > 
  >  Reverses the array in place by swapping elements from both ends until
  > reaching the middle.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to be reversed. The array will be modified in place.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "rev_inplace" {
  >    let arr : FixedArray[_] = [1, 2, 3, 4, 5]
  >    arr.rev_inplace()
  >    inspect!(arr, content="[5, 4, 3, 2, 1]")
  >  }
  >  ```
- #### search
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,772:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::search[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], value : T) -> Int?
  ```
  > 
  >  Search the array index for a given element.
  > 
  >  #### Example
  >  ```
  >  let arr: FixedArray[Int] = [3, 4, 5]
  >  assert_eq!(arr.search(3), Some(0))
  >  ```
- #### sort
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray_sort.mbt,216:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::sort[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]) -> Unit
  ```
  > 
  >  Sorts the array
  >  
  >  It's an in-place, unstable sort(it will reorder equal elements). The time complexity is O(n log n) in the worst case.
  >  
  >  #### Example
  >  
  >  ```
  >  let arr = [5, 4, 3, 2, 1]
  >  arr.sort()
  >  assert_eq!(arr, [1, 2, 3, 4, 5])
  >  ```
- #### sort\_by
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray_sort_by.mbt,61:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::sort_by[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], cmp : (T, T) -> Int) -> Unit
  ```
  > 
  >  Sorts the array with a custom comparison function.
  > 
  >  It's an in-place, unstable sort(it will reorder equal elements). The time complexity is O(n log n) in the worst case.
  > 
  >  #### Example
  > 
  >  ```
  >  let arr = [5, 3, 2, 4, 1]
  >  arr.sort_by(fn (a, b) { a - b })
  >  assert_eq!(arr, [1, 2, 3, 4, 5])
  >  ```
- #### sort\_by\_key
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray_sort_by.mbt,27:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::sort_by_key[T, K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], map : (T) -> K) -> Unit
  ```
  > 
  >  Sorts the array with a key extraction function.
  > 
  >  It's an in-place, unstable sort(it will reorder equal elements). The time complexity is O(n log n) in the worst case.
  > 
  >  #### Example
  > 
  >  ```
  >  let arr = [5, 3, 2, 4, 1]
  >  arr.sort_by_key(fn (x) {-x})
  >  assert_eq!(arr, [5, 4, 3, 2, 1])
  >  ```
- #### stable\_sort
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray_sort.mbt,27:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::stable_sort[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]) -> Unit
  ```
  > 
  >  Sorts the array
  >  
  >  It's an stable sort(it will not reorder equal elements). The time complexity is *O*(*n* \* log(*n*)) in the worst case.
  >  
  >  #### Example
  >  
  >  ```
  >  let arr: FixedArray[Int] = [5, 4, 3, 2, 1]
  >  arr.stable_sort()
  >  assert_eq!(arr, [1, 2, 3, 4, 5])
  >  ```
- #### starts\_with
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,844:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::starts_with[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], prefix : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]) -> Bool
  ```
  > 
  >  Check if the array starts with a given prefix.
  > 
  >  #### Example
  >  ```
  >  let arr: FixedArray[Int] = [3, 4, 5]
  >  assert_true!(arr.starts_with([3, 4]))
  >  ```
- #### swap
  ```moonbit
  :::source,moonbitlang/core/array/fixedarray.mbt,648:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::swap[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], i : Int, j : Int) -> Unit
  ```
  > 
  >  Swap two elements in the array.
  > 
  >  #### Example
  > 
  >  ```
  >  let arr = [1, 2, 3, 4, 5]
  >  arr.swap(0, 1)
  >  assert_eq!(arr, [2, 1, 3, 4, 5])
  >  ```
