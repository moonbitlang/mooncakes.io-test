# Documentation
|Type|description|
|---|---|
|[T](#T)||

|Value|description|
|---|---|
|[add](#add)||
|[all](#all)||
|[any](#any)||
|[contains](#contains)||
|[diff](#diff)||
|[difference](#difference)||
|[disjoint](#disjoint)||
|[each](#each)||
|[filter](#filter)||
|[fold](#fold)||
|[from\_array](#from_array)||
|[from\_iter](#from_iter)||
|[from\_json](#from_json)||
|[inter](#inter)||
|[intersection](#intersection)||
|[is\_empty](#is_empty)||
|[iter](#iter)||
|[map](#map)||
|[max](#max)||
|[max\_option](#max_option)||
|[min](#min)||
|[min\_option](#min_option)||
|[new](#new)||
|[of](#of)||
|[remove](#remove)||
|[remove\_min](#remove_min)||
|[singleton](#singleton)||
|[size](#size)||
|[split](#split)||
|[subset](#subset)||
|[to\_array](#to_array)||
|[to\_json](#to_json)||
|[union](#union)||

## T

```moonbit
:::source,moonbitlang/core/immut/sorted_set/types.mbt,21:::type T[A]
```

 ImmutableSets are represented by balanced binary trees (the heights of the children differ by at most 2).

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,306:::impl[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Add">Add</a> for <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,306:::fn op_add[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], other : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
    ```
    > 
    >  a convenient alias of `union`
    >  #### Example
    >  
    >  ```
    >  assert_eq!(@sorted_set.of([3, 4, 5]) + (@sorted_set.of([4, 5, 6])), @sorted_set.of([3, 4, 5, 6]))
    >  ```
- ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/generic.mbt,70:::impl[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/sorted_set/generic.mbt,70:::fn compare[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], other : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,26:::impl[A] <a href="moonbitlang/core/builtin#Default">Default</a> for <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,26:::fn default[A]() -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/generic.mbt,54:::impl[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/sorted_set/generic.mbt,54:::fn op_equal[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], other : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,766:::impl[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>] <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,766:::fn hash_combine[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,536:::impl[A : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,536:::fn output[A : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,541:::impl[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,541:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,555:::impl[A : <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,555:::fn from_json[A : <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](json : <a href="moonbitlang/core/json#Json">Json</a>, path : <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,579:::impl[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for <a href="moonbitlang/core/immut/sorted_set#T">T</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,579:::fn arbitrary[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](size : Int, rs : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[X]
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### add
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,95:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::add[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], value : A) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
  >  Insert a value into the ImmutableSet.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@sorted_set.of([6, 3, 8, 1]).add(5), @sorted_set.of([1, 3, 5, 6, 8]))
  >  ```
- #### all
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,485:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::all[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], f : (A) -> Bool) -> Bool
  ```
  > 
  >  Test if all values of the ImmutableSet satisfy the predicate.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@sorted_set.of([2, 4, 6]).all(fn(v) { v % 2 == 0}), true)
  >  ```
- #### any
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,500:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::any[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], f : (A) -> Bool) -> Bool
  ```
  > 
  >  Checks if at least one element of the set satisfies the predicate.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@sorted_set.of([1, 4, 3]).any(fn(v) { v % 2 == 0}), true)
  >  ```
- #### contains
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,256:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::contains[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], value : A) -> Bool
  ```
  > 
  >  Return true if value contain in sorted\_set
- #### diff
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,347:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::diff[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], other : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
  >  Returns the difference between self and other.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@sorted_set.of([1, 2, 3]).difference(@sorted_set.of([4, 5, 1])), @sorted_set.of([2, 3]))
  >  ```
  > 
- #### difference
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,359:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::difference[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], other : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
  >  Returns the difference between self and other.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@sorted_set.of([1, 2, 3]).difference(@sorted_set.of([4, 5, 1])), @sorted_set.of([2, 3]))
  >  ```
- #### disjoint
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,409:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::disjoint[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], other : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> Bool
  ```
  > 
  >  Returns true if the two sets do not intersect.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@sorted_set.of([1, 2, 3]).disjoint(@sorted_set.of([4, 5, 6])), true)
  >  ```
- #### each
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,434:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::each[A](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], f : (A) -> Unit) -> Unit
  ```
  > 
  >  Iterates over the ImmutableSet.
  > 
  >  #### Example
  > 
  >  ```
  >  let arr = []
  >  @sorted_set.of([7, 2, 9, 4, 5, 6, 3, 8, 1]).each(fn(x) { arr.push(x) })
  >  assert_eq!(arr, [1, 2, 3, 4, 5, 6, 7, 8, 9])
  >  ```
- #### filter
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,515:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::filter[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], f : (A) -> Bool) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
  >  Filter the ImmutableSet.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@sorted_set.of([1, 2, 3, 4, 5, 6]).filter(fn(v) { v % 2 == 0}), @sorted_set.of([2, 4, 6]))
  >  ```
- #### fold
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,453:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::fold[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, B](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], init~ : B, f : (B, A) -> B) -> B
  ```
  > 
  >  Fold the ImmutableSet.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@sorted_set.of([1, 2, 3, 4, 5]).fold(init=0, fn(acc, x) { acc + x }), 15)
  >  ```
- #### from\_array
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/deprecated.mbt,32:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::from_array[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](array : <a href="moonbitlang/core/array#Array">Array</a>[A]) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
- #### from\_iter
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/generic.mbt,44:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::from_iter[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  >  @alert deprecated "use `@immut/sorted_set.from_iter` instead"
- #### from\_json
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/deprecated.mbt,39:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::from_json[A : <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](json : <a href="moonbitlang/core/json#Json">Json</a>) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
  ```
  > 
- #### inter
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,313:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::inter[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], other : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
- #### intersection
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,325:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::intersection[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], other : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
  >  Returns the intersection of self with other.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@sorted_set.of([3, 4, 5]).intersection(@sorted_set.of([4, 5, 6])), @sorted_set.of([4, 5]))
  >  ```
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,250:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::is_empty[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> Bool
  ```
  > 
  >  Returns true if sorted\_set is empty
- #### iter
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/generic.mbt,20:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::iter[A](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
  ```
  > 
- #### map
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,469:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::map[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, B : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], f : (A) -> B) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[B]
  ```
  > 
  >  Maps the ImmutableSet.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@sorted_set.of([1, 2, 3]).map(fn(x){ x * 2}), @sorted_set.of([2, 4, 6]))
  >  ```
- #### max
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,195:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::max[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> A
  ```
  > 
  >  Returns the largest value in the sorted\_set.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@sorted_set.of([7, 2, 9, 4, 5, 6, 3, 8, 1]).max(), 9)
  >  ```
  >  @alert unsafe "Panic if the sorted\_set is empty."
- #### max\_option
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,205:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::max_option[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> A?
  ```
  > 
  >  Returns the largest value in the ImmutableSet.
  > But returns None when the value does not exist.
- #### min
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,164:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::min[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> A
  ```
  > 
  >  Returns the smallest value in the sorted\_set.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@sorted_set.of([7, 2, 9, 4, 5, 6, 3, 8, 1]).min(), 1)
  >  ```
  >  @alert unsafe "Panic if the sorted\_set is empty."
- #### min\_option
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,174:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::min_option[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> A?
  ```
  > 
  >  Returns the smallest value in the sorted\_set.
  > But returns None when the value does not exist.
- #### new
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/deprecated.mbt,18:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::new[A]() -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
- #### of
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/deprecated.mbt,48:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::of[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](array : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A]) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
- #### remove
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,129:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::remove[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], value : A) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
  >  Remove n value from the ImmutableSet.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@sorted_set.of([3, 8, 1]).remove(8), @sorted_set.of([1, 3]))
  >  ```
- #### remove\_min
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,75:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::remove_min[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
  >  Remove the smallest value,
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@sorted_set.of([3, 4, 5]).remove_min(), @sorted_set.of([4, 5]))
  >  ```
  >  @alert unsafe "Panic if the ImmutableSet is empty."
- #### singleton
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/deprecated.mbt,25:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::singleton[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](value : A) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
- #### size
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,634:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::size[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> Int
  ```
  > 
  >  Get the height of set.
- #### split
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,230:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::split[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], divide : A) -> (<a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], Bool, <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A])
  ```
  > 
  >  Returns a triple (left, present, right), where left \< divide \< right.
  > present == false if self contains no value equal to divide,
  > present == true  if self contains an value equal to divide.
  > 
  >  #### Example
  > 
  >  ```
  >  let (left, present, right) = @sorted_set.of([7, 2, 9, 4, 5, 6, 3, 8, 1]).split(5)
  >  assert_eq!(present, true)
  >  assert_eq!(left, @sorted_set.of([1, 2, 3, 4]))
  >  assert_eq!(right, @sorted_set.of([6, 7, 8, 9]))
  >  ```
- #### subset
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,379:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::subset[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], other : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> Bool
  ```
  > 
  >  Returns true if self is a subset of other.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@sorted_set.of([1, 2, 3]).subset(@sorted_set.of([7, 2, 9, 4, 5, 6, 3, 8, 1])), true)
  >  ```
- #### to\_array
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,48:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::to_array[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/array#Array">Array</a>[A]
  ```
  > 
  >  Convert ImmutableSet\[T\] to Array\[T\], the result must be ordered.
- #### to\_json
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,550:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/json#Json">Json</a>
  ```
  > 
- #### union
  ```moonbit
  :::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,275:::fn <a href="moonbitlang/core/immut/sorted_set#T">T</a>::union[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], other : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
  ```
  > 
  >  Returns the union of self and other.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@sorted_set.of([3, 4, 5]).union(@sorted_set.of([4, 5, 6])), @sorted_set.of([3, 4, 5, 6]))
  >  ```

## add

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,95:::fn add[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], value : A) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
```

 Insert a value into the ImmutableSet.

 #### Example

 ```
 assert_eq!(@sorted_set.of([6, 3, 8, 1]).add(5), @sorted_set.of([1, 3, 5, 6, 8]))
 ```

## all

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,485:::fn all[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], f : (A) -> Bool) -> Bool
```

 Test if all values of the ImmutableSet satisfy the predicate.

 #### Example

 ```
 assert_eq!(@sorted_set.of([2, 4, 6]).all(fn(v) { v % 2 == 0}), true)
 ```

## any

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,500:::fn any[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], f : (A) -> Bool) -> Bool
```

 Checks if at least one element of the set satisfies the predicate.

 #### Example

 ```
 assert_eq!(@sorted_set.of([1, 4, 3]).any(fn(v) { v % 2 == 0}), true)
 ```

## contains

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,256:::fn contains[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], value : A) -> Bool
```

 Return true if value contain in sorted\_set

## diff

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,347:::fn diff[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], other : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
```

 Returns the difference between self and other.

 #### Example

 ```
 assert_eq!(@sorted_set.of([1, 2, 3]).difference(@sorted_set.of([4, 5, 1])), @sorted_set.of([2, 3]))
 ```


## difference

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,359:::fn difference[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], other : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
```

 Returns the difference between self and other.

 #### Example

 ```
 assert_eq!(@sorted_set.of([1, 2, 3]).difference(@sorted_set.of([4, 5, 1])), @sorted_set.of([2, 3]))
 ```

## disjoint

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,409:::fn disjoint[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], other : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> Bool
```

 Returns true if the two sets do not intersect.

 #### Example

 ```
 assert_eq!(@sorted_set.of([1, 2, 3]).disjoint(@sorted_set.of([4, 5, 6])), true)
 ```

## each

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,434:::fn each[A](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], f : (A) -> Unit) -> Unit
```

 Iterates over the ImmutableSet.

 #### Example

 ```
 let arr = []
 @sorted_set.of([7, 2, 9, 4, 5, 6, 3, 8, 1]).each(fn(x) { arr.push(x) })
 assert_eq!(arr, [1, 2, 3, 4, 5, 6, 7, 8, 9])
 ```

## filter

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,515:::fn filter[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], f : (A) -> Bool) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
```

 Filter the ImmutableSet.

 #### Example

 ```
 assert_eq!(@sorted_set.of([1, 2, 3, 4, 5, 6]).filter(fn(v) { v % 2 == 0}), @sorted_set.of([2, 4, 6]))
 ```

## fold

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,453:::fn fold[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, B](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], init~ : B, f : (B, A) -> B) -> B
```

 Fold the ImmutableSet.

 #### Example

 ```
 assert_eq!(@sorted_set.of([1, 2, 3, 4, 5]).fold(init=0, fn(acc, x) { acc + x }), 15)
 ```

## from\_array

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,38:::fn from_array[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](array : <a href="moonbitlang/core/array#Array">Array</a>[A]) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
```

 Initialize an ImmutableSet\[T\] from a Array\[T\]

## from\_iter

```moonbit
:::source,moonbitlang/core/immut/sorted_set/generic.mbt,39:::fn from_iter[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
```


## from\_json

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,572:::fn from_json[A : <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](json : <a href="moonbitlang/core/json#Json">Json</a>) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
```


## inter

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,313:::fn inter[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], other : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
```


## intersection

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,325:::fn intersection[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], other : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
```

 Returns the intersection of self with other.

 #### Example

 ```
 assert_eq!(@sorted_set.of([3, 4, 5]).intersection(@sorted_set.of([4, 5, 6])), @sorted_set.of([4, 5]))
 ```

## is\_empty

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,250:::fn is_empty[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> Bool
```

 Returns true if sorted\_set is empty

## iter

```moonbit
:::source,moonbitlang/core/immut/sorted_set/generic.mbt,20:::fn iter[A](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
```


## map

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,469:::fn map[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, B : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], f : (A) -> B) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[B]
```

 Maps the ImmutableSet.

 #### Example

 ```
 assert_eq!(@sorted_set.of([1, 2, 3]).map(fn(x){ x * 2}), @sorted_set.of([2, 4, 6]))
 ```

## max

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,195:::fn max[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> A
```

 Returns the largest value in the sorted\_set.

 #### Example

 ```
 assert_eq!(@sorted_set.of([7, 2, 9, 4, 5, 6, 3, 8, 1]).max(), 9)
 ```
 @alert unsafe "Panic if the sorted\_set is empty."

## max\_option

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,205:::fn max_option[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> A?
```

 Returns the largest value in the ImmutableSet.
But returns None when the value does not exist.

## min

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,164:::fn min[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> A
```

 Returns the smallest value in the sorted\_set.

 #### Example

 ```
 assert_eq!(@sorted_set.of([7, 2, 9, 4, 5, 6, 3, 8, 1]).min(), 1)
 ```
 @alert unsafe "Panic if the sorted\_set is empty."

## min\_option

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,174:::fn min_option[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> A?
```

 Returns the smallest value in the sorted\_set.
But returns None when the value does not exist.

## new

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,21:::fn new[A]() -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
```


## of

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,757:::fn of[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](array : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A]) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
```


## remove

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,129:::fn remove[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], value : A) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
```

 Remove n value from the ImmutableSet.

 #### Example

 ```
 assert_eq!(@sorted_set.of([3, 8, 1]).remove(8), @sorted_set.of([1, 3]))
 ```

## remove\_min

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,75:::fn remove_min[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
```

 Remove the smallest value,

 #### Example

 ```
 assert_eq!(@sorted_set.of([3, 4, 5]).remove_min(), @sorted_set.of([4, 5]))
 ```
 @alert unsafe "Panic if the ImmutableSet is empty."

## singleton

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,32:::fn singleton[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](value : A) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
```

 Returns the one-value ImmutableSet containing only `value`.

## size

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,634:::fn size[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> Int
```

 Get the height of set.

## split

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,230:::fn split[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], divide : A) -> (<a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], Bool, <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A])
```

 Returns a triple (left, present, right), where left \< divide \< right.
present == false if self contains no value equal to divide,
present == true  if self contains an value equal to divide.

 #### Example

 ```
 let (left, present, right) = @sorted_set.of([7, 2, 9, 4, 5, 6, 3, 8, 1]).split(5)
 assert_eq!(present, true)
 assert_eq!(left, @sorted_set.of([1, 2, 3, 4]))
 assert_eq!(right, @sorted_set.of([6, 7, 8, 9]))
 ```

## subset

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,379:::fn subset[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], other : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> Bool
```

 Returns true if self is a subset of other.

 #### Example

 ```
 assert_eq!(@sorted_set.of([1, 2, 3]).subset(@sorted_set.of([7, 2, 9, 4, 5, 6, 3, 8, 1])), true)
 ```

## to\_array

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,48:::fn to_array[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/array#Array">Array</a>[A]
```

 Convert ImmutableSet\[T\] to Array\[T\], the result must be ordered.

## to\_json

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,550:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/json#Json">Json</a>
```


## union

```moonbit
:::source,moonbitlang/core/immut/sorted_set/immutable_set.mbt,275:::fn union[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A], other : <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]) -> <a href="moonbitlang/core/immut/sorted_set#T">T</a>[A]
```

 Returns the union of self and other.

 #### Example

 ```
 assert_eq!(@sorted_set.of([3, 4, 5]).union(@sorted_set.of([4, 5, 6])), @sorted_set.of([3, 4, 5, 6]))
 ```
