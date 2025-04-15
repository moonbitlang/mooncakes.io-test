# Documentation
|Type|description|
|---|---|
|[T](#T)||

|Value|description|
|---|---|
|[back](#back)||
|[capacity](#capacity)||
|[clear](#clear)||
|[contains](#contains)||
|[copy](#copy)||
|[each](#each)||
|[eachi](#eachi)||
|[filter\_map\_inplace](#filter_map_inplace)||
|[from\_array](#from_array)||
|[from\_iter](#from_iter)||
|[front](#front)||
|[is\_empty](#is_empty)||
|[iter](#iter)||
|[iter2](#iter2)||
|[length](#length)||
|[map](#map)||
|[mapi](#mapi)||
|[new](#new)||
|[of](#of)||
|[op\_get](#op_get)||
|[op\_set](#op_set)||
|[pop\_back](#pop_back)||
|[pop\_back\_exn](#pop_back_exn)||
|[pop\_front](#pop_front)||
|[pop\_front\_exn](#pop_front_exn)||
|[push\_back](#push_back)||
|[push\_front](#push_front)||
|[reserve\_capacity](#reserve_capacity)||
|[retain](#retain)||
|[retain\_map](#retain_map)||
|[rev\_each](#rev_each)||
|[rev\_eachi](#rev_eachi)||
|[rev\_iter](#rev_iter)||
|[rev\_iter2](#rev_iter2)||
|[search](#search)||
|[shrink\_to\_fit](#shrink_to_fit)||
|[to\_array](#to_array)||
|[truncate](#truncate)||
|[unsafe\_pop\_back](#unsafe_pop_back)||
|[unsafe\_pop\_front](#unsafe_pop_front)||

## T

```moonbit
:::source,moonbitlang/core/deque/types.mbt,17:::type T[A]
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,588:::impl[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/deque#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/deque/deque.mbt,588:::fn op_equal[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/deque#T">T</a>[A], other : <a href="moonbitlang/core/deque#T">T</a>[A]) -> Bool
    ```
    > 
    >  Compares two deques for equality. Returns `true` if both deques contain the
    > same elements in the same order.
    > 
    >  Parameters:
    > 
    >  * `self` : The first deque to compare.
    >  * `other` : The second deque to compare with.
    > 
    >  Returns `true` if both deques are equal, `false` otherwise.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "op_equal" {
    >    let dq1 = @deque.of([1, 2, 3])
    >    let dq2 = @deque.of([1, 2, 3])
    >    let dq3 = @deque.of([3, 2, 1])
    >    inspect!(dq1 == dq2, content="true")
    >    inspect!(dq1 == dq3, content="false")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,49:::impl[A : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/deque#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/deque/deque.mbt,49:::fn output[A : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/deque#T">T</a>[A], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,1256:::impl[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="moonbitlang/core/deque#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/deque/deque.mbt,1256:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,1265:::impl[A : <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a>] <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="moonbitlang/core/deque#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/deque/deque.mbt,1265:::fn from_json[A : <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a>](json : <a href="moonbitlang/core/json#Json">Json</a>, path : <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="moonbitlang/core/deque#T">T</a>[A]!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### as\_views
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,554:::fn <a href="moonbitlang/core/deque#T">T</a>::as_views[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> (<a href="moonbitlang/core/array#ArrayView">ArrayView</a>[A], <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[A])
  ```
  > 
  >  Returns two array views that together represent all elements in the deque in
  > their correct order. The first view contains elements from the head to the
  > end of the internal buffer, and the second view contains any remaining
  > elements from the start of the buffer.
  > 
  >  If the deque is empty, returns a pair of empty views. If all elements are
  > contiguous in memory, the second view will be empty.
  > 
  >  Parameters:
  > 
  >  * `self` : The deque to be viewed.
  > 
  >  Returns a tuple of two array views that together contain all elements of the
  > deque in order.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "T::as_views" {
  >    let dq = @deque.of([1, 2, 3, 4, 5])
  >    let (v1, v2) = dq.as_views()
  >    inspect!(v1.length(), content="5")
  >    inspect!(v2.length(), content="0")
  >  }
  >  ```
- #### back
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,251:::fn <a href="moonbitlang/core/deque#T">T</a>::back[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> A?
  ```
  > 
  >  Return the back element from a deque, or `None` if it is empty.
  > 
  >  #### Example
  >  ```
  >  let dv = @deque.of([1, 2, 3, 4, 5])
  >  assert_eq!(dv.back(), Some(5))
  >  ```
- #### capacity
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,193:::fn <a href="moonbitlang/core/deque#T">T</a>::capacity[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> Int
  ```
  > 
  >  Returns the total number of elements the deque can hold in its internal
  > buffer before requiring reallocation.
  > 
  >  Parameters:
  > 
  >  * `deque` : The deque whose capacity is being queried.
  > 
  >  Returns the current capacity of the deque's internal buffer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "capacity" {
  >    let dq = @deque.new(capacity=10)
  >    dq.push_back(1)
  >    dq.push_back(2)
  >    inspect!(dq.capacity(), content="10")
  >  }
  >  ```
- #### clear
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,675:::fn <a href="moonbitlang/core/deque#T">T</a>::clear[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> Unit
  ```
  > 
  >  Clears the deque, removing all values.
  > 
  >  This method has no effect on the allocated capacity of the deque, only setting the length to 0.
  > 
  >  #### Example
  >  ```
  >  let dv = @deque.of([1, 2, 3, 4, 5])
  >  dv.clear()
  >  assert_eq!(dv.length(), 0)
  >  ```
- #### contains
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,801:::fn <a href="moonbitlang/core/deque#T">T</a>::contains[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/deque#T">T</a>[A], value : A) -> Bool
  ```
  > 
  >  Tests whether a deque contains a specific element.
  > 
  >  Parameters:
  > 
  >  * `self` : The deque to search in.
  >  * `value` : The element to search for.
  > 
  >  Returns `true` if the deque contains the specified element, `false`
  > otherwise.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "T::contains" {
  >    let dq = @deque.of([1, 2, 3, 4, 5])
  >    inspect!(dq.contains(3), content="true")
  >    inspect!(dq.contains(6), content="false")
  >  }
  >  ```
- #### copy
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,106:::fn <a href="moonbitlang/core/deque#T">T</a>::copy[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> <a href="moonbitlang/core/deque#T">T</a>[A]
  ```
  > 
  >  Creates a new deque with the same elements as the original deque. The new
  > deque will have a capacity equal to its length, and its elements will be
  > stored contiguously starting from index 0.
  > 
  >  Parameters:
  > 
  >  * `self` : The deque to be copied.
  > 
  >  Returns a new deque containing all elements from the original deque in the
  > same order.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "T::copy" {
  >    let dq = @deque.of([1, 2, 3, 4, 5])
  >    let copied = dq.copy()
  >    inspect!(copied, content="@deque.of([1, 2, 3, 4, 5])")
  >  }
  >  ```
- #### each
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,610:::fn <a href="moonbitlang/core/deque#T">T</a>::each[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], f : (A) -> Unit) -> Unit
  ```
  > 
  >  Iterates over the elements of the deque.
  > 
  >  #### Example
  >  ```
  >  let dv = @deque.of([1, 2, 3, 4, 5])
  >  let mut sum = 0
  >  dv.each(fn (x) {sum = sum + x})
  >  assert_eq!(sum, 15)
  >  ```
- #### eachi
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,626:::fn <a href="moonbitlang/core/deque#T">T</a>::eachi[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], f : (Int, A) -> Unit) -> Unit
  ```
  > 
  >  Iterates over the elements of the deque with index.
  > 
  >  #### Example
  >  ```
  >  let dv = @deque.of([1, 2, 3, 4, 5])
  >  let mut idx_sum = 0
  >  dv.eachi(fn (i, _x) {idx_sum = idx_sum + i})
  >  assert_eq!(idx_sum, 10)
  >  ```
- #### filter\_map\_inplace
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,974:::fn <a href="moonbitlang/core/deque#T">T</a>::filter_map_inplace[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], f : (A) -> A?) -> Unit
  ```
  > 
  >  Filters and maps elements in-place using a provided function. Modifies the
  > deque to retain only elements for which the provided function returns `Some`,
  > and updates those elements with the values inside the `Some` variant.
  > 
- #### front
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,235:::fn <a href="moonbitlang/core/deque#T">T</a>::front[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> A?
  ```
  > 
  >  Return the front element from a deque, or `None` if it is empty.
  > 
  >  #### Example
  >  ```
  >  let dv = @deque.of([1, 2, 3, 4, 5])
  >  assert_eq!(dv.front(), Some(1))
  >  ```
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,748:::fn <a href="moonbitlang/core/deque#T">T</a>::is_empty[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> Bool
  ```
  > 
  >  Test if the deque is empty.
  > 
  >  #### Example
  >  ```
  >  let dv = @deque.new()
  >  assert_eq!(dv.is_empty(), true)
  >  dv.push_back(1)
  >  assert_eq!(dv.is_empty(), false)
  >  ```
- #### iter
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,1051:::fn <a href="moonbitlang/core/deque#T">T</a>::iter[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
  ```
  > 
  >  Creates an iterator over the elements of the deque, allowing sequential
  > access to its elements in order from front to back.
  > 
  >  Parameters:
  > 
  >  * `deque` : The deque to iterate over.
  > 
  >  Returns an iterator that yields each element in the deque in order.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "T::iter" {
  >    let dq = @deque.of([1, 2, 3, 4, 5])
  >    let mut sum = 0
  >    dq.iter().each(fn(x) { sum = sum + x })
  >    inspect!(sum, content="15")
  >  }
  >  ```
- #### iter2
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,1098:::fn <a href="moonbitlang/core/deque#T">T</a>::iter2[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[Int, A]
  ```
  > 
  >  Returns an iterator that yields pairs of indices and elements from the deque
  > in order, starting from the front.
  > 
  >  Parameters:
  > 
  >  * `self` : The deque to iterate over.
  > 
  >  Returns an iterator of type `Iter2[Int, A]` that produces tuples of `(index,
  > element)`, where `index` starts from 0 and increments by 1 for each element,
  > and `element` is the corresponding element from the deque.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "iter2" {
  >    let dq = @deque.of([10, 20, 30])
  >    let mut sum = 0
  >    dq.iter2().each(fn(i, x) { sum = sum + i * x })
  >    inspect!(sum, content="80") // 0*10 + 1*20 + 2*30 = 80
  >  }
  >  ```
- #### length
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,169:::fn <a href="moonbitlang/core/deque#T">T</a>::length[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> Int
  ```
  > 
  >  Returns the number of elements in the deque.
  > 
  >  Parameters:
  > 
  >  * `deque` : The deque to get the length of.
  > 
  >  Returns the current number of elements in the deque.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "length" {
  >    let dq = @deque.of([1, 2, 3])
  >    inspect!(dq.length(), content="3")
  >    dq.push_back(4)
  >    inspect!(dq.length(), content="4")
  >  }
  >  ```
- #### map
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,705:::fn <a href="moonbitlang/core/deque#T">T</a>::map[A, U](self : <a href="moonbitlang/core/deque#T">T</a>[A], f : (A) -> U) -> <a href="moonbitlang/core/deque#T">T</a>[U]
  ```
  > 
  >  Maps a function over the elements of the deque.
  > 
  >  #### Example
  >  ```
  >  let dv = @deque.of([3, 4, 5])
  >  let dv2 = dv.map(fn (x) {x + 1})
  >  assert_eq!(dv2, @deque.of([4, 5, 6]))
  >  ```
- #### mapi
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,726:::fn <a href="moonbitlang/core/deque#T">T</a>::mapi[A, U](self : <a href="moonbitlang/core/deque#T">T</a>[A], f : (Int, A) -> U) -> <a href="moonbitlang/core/deque#T">T</a>[U]
  ```
  > 
  >  Maps a function over the elements of the deque with index.
  > 
  >  #### Example
  >  ```
  >  let dv = @deque.of([3, 4, 5])
  >  let dv2 = dv.mapi(fn (i, x) {x + i}) // @deque.of([3, 5, 7])
  >  assert_eq!(dv2, @deque.of([3, 5, 7]))
  >  ```
- #### op\_get
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,488:::fn <a href="moonbitlang/core/deque#T">T</a>::op_get[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], index : Int) -> A
  ```
  > 
  >  Retrieves the element at the specified index from the deque.
  > 
  >  If you try to access an index which isn’t in the Deque, it will panic.
  > 
  >  #### Example
  >  ```
  >  let dv = @deque.of([1, 2, 3, 4, 5])
  >  assert_eq!(dv[2], 3)
  >  ```
  >  @alert unsafe "Panic if the index is out of bounds."
- #### op\_set
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,514:::fn <a href="moonbitlang/core/deque#T">T</a>::op_set[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], index : Int, value : A) -> Unit
  ```
  > 
  >  Sets the value of the element at the specified index.
  > 
  >  If you try to access an index which isn’t in the Deque, it will panic.
  > 
  >  #### Example
  >  ```
  >  let dv = @deque.of([1, 2, 3, 4, 5])
  >  dv[2] = 1
  >  assert_eq!(dv[2], 1)
  >  ```
  >  @alert unsafe "Panic if the index is out of bounds."
- #### pop\_back
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,454:::fn <a href="moonbitlang/core/deque#T">T</a>::pop_back[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> A?
  ```
  > 
  >  Removes a back element from a deque and returns it, or `None` if it is empty.
  > 
  >  #### Example
  >  ```
  >  let dv = @deque.of([1, 2, 3, 4, 5])
  >  assert_eq!(dv.pop_back(), Some(5))
  >  ```
- #### pop\_back\_exn
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,411:::fn <a href="moonbitlang/core/deque#T">T</a>::pop_back_exn[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> Unit
  ```
  > 
  >  Removes and discards the last element from a deque.
  > 
  >  Parameters:
  > 
  >  * `deque` : The deque to remove the last element from.
  > 
  >  Throws a runtime error if the deque is empty.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "pop_back_exn" {
  >    let dq = @deque.of([1, 2, 3])
  >    // Deprecated way:
  >    // dq.pop_back_exn()
  >    // Recommended way:
  >    dq.unsafe_pop_back()
  >    inspect!(dq, content="@deque.of([1, 2])")
  >  }
  >  ```
  > 
- #### pop\_front
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,423:::fn <a href="moonbitlang/core/deque#T">T</a>::pop_front[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> A?
  ```
  > 
  >  Removes a front element from a deque and returns it, or `None` if it is empty.
  > 
  >  #### Example
  >  ```
  >  let dv = @deque.of([1, 2, 3, 4, 5])
  >  assert_eq!(dv.pop_front(), Some(1))
  >  ```
- #### pop\_front\_exn
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,354:::fn <a href="moonbitlang/core/deque#T">T</a>::pop_front_exn[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> Unit
  ```
  > 
  >  Removes and discards the first element from the deque. This function is a
  > deprecated version of `unsafe_pop_front`.
  > 
  >  Parameters:
  > 
  >  * `self` : The deque to remove the first element from.
  > 
  >  Throws a runtime error if the deque is empty.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "pop_front_exn" {
  >    let dq = @deque.of([1, 2, 3])
  >    dq.unsafe_pop_front()
  >    inspect!(dq, content="@deque.of([2, 3])")
  >  }
  >  ```
  > 
- #### push\_back
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,292:::fn <a href="moonbitlang/core/deque#T">T</a>::push_back[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], value : A) -> Unit
  ```
  > 
  >  Adds an element to the back of the deque.
  > 
  >  If the deque is at capacity, it will be reallocated.
  > 
  >  #### Example
  >  ```
  >  let dv = @deque.of([1, 2, 3, 4, 5])
  >  dv.push_back(6)
  >  assert_eq!(dv.back(), Some(6))
  >  ```
- #### push\_front
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,270:::fn <a href="moonbitlang/core/deque#T">T</a>::push_front[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], value : A) -> Unit
  ```
  > 
  >  Adds an element to the front of the deque.
  > 
  >  If the deque is at capacity, it will be reallocated.
  > 
  >  #### Example
  >  ```
  >  let dv = @deque.of([1, 2, 3, 4, 5])
  >  dv.push_front(0)
  >  assert_eq!(dv.front(), Some(0))
  >  ```
- #### reserve\_capacity
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,816:::fn <a href="moonbitlang/core/deque#T">T</a>::reserve_capacity[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], capacity : Int) -> Unit
  ```
  > 
  >  Reserves capacity to ensure that it can hold at least the number of elements
  > specified by the `capacity` argument.
  > 
  >  #### Example
  > 
  >  ```
  >  let dv = @deque.of([1])
  >  dv.reserve_capacity(10)
  >  assert_eq!(dv.capacity(), 10)
  >  ```
- #### retain
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,998:::fn <a href="moonbitlang/core/deque#T">T</a>::retain[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], f : (A) -> Bool) -> Unit
  ```
  > 
  >  Filters elements in-place by retaining only the elements that satisfy the
  > given predicate. Modifies the deque to keep only the elements for which the
  > predicate function returns `true`.
  > 
  >  Parameters:
  > 
  >  * `self` : The deque to be filtered.
  >  * `predicate` : A function that takes an element and returns `true` if the
  >    element should be kept, `false` if it should be removed.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "retain" {
  >    let dq = @deque.of([1, 2, 3, 4, 5])
  >    dq.retain(fn(x) { x % 2 == 0 })
  >    inspect!(dq, content="@deque.of([2, 4])")
  >  }
  >  ```
- #### retain\_map
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,935:::fn <a href="moonbitlang/core/deque#T">T</a>::retain_map[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], f : (A) -> A?) -> Unit
  ```
  > 
  >  Filters and maps elements in-place using a provided function. Modifies the
  > deque to retain only elements for which the provided function returns `Some`,
  > and updates those elements with the values inside the `Some` variant.
  > 
  >  Parameters:
  > 
  >  * `self` : The deque to be filtered and mapped.
  >  * `f` : A function that takes an element and returns either `Some` with a new
  >    value to replace the element, or `None` to remove the element.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "retain_map" {
  >    let dq = @deque.of([1, 2, 3, 4, 5])
  >    dq.retain_map(fn(x) { if x % 2 == 0 { Some(x * 2) } else { None } })
  >    inspect!(dq, content="@deque.of([4, 8])")
  >  }
  >  ```
- #### rev\_each
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,642:::fn <a href="moonbitlang/core/deque#T">T</a>::rev_each[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], f : (A) -> Unit) -> Unit
  ```
  > 
  >  Iterates over the elements of the deque in reversed turn.
  > 
  >  #### Example
  >  ```
  >  let dv = @deque.of([1, 2, 3, 4, 5])
  >  let mut sum = 0
  >  dv.rev_each(fn (x) {sum = sum + x})
  >  assert_eq!(sum, 15)
  >  ```
- #### rev\_eachi
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,658:::fn <a href="moonbitlang/core/deque#T">T</a>::rev_eachi[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], f : (Int, A) -> Unit) -> Unit
  ```
  > 
  >  Iterates over the elements of the deque in reversed turn with index.
  > 
  >  #### Example
  >  ```
  >  let dv = @deque.of([1, 2, 3, 4, 5])
  >  let mut idx_sum = 0
  >  dv.rev_eachi(fn (i, _x) {idx_sum = idx_sum + i})
  >  assert_eq!(idx_sum, 10)
  >  ```
- #### rev\_iter
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,1144:::fn <a href="moonbitlang/core/deque#T">T</a>::rev_iter[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
  ```
  > 
  >  Creates an iterator that yields elements in reverse order.
  > 
  >  Parameters:
  > 
  >  * `self` : The deque to iterate over.
  > 
  >  Returns an iterator that yields elements from the deque in reverse order,
  > starting from the last element.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "T::rev_iter" {
  >    let dq = @deque.of([1, 2, 3])
  >    let mut sum = 0
  >    dq.rev_iter().each(fn(x) { sum = sum * 10 + x })
  >    inspect!(sum, content="321")
  >  }
  >  ```
- #### rev\_iter2
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,1191:::fn <a href="moonbitlang/core/deque#T">T</a>::rev_iter2[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[Int, A]
  ```
  > 
  >  Creates an iterator that yields index-value pairs of elements in the deque in
  > reverse order.
  > 
  >  Parameters:
  > 
  >  * `self` : The deque to iterate over.
  > 
  >  Returns an iterator that yields tuples of `(index, value)` pairs, where the
  > index starts from 0 and increments by 1, while values are taken from the
  > deque in reverse order.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "rev_iter2" {
  >    let dq = @deque.of([1, 2, 3])
  >    let mut s = ""
  >    dq.rev_iter2().each(fn(i, x) { s = s + "\{i}:\{x} " })
  >    inspect!(s, content="0:3 1:2 2:1 ")
  >  }
  >  ```
- #### search
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,772:::fn <a href="moonbitlang/core/deque#T">T</a>::search[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/deque#T">T</a>[A], value : A) -> Int?
  ```
  > 
  >  Searches for a value in the deque and returns its position.
  > 
  >  Parameters:
  > 
  >  * `self` : The deque to search in.
  >  * `value` : The value to search for.
  > 
  >  Returns the index of the first occurrence of the value in the deque, or
  > `None` if the value is not found.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "search" {
  >    let dq = @deque.of([1, 2, 3, 2, 1])
  >    inspect!(dq.search(2), content="Some(1)")
  >    inspect!(dq.search(4), content="None")
  >  }
  >  ```
- #### shrink\_to\_fit
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,846:::fn <a href="moonbitlang/core/deque#T">T</a>::shrink_to_fit[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> Unit
  ```
  > 
  >  Shrinks the capacity of the deque as much as possible.
  > 
  >  #### Example
  > 
  >  ```
  >  let dv = @deque.new(capacity=10)
  >  dv.push_back(1)
  >  dv.push_back(2)
  >  dv.push_back(3)
  >  assert_eq!(dv.capacity(), 10)
  >  dv.shrink_to_fit()
  >  assert_eq!(dv.capacity(), 3)
  >  ```
- #### to\_array
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,1243:::fn <a href="moonbitlang/core/deque#T">T</a>::to_array[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> <a href="moonbitlang/core/array#Array">Array</a>[A]
  ```
  > 
- #### truncate
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,881:::fn <a href="moonbitlang/core/deque#T">T</a>::truncate[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], len : Int) -> Unit
  ```
  > 
  >  Shortens the deque in-place, keeping the first `len` elements and dropping
  > the rest.
  > 
  >  If `len` is greater than or equal to the deque's current length, this has no
  > effect; if `len` is negative, the function will panic.
  > 
  >  Parameters:
  > 
  >  * `self` : The deque to be truncated.
  >  * `len` : The new length of the deque.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "truncate" {
  >    let dq = @deque.of([1, 2, 3, 4, 5])
  >    dq.truncate(3)
  >    inspect!(dq, content="@deque.of([1, 2, 3])")
  >  }
  >  ```
- #### unsafe\_pop\_back
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,368:::fn <a href="moonbitlang/core/deque#T">T</a>::unsafe_pop_back[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> Unit
  ```
  > 
  >  Removes a back element from a deque.
  > 
  >  #### Example
  >  ```
  >  let dv = @deque.of([1, 2, 3, 4, 5])
  >  dv.unsafe_pop_back()
  >  assert_eq!(dv.back(), Some(4))
  >  ```
  >  @alert unsafe "Panic if the deque is empty."
- #### unsafe\_pop\_front
  ```moonbit
  :::source,moonbitlang/core/deque/deque.mbt,313:::fn <a href="moonbitlang/core/deque#T">T</a>::unsafe_pop_front[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> Unit
  ```
  > 
  >  Removes a front element from a deque.
  > 
  >  #### Example
  >  ```
  >  let dv = @deque.of([1, 2, 3, 4, 5])
  >  dv.unsafe_pop_front()
  >  assert_eq!(dv.front(), Some(2))
  >  ```
  >  @alert unsafe "Panic if the deque is empty."

## back

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,251:::fn back[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> A?
```

 Return the back element from a deque, or `None` if it is empty.

 #### Example
 ```
 let dv = @deque.of([1, 2, 3, 4, 5])
 assert_eq!(dv.back(), Some(5))
 ```

## capacity

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,193:::fn capacity[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> Int
```

 Returns the total number of elements the deque can hold in its internal
buffer before requiring reallocation.

 Parameters:

 * `deque` : The deque whose capacity is being queried.

 Returns the current capacity of the deque's internal buffer.

 Example:

 ```moonbit
 test "capacity" {
   let dq = @deque.new(capacity=10)
   dq.push_back(1)
   dq.push_back(2)
   inspect!(dq.capacity(), content="10")
 }
 ```

## clear

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,675:::fn clear[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> Unit
```

 Clears the deque, removing all values.

 This method has no effect on the allocated capacity of the deque, only setting the length to 0.

 #### Example
 ```
 let dv = @deque.of([1, 2, 3, 4, 5])
 dv.clear()
 assert_eq!(dv.length(), 0)
 ```

## contains

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,801:::fn contains[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/deque#T">T</a>[A], value : A) -> Bool
```

 Tests whether a deque contains a specific element.

 Parameters:

 * `self` : The deque to search in.
 * `value` : The element to search for.

 Returns `true` if the deque contains the specified element, `false`
otherwise.

 Example:

 ```moonbit
 test "T::contains" {
   let dq = @deque.of([1, 2, 3, 4, 5])
   inspect!(dq.contains(3), content="true")
   inspect!(dq.contains(6), content="false")
 }
 ```

## copy

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,106:::fn copy[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> <a href="moonbitlang/core/deque#T">T</a>[A]
```

 Creates a new deque with the same elements as the original deque. The new
deque will have a capacity equal to its length, and its elements will be
stored contiguously starting from index 0.

 Parameters:

 * `self` : The deque to be copied.

 Returns a new deque containing all elements from the original deque in the
same order.

 Example:

 ```moonbit
 test "T::copy" {
   let dq = @deque.of([1, 2, 3, 4, 5])
   let copied = dq.copy()
   inspect!(copied, content="@deque.of([1, 2, 3, 4, 5])")
 }
 ```

## each

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,610:::fn each[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], f : (A) -> Unit) -> Unit
```

 Iterates over the elements of the deque.

 #### Example
 ```
 let dv = @deque.of([1, 2, 3, 4, 5])
 let mut sum = 0
 dv.each(fn (x) {sum = sum + x})
 assert_eq!(sum, 15)
 ```

## eachi

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,626:::fn eachi[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], f : (Int, A) -> Unit) -> Unit
```

 Iterates over the elements of the deque with index.

 #### Example
 ```
 let dv = @deque.of([1, 2, 3, 4, 5])
 let mut idx_sum = 0
 dv.eachi(fn (i, _x) {idx_sum = idx_sum + i})
 assert_eq!(idx_sum, 10)
 ```

## filter\_map\_inplace

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,974:::fn filter_map_inplace[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], f : (A) -> A?) -> Unit
```

 Filters and maps elements in-place using a provided function. Modifies the
deque to retain only elements for which the provided function returns `Some`,
and updates those elements with the values inside the `Some` variant.


## from\_array

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,72:::fn from_array[A](arr : <a href="moonbitlang/core/array#Array">Array</a>[A]) -> <a href="moonbitlang/core/deque#T">T</a>[A]
```

 Creates a new deque with elements copied from an array.

 Parameters:

 * `array` : The array to initialize the deque with. All elements from the
   array will be copied into the new deque in the same order.

 Returns a new deque containing all elements from the input array.

 Example:

 ```moonbit
 test "from_array" {
   let arr = [1, 2, 3, 4, 5]
   let dq = @deque.from_array(arr)
   inspect!(dq, content="@deque.of([1, 2, 3, 4, 5])")
 }
 ```

## from\_iter

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,1236:::fn from_iter[A](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]) -> <a href="moonbitlang/core/deque#T">T</a>[A]
```

 Creates a new deque containing the elements from the given iterator.

 Parameters:

 * `iter` : An iterator containing the elements to be added to the deque.

 Returns a new deque containing all elements from the iterator in the same
order.

 Example:

 ```moonbit
 test "from_iter" {
   let arr = [1, 2, 3, 4, 5]
   let dq = @deque.from_iter(arr.iter())
   inspect!(dq, content="@deque.of([1, 2, 3, 4, 5])")
 }
 ```

## front

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,235:::fn front[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> A?
```

 Return the front element from a deque, or `None` if it is empty.

 #### Example
 ```
 let dv = @deque.of([1, 2, 3, 4, 5])
 assert_eq!(dv.front(), Some(1))
 ```

## is\_empty

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,748:::fn is_empty[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> Bool
```

 Test if the deque is empty.

 #### Example
 ```
 let dv = @deque.new()
 assert_eq!(dv.is_empty(), true)
 dv.push_back(1)
 assert_eq!(dv.is_empty(), false)
 ```

## iter

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,1051:::fn iter[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
```

 Creates an iterator over the elements of the deque, allowing sequential
access to its elements in order from front to back.

 Parameters:

 * `deque` : The deque to iterate over.

 Returns an iterator that yields each element in the deque in order.

 Example:

 ```moonbit
 test "T::iter" {
   let dq = @deque.of([1, 2, 3, 4, 5])
   let mut sum = 0
   dq.iter().each(fn(x) { sum = sum + x })
   inspect!(sum, content="15")
 }
 ```

## iter2

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,1098:::fn iter2[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[Int, A]
```

 Returns an iterator that yields pairs of indices and elements from the deque
in order, starting from the front.

 Parameters:

 * `self` : The deque to iterate over.

 Returns an iterator of type `Iter2[Int, A]` that produces tuples of `(index,
element)`, where `index` starts from 0 and increments by 1 for each element,
and `element` is the corresponding element from the deque.

 Example:

 ```moonbit
 test "iter2" {
   let dq = @deque.of([10, 20, 30])
   let mut sum = 0
   dq.iter2().each(fn(i, x) { sum = sum + i * x })
   inspect!(sum, content="80") // 0*10 + 1*20 + 2*30 = 80
 }
 ```

## length

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,169:::fn length[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> Int
```

 Returns the number of elements in the deque.

 Parameters:

 * `deque` : The deque to get the length of.

 Returns the current number of elements in the deque.

 Example:

 ```moonbit
 test "length" {
   let dq = @deque.of([1, 2, 3])
   inspect!(dq.length(), content="3")
   dq.push_back(4)
   inspect!(dq.length(), content="4")
 }
 ```

## map

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,705:::fn map[A, U](self : <a href="moonbitlang/core/deque#T">T</a>[A], f : (A) -> U) -> <a href="moonbitlang/core/deque#T">T</a>[U]
```

 Maps a function over the elements of the deque.

 #### Example
 ```
 let dv = @deque.of([3, 4, 5])
 let dv2 = dv.map(fn (x) {x + 1})
 assert_eq!(dv2, @deque.of([4, 5, 6]))
 ```

## mapi

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,726:::fn mapi[A, U](self : <a href="moonbitlang/core/deque#T">T</a>[A], f : (Int, A) -> U) -> <a href="moonbitlang/core/deque#T">T</a>[U]
```

 Maps a function over the elements of the deque with index.

 #### Example
 ```
 let dv = @deque.of([3, 4, 5])
 let dv2 = dv.mapi(fn (i, x) {x + i}) // @deque.of([3, 5, 7])
 assert_eq!(dv2, @deque.of([3, 5, 7]))
 ```

## new

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,44:::fn new[A](capacity~ : Int = ..) -> <a href="moonbitlang/core/deque#T">T</a>[A]
```

 Creates a new empty deque with an optional initial capacity.

 Parameters:

 * `capacity` : The initial capacity of the deque. If not specified, defaults
   to 0 and will be automatically adjusted as elements are added.

 Returns a new empty deque of type `T[A]` where `A` is the type of elements
the deque will hold.

 Example:

 ```moonbit
 test "T::new" {
   let dq : @deque.T[Int] = @deque.new()
   inspect!(dq.length(), content="0")
   inspect!(dq.capacity(), content="0")
 }
 
 test "T::new/with_capacity" {
   let dq : @deque.T[Int] = @deque.new(capacity=10)
   inspect!(dq.length(), content="0")
   inspect!(dq.capacity(), content="10")
 }
 ```

## of

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,137:::fn of[A](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A]) -> <a href="moonbitlang/core/deque#T">T</a>[A]
```

 Creates a new deque from a fixed array, preserving the order of elements.

 Parameters:

 * `array` : A fixed-size array containing the initial elements of the deque.

 Returns a new deque containing all elements from the input array.

 Example:

 ```moonbit
 test "of" {
   let dq = @deque.of([1, 2, 3])
   inspect!(dq, content="@deque.of([1, 2, 3])")
 }
 ```

## op\_get

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,488:::fn op_get[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], index : Int) -> A
```

 Retrieves the element at the specified index from the deque.

 If you try to access an index which isn’t in the Deque, it will panic.

 #### Example
 ```
 let dv = @deque.of([1, 2, 3, 4, 5])
 assert_eq!(dv[2], 3)
 ```
 @alert unsafe "Panic if the index is out of bounds."

## op\_set

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,514:::fn op_set[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], index : Int, value : A) -> Unit
```

 Sets the value of the element at the specified index.

 If you try to access an index which isn’t in the Deque, it will panic.

 #### Example
 ```
 let dv = @deque.of([1, 2, 3, 4, 5])
 dv[2] = 1
 assert_eq!(dv[2], 1)
 ```
 @alert unsafe "Panic if the index is out of bounds."

## pop\_back

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,454:::fn pop_back[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> A?
```

 Removes a back element from a deque and returns it, or `None` if it is empty.

 #### Example
 ```
 let dv = @deque.of([1, 2, 3, 4, 5])
 assert_eq!(dv.pop_back(), Some(5))
 ```

## pop\_back\_exn

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,411:::fn pop_back_exn[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> Unit
```

 Removes and discards the last element from a deque.

 Parameters:

 * `deque` : The deque to remove the last element from.

 Throws a runtime error if the deque is empty.

 Example:

 ```moonbit
 test "pop_back_exn" {
   let dq = @deque.of([1, 2, 3])
   // Deprecated way:
   // dq.pop_back_exn()
   // Recommended way:
   dq.unsafe_pop_back()
   inspect!(dq, content="@deque.of([1, 2])")
 }
 ```


## pop\_front

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,423:::fn pop_front[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> A?
```

 Removes a front element from a deque and returns it, or `None` if it is empty.

 #### Example
 ```
 let dv = @deque.of([1, 2, 3, 4, 5])
 assert_eq!(dv.pop_front(), Some(1))
 ```

## pop\_front\_exn

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,354:::fn pop_front_exn[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> Unit
```

 Removes and discards the first element from the deque. This function is a
deprecated version of `unsafe_pop_front`.

 Parameters:

 * `self` : The deque to remove the first element from.

 Throws a runtime error if the deque is empty.

 Example:

 ```moonbit
 test "pop_front_exn" {
   let dq = @deque.of([1, 2, 3])
   dq.unsafe_pop_front()
   inspect!(dq, content="@deque.of([2, 3])")
 }
 ```


## push\_back

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,292:::fn push_back[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], value : A) -> Unit
```

 Adds an element to the back of the deque.

 If the deque is at capacity, it will be reallocated.

 #### Example
 ```
 let dv = @deque.of([1, 2, 3, 4, 5])
 dv.push_back(6)
 assert_eq!(dv.back(), Some(6))
 ```

## push\_front

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,270:::fn push_front[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], value : A) -> Unit
```

 Adds an element to the front of the deque.

 If the deque is at capacity, it will be reallocated.

 #### Example
 ```
 let dv = @deque.of([1, 2, 3, 4, 5])
 dv.push_front(0)
 assert_eq!(dv.front(), Some(0))
 ```

## reserve\_capacity

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,816:::fn reserve_capacity[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], capacity : Int) -> Unit
```

 Reserves capacity to ensure that it can hold at least the number of elements
specified by the `capacity` argument.

 #### Example

 ```
 let dv = @deque.of([1])
 dv.reserve_capacity(10)
 assert_eq!(dv.capacity(), 10)
 ```

## retain

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,998:::fn retain[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], f : (A) -> Bool) -> Unit
```

 Filters elements in-place by retaining only the elements that satisfy the
given predicate. Modifies the deque to keep only the elements for which the
predicate function returns `true`.

 Parameters:

 * `self` : The deque to be filtered.
 * `predicate` : A function that takes an element and returns `true` if the
   element should be kept, `false` if it should be removed.

 Example:

 ```moonbit
 test "retain" {
   let dq = @deque.of([1, 2, 3, 4, 5])
   dq.retain(fn(x) { x % 2 == 0 })
   inspect!(dq, content="@deque.of([2, 4])")
 }
 ```

## retain\_map

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,935:::fn retain_map[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], f : (A) -> A?) -> Unit
```

 Filters and maps elements in-place using a provided function. Modifies the
deque to retain only elements for which the provided function returns `Some`,
and updates those elements with the values inside the `Some` variant.

 Parameters:

 * `self` : The deque to be filtered and mapped.
 * `f` : A function that takes an element and returns either `Some` with a new
   value to replace the element, or `None` to remove the element.

 Example:

 ```moonbit
 test "retain_map" {
   let dq = @deque.of([1, 2, 3, 4, 5])
   dq.retain_map(fn(x) { if x % 2 == 0 { Some(x * 2) } else { None } })
   inspect!(dq, content="@deque.of([4, 8])")
 }
 ```

## rev\_each

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,642:::fn rev_each[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], f : (A) -> Unit) -> Unit
```

 Iterates over the elements of the deque in reversed turn.

 #### Example
 ```
 let dv = @deque.of([1, 2, 3, 4, 5])
 let mut sum = 0
 dv.rev_each(fn (x) {sum = sum + x})
 assert_eq!(sum, 15)
 ```

## rev\_eachi

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,658:::fn rev_eachi[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], f : (Int, A) -> Unit) -> Unit
```

 Iterates over the elements of the deque in reversed turn with index.

 #### Example
 ```
 let dv = @deque.of([1, 2, 3, 4, 5])
 let mut idx_sum = 0
 dv.rev_eachi(fn (i, _x) {idx_sum = idx_sum + i})
 assert_eq!(idx_sum, 10)
 ```

## rev\_iter

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,1144:::fn rev_iter[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
```

 Creates an iterator that yields elements in reverse order.

 Parameters:

 * `self` : The deque to iterate over.

 Returns an iterator that yields elements from the deque in reverse order,
starting from the last element.

 Example:

 ```moonbit
 test "T::rev_iter" {
   let dq = @deque.of([1, 2, 3])
   let mut sum = 0
   dq.rev_iter().each(fn(x) { sum = sum * 10 + x })
   inspect!(sum, content="321")
 }
 ```

## rev\_iter2

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,1191:::fn rev_iter2[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[Int, A]
```

 Creates an iterator that yields index-value pairs of elements in the deque in
reverse order.

 Parameters:

 * `self` : The deque to iterate over.

 Returns an iterator that yields tuples of `(index, value)` pairs, where the
index starts from 0 and increments by 1, while values are taken from the
deque in reverse order.

 Example:

 ```moonbit
 test "rev_iter2" {
   let dq = @deque.of([1, 2, 3])
   let mut s = ""
   dq.rev_iter2().each(fn(i, x) { s = s + "\{i}:\{x} " })
   inspect!(s, content="0:3 1:2 2:1 ")
 }
 ```

## search

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,772:::fn search[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/deque#T">T</a>[A], value : A) -> Int?
```

 Searches for a value in the deque and returns its position.

 Parameters:

 * `self` : The deque to search in.
 * `value` : The value to search for.

 Returns the index of the first occurrence of the value in the deque, or
`None` if the value is not found.

 Example:

 ```moonbit
 test "search" {
   let dq = @deque.of([1, 2, 3, 2, 1])
   inspect!(dq.search(2), content="Some(1)")
   inspect!(dq.search(4), content="None")
 }
 ```

## shrink\_to\_fit

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,846:::fn shrink_to_fit[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> Unit
```

 Shrinks the capacity of the deque as much as possible.

 #### Example

 ```
 let dv = @deque.new(capacity=10)
 dv.push_back(1)
 dv.push_back(2)
 dv.push_back(3)
 assert_eq!(dv.capacity(), 10)
 dv.shrink_to_fit()
 assert_eq!(dv.capacity(), 3)
 ```

## to\_array

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,1243:::fn to_array[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> <a href="moonbitlang/core/array#Array">Array</a>[A]
```


## truncate

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,881:::fn truncate[A](self : <a href="moonbitlang/core/deque#T">T</a>[A], len : Int) -> Unit
```

 Shortens the deque in-place, keeping the first `len` elements and dropping
the rest.

 If `len` is greater than or equal to the deque's current length, this has no
effect; if `len` is negative, the function will panic.

 Parameters:

 * `self` : The deque to be truncated.
 * `len` : The new length of the deque.

 Example:

 ```moonbit
 test "truncate" {
   let dq = @deque.of([1, 2, 3, 4, 5])
   dq.truncate(3)
   inspect!(dq, content="@deque.of([1, 2, 3])")
 }
 ```

## unsafe\_pop\_back

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,368:::fn unsafe_pop_back[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> Unit
```

 Removes a back element from a deque.

 #### Example
 ```
 let dv = @deque.of([1, 2, 3, 4, 5])
 dv.unsafe_pop_back()
 assert_eq!(dv.back(), Some(4))
 ```
 @alert unsafe "Panic if the deque is empty."

## unsafe\_pop\_front

```moonbit
:::source,moonbitlang/core/deque/deque.mbt,313:::fn unsafe_pop_front[A](self : <a href="moonbitlang/core/deque#T">T</a>[A]) -> Unit
```

 Removes a front element from a deque.

 #### Example
 ```
 let dv = @deque.of([1, 2, 3, 4, 5])
 dv.unsafe_pop_front()
 assert_eq!(dv.front(), Some(2))
 ```
 @alert unsafe "Panic if the deque is empty."
