# Documentation
|Type|description|
|---|---|
|[T](#T)||

|Value|description|
|---|---|
|[capacity](#capacity)||
|[clear](#clear)||
|[contains](#contains)||
|[each](#each)||
|[eachi](#eachi)||
|[from\_array](#from_array)||
|[from\_iter](#from_iter)||
|[get](#get)||
|[get\_or\_default](#get_or_default)||
|[get\_or\_init](#get_or_init)||
|[is\_empty](#is_empty)||
|[iter](#iter)||
|[iter2](#iter2)||
|[new](#new)||
|[of](#of)||
|[op\_get](#op_get)||
|[op\_set](#op_set)||
|[remove](#remove)||
|[set](#set)||
|[size](#size)||
|[to\_array](#to_array)||

## T

```moonbit
:::source,moonbitlang/core/hashmap/types.mbt,41:::type T[K, V]
```

 Mutable hash map, not thread safe.

 #### Example

 ```
 let map = @hashmap.of([(3, "three"), (8, "eight"), (1, "one")])
 assert_eq!(map.get(2), None)
 assert_eq!(map.get(3), Some("three"))
 map.set(3, "updated")
 assert_eq!(map.get(3), Some("updated"))
 ```

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/hashmap/utils.mbt,388:::impl[K : <a href="moonbitlang/core/builtin#Show">Show</a>, V : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/hashmap#T">T</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/hashmap/utils.mbt,388:::fn output[K : <a href="moonbitlang/core/builtin#Show">Show</a>, V : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
    >  Provides string representation for hash maps.
    > 
    >  Parameters:
    > 
    >  * `self` : The hash map to be converted to string.
    >  * `logger` : The buffer to write the string representation to.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "show" {
    >    let map = @hashmap.of([(1, "one"), (2, "two")])
    >    inspect!(map, content=
    >    #|HashMap::of([(2, "two"), (1, "one")])
    >  )
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/hashmap/json.mbt,16:::impl[K : <a href="moonbitlang/core/builtin#Show">Show</a>, V : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="moonbitlang/core/hashmap#T">T</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/hashmap/json.mbt,16:::fn to_json[K : <a href="moonbitlang/core/builtin#Show">Show</a>, V : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V]) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/hashmap/hashmap.mbt,478:::impl[K : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for <a href="moonbitlang/core/hashmap#T">T</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/hashmap/hashmap.mbt,481:::fn arbitrary[K : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>](size : Int, rs : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> <a href="moonbitlang/core/hashmap#T">T</a>[K, V]
    ```
    > 
    >  Implements random generation of hashmaps for property-based testing through
    > the `Arbitrary` trait.
    > 
    >  Parameters:
    > 
    >  * `size` : The size hint for generating random key-value pairs. Larger values
    >    typically result in larger hashmaps.
    >  * `random_state` : The random state used for generating key-value pairs.
    > 
    >  Returns a randomly generated hashmap containing arbitrary key-value pairs.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "arbitrary" {
    >    let samples : Array[@hashmap.T[Int, String]] = @quickcheck.samples(5)
    >    inspect!(samples.length(), content="5")
    >  }
    >  ```

#### mooncakes-io-method-mark-Methods
- #### capacity
  ```moonbit
  :::source,moonbitlang/core/hashmap/utils.mbt,278:::fn <a href="moonbitlang/core/hashmap#T">T</a>::capacity[K, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V]) -> Int
  ```
  > 
  >  Returns the current capacity of the hash map. The capacity is the number of
  > key-value pairs the hash map can hold before it needs to reallocate its
  > internal storage.
  > 
  >  Parameters:
  > 
  >  * `map` : The hash map whose capacity is to be queried.
  > 
  >  Returns the number of key-value pairs that can be stored in the hash map
  > before triggering a reallocation.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "capacity" {
  >    let map : @hashmap.T[Int, String] = @hashmap.new(capacity=16)
  >    inspect!(map.capacity(), content="16")
  >  }
  >  ```
- #### clear
  ```moonbit
  :::source,moonbitlang/core/hashmap/utils.mbt,48:::fn <a href="moonbitlang/core/hashmap#T">T</a>::clear[K, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V]) -> Unit
  ```
  > 
  >  Removes all key-value pairs from the map while retaining the allocated
  > capacity. After calling this method, the size of the map will be zero but the
  > capacity remains unchanged.
  > 
  >  Parameters:
  > 
  >  * `self` : The hash map to be cleared.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "clear" {
  >    let map = @hashmap.of([("a", 1), ("b", 2)])
  >    map.clear()
  >    inspect!(map.size(), content="0")
  >    inspect!(map.get("a"), content="None")
  >  }
  >  ```
- #### contains
  ```moonbit
  :::source,moonbitlang/core/hashmap/hashmap.mbt,344:::fn <a href="moonbitlang/core/hashmap#T">T</a>::contains[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], key : K) -> Bool
  ```
  > 
  >  Checks if a key exists in the hash map.
  > 
  >  Parameters:
  > 
  >  * `self` : The hash map to search in.
  >  * `key` : The key to look for in the hash map.
  > 
  >  Returns `true` if the key exists in the hash map, `false` otherwise.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "contains" {
  >    let map = @hashmap.of([("a", 1), ("b", 2)])
  >    inspect!(map.contains("a"), content="true")
  >    inspect!(map.contains("c"), content="false")
  >  }
  >  ```
- #### each
  ```moonbit
  :::source,moonbitlang/core/hashmap/utils.mbt,326:::fn <a href="moonbitlang/core/hashmap#T">T</a>::each[K, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], f : (K, V) -> Unit) -> Unit
  ```
  > 
  >  Iterates over all key-value pairs in the hash map and applies the given
  > function to each pair.
  > 
  >  Parameters:
  > 
  >  * `map` : The hash map to iterate over.
  >  * `action` : A function that takes a key and a value as arguments and
  >    performs some action. The function should not return any value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "each" {
  >    let map = @hashmap.of([(1, "one"), (2, "two")])
  >    let mut result = ""
  >    map.each(fn(k, v) { result = result + "\{k}:\{v}," })
  >    inspect!(result, content="2:two,1:one,")
  >  }
  >  ```
- #### eachi
  ```moonbit
  :::source,moonbitlang/core/hashmap/utils.mbt,358:::fn <a href="moonbitlang/core/hashmap#T">T</a>::eachi[K, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], f : (Int, K, V) -> Unit) -> Unit
  ```
  > 
  >  Iterates over all key-value pairs in the map with their index, applying the
  > given function to each element. The index starts from 0 and only counts
  > non-empty entries.
  > 
  >  Parameters:
  > 
  >  * `self` : The hash map to iterate over.
  >  * `callback` : A function that takes three arguments:
  >   * An integer representing the index of the current key-value pair
  >   * The key of the current entry
  >   * The value of the current entry
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "eachi" {
  >    let map = @hashmap.of([("a", 1), ("b", 2), ("c", 3)])
  >    let mut result = 0
  >    map.eachi(fn(i, k, _) { if k == "b" { result = i } })
  >    // "b" is at index 1
  >    inspect!(result, content="2")
  >  }
  >  ```
- #### from\_array
  ```moonbit
  :::source,moonbitlang/core/hashmap/deprecated.mbt,68:::fn <a href="moonbitlang/core/hashmap#T">T</a>::from_array[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](arr : <a href="moonbitlang/core/array#Array">Array</a>[(K, V)]) -> <a href="moonbitlang/core/hashmap#T">T</a>[K, V]
  ```
  > 
  >  Creates a new hash map from an array of key-value pairs.
  > 
  >  Parameters:
  > 
  >  * `arr` : An array of tuples, where each tuple contains a key and its
  >    corresponding value.
  >   * Keys must implement both `Hash` and `Eq` traits
  >   * Values can be of any type
  > 
  >  Returns a new hash map containing all the key-value pairs from the array.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "T::from_array" {
  >    let map = @hashmap.from_array([(1, "one"), (2, "two")])
  >    inspect!(map.get(1), content="Some(\"one\")")
  >    inspect!(map.get(2), content="Some(\"two\")")
  >  }
  >  ```
  > 
- #### from\_iter
  ```moonbit
  :::source,moonbitlang/core/hashmap/utils.mbt,188:::fn <a href="moonbitlang/core/hashmap#T">T</a>::from_iter[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[(K, V)]) -> <a href="moonbitlang/core/hashmap#T">T</a>[K, V]
  ```
  > 
  >  Creates a new hash map and inserts all key-value pairs from the given
  > iterator.
  > 
  >  Parameters:
  > 
  >  * `iter` : An iterator of key-value pairs, where each pair consists of a
  >    hashable and equatable key of type `K` and a value of type `V`.
  > 
  >  Returns a new hash map containing all key-value pairs from the iterator.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "T::from_iter" {
  >    let pairs = [(1, "one"), (2, "two")]
  >    let map = @hashmap.from_iter(pairs.iter())
  >    inspect!(map.get(1), content="Some(\"one\")")
  >    inspect!(map.get(2), content="Some(\"two\")")
  >  }
  >  ```
  > 
- #### get
  ```moonbit
  :::source,moonbitlang/core/hashmap/hashmap.mbt,203:::fn <a href="moonbitlang/core/hashmap#T">T</a>::get[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], key : K) -> V?
  ```
  > 
  >  Retrieves the value associated with a given key in the hash map.
  > 
  >  Parameters:
  > 
  >  * `self` : The hash map to search in.
  >  * `key` : The key to look up in the map.
  > 
  >  Returns `Some(value)` if the key exists in the map, `None` otherwise.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "get" {
  >    let map = @hashmap.of([("key", 42)])
  >    inspect!(map.get("key"), content="Some(42)")
  >    inspect!(map.get("nonexistent"), content="None")
  >  }
  >  ```
- #### get\_or\_default
  ```moonbit
  :::source,moonbitlang/core/hashmap/hashmap.mbt,314:::fn <a href="moonbitlang/core/hashmap#T">T</a>::get_or_default[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], key : K, default : V) -> V
  ```
  > 
  >  Gets the value associated with a given key from the hash map. If the key
  > doesn't exist, returns the provided default value instead.
  > 
  >  Parameters:
  > 
  >  * `map` : The hash map to retrieve the value from.
  >  * `key` : The key to look up in the map.
  >  * `default` : The value to return if the key is not found in the map.
  > 
  >  Returns the value associated with the key if it exists, otherwise returns the
  > default value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "get_or_default" {
  >    let map = @hashmap.of([("a", 1), ("b", 2)])
  >    inspect!(map.get_or_default("a", 0), content="1")
  >    inspect!(map.get_or_default("c", 0), content="0")
  >  }
  >  ```
- #### get\_or\_init
  ```moonbit
  :::source,moonbitlang/core/hashmap/hashmap.mbt,276:::fn <a href="moonbitlang/core/hashmap#T">T</a>::get_or_init[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], key : K, init : () -> V) -> V
  ```
  > 
  >  Gets the value associated with the given key. If the key doesn't exist in the
  > map, initializes it with the result of calling the provided initialization
  > function.
  > 
  >  Parameters:
  > 
  >  * `self` : The hash map.
  >  * `key` : The key to look up in the map.
  >  * `init` : A function that takes no arguments and returns a value to be
  >    associated with the key if it doesn't exist.
  > 
  >  Returns the value associated with the key, either existing or newly
  > initialized.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "get_or_init" {
  >    let map : @hashmap.T[String, Int] = @hashmap.new()
  >    let value = map.get_or_init("key", fn() { 42 })
  >    inspect!(value, content="42")
  >    inspect!(map.get("key"), content="Some(42)")
  >  }
  >  ```
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/hashmap/utils.mbt,302:::fn <a href="moonbitlang/core/hashmap#T">T</a>::is_empty[K, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V]) -> Bool
  ```
  > 
  >  Returns whether the hash map contains no key-value pairs.
  > 
  >  Parameters:
  > 
  >  * `map` : The hash map to check.
  > 
  >  Returns `true` if the hash map contains no key-value pairs, `false`
  > otherwise.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "is_empty" {
  >    let map : @hashmap.T[String, Int] = @hashmap.new()
  >    inspect!(map.is_empty(), content="true")
  >    map.set("key", 42)
  >    inspect!(map.is_empty(), content="false")
  >  }
  >  ```
- #### iter
  ```moonbit
  :::source,moonbitlang/core/hashmap/utils.mbt,74:::fn <a href="moonbitlang/core/hashmap#T">T</a>::iter[K, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[(K, V)]
  ```
  > 
  >  Returns an iterator over the key-value pairs in the map.
  > 
  >  Parameters:
  > 
  >  * `map` : The hash map to iterate over.
  > 
  >  Returns an iterator that yields tuples of `(key, value)` for each entry in
  > the map, in unspecified order.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "iter" {
  >    let map = @hashmap.of([(1, "one"), (2, "two")])
  >    let pairs = map.iter().to_array()
  >    inspect!(pairs.length(), content="2")
  >    inspect!(pairs.contains((1, "one")), content="true")
  >    inspect!(pairs.contains((2, "two")), content="true")
  >  }
  >  ```
- #### iter2
  ```moonbit
  :::source,moonbitlang/core/hashmap/utils.mbt,112:::fn <a href="moonbitlang/core/hashmap#T">T</a>::iter2[K, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[K, V]
  ```
  > 
  >  Creates an iterator over the key-value pairs in the map, where the key and
  > value are passed as separate arguments to the yielding function.
  > 
  >  Parameters:
  > 
  >  * `map` : The hash map to iterate over.
  > 
  >  Returns an iterator `Iter2[K, V]` that yields each key-value pair in the map
  > as separate arguments. This differs from `iter()` which yields tuples of
  > key-value pairs.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "iter2" {
  >    let map = @hashmap.of([(1, "one"), (2, "two")])
  >    let mut sum = 0
  >    map.iter2().each(fn(k, _) { sum = sum + k })
  >    inspect!(sum, content="3")
  >  }
  >  ```
- #### new
  ```moonbit
  :::source,moonbitlang/core/hashmap/deprecated.mbt,40:::fn <a href="moonbitlang/core/hashmap#T">T</a>::new[K, V](capacity~ : Int = ..) -> <a href="moonbitlang/core/hashmap#T">T</a>[K, V]
  ```
  > 
  >  Creates a new empty hash map with the specified capacity. This is a
  > deprecated static method of type `T`.
  > 
  >  Parameters:
  > 
  >  * `capacity` : The initial capacity of the hash map. Must be a positive
  >    integer. The actual capacity will be rounded up to the nearest power of 2
  >    that is greater than or equal to this value. Defaults to 8 if not specified.
  > 
  >  Returns a new empty hash map of type `T[K, V]` where `K` is the key type and
  > `V` is the value type.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "T::new" {
  >    let map : @hashmap.T[String, Int] = @hashmap.new()
  >    inspect!(map.size(), content="0")
  >    inspect!(map.capacity(), content="8")
  >  }
  >  ```
  > 
- #### of
  ```moonbit
  :::source,moonbitlang/core/hashmap/deprecated.mbt,94:::fn <a href="moonbitlang/core/hashmap#T">T</a>::of[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[(K, V)]) -> <a href="moonbitlang/core/hashmap#T">T</a>[K, V]
  ```
  > 
  >  Creates a new hash map from a fixed array of key-value pairs.
  > 
  >  Parameters:
  > 
  >  * `arr` : A fixed array of key-value pairs. Each pair contains a hashable and
  >    equatable key of type `K` and a value of type `V`.
  > 
  >  Returns a new hash map containing all key-value pairs from the input array.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "T::of" {
  >    let map = @hashmap.of([(1, "one"), (2, "two")])
  >    inspect!(map.get(1), content="Some(\"one\")")
  >    inspect!(map.get(2), content="Some(\"two\")")
  >  }
  >  ```
  > 
- #### op\_get
  ```moonbit
  :::source,moonbitlang/core/hashmap/hashmap.mbt,247:::fn <a href="moonbitlang/core/hashmap#T">T</a>::op_get[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], key : K) -> V?
  ```
  > 
  >  Retrieves a value from the hash map using the index operator syntax. This
  > method is automatically called when using the square bracket notation
  > `map[key]`.
  > 
  >  Parameters:
  > 
  >  * `map` : The hash map to retrieve the value from.
  >  * `key` : The key to look up in the map. Must implement both `Hash` and `Eq`
  >    traits.
  > 
  >  Returns `Some(value)` if the key exists in the map, `None` otherwise.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "op_get" {
  >    let map = @hashmap.of([("key", 42)])
  >    inspect!(map["key"], content="Some(42)")
  >    inspect!(map["nonexistent"], content="None")
  >  }
  >  ```
- #### op\_set
  ```moonbit
  :::source,moonbitlang/core/hashmap/hashmap.mbt,180:::fn <a href="moonbitlang/core/hashmap#T">T</a>::op_set[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], key : K, value : V) -> Unit
  ```
  > 
  >  Sets the value associated with a key in the hash map. If the key already
  > exists, updates its value; otherwise, adds a new key-value pair. This
  > function is automatically called when using the index assignment syntax
  > `map[key] = value`.
  > 
  >  Parameters:
  > 
  >  * `map` : The hash map to modify.
  >  * `key` : The key to associate with the value. Must implement `Hash` and `Eq`
  >    traits.
  >  * `value` : The value to associate with the key.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "op_set" {
  >    let map : @hashmap.T[String, Int] = @hashmap.new()
  >    map["key"] = 42
  >    inspect!(map.get("key"), content="Some(42)")
  >  }
  >  ```
- #### remove
  ```moonbit
  :::source,moonbitlang/core/hashmap/hashmap.mbt,372:::fn <a href="moonbitlang/core/hashmap#T">T</a>::remove[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], key : K) -> Unit
  ```
  > 
  >  Removes the entry for the specified key from the hash map. If the key exists
  > in the map, removes its entry and adjusts the probe sequence length (PSL) of
  > subsequent entries to maintain the Robin Hood hashing invariant. If the key
  > does not exist, the map remains unchanged.
  > 
  >  Parameters:
  > 
  >  * `self` : The hash map to remove the entry from.
  >  * `key` : The key to remove from the map.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "remove" {
  >    let map = @hashmap.of([("a", 1), ("b", 2)])
  >    map.remove("a")
  >    inspect!(map.get("a"), content="None")
  >    inspect!(map.size(), content="1")
  >  }
  >  ```
- #### set
  ```moonbit
  :::source,moonbitlang/core/hashmap/hashmap.mbt,119:::fn <a href="moonbitlang/core/hashmap#T">T</a>::set[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], key : K, value : V) -> Unit
  ```
  > 
  >  Sets a key-value pair into the hash map. If the key already exists, updates
  > its value. If the hash map is near full capacity (\>= 50%), automatically
  > grows the internal storage to accommodate more entries.
  > 
  >  Parameters:
  > 
  >  * `map` : The hash map to modify.
  >  * `key` : The key to insert or update. Must implement `Hash` and `Eq` traits.
  >  * `value` : The value to associate with the key.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "set" {
  >    let map : @hashmap.T[String, Int] = @hashmap.new()
  >    map.set("key", 42)
  >    inspect!(map.get("key"), content="Some(42)")
  >    map.set("key", 24) // update existing key
  >    inspect!(map.get("key"), content="Some(24)")
  >  }
  >  ```
  > 
  >  @alert unsafe "Panic if the hash map is full."
- #### size
  ```moonbit
  :::source,moonbitlang/core/hashmap/utils.mbt,254:::fn <a href="moonbitlang/core/hashmap#T">T</a>::size[K, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V]) -> Int
  ```
  > 
  >  Returns the number of key-value pairs currently stored in the hash map.
  > 
  >  Parameters:
  > 
  >  * `self` : The hash map to get the size from.
  > 
  >  Returns the number of key-value pairs in the hash map.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "size" {
  >    let map = @hashmap.of([("a", 1), ("b", 2), ("c", 3)])
  >    inspect!(map.size(), content="3")
  >  }
  >  ```
- #### to\_array
  ```moonbit
  :::source,moonbitlang/core/hashmap/utils.mbt,213:::fn <a href="moonbitlang/core/hashmap#T">T</a>::to_array[K, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V]) -> <a href="moonbitlang/core/array#Array">Array</a>[(K, V)]
  ```
  > 
  >  Converts the hash map into an array of key-value pairs. The order of elements
  > in the resulting array follows the internal storage order of the hash map.
  > 
  >  Parameters:
  > 
  >  * `self` : The hash map to be converted.
  > 
  >  Returns an array containing tuples of key-value pairs from the hash map.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "to_array" {
  >    let map = @hashmap.of([(1, "one"), (2, "two")])
  >    let arr = map.to_array()
  >    inspect!(arr, content=
  >    #|[(2, "two"), (1, "one")]
  >  )
  >  }
  >  ```

## capacity

```moonbit
:::source,moonbitlang/core/hashmap/utils.mbt,278:::fn capacity[K, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V]) -> Int
```

 Returns the current capacity of the hash map. The capacity is the number of
key-value pairs the hash map can hold before it needs to reallocate its
internal storage.

 Parameters:

 * `map` : The hash map whose capacity is to be queried.

 Returns the number of key-value pairs that can be stored in the hash map
before triggering a reallocation.

 Example:

 ```moonbit
 test "capacity" {
   let map : @hashmap.T[Int, String] = @hashmap.new(capacity=16)
   inspect!(map.capacity(), content="16")
 }
 ```

## clear

```moonbit
:::source,moonbitlang/core/hashmap/utils.mbt,48:::fn clear[K, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V]) -> Unit
```

 Removes all key-value pairs from the map while retaining the allocated
capacity. After calling this method, the size of the map will be zero but the
capacity remains unchanged.

 Parameters:

 * `self` : The hash map to be cleared.

 Example:

 ```moonbit
 test "clear" {
   let map = @hashmap.of([("a", 1), ("b", 2)])
   map.clear()
   inspect!(map.size(), content="0")
   inspect!(map.get("a"), content="None")
 }
 ```

## contains

```moonbit
:::source,moonbitlang/core/hashmap/hashmap.mbt,344:::fn contains[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], key : K) -> Bool
```

 Checks if a key exists in the hash map.

 Parameters:

 * `self` : The hash map to search in.
 * `key` : The key to look for in the hash map.

 Returns `true` if the key exists in the hash map, `false` otherwise.

 Example:

 ```moonbit
 test "contains" {
   let map = @hashmap.of([("a", 1), ("b", 2)])
   inspect!(map.contains("a"), content="true")
   inspect!(map.contains("c"), content="false")
 }
 ```

## each

```moonbit
:::source,moonbitlang/core/hashmap/utils.mbt,326:::fn each[K, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], f : (K, V) -> Unit) -> Unit
```

 Iterates over all key-value pairs in the hash map and applies the given
function to each pair.

 Parameters:

 * `map` : The hash map to iterate over.
 * `action` : A function that takes a key and a value as arguments and
   performs some action. The function should not return any value.

 Example:

 ```moonbit
 test "each" {
   let map = @hashmap.of([(1, "one"), (2, "two")])
   let mut result = ""
   map.each(fn(k, v) { result = result + "\{k}:\{v}," })
   inspect!(result, content="2:two,1:one,")
 }
 ```

## eachi

```moonbit
:::source,moonbitlang/core/hashmap/utils.mbt,358:::fn eachi[K, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], f : (Int, K, V) -> Unit) -> Unit
```

 Iterates over all key-value pairs in the map with their index, applying the
given function to each element. The index starts from 0 and only counts
non-empty entries.

 Parameters:

 * `self` : The hash map to iterate over.
 * `callback` : A function that takes three arguments:
  * An integer representing the index of the current key-value pair
  * The key of the current entry
  * The value of the current entry

 Example:

 ```moonbit
 test "eachi" {
   let map = @hashmap.of([("a", 1), ("b", 2), ("c", 3)])
   let mut result = 0
   map.eachi(fn(i, k, _) { if k == "b" { result = i } })
   // "b" is at index 1
   inspect!(result, content="2")
 }
 ```

## from\_array

```moonbit
:::source,moonbitlang/core/hashmap/hashmap.mbt,89:::fn from_array[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](arr : <a href="moonbitlang/core/array#Array">Array</a>[(K, V)]) -> <a href="moonbitlang/core/hashmap#T">T</a>[K, V]
```

 Creates a new hash map from an array of key-value pairs. Pairs with duplicate
keys will keep the latest value, overwriting the previous ones.

 Parameters:

 * `arr` : An array of key-value tuples. Each tuple contains a hashable and
   comparable key of type `K`, and an associated value of type `V`.

 Returns a new hash map containing all the key-value pairs from the input
array.

 Example:

 ```moonbit
 test "from_array" {
   let arr = [(1, "one"), (2, "two"), (1, "ONE")]
   let map = @hashmap.from_array(arr)
   inspect!(map.get(1), content="Some(\"ONE\")")
   inspect!(map.get(2), content="Some(\"two\")")
 }
 ```

## from\_iter

```moonbit
:::source,moonbitlang/core/hashmap/utils.mbt,159:::fn from_iter[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[(K, V)]) -> <a href="moonbitlang/core/hashmap#T">T</a>[K, V]
```

 Creates a new hash map from an iterator of key-value pairs.

 Parameters:

 * `iter` : An iterator that yields key-value pairs. The key type must
   implement both `Hash` and `Eq` traits.

 Returns a new hash map containing all key-value pairs from the iterator. If
the iterator yields multiple pairs with the same key, the later value will
overwrite the earlier one.

 Example:

 ```moonbit
 test "from_iter" {
   let arr = [(1, "one"), (2, "two")]
   let iter = Iter::new(fn(yield_) {
     for pair in arr {
       if yield_(pair) == IterEnd {
         break IterEnd
       }
     } else {
       IterContinue
     }
   })
   let map = @hashmap.from_iter(iter)
   inspect!(map.get(1), content="Some(\"one\")")
   inspect!(map.get(2), content="Some(\"two\")")
 }
 ```

## get

```moonbit
:::source,moonbitlang/core/hashmap/hashmap.mbt,203:::fn get[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], key : K) -> V?
```

 Retrieves the value associated with a given key in the hash map.

 Parameters:

 * `self` : The hash map to search in.
 * `key` : The key to look up in the map.

 Returns `Some(value)` if the key exists in the map, `None` otherwise.

 Example:

 ```moonbit
 test "get" {
   let map = @hashmap.of([("key", 42)])
   inspect!(map.get("key"), content="Some(42)")
   inspect!(map.get("nonexistent"), content="None")
 }
 ```

## get\_or\_default

```moonbit
:::source,moonbitlang/core/hashmap/hashmap.mbt,314:::fn get_or_default[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], key : K, default : V) -> V
```

 Gets the value associated with a given key from the hash map. If the key
doesn't exist, returns the provided default value instead.

 Parameters:

 * `map` : The hash map to retrieve the value from.
 * `key` : The key to look up in the map.
 * `default` : The value to return if the key is not found in the map.

 Returns the value associated with the key if it exists, otherwise returns the
default value.

 Example:

 ```moonbit
 test "get_or_default" {
   let map = @hashmap.of([("a", 1), ("b", 2)])
   inspect!(map.get_or_default("a", 0), content="1")
   inspect!(map.get_or_default("c", 0), content="0")
 }
 ```

## get\_or\_init

```moonbit
:::source,moonbitlang/core/hashmap/hashmap.mbt,276:::fn get_or_init[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], key : K, init : () -> V) -> V
```

 Gets the value associated with the given key. If the key doesn't exist in the
map, initializes it with the result of calling the provided initialization
function.

 Parameters:

 * `self` : The hash map.
 * `key` : The key to look up in the map.
 * `init` : A function that takes no arguments and returns a value to be
   associated with the key if it doesn't exist.

 Returns the value associated with the key, either existing or newly
initialized.

 Example:

 ```moonbit
 test "get_or_init" {
   let map : @hashmap.T[String, Int] = @hashmap.new()
   let value = map.get_or_init("key", fn() { 42 })
   inspect!(value, content="42")
   inspect!(map.get("key"), content="Some(42)")
 }
 ```

## is\_empty

```moonbit
:::source,moonbitlang/core/hashmap/utils.mbt,302:::fn is_empty[K, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V]) -> Bool
```

 Returns whether the hash map contains no key-value pairs.

 Parameters:

 * `map` : The hash map to check.

 Returns `true` if the hash map contains no key-value pairs, `false`
otherwise.

 Example:

 ```moonbit
 test "is_empty" {
   let map : @hashmap.T[String, Int] = @hashmap.new()
   inspect!(map.is_empty(), content="true")
   map.set("key", 42)
   inspect!(map.is_empty(), content="false")
 }
 ```

## iter

```moonbit
:::source,moonbitlang/core/hashmap/utils.mbt,74:::fn iter[K, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[(K, V)]
```

 Returns an iterator over the key-value pairs in the map.

 Parameters:

 * `map` : The hash map to iterate over.

 Returns an iterator that yields tuples of `(key, value)` for each entry in
the map, in unspecified order.

 Example:

 ```moonbit
 test "iter" {
   let map = @hashmap.of([(1, "one"), (2, "two")])
   let pairs = map.iter().to_array()
   inspect!(pairs.length(), content="2")
   inspect!(pairs.contains((1, "one")), content="true")
   inspect!(pairs.contains((2, "two")), content="true")
 }
 ```

## iter2

```moonbit
:::source,moonbitlang/core/hashmap/utils.mbt,112:::fn iter2[K, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[K, V]
```

 Creates an iterator over the key-value pairs in the map, where the key and
value are passed as separate arguments to the yielding function.

 Parameters:

 * `map` : The hash map to iterate over.

 Returns an iterator `Iter2[K, V]` that yields each key-value pair in the map
as separate arguments. This differs from `iter()` which yields tuples of
key-value pairs.

 Example:

 ```moonbit
 test "iter2" {
   let map = @hashmap.of([(1, "one"), (2, "two")])
   let mut sum = 0
   map.iter2().each(fn(k, _) { sum = sum + k })
   inspect!(sum, content="3")
 }
 ```

## new

```moonbit
:::source,moonbitlang/core/hashmap/hashmap.mbt,62:::fn new[K, V](capacity~ : Int = ..) -> <a href="moonbitlang/core/hashmap#T">T</a>[K, V]
```

 Creates a new empty hash map with the specified initial capacity. The actual
capacity will be rounded up to the next power of 2 that is greater than or
equal to the requested capacity, with a minimum of 8.

 Parameters:

 * `capacity` : The desired minimum capacity of the hash map. Must be a
   non-negative integer. Defaults to 8 if not specified.

 Returns a new empty hash map of type `T[K, V]`, where `K` is the key type and
`V` is the value type.

 Example:

 ```moonbit
 test "new" {
   let map : @hashmap.T[String, Int] = @hashmap.new(capacity=16)
   inspect!(map.capacity(), content="16")
   inspect!(map.is_empty(), content="true")
 }
 ```

## of

```moonbit
:::source,moonbitlang/core/hashmap/hashmap.mbt,445:::fn of[K : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Hash">Hash</a>, V](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[(K, V)]) -> <a href="moonbitlang/core/hashmap#T">T</a>[K, V]
```

 Creates a new hash map from a fixed array of key-value pairs.

 Parameters:

 * `pairs` : A fixed array of tuples, where each tuple contains a key of type
   `K` and a value of type `V`. The key type must implement both `Eq` and `Hash`
   traits.

 Returns a new hash map containing all the key-value pairs from the input
array.

 Example:

 ```moonbit
 test "of" {
   let map = @hashmap.of([(1, "one"), (2, "two")])
   inspect!(map.get(1), content="Some(\"one\")")
   inspect!(map.get(2), content="Some(\"two\")")
 }
 ```

## op\_get

```moonbit
:::source,moonbitlang/core/hashmap/hashmap.mbt,247:::fn op_get[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], key : K) -> V?
```

 Retrieves a value from the hash map using the index operator syntax. This
method is automatically called when using the square bracket notation
`map[key]`.

 Parameters:

 * `map` : The hash map to retrieve the value from.
 * `key` : The key to look up in the map. Must implement both `Hash` and `Eq`
   traits.

 Returns `Some(value)` if the key exists in the map, `None` otherwise.

 Example:

 ```moonbit
 test "op_get" {
   let map = @hashmap.of([("key", 42)])
   inspect!(map["key"], content="Some(42)")
   inspect!(map["nonexistent"], content="None")
 }
 ```

## op\_set

```moonbit
:::source,moonbitlang/core/hashmap/hashmap.mbt,180:::fn op_set[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], key : K, value : V) -> Unit
```

 Sets the value associated with a key in the hash map. If the key already
exists, updates its value; otherwise, adds a new key-value pair. This
function is automatically called when using the index assignment syntax
`map[key] = value`.

 Parameters:

 * `map` : The hash map to modify.
 * `key` : The key to associate with the value. Must implement `Hash` and `Eq`
   traits.
 * `value` : The value to associate with the key.

 Example:

 ```moonbit
 test "op_set" {
   let map : @hashmap.T[String, Int] = @hashmap.new()
   map["key"] = 42
   inspect!(map.get("key"), content="Some(42)")
 }
 ```

## remove

```moonbit
:::source,moonbitlang/core/hashmap/hashmap.mbt,372:::fn remove[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], key : K) -> Unit
```

 Removes the entry for the specified key from the hash map. If the key exists
in the map, removes its entry and adjusts the probe sequence length (PSL) of
subsequent entries to maintain the Robin Hood hashing invariant. If the key
does not exist, the map remains unchanged.

 Parameters:

 * `self` : The hash map to remove the entry from.
 * `key` : The key to remove from the map.

 Example:

 ```moonbit
 test "remove" {
   let map = @hashmap.of([("a", 1), ("b", 2)])
   map.remove("a")
   inspect!(map.get("a"), content="None")
   inspect!(map.size(), content="1")
 }
 ```

## set

```moonbit
:::source,moonbitlang/core/hashmap/hashmap.mbt,119:::fn set[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V], key : K, value : V) -> Unit
```

 Sets a key-value pair into the hash map. If the key already exists, updates
its value. If the hash map is near full capacity (\>= 50%), automatically
grows the internal storage to accommodate more entries.

 Parameters:

 * `map` : The hash map to modify.
 * `key` : The key to insert or update. Must implement `Hash` and `Eq` traits.
 * `value` : The value to associate with the key.

 Example:

 ```moonbit
 test "set" {
   let map : @hashmap.T[String, Int] = @hashmap.new()
   map.set("key", 42)
   inspect!(map.get("key"), content="Some(42)")
   map.set("key", 24) // update existing key
   inspect!(map.get("key"), content="Some(24)")
 }
 ```

 @alert unsafe "Panic if the hash map is full."

## size

```moonbit
:::source,moonbitlang/core/hashmap/utils.mbt,254:::fn size[K, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V]) -> Int
```

 Returns the number of key-value pairs currently stored in the hash map.

 Parameters:

 * `self` : The hash map to get the size from.

 Returns the number of key-value pairs in the hash map.

 Example:

 ```moonbit
 test "size" {
   let map = @hashmap.of([("a", 1), ("b", 2), ("c", 3)])
   inspect!(map.size(), content="3")
 }
 ```

## to\_array

```moonbit
:::source,moonbitlang/core/hashmap/utils.mbt,213:::fn to_array[K, V](self : <a href="moonbitlang/core/hashmap#T">T</a>[K, V]) -> <a href="moonbitlang/core/array#Array">Array</a>[(K, V)]
```

 Converts the hash map into an array of key-value pairs. The order of elements
in the resulting array follows the internal storage order of the hash map.

 Parameters:

 * `self` : The hash map to be converted.

 Returns an array containing tuples of key-value pairs from the hash map.

 Example:

 ```moonbit
 test "to_array" {
   let map = @hashmap.of([(1, "one"), (2, "two")])
   let arr = map.to_array()
   inspect!(arr, content=
   #|[(2, "two"), (1, "one")]
 )
 }
 ```
