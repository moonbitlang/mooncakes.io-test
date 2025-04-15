# Documentation
|Type|description|
|---|---|
|[T](#T)||

|Value|description|
|---|---|
|[add](#add)||
|[all](#all)||
|[any](#any)||
|[concat](#concat)||
|[concat\_map](#concat_map)||
|[contains](#contains)||
|[default](#default)||
|[drop](#drop)||
|[drop\_while](#drop_while)||
|[each](#each)||
|[eachi](#eachi)||
|[equal](#equal)||
|[filter](#filter)||
|[filter\_map](#filter_map)||
|[find](#find)||
|[findi](#findi)||
|[flat\_map](#flat_map)||
|[flatten](#flatten)||
|[fold](#fold)||
|[fold\_left](#fold_left)||
|[fold\_lefti](#fold_lefti)||
|[fold\_right](#fold_right)||
|[fold\_righti](#fold_righti)||
|[foldi](#foldi)||
|[from\_array](#from_array)||
|[from\_iter](#from_iter)||
|[from\_iter\_rev](#from_iter_rev)||
|[from\_json](#from_json)||
|[head](#head)||
|[head\_exn](#head_exn)||
|[init\_](#init_)||
|[intercalate](#intercalate)||
|[intersperse](#intersperse)||
|[is\_empty](#is_empty)||
|[is\_prefix](#is_prefix)||
|[is\_suffix](#is_suffix)||
|[iter](#iter)||
|[iter2](#iter2)||
|[last](#last)||
|[length](#length)||
|[lookup](#lookup)||
|[map](#map)||
|[mapi](#mapi)||
|[maximum](#maximum)||
|[minimum](#minimum)||
|[nth](#nth)||
|[nth\_exn](#nth_exn)||
|[of](#of)||
|[remove](#remove)||
|[remove\_at](#remove_at)||
|[repeat](#repeat)||
|[rev](#rev)||
|[rev\_concat](#rev_concat)||
|[rev\_fold](#rev_fold)||
|[rev\_foldi](#rev_foldi)||
|[rev\_map](#rev_map)||
|[scan\_left](#scan_left)||
|[scan\_right](#scan_right)||
|[singleton](#singleton)||
|[sort](#sort)||
|[tail](#tail)||
|[take](#take)||
|[take\_while](#take_while)||
|[to\_array](#to_array)||
|[to\_json](#to_json)||
|[unfold](#unfold)||
|[unsafe\_head](#unsafe_head)||
|[unsafe\_last](#unsafe_last)||
|[unsafe\_maximum](#unsafe_maximum)||
|[unsafe\_minimum](#unsafe_minimum)||
|[unsafe\_nth](#unsafe_nth)||
|[unzip](#unzip)||
|[zip](#zip)||

## T

```moonbit
:::source,moonbitlang/core/immut/list/types.mbt,16:::pub(all) enum T[A] {
  Nil
  Cons(A, <a href="moonbitlang/core/immut/list#T">T</a>[A])
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,736:::impl[A] <a href="moonbitlang/core/builtin#Add">Add</a> for <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/list/list.mbt,736:::fn op_add[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], other : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
    ```
    > 
    >  Concatenate two lists.
    > 
    >  `a + b` equal to `a.concat(b)`
- ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,1034:::impl[X] <a href="moonbitlang/core/builtin#Default">Default</a> for <a href="moonbitlang/core/immut/list#T">T</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/list/list.mbt,1034:::fn default[X]() -> <a href="moonbitlang/core/immut/list#T">T</a>[X]
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/list/types.mbt,19:::impl[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/list/types.mbt,19:::fn op_equal[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](<a href="moonbitlang/core/immut/list#T">T</a>[A], <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,1110:::impl[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>] <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/list/list.mbt,1110:::fn hash_combine[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,21:::impl[A : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/list/list.mbt,21:::fn output[A : <a href="moonbitlang/core/builtin#Show">Show</a>](xs : <a href="moonbitlang/core/immut/list#T">T</a>[A], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,26:::impl[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/list/list.mbt,26:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,42:::impl[A : <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a>] <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/list/list.mbt,42:::fn from_json[A : <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a>](json : <a href="moonbitlang/core/json#Json">Json</a>, path : <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,1097:::impl[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for <a href="moonbitlang/core/immut/list#T">T</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/immut/list/list.mbt,1097:::fn arbitrary[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>](size : Int, rs : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> <a href="moonbitlang/core/immut/list#T">T</a>[X]
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### add
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,16:::fn <a href="moonbitlang/core/immut/list#T">T</a>::add[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], head : A) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
- #### all
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,209:::fn <a href="moonbitlang/core/immut/list#T">T</a>::all[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> Bool) -> Bool
  ```
  > 
  >  Test if all elements of the list satisfy the predicate.
- #### any
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,218:::fn <a href="moonbitlang/core/immut/list#T">T</a>::any[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> Bool) -> Bool
  ```
  > 
  >  Test if any element of the list satisfies the predicate.
- #### concat
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,307:::fn <a href="moonbitlang/core/immut/list#T">T</a>::concat[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], other : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  >  Concatenate two lists.
  > 
  >  #### Example
  > 
  >  ```
  >  let ls = @list.of([1, 2, 3, 4, 5]).concat(@list.of([6, 7, 8, 9, 10]))
  >  assert_eq!(ls, @list.of([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]))
  >  ```
- #### concat\_map
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,498:::fn <a href="moonbitlang/core/immut/list#T">T</a>::concat_map[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> <a href="moonbitlang/core/immut/list#T">T</a>[B]) -> <a href="moonbitlang/core/immut/list#T">T</a>[B]
  ```
  > 
  >  map over the list and concat all results.
  > 
  >  `concat_map(f, ls)` equal to `ls.map(f).fold(Nil, fn(acc, x) { acc.concat(x) })))`
  > 
  >  #### Example
  > 
  >  ```
  >  let ls = @list.from_array([1, 2, 3])
  >  let r = ls.flat_map(fn(x) { @list.from_array([x, x * 2]) })
  >  assert_eq!(r, @list.from_array([1, 2, 2, 4, 3, 6]))
  >  ```
- #### contains
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,742:::fn <a href="moonbitlang/core/immut/list#T">T</a>::contains[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], value : A) -> Bool
  ```
  > 
  >  Check if the list contains the value.
- #### default
  ```moonbit
  :::source,moonbitlang/core/immut/list/deprecated.mbt,73:::fn <a href="moonbitlang/core/immut/list#T">T</a>::default[X]() -> <a href="moonbitlang/core/immut/list#T">T</a>[X]
  ```
  > 
- #### drop
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,801:::fn <a href="moonbitlang/core/immut/list#T">T</a>::drop[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], n : Int) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  >  Drop first n elements of the list.
  > If the list is shorter than n, return an empty list.
  > 
  >  #### Example
  > 
  >  ```
  >  let ls = @list.of([1, 2, 3, 4, 5])
  >  let r = ls.drop(3)
  >  assert_eq!(r, @list.of([4, 5]))
  >  ```
- #### drop\_while
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,842:::fn <a href="moonbitlang/core/immut/list#T">T</a>::drop_while[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], p : (A) -> Bool) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  >  Drop the longest prefix of a list of elements that satisfies a given predicate.
  > 
  >  #### Example
  > 
  >  ```
  >  let ls = @list.from_array([1, 2, 3, 4])
  >  let r = ls.drop_while(fn(x) { x < 3 })
  >  assert_eq!(r, @list.of([3, 4]))
  >  ```
- #### each
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,94:::fn <a href="moonbitlang/core/immut/list#T">T</a>::each[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> Unit) -> Unit
  ```
  > 
  >  Iterates over the list.
  > 
  >  #### Example
  > 
  >  ```
  >  let arr = []
  >  @list.of([1, 2, 3, 4, 5]).each(fn(x) { arr.push(x) })
  >  assert_eq!(arr, [1, 2, 3, 4, 5])
  >  ```
- #### eachi
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,114:::fn <a href="moonbitlang/core/immut/list#T">T</a>::eachi[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (Int, A) -> Unit) -> Unit
  ```
  > 
  >  Iterates over the list with index.
  > 
  >  #### Example
  > 
  >  ```
  >  let arr = []
  >  @list.of([1, 2, 3, 4, 5]).eachi(fn(i, x) { arr.push("(\{i},\{x})") })
  >  assert_eq!(arr, ["(0,1)", "(1,2)", "(2,3)", "(3,4)", "(4,5)"])
  >  ```
- #### equal
  ```moonbit
  :::source,moonbitlang/core/immut/list/deprecated.mbt,55:::fn <a href="moonbitlang/core/immut/list#T">T</a>::equal[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], other : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> Bool
  ```
  > 
  >  Compares two lists for equality.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@list.of([1, 2, 3]) == @list.of([1, 2, 3]), true)
  >  ```
- #### filter
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,195:::fn <a href="moonbitlang/core/immut/list#T">T</a>::filter[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> Bool) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  >  Filter the list.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@list.of([1, 2, 3, 4, 5]).filter(fn(x){ x % 2 == 0}), @list.of([2, 4]))
  >  ```
- #### filter\_map
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,531:::fn <a href="moonbitlang/core/immut/list#T">T</a>::filter_map[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> B?) -> <a href="moonbitlang/core/immut/list#T">T</a>[B]
  ```
  > 
  >  Map over the list and keep all `value`s for which the mapped result is `Some(value)`.
  > 
  >  #### Example
  > 
  >  ```
  >  let ls = @list.of([4, 2, 2, 6, 3, 1])
  >  let r = ls.filter_map(fn(x) { if (x >= 3) { Some(x) } else { None } })
  >  assert_eq!(r, @list.of([4, 6, 3]))
  >  ```
- #### find
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,915:::fn <a href="moonbitlang/core/immut/list#T">T</a>::find[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> Bool) -> A?
  ```
  > 
  >  Find the first element in the list that satisfies f.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@list.of([1, 3, 5, 8]).find(fn(element) -> Bool { element % 2 == 0}), Some(8))
  >  assert_eq!(@list.of([1, 3, 5]).find(fn(element) -> Bool { element % 2 == 0}), None)
  >  ```
- #### findi
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,936:::fn <a href="moonbitlang/core/immut/list#T">T</a>::findi[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A, Int) -> Bool) -> A?
  ```
  > 
  >  Find the first element in the list that satisfies f and passes the index as an argument.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@list.of([1, 3, 5, 8]).findi(fn(element, index) -> Bool { (element % 2 == 0) && (index == 3) }), Some(8))
  >  assert_eq!(@list.of([1, 3, 8, 5]).findi(fn(element, index) -> Bool { (element % 2 == 0) && (index == 3) }), None)
  >  ```
- #### flat\_map
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,514:::fn <a href="moonbitlang/core/immut/list#T">T</a>::flat_map[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> <a href="moonbitlang/core/immut/list#T">T</a>[B]) -> <a href="moonbitlang/core/immut/list#T">T</a>[B]
  ```
  > 
  >  map over the list and concat all results.
  > 
  >  `flat_map(f, ls)` equal to `ls.map(f).fold(Nil, fn(acc, x) { acc.concat(x) })))`
  > 
  >  #### Example
  > 
  >  ```
  >  let ls = @list.from_array([1, 2, 3])
  >  let r = ls.flat_map(fn(x) { @list.from_array([x, x * 2]) })
  >  assert_eq!(r, @list.from_array([1, 2, 2, 4, 3, 6]))
  >  ```
- #### flatten
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,642:::fn <a href="moonbitlang/core/immut/list#T">T</a>::flatten[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[<a href="moonbitlang/core/immut/list#T">T</a>[A]]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  >  flatten a list of lists.
  > 
  >  #### Example
  > 
  >  ```
  >  let ls = @list.flatten(@list.from_array([@list.from_array([1,2,3]), @list.from_array([4,5,6]), @list.from_array([7,8,9])]))
  >  assert_eq!(ls, @list.from_array([1, 2, 3, 4, 5, 6, 7, 8, 9]))
  >  ```
- #### fold
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,351:::fn <a href="moonbitlang/core/immut/list#T">T</a>::fold[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], init~ : B, f : (B, A) -> B) -> B
  ```
  > 
  >  Fold the list from left.
  > 
  >  #### Example
  > 
  >  ```
  >  let r = @list.of([1, 2, 3, 4, 5]).fold(init=0, fn(acc, x) { acc + x })
  >  assert_eq!(r, 15)
  >  ```
- #### fold\_left
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,384:::fn <a href="moonbitlang/core/immut/list#T">T</a>::fold_left[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (B, A) -> B, init~ : B) -> B
  ```
  > 
  >  Fold the list from left.
  > 
  >  #### Example
  > 
  >  ```
  >  let r = @list.of([1, 2, 3, 4, 5]).fold(init=0, fn(acc, x) { acc + x })
  >  assert_eq!(r, 15)
  >  ```
- #### fold\_lefti
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,435:::fn <a href="moonbitlang/core/immut/list#T">T</a>::fold_lefti[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (Int, B, A) -> B, init~ : B) -> B
  ```
  > 
  >  Fold the list from left with index.
- #### fold\_right
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,398:::fn <a href="moonbitlang/core/immut/list#T">T</a>::fold_right[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A, B) -> B, init~ : B) -> B
  ```
  > 
  >  Fold the list from right.
  > 
  >  #### Example
  >  ```
  >  let r = @list.of([1, 2, 3, 4, 5]).rev_fold(fn(x, acc) { x + acc }, init=0)
  >  assert_eq!(r, 15)
  >  ```
- #### fold\_righti
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,450:::fn <a href="moonbitlang/core/immut/list#T">T</a>::fold_righti[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (Int, A, B) -> B, init~ : B) -> B
  ```
  > 
  >  Fold the list from right with index.
- #### foldi
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,407:::fn <a href="moonbitlang/core/immut/list#T">T</a>::foldi[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], init~ : B, f : (Int, B, A) -> B) -> B
  ```
  > 
  >  Fold the list from left with index.
- #### from\_array
  ```moonbit
  :::source,moonbitlang/core/immut/list/deprecated.mbt,66:::fn <a href="moonbitlang/core/immut/list#T">T</a>::from_array[A](arr : <a href="moonbitlang/core/array#Array">Array</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
- #### from\_iter
  ```moonbit
  :::source,moonbitlang/core/immut/list/deprecated.mbt,80:::fn <a href="moonbitlang/core/immut/list#T">T</a>::from_iter[A](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
- #### from\_json
  ```moonbit
  :::source,moonbitlang/core/immut/list/deprecated.mbt,18:::fn <a href="moonbitlang/core/immut/list#T">T</a>::from_json[A : <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a>](json : <a href="moonbitlang/core/json#Json">Json</a>) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
  ```
  > 
- #### head
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,265:::fn <a href="moonbitlang/core/immut/list#T">T</a>::head[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> A?
  ```
  > 
  >  Get first element of the list.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@list.of([1, 2, 3, 4, 5]).head(), Some(1))
  >  ```
- #### head\_exn
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,253:::fn <a href="moonbitlang/core/immut/list#T">T</a>::head_exn[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> A
  ```
  > 
- #### init\_
  ```moonbit
  :::source,moonbitlang/core/immut/list/deprecated.mbt,34:::fn <a href="moonbitlang/core/immut/list#T">T</a>::init_[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  >  Init of the list.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@list.of([1, 2, 3, 4, 5]).init_(), @list.of([1, 2, 3, 4]))
  >  ```
- #### intercalate
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,1029:::fn <a href="moonbitlang/core/immut/list#T">T</a>::intercalate[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[<a href="moonbitlang/core/immut/list#T">T</a>[A]], sep : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  >  Similar to intersperse but with a list of values.
  > 
  >  #### Example
  >  ```
  >  let ls = @list.of([
  >     @list.of([1, 2, 3]),
  >     @list.of([4, 5, 6]),
  >     @list.of([7, 8, 9]),
  >  ])
  >  let r = ls.intercalate(@list.of([0]))
  >  assert_eq!(r, @list.of([1, 2, 3, 0, 4, 5, 6, 0, 7, 8, 9]))
  >  ```
- #### intersperse
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,594:::fn <a href="moonbitlang/core/immut/list#T">T</a>::intersperse[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], separator : A) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  >  Insert separator to the list.
  > 
  >  #### Example
  > 
  >  ```
  >  let ls = @list.intersperse(@list.from_array(["1", "2", "3", "4", "5"]), "|")
  >  assert_eq!(ls, @list.from_array(["1", "|", "2", "|", "3", "|", "4", "|", "5"]))
  >  ```
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,605:::fn <a href="moonbitlang/core/immut/list#T">T</a>::is_empty[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> Bool
  ```
  > 
  >  Check if the list is empty.
- #### is\_prefix
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,996:::fn <a href="moonbitlang/core/immut/list#T">T</a>::is_prefix[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], prefix : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> Bool
  ```
  > 
  >  Returns true if list starts with prefix.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@list.of([1, 2, 3, 4, 5]).is_prefix(@list.of([1, 2, 3])), true)
  >  ```
- #### is\_suffix
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,1012:::fn <a href="moonbitlang/core/immut/list#T">T</a>::is_suffix[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], suffix : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> Bool
  ```
  > 
  >  Returns true if list ends with suffix.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@list.of([1, 2, 3, 4, 5]).is_suffix(@list.of([3, 4, 5])), true)
  >  ```
- #### iter
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,1045:::fn <a href="moonbitlang/core/immut/list#T">T</a>::iter[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
  ```
  > 
- #### iter2
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,1060:::fn <a href="moonbitlang/core/immut/list#T">T</a>::iter2[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[Int, A]
  ```
  > 
- #### last
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,290:::fn <a href="moonbitlang/core/immut/list#T">T</a>::last[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> A?
  ```
  > 
  >  Last element of the list.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@list.of([1, 2, 3, 4, 5]).last(), Some(5))
  >  ```
- #### length
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,77:::fn <a href="moonbitlang/core/immut/list#T">T</a>::length[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> Int
  ```
  > 
  >  Get the length of the list.
- #### lookup
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,899:::fn <a href="moonbitlang/core/immut/list#T">T</a>::lookup[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[(A, B)], v : A) -> B?
  ```
  > 
  >  Looks up a key in an association list.
  > 
  >  #### Example
  > 
  >  ```
  >  let ls = @list.from_array([(1, "a"), (2, "b"), (3, "c")])
  >  assert_eq!(ls.lookup(3), Some("c"))
  >  ```
- #### map
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,132:::fn <a href="moonbitlang/core/immut/list#T">T</a>::map[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> B) -> <a href="moonbitlang/core/immut/list#T">T</a>[B]
  ```
  > 
  >  Maps the list.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@list.of([1, 2, 3, 4, 5]).map(fn(x){ x * 2}), @list.of([2, 4, 6, 8, 10]))
  >  ```
- #### mapi
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,141:::fn <a href="moonbitlang/core/immut/list#T">T</a>::mapi[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (Int, A) -> B) -> <a href="moonbitlang/core/immut/list#T">T</a>[B]
  ```
  > 
  >  Maps the list with index.
- #### maximum
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,669:::fn <a href="moonbitlang/core/immut/list#T">T</a>::maximum[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> A?
  ```
  > 
  >  Get maximum element of the list.
  > Returns None if the list is empty.
- #### minimum
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,700:::fn <a href="moonbitlang/core/immut/list#T">T</a>::minimum[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> A?
  ```
  > 
  >  Get minimum element of the list.
- #### nth
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,561:::fn <a href="moonbitlang/core/immut/list#T">T</a>::nth[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], n : Int) -> A?
  ```
  > 
  >  Get nth element of the list or None if the index is out of bounds
- #### nth\_exn
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,555:::fn <a href="moonbitlang/core/immut/list#T">T</a>::nth_exn[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], n : Int) -> A
  ```
  > 
- #### of
  ```moonbit
  :::source,moonbitlang/core/immut/list/deprecated.mbt,87:::fn <a href="moonbitlang/core/immut/list#T">T</a>::of[A](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
- #### remove
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,976:::fn <a href="moonbitlang/core/immut/list#T">T</a>::remove[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], elem : A) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  >  Removes the first occurrence of the specified element from the list, if it is present.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@list.of([1, 2, 3, 4, 5]).remove(3), @list.of([1, 2, 4, 5]))
  >  ```
- #### remove\_at
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,959:::fn <a href="moonbitlang/core/immut/list#T">T</a>::remove_at[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], index : Int) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  >  Removes the element at the specified index in the list.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@list.of([1, 2, 3, 4, 5]).remove_at(2), @list.of([1, 2, 4, 5]))
  >  ```
- #### rev
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,338:::fn <a href="moonbitlang/core/immut/list#T">T</a>::rev[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  >  Reverse the list.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@list.of([1, 2, 3, 4, 5]).rev(), @list.of([5, 4, 3, 2, 1]))
  >  ```
- #### rev\_concat
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,323:::fn <a href="moonbitlang/core/immut/list#T">T</a>::rev_concat[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], other : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  >  Reverse the first list and concatenate it with the second.
  > 
  >  #### Example
  > 
  >  ```
  >  let ls = @list.of([1, 2, 3, 4, 5]).rev_concat(@list.of([6, 7, 8, 9, 10]))
  >  assert_eq!(ls, @list.of([5, 4, 3, 2, 1, 6, 7, 8, 9, 10]))
  >  ```
- #### rev\_fold
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,366:::fn <a href="moonbitlang/core/immut/list#T">T</a>::rev_fold[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], init~ : B, f : (A, B) -> B) -> B
  ```
  > 
  >  Fold the list from right.
  > 
  >  #### Example
  >  ```
  >  let r = @list.of([1, 2, 3, 4, 5]).rev_fold(fn(x, acc) { x + acc }, init=0)
  >  assert_eq!(r, 15)
  >  ```
- #### rev\_foldi
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,420:::fn <a href="moonbitlang/core/immut/list#T">T</a>::rev_foldi[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], init~ : B, f : (Int, A, B) -> B) -> B
  ```
  > 
  >  Fold the list from right with index.
- #### rev\_map
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,161:::fn <a href="moonbitlang/core/immut/list#T">T</a>::rev_map[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> B) -> <a href="moonbitlang/core/immut/list#T">T</a>[B]
  ```
  > 
  >  Maps the list and reverses the result.
  > 
  >  `list.rev_map(f)` is equivalent to `list.map(f).rev()` but more efficient.
  > 
  >  #### Example
  >  ```
  >  assert_eq!(@list.of([1, 2, 3, 4, 5]).rev_map(fn(x) { x * 2 }), @list.of([10, 8, 6, 4, 2]))
  >  ```
- #### scan\_left
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,859:::fn <a href="moonbitlang/core/immut/list#T">T</a>::scan_left[A, E](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (E, A) -> E, init~ : E) -> <a href="moonbitlang/core/immut/list#T">T</a>[E]
  ```
  > 
  >  Fold a list and return a list of successive reduced values from the left
  > 
  >  #### Example
  > 
  >  ```
  >  let ls = @list.of([1, 2, 3, 4, 5])
  >  let r = ls.scan_left(fn(acc, x) { acc + x }, init=0)
  >  assert_eq!(r, @list.of([0, 1, 3, 6, 10, 15]))
  >  ```
- #### scan\_right
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,880:::fn <a href="moonbitlang/core/immut/list#T">T</a>::scan_right[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A, B) -> B, init~ : B) -> <a href="moonbitlang/core/immut/list#T">T</a>[B]
  ```
  > 
  >  Fold a list and return a list of successive reduced values from the right
  > 
  >  Note that the order of parameters on the accumulating function are reversed.
  > 
  >  #### Example
  >  ```
  >  let ls = @list.of([1, 2, 3, 4, 5])
  >  let r = ls.scan_right(fn(x, acc) { acc + x }, init=0)
  >  assert_eq!(r, @list.of([15, 14, 12, 9, 5, 0]))
  >  ```
- #### sort
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,721:::fn <a href="moonbitlang/core/immut/list#T">T</a>::sort[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  >  Sort the list in ascending order.
  > 
  >  #### Example
  > 
  >  ```
  >  let ls = @list.sort(@list.from_array([1,123,52,3,6,0,-6,-76]))
  >  assert_eq!(ls, @list.from_array([-76, -6, 0, 1, 3, 6, 52, 123]))
  >  ```
- #### tail
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,233:::fn <a href="moonbitlang/core/immut/list#T">T</a>::tail[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  >  Tail of the list.
  > 
  >  #### Example
  > 
  >  ```
  >  assert_eq!(@list.of([1, 2, 3, 4, 5]).tail(), @list.of([2, 3, 4, 5]))
  >  ```
- #### take
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,776:::fn <a href="moonbitlang/core/immut/list#T">T</a>::take[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], n : Int) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  >  Take first n elements of the list.
  > If the list is shorter than n, return the whole list.
  > 
  >  #### Example
  > 
  >  ```
  >  let ls = @list.of([1, 2, 3, 4, 5])
  >  let r = ls.take(3)
  >  assert_eq!(r, @list.of([1, 2, 3]))
  >  ```
- #### take\_while
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,825:::fn <a href="moonbitlang/core/immut/list#T">T</a>::take_while[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], p : (A) -> Bool) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
  ```
  > 
  >  Take the longest prefix of a list of elements that satisfies a given predicate.
  > 
  >  #### Example
  > 
  >  ```
  >  let ls = @list.from_array([1, 2, 3, 4])
  >  let r = ls.take_while(fn(x) { x < 3 })
  >  assert_eq!(r, @list.of([1, 2]))
  >  ```
- #### to\_array
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,170:::fn <a href="moonbitlang/core/immut/list#T">T</a>::to_array[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/array#Array">Array</a>[A]
  ```
  > 
  >  Convert list to array.
- #### to\_json
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,37:::fn <a href="moonbitlang/core/immut/list#T">T</a>::to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/json#Json">Json</a>
  ```
  > 
- #### unsafe\_head
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,243:::fn <a href="moonbitlang/core/immut/list#T">T</a>::unsafe_head[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> A
  ```
  > 
  >  Get first element of the list.
  > @alert unsafe "Panic if the list is empty"
- #### unsafe\_last
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,274:::fn <a href="moonbitlang/core/immut/list#T">T</a>::unsafe_last[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> A
  ```
  > 
  >  @alert unsafe "Panic if the list is empty"
- #### unsafe\_maximum
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,651:::fn <a href="moonbitlang/core/immut/list#T">T</a>::unsafe_maximum[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> A
  ```
  > 
  >  @alert unsafe "Panic if the list is empty"
- #### unsafe\_minimum
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,683:::fn <a href="moonbitlang/core/immut/list#T">T</a>::unsafe_minimum[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> A
  ```
  > 
  >  @alert unsafe "Panic if the list is empty"
- #### unsafe\_nth
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,544:::fn <a href="moonbitlang/core/immut/list#T">T</a>::unsafe_nth[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], n : Int) -> A
  ```
  > 
  >  @alert unsafe "Panic if the index is out of bounds"
- #### unzip
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,619:::fn <a href="moonbitlang/core/immut/list#T">T</a>::unzip[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[(A, B)]) -> (<a href="moonbitlang/core/immut/list#T">T</a>[A], <a href="moonbitlang/core/immut/list#T">T</a>[B])
  ```
  > 
  >  Unzip two lists.
  > 
  >  #### Example
  > 
  >  ```
  >  let (a,b) = @list.unzip(@list.from_array([(1,2),(3,4),(5,6)]))
  >  assert_eq!(a, @list.from_array([1, 3, 5]))
  >  assert_eq!(b, @list.from_array([2, 4, 6]))
  >  ```
- #### zip
  ```moonbit
  :::source,moonbitlang/core/immut/list/list.mbt,471:::fn <a href="moonbitlang/core/immut/list#T">T</a>::zip[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], other : <a href="moonbitlang/core/immut/list#T">T</a>[B]) -> <a href="moonbitlang/core/immut/list#T">T</a>[(A, B)]?
  ```
  > 
  >  Zip two lists.
  > If the lists have different lengths, it will return None.
  > 
  >  #### Example
  > 
  >  ```
  >  let r = @list.zip(@list.of([1, 2, 3, 4, 5]), @list.of([6, 7, 8, 9, 10]))
  >  assert_eq!(r, Some(@list.from_array([(1, 6), (2, 7), (3, 8), (4, 9), (5, 10)])))
  >  ```

## add

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,16:::fn add[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], head : A) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```


## all

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,209:::fn all[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> Bool) -> Bool
```

 Test if all elements of the list satisfy the predicate.

## any

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,218:::fn any[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> Bool) -> Bool
```

 Test if any element of the list satisfies the predicate.

## concat

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,307:::fn concat[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], other : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 Concatenate two lists.

 #### Example

 ```
 let ls = @list.of([1, 2, 3, 4, 5]).concat(@list.of([6, 7, 8, 9, 10]))
 assert_eq!(ls, @list.of([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]))
 ```

## concat\_map

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,498:::fn concat_map[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> <a href="moonbitlang/core/immut/list#T">T</a>[B]) -> <a href="moonbitlang/core/immut/list#T">T</a>[B]
```

 map over the list and concat all results.

 `concat_map(f, ls)` equal to `ls.map(f).fold(Nil, fn(acc, x) { acc.concat(x) })))`

 #### Example

 ```
 let ls = @list.from_array([1, 2, 3])
 let r = ls.flat_map(fn(x) { @list.from_array([x, x * 2]) })
 assert_eq!(r, @list.from_array([1, 2, 2, 4, 3, 6]))
 ```

## contains

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,742:::fn contains[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], value : A) -> Bool
```

 Check if the list contains the value.

## default

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,1040:::fn default[X]() -> <a href="moonbitlang/core/immut/list#T">T</a>[X]
```

 The empty list

## drop

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,801:::fn drop[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], n : Int) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 Drop first n elements of the list.
If the list is shorter than n, return an empty list.

 #### Example

 ```
 let ls = @list.of([1, 2, 3, 4, 5])
 let r = ls.drop(3)
 assert_eq!(r, @list.of([4, 5]))
 ```

## drop\_while

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,842:::fn drop_while[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], p : (A) -> Bool) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 Drop the longest prefix of a list of elements that satisfies a given predicate.

 #### Example

 ```
 let ls = @list.from_array([1, 2, 3, 4])
 let r = ls.drop_while(fn(x) { x < 3 })
 assert_eq!(r, @list.of([3, 4]))
 ```

## each

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,94:::fn each[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> Unit) -> Unit
```

 Iterates over the list.

 #### Example

 ```
 let arr = []
 @list.of([1, 2, 3, 4, 5]).each(fn(x) { arr.push(x) })
 assert_eq!(arr, [1, 2, 3, 4, 5])
 ```

## eachi

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,114:::fn eachi[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (Int, A) -> Unit) -> Unit
```

 Iterates over the list with index.

 #### Example

 ```
 let arr = []
 @list.of([1, 2, 3, 4, 5]).eachi(fn(i, x) { arr.push("(\{i},\{x})") })
 assert_eq!(arr, ["(0,1)", "(1,2)", "(2,3)", "(3,4)", "(4,5)"])
 ```

## equal

```moonbit
:::source,moonbitlang/core/immut/list/deprecated.mbt,55:::fn equal[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], other : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> Bool
```

 Compares two lists for equality.

 #### Example

 ```
 assert_eq!(@list.of([1, 2, 3]) == @list.of([1, 2, 3]), true)
 ```

## filter

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,195:::fn filter[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> Bool) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 Filter the list.

 #### Example

 ```
 assert_eq!(@list.of([1, 2, 3, 4, 5]).filter(fn(x){ x % 2 == 0}), @list.of([2, 4]))
 ```

## filter\_map

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,531:::fn filter_map[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> B?) -> <a href="moonbitlang/core/immut/list#T">T</a>[B]
```

 Map over the list and keep all `value`s for which the mapped result is `Some(value)`.

 #### Example

 ```
 let ls = @list.of([4, 2, 2, 6, 3, 1])
 let r = ls.filter_map(fn(x) { if (x >= 3) { Some(x) } else { None } })
 assert_eq!(r, @list.of([4, 6, 3]))
 ```

## find

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,915:::fn find[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> Bool) -> A?
```

 Find the first element in the list that satisfies f.

 #### Example

 ```
 assert_eq!(@list.of([1, 3, 5, 8]).find(fn(element) -> Bool { element % 2 == 0}), Some(8))
 assert_eq!(@list.of([1, 3, 5]).find(fn(element) -> Bool { element % 2 == 0}), None)
 ```

## findi

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,936:::fn findi[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A, Int) -> Bool) -> A?
```

 Find the first element in the list that satisfies f and passes the index as an argument.

 #### Example

 ```
 assert_eq!(@list.of([1, 3, 5, 8]).findi(fn(element, index) -> Bool { (element % 2 == 0) && (index == 3) }), Some(8))
 assert_eq!(@list.of([1, 3, 8, 5]).findi(fn(element, index) -> Bool { (element % 2 == 0) && (index == 3) }), None)
 ```

## flat\_map

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,514:::fn flat_map[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> <a href="moonbitlang/core/immut/list#T">T</a>[B]) -> <a href="moonbitlang/core/immut/list#T">T</a>[B]
```

 map over the list and concat all results.

 `flat_map(f, ls)` equal to `ls.map(f).fold(Nil, fn(acc, x) { acc.concat(x) })))`

 #### Example

 ```
 let ls = @list.from_array([1, 2, 3])
 let r = ls.flat_map(fn(x) { @list.from_array([x, x * 2]) })
 assert_eq!(r, @list.from_array([1, 2, 2, 4, 3, 6]))
 ```

## flatten

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,642:::fn flatten[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[<a href="moonbitlang/core/immut/list#T">T</a>[A]]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 flatten a list of lists.

 #### Example

 ```
 let ls = @list.flatten(@list.from_array([@list.from_array([1,2,3]), @list.from_array([4,5,6]), @list.from_array([7,8,9])]))
 assert_eq!(ls, @list.from_array([1, 2, 3, 4, 5, 6, 7, 8, 9]))
 ```

## fold

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,351:::fn fold[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], init~ : B, f : (B, A) -> B) -> B
```

 Fold the list from left.

 #### Example

 ```
 let r = @list.of([1, 2, 3, 4, 5]).fold(init=0, fn(acc, x) { acc + x })
 assert_eq!(r, 15)
 ```

## fold\_left

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,384:::fn fold_left[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (B, A) -> B, init~ : B) -> B
```

 Fold the list from left.

 #### Example

 ```
 let r = @list.of([1, 2, 3, 4, 5]).fold(init=0, fn(acc, x) { acc + x })
 assert_eq!(r, 15)
 ```

## fold\_lefti

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,435:::fn fold_lefti[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (Int, B, A) -> B, init~ : B) -> B
```

 Fold the list from left with index.

## fold\_right

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,398:::fn fold_right[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A, B) -> B, init~ : B) -> B
```

 Fold the list from right.

 #### Example
 ```
 let r = @list.of([1, 2, 3, 4, 5]).rev_fold(fn(x, acc) { x + acc }, init=0)
 assert_eq!(r, 15)
 ```

## fold\_righti

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,450:::fn fold_righti[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (Int, A, B) -> B, init~ : B) -> B
```

 Fold the list from right with index.

## foldi

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,407:::fn foldi[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], init~ : B, f : (Int, B, A) -> B) -> B
```

 Fold the list from left with index.

## from\_array

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,67:::fn from_array[A](arr : <a href="moonbitlang/core/array#Array">Array</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 Convert array to list.

 #### Example

 ```
 let ls = @list.of([1, 2, 3, 4, 5])
 assert_eq!(ls, @list.from_array([1, 2, 3, 4, 5]))
 ```

## from\_iter

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,1078:::fn from_iter[A](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 Convert the iterator into a list. Preserves order of elements.
This function is tail-recursive, but consumes 2\*n memory.
If the order of elements is not important, use `from_iter_rev` instead.

## from\_iter\_rev

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,1083:::fn from_iter_rev[A](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```


## from\_json

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,54:::fn from_json[A : <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a>](json : <a href="moonbitlang/core/json#Json">Json</a>) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
```


## head

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,265:::fn head[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> A?
```

 Get first element of the list.

 #### Example

 ```
 assert_eq!(@list.of([1, 2, 3, 4, 5]).head(), Some(1))
 ```

## head\_exn

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,253:::fn head_exn[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> A
```


## init\_

```moonbit
:::source,moonbitlang/core/immut/list/deprecated.mbt,34:::fn init_[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 Init of the list.

 #### Example

 ```
 assert_eq!(@list.of([1, 2, 3, 4, 5]).init_(), @list.of([1, 2, 3, 4]))
 ```

## intercalate

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,1029:::fn intercalate[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[<a href="moonbitlang/core/immut/list#T">T</a>[A]], sep : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 Similar to intersperse but with a list of values.

 #### Example
 ```
 let ls = @list.of([
    @list.of([1, 2, 3]),
    @list.of([4, 5, 6]),
    @list.of([7, 8, 9]),
 ])
 let r = ls.intercalate(@list.of([0]))
 assert_eq!(r, @list.of([1, 2, 3, 0, 4, 5, 6, 0, 7, 8, 9]))
 ```

## intersperse

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,594:::fn intersperse[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], separator : A) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 Insert separator to the list.

 #### Example

 ```
 let ls = @list.intersperse(@list.from_array(["1", "2", "3", "4", "5"]), "|")
 assert_eq!(ls, @list.from_array(["1", "|", "2", "|", "3", "|", "4", "|", "5"]))
 ```

## is\_empty

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,605:::fn is_empty[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> Bool
```

 Check if the list is empty.

## is\_prefix

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,996:::fn is_prefix[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], prefix : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> Bool
```

 Returns true if list starts with prefix.

 #### Example

 ```
 assert_eq!(@list.of([1, 2, 3, 4, 5]).is_prefix(@list.of([1, 2, 3])), true)
 ```

## is\_suffix

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,1012:::fn is_suffix[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], suffix : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> Bool
```

 Returns true if list ends with suffix.

 #### Example

 ```
 assert_eq!(@list.of([1, 2, 3, 4, 5]).is_suffix(@list.of([3, 4, 5])), true)
 ```

## iter

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,1045:::fn iter[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
```


## iter2

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,1060:::fn iter2[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[Int, A]
```


## last

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,290:::fn last[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> A?
```

 Last element of the list.

 #### Example

 ```
 assert_eq!(@list.of([1, 2, 3, 4, 5]).last(), Some(5))
 ```

## length

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,77:::fn length[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> Int
```

 Get the length of the list.

## lookup

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,899:::fn lookup[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[(A, B)], v : A) -> B?
```

 Looks up a key in an association list.

 #### Example

 ```
 let ls = @list.from_array([(1, "a"), (2, "b"), (3, "c")])
 assert_eq!(ls.lookup(3), Some("c"))
 ```

## map

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,132:::fn map[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> B) -> <a href="moonbitlang/core/immut/list#T">T</a>[B]
```

 Maps the list.

 #### Example

 ```
 assert_eq!(@list.of([1, 2, 3, 4, 5]).map(fn(x){ x * 2}), @list.of([2, 4, 6, 8, 10]))
 ```

## mapi

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,141:::fn mapi[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (Int, A) -> B) -> <a href="moonbitlang/core/immut/list#T">T</a>[B]
```

 Maps the list with index.

## maximum

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,669:::fn maximum[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> A?
```

 Get maximum element of the list.
Returns None if the list is empty.

## minimum

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,700:::fn minimum[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> A?
```

 Get minimum element of the list.

## nth

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,561:::fn nth[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], n : Int) -> A?
```

 Get nth element of the list or None if the index is out of bounds

## nth\_exn

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,555:::fn nth_exn[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], n : Int) -> A
```


## of

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,1088:::fn of[A](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```


## remove

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,976:::fn remove[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], elem : A) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 Removes the first occurrence of the specified element from the list, if it is present.

 #### Example

 ```
 assert_eq!(@list.of([1, 2, 3, 4, 5]).remove(3), @list.of([1, 2, 4, 5]))
 ```

## remove\_at

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,959:::fn remove_at[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], index : Int) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 Removes the element at the specified index in the list.

 #### Example

 ```
 assert_eq!(@list.of([1, 2, 3, 4, 5]).remove_at(2), @list.of([1, 2, 4, 5]))
 ```

## repeat

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,577:::fn repeat[A](n : Int, x : A) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 Create a list of length n with the given value

 #### Example

 ```
 assert_eq!(@list.repeat(5, 1), @list.from_array([1, 1, 1, 1, 1]))
 ```

## rev

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,338:::fn rev[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 Reverse the list.

 #### Example

 ```
 assert_eq!(@list.of([1, 2, 3, 4, 5]).rev(), @list.of([5, 4, 3, 2, 1]))
 ```

## rev\_concat

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,323:::fn rev_concat[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], other : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 Reverse the first list and concatenate it with the second.

 #### Example

 ```
 let ls = @list.of([1, 2, 3, 4, 5]).rev_concat(@list.of([6, 7, 8, 9, 10]))
 assert_eq!(ls, @list.of([5, 4, 3, 2, 1, 6, 7, 8, 9, 10]))
 ```

## rev\_fold

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,366:::fn rev_fold[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], init~ : B, f : (A, B) -> B) -> B
```

 Fold the list from right.

 #### Example
 ```
 let r = @list.of([1, 2, 3, 4, 5]).rev_fold(fn(x, acc) { x + acc }, init=0)
 assert_eq!(r, 15)
 ```

## rev\_foldi

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,420:::fn rev_foldi[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], init~ : B, f : (Int, A, B) -> B) -> B
```

 Fold the list from right with index.

## rev\_map

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,161:::fn rev_map[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A) -> B) -> <a href="moonbitlang/core/immut/list#T">T</a>[B]
```

 Maps the list and reverses the result.

 `list.rev_map(f)` is equivalent to `list.map(f).rev()` but more efficient.

 #### Example
 ```
 assert_eq!(@list.of([1, 2, 3, 4, 5]).rev_map(fn(x) { x * 2 }), @list.of([10, 8, 6, 4, 2]))
 ```

## scan\_left

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,859:::fn scan_left[A, E](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (E, A) -> E, init~ : E) -> <a href="moonbitlang/core/immut/list#T">T</a>[E]
```

 Fold a list and return a list of successive reduced values from the left

 #### Example

 ```
 let ls = @list.of([1, 2, 3, 4, 5])
 let r = ls.scan_left(fn(acc, x) { acc + x }, init=0)
 assert_eq!(r, @list.of([0, 1, 3, 6, 10, 15]))
 ```

## scan\_right

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,880:::fn scan_right[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], f : (A, B) -> B, init~ : B) -> <a href="moonbitlang/core/immut/list#T">T</a>[B]
```

 Fold a list and return a list of successive reduced values from the right

 Note that the order of parameters on the accumulating function are reversed.

 #### Example
 ```
 let ls = @list.of([1, 2, 3, 4, 5])
 let r = ls.scan_right(fn(x, acc) { acc + x }, init=0)
 assert_eq!(r, @list.of([15, 14, 12, 9, 5, 0]))
 ```

## singleton

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,1105:::fn singleton[A](x : A) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```


## sort

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,721:::fn sort[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 Sort the list in ascending order.

 #### Example

 ```
 let ls = @list.sort(@list.from_array([1,123,52,3,6,0,-6,-76]))
 assert_eq!(ls, @list.from_array([-76, -6, 0, 1, 3, 6, 52, 123]))
 ```

## tail

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,233:::fn tail[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 Tail of the list.

 #### Example

 ```
 assert_eq!(@list.of([1, 2, 3, 4, 5]).tail(), @list.of([2, 3, 4, 5]))
 ```

## take

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,776:::fn take[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], n : Int) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 Take first n elements of the list.
If the list is shorter than n, return the whole list.

 #### Example

 ```
 let ls = @list.of([1, 2, 3, 4, 5])
 let r = ls.take(3)
 assert_eq!(r, @list.of([1, 2, 3]))
 ```

## take\_while

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,825:::fn take_while[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], p : (A) -> Bool) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 Take the longest prefix of a list of elements that satisfies a given predicate.

 #### Example

 ```
 let ls = @list.from_array([1, 2, 3, 4])
 let r = ls.take_while(fn(x) { x < 3 })
 assert_eq!(r, @list.of([1, 2]))
 ```

## to\_array

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,170:::fn to_array[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/array#Array">Array</a>[A]
```

 Convert list to array.

## to\_json

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,37:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> <a href="moonbitlang/core/json#Json">Json</a>
```


## unfold

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,758:::fn unfold[A, S](f : (S) -> (A, S)?, init~ : S) -> <a href="moonbitlang/core/immut/list#T">T</a>[A]
```

 Produces a collection iteratively.

 #### Example

 ```
 let r = @list.unfold(init=0, fn { i => if i == 3 { None } else { Some((i, i + 1)) } })
 assert_eq!(r, @list.from_array([0, 1, 2]))
 ```

## unsafe\_head

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,243:::fn unsafe_head[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> A
```

 Get first element of the list.
@alert unsafe "Panic if the list is empty"

## unsafe\_last

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,274:::fn unsafe_last[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> A
```

 @alert unsafe "Panic if the list is empty"

## unsafe\_maximum

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,651:::fn unsafe_maximum[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> A
```

 @alert unsafe "Panic if the list is empty"

## unsafe\_minimum

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,683:::fn unsafe_minimum[A : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/immut/list#T">T</a>[A]) -> A
```

 @alert unsafe "Panic if the list is empty"

## unsafe\_nth

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,544:::fn unsafe_nth[A](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], n : Int) -> A
```

 @alert unsafe "Panic if the index is out of bounds"

## unzip

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,619:::fn unzip[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[(A, B)]) -> (<a href="moonbitlang/core/immut/list#T">T</a>[A], <a href="moonbitlang/core/immut/list#T">T</a>[B])
```

 Unzip two lists.

 #### Example

 ```
 let (a,b) = @list.unzip(@list.from_array([(1,2),(3,4),(5,6)]))
 assert_eq!(a, @list.from_array([1, 3, 5]))
 assert_eq!(b, @list.from_array([2, 4, 6]))
 ```

## zip

```moonbit
:::source,moonbitlang/core/immut/list/list.mbt,471:::fn zip[A, B](self : <a href="moonbitlang/core/immut/list#T">T</a>[A], other : <a href="moonbitlang/core/immut/list#T">T</a>[B]) -> <a href="moonbitlang/core/immut/list#T">T</a>[(A, B)]?
```

 Zip two lists.
If the lists have different lengths, it will return None.

 #### Example

 ```
 let r = @list.zip(@list.of([1, 2, 3, 4, 5]), @list.of([6, 7, 8, 9, 10]))
 assert_eq!(r, Some(@list.from_array([(1, 6), (2, 7), (3, 8), (4, 9), (5, 10)])))
 ```
