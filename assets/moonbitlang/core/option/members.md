# Documentation
|Type|description|
|---|---|
|[Option](#Option)||

|Value|description|
|---|---|
|[bind](#bind)||
|[empty](#empty)||
|[filter](#filter)||
|[flatten](#flatten)||
|[is\_empty](#is_empty)||
|[iter](#iter)||
|[map](#map)||
|[map\_or](#map_or)||
|[map\_or\_else](#map_or_else)||
|[or](#or)||
|[or\_default](#or_default)||
|[or\_else](#or_else)||
|[or\_error](#or_error)||
|[some](#some)||
|[unless](#unless)||
|[when](#when)||

## bind

```moonbit
:::source,moonbitlang/core/option/option.mbt,191:::fn bind[T, U](self : T?, f : (T) -> U?) -> U?
```

 Binds an option to a function that returns another option.

 #### Example

 ```
 let a = Option::Some(5)
 let r1 = a.bind(fn(x){ Some(x * 2) })
 assert_eq!(r1, Some(10))
 let b : Option[Int] = None
 let r2 = b.bind(fn(x){ Some(x * 2) })
 assert_eq!(r2, None)
 ```

## empty

```moonbit
:::source,moonbitlang/core/option/option.mbt,77:::fn empty[T]() -> T?
```

 Creates an empty `Option` of type `T`.

## filter

```moonbit
:::source,moonbitlang/core/option/option.mbt,260:::fn filter[T](self : T?, f : (T) -> Bool) -> T?
```

 Filters the option by applying the given predicate function `f`.

 If the predicate function `f` returns `true` for the value contained in the option,
the same option is returned. Otherwise, `None` is returned.

 #### Example
 ```
 let x = Some(3)
 assert_eq!(x.filter(fn(x){ x > 5 }), None)
 assert_eq!(x.filter(fn(x){ x < 5 }), Some(3))
 ```

## flatten

```moonbit
:::source,moonbitlang/core/option/option.mbt,219:::fn flatten[T](self : T??) -> T?
```

 Flattens an `Option` of `Option` into a single `Option`.

 If the input `Option` is `Some(Some(value))`, the function returns `Some(value)`.

 #### Example

 ```
 let a = Some(Some(42));
 assert_eq!(@option.flatten(a), Some(42))
 let b : Int?? = Some(None)
 assert_eq!(@option.flatten(b), None)
 ```

## is\_empty

```moonbit
:::source,moonbitlang/core/option/option.mbt,236:::fn is_empty[T](self : T?) -> Bool
```

 Checks if the option is empty.

## iter

```moonbit
:::source,moonbitlang/core/option/option.mbt,360:::fn iter[T](self : T?) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
```


## map

```moonbit
:::source,moonbitlang/core/option/option.mbt,113:::fn map[T, U](self : T?, f : (T) -> U) -> U?
```

 Maps the value of an `Option` using a provided function.

 #### Example

 ```
 let a = Some(5)
 assert_eq!(a.map(fn(x){ x * 2 }), Some(10))
 
 let b = None
 assert_eq!(b.map(fn(x){ x * 2 }), None)
 ```

## map\_or

```moonbit
:::source,moonbitlang/core/option/option.mbt,138:::fn map_or[T, U](self : T?, default : U, f : (T) -> U) -> U
```

 Returns the provided default result (if none), or applies a function to the contained value (if any).
Arguments passed to map\_or are eagerly evaluated; if you are passing the result of a function call, it is recommended to use `map_or_else`, which is lazily evaluated.

 #### Example

 ```
 let a = Some(5)
 assert_eq!(a.map_or(3, fn(x){ x * 2 }), 10)
 ```

## map\_or\_else

```moonbit
:::source,moonbitlang/core/option/option.mbt,162:::fn map_or_else[T, U](self : T?, default : () -> U, f : (T) -> U) -> U
```

 Computes a default function result (if none), or applies a different function to the contained value (if any).

 #### Example

 ```
 let a = Some(5)
 assert_eq!(a.map_or_else(fn(){ 3 }, fn(x){ x * 2 }), 10)
 ```

## or

```moonbit
:::source,moonbitlang/core/option/option.mbt,276:::fn or[T](self : T?, default : T) -> T
```

 Return the contained `Some` value or the provided default.

## or\_default

```moonbit
:::source,moonbitlang/core/option/option.mbt,310:::fn or_default[T : <a href="moonbitlang/core/builtin#Default">Default</a>](self : T?) -> T
```

 Return the contained `Some` value or the result of the `T::default()`.

## or\_else

```moonbit
:::source,moonbitlang/core/option/option.mbt,294:::fn or_else[T](self : T?, default : () -> T) -> T
```

 Return the contained `Some` value or the provided default.

 Default is lazily evaluated

## or\_error

```moonbit
:::source,moonbitlang/core/option/option.mbt,396:::fn or_error[T, Err : <a href="moonbitlang/core/error#Error">Error</a>](self : T?, err : Err) -> T!Err
```


## some

```moonbit
:::source,moonbitlang/core/option/option.mbt,90:::fn some[T](value : T) -> T?
```

 Creates an `Option` that contains a value.

## unless

```moonbit
:::source,moonbitlang/core/option/option.mbt,63:::fn unless[T](condition : Bool, value : () -> T) -> T?
```

 The `unless` function returns an `Option` value based on a condition.

 `unless(condition, value)` is equivalent to `when(not(condition), value)`.

 #### Arguments

 * `condition`: A boolean value indicating whether the condition is true or false.
 * `value`: A function that returns a value of type `T`.

 #### Returns

 An `Option` value that is `Some(value())` if the condition is false, otherwise `None`.


## when

```moonbit
:::source,moonbitlang/core/option/option.mbt,33:::fn when[T](condition : Bool, value : () -> T) -> T?
```

 Creates an `Option` containing a value if the given condition is true, otherwise returns `None`.

 #### Arguments

 * `condition`: A boolean value indicating whether the option should contain a value.
 * `value`: A function that returns the value to be contained in the option.

 #### Returns

 An `Option` containing the value if the condition is true, otherwise `None`.

 #### Example

 ```
 let result = @option.when(true, fn(){ "Hello, World!" })
 assert_eq!(result, Some("Hello, World!"))
 ```

## Option


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/option/option.mbt,325:::impl[X : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for X?
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/option/option.mbt,325:::fn compare[X : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : X?, other : X?) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/option/option.mbt,355:::impl[X] <a href="moonbitlang/core/builtin#Default">Default</a> for X?
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/option/option.mbt,355:::fn default[X]() -> X?
    ```
    > 
    >  `None`
- ```moonbit
  :::source,moonbitlang/core/option/option.mbt,424:::impl[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for X?
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/option/option.mbt,424:::fn arbitrary[X : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>](i : Int, rs : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> X?
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### bind
  ```moonbit
  :::source,moonbitlang/core/option/option.mbt,191:::fn <a href="moonbitlang/core/option#Option">Option</a>::bind[T, U](self : T?, f : (T) -> U?) -> U?
  ```
  > 
  >  Binds an option to a function that returns another option.
  > 
  >  #### Example
  > 
  >  ```
  >  let a = Option::Some(5)
  >  let r1 = a.bind(fn(x){ Some(x * 2) })
  >  assert_eq!(r1, Some(10))
  >  let b : Option[Int] = None
  >  let r2 = b.bind(fn(x){ Some(x * 2) })
  >  assert_eq!(r2, None)
  >  ```
- #### filter
  ```moonbit
  :::source,moonbitlang/core/option/option.mbt,260:::fn <a href="moonbitlang/core/option#Option">Option</a>::filter[T](self : T?, f : (T) -> Bool) -> T?
  ```
  > 
  >  Filters the option by applying the given predicate function `f`.
  > 
  >  If the predicate function `f` returns `true` for the value contained in the option,
  > the same option is returned. Otherwise, `None` is returned.
  > 
  >  #### Example
  >  ```
  >  let x = Some(3)
  >  assert_eq!(x.filter(fn(x){ x > 5 }), None)
  >  assert_eq!(x.filter(fn(x){ x < 5 }), Some(3))
  >  ```
- #### flatten
  ```moonbit
  :::source,moonbitlang/core/option/option.mbt,219:::fn <a href="moonbitlang/core/option#Option">Option</a>::flatten[T](self : T??) -> T?
  ```
  > 
  >  Flattens an `Option` of `Option` into a single `Option`.
  > 
  >  If the input `Option` is `Some(Some(value))`, the function returns `Some(value)`.
  > 
  >  #### Example
  > 
  >  ```
  >  let a = Some(Some(42));
  >  assert_eq!(@option.flatten(a), Some(42))
  >  let b : Int?? = Some(None)
  >  assert_eq!(@option.flatten(b), None)
  >  ```
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/option/option.mbt,236:::fn <a href="moonbitlang/core/option#Option">Option</a>::is_empty[T](self : T?) -> Bool
  ```
  > 
  >  Checks if the option is empty.
- #### iter
  ```moonbit
  :::source,moonbitlang/core/option/option.mbt,360:::fn <a href="moonbitlang/core/option#Option">Option</a>::iter[T](self : T?) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
- #### map
  ```moonbit
  :::source,moonbitlang/core/option/option.mbt,113:::fn <a href="moonbitlang/core/option#Option">Option</a>::map[T, U](self : T?, f : (T) -> U) -> U?
  ```
  > 
  >  Maps the value of an `Option` using a provided function.
  > 
  >  #### Example
  > 
  >  ```
  >  let a = Some(5)
  >  assert_eq!(a.map(fn(x){ x * 2 }), Some(10))
  >  
  >  let b = None
  >  assert_eq!(b.map(fn(x){ x * 2 }), None)
  >  ```
- #### map\_or
  ```moonbit
  :::source,moonbitlang/core/option/option.mbt,138:::fn <a href="moonbitlang/core/option#Option">Option</a>::map_or[T, U](self : T?, default : U, f : (T) -> U) -> U
  ```
  > 
  >  Returns the provided default result (if none), or applies a function to the contained value (if any).
  > Arguments passed to map\_or are eagerly evaluated; if you are passing the result of a function call, it is recommended to use `map_or_else`, which is lazily evaluated.
  > 
  >  #### Example
  > 
  >  ```
  >  let a = Some(5)
  >  assert_eq!(a.map_or(3, fn(x){ x * 2 }), 10)
  >  ```
- #### map\_or\_else
  ```moonbit
  :::source,moonbitlang/core/option/option.mbt,162:::fn <a href="moonbitlang/core/option#Option">Option</a>::map_or_else[T, U](self : T?, default : () -> U, f : (T) -> U) -> U
  ```
  > 
  >  Computes a default function result (if none), or applies a different function to the contained value (if any).
  > 
  >  #### Example
  > 
  >  ```
  >  let a = Some(5)
  >  assert_eq!(a.map_or_else(fn(){ 3 }, fn(x){ x * 2 }), 10)
  >  ```
- #### or
  ```moonbit
  :::source,moonbitlang/core/option/option.mbt,276:::fn <a href="moonbitlang/core/option#Option">Option</a>::or[T](self : T?, default : T) -> T
  ```
  > 
  >  Return the contained `Some` value or the provided default.
- #### or\_default
  ```moonbit
  :::source,moonbitlang/core/option/option.mbt,310:::fn <a href="moonbitlang/core/option#Option">Option</a>::or_default[T : <a href="moonbitlang/core/builtin#Default">Default</a>](self : T?) -> T
  ```
  > 
  >  Return the contained `Some` value or the result of the `T::default()`.
- #### or\_else
  ```moonbit
  :::source,moonbitlang/core/option/option.mbt,294:::fn <a href="moonbitlang/core/option#Option">Option</a>::or_else[T](self : T?, default : () -> T) -> T
  ```
  > 
  >  Return the contained `Some` value or the provided default.
  > 
  >  Default is lazily evaluated
- #### or\_error
  ```moonbit
  :::source,moonbitlang/core/option/option.mbt,396:::fn <a href="moonbitlang/core/option#Option">Option</a>::or_error[T, Err : <a href="moonbitlang/core/error#Error">Error</a>](self : T?, err : Err) -> T!Err
  ```
  > 
