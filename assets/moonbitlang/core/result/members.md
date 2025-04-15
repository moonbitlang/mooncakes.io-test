# Documentation
|Type|description|
|---|---|
|[Result](#Result)||

|Value|description|
|---|---|
|[bind](#bind)||
|[err](#err)||
|[flatten](#flatten)||
|[fold](#fold)||
|[is\_err](#is_err)||
|[is\_ok](#is_ok)||
|[map](#map)||
|[map\_err](#map_err)||
|[ok](#ok)||
|[or](#or)||
|[or\_else](#or_else)||
|[to\_option](#to_option)||
|[unwrap](#unwrap)||
|[unwrap\_or\_error](#unwrap_or_error)||
|[wrap0](#wrap0)||
|[wrap1](#wrap1)||
|[wrap2](#wrap2)||

## bind

```moonbit
:::source,moonbitlang/core/result/result.mbt,229:::fn bind[T, E, U](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E], g : (T) -> <a href="moonbitlang/core/result#Result">Result</a>[U, E]) -> <a href="moonbitlang/core/result#Result">Result</a>[U, E]
```

 Binds a result to a function that returns another result.

 #### Example

 ```
 let x: Result[Int, String] = Ok(6)
 let y = x.bind(fn(v : Int) { Ok(v * 7) })
 assert_eq!(y, Ok(42))
 ```

## err

```moonbit
:::source,moonbitlang/core/result/result.mbt,78:::fn err[T, E](value : E) -> <a href="moonbitlang/core/result#Result">Result</a>[T, E]
```

 Create an `Err` of type `E`.

 #### Example

 ```
 let x: Result[Int, String] = Err("error")
 assert_eq!(x, Err("error"))
 ```

## flatten

```moonbit
:::source,moonbitlang/core/result/result.mbt,202:::fn flatten[T, E](self : <a href="moonbitlang/core/result#Result">Result</a>[<a href="moonbitlang/core/result#Result">Result</a>[T, E], E]) -> <a href="moonbitlang/core/result#Result">Result</a>[T, E]
```

 Flatten a `Result` of `Result` into a single `Result`.

 If the outer `Result` is an `Ok`, the inner `Result` is returned. If the outer `Result` is an `Err`, the inner `Result` is ignored and the `Err` is returned.

 #### Example

 ```
 let x: Result[Result[Int, String], String] = Ok(Ok(6))
 let y = x.flatten()
 assert_eq!(y, Ok(6))
 ```

## fold

```moonbit
:::source,moonbitlang/core/result/result.mbt,257:::fn fold[T, E, V](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E], ok : (T) -> V, err : (E) -> V) -> V
```

 Folds a `Result` into a single value.

 If the `Result` is an `Ok`, the `ok` function is applied to the value. If the `Result` is an `Err`, the `err` function is applied to the value.
 #### Example

 ```
 let x = Ok(6)
 let y = x.fold(fn(v : Int) -> Int { v * 7 }, fn(_e : String) -> Int { 0 })
 assert_eq!(y, 42)
 ```

## is\_err

```moonbit
:::source,moonbitlang/core/result/result.mbt,123:::fn is_err[T, E](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E]) -> Bool
```

 Check if a `Result` is an `Err`.

## is\_ok

```moonbit
:::source,moonbitlang/core/result/result.mbt,109:::fn is_ok[T, E](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E]) -> Bool
```

 Check if a `Result` is an `Ok`.

## map

```moonbit
:::source,moonbitlang/core/result/result.mbt,25:::fn map[T, E, U](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E], f : (T) -> U) -> <a href="moonbitlang/core/result#Result">Result</a>[U, E]
```

 Maps the value of a Result if it is `Ok` into another, otherwise returns the `Err` value unchanged.

 #### Example

 ```
 let x: Result[Int, Unit] = Ok(6)
 let y = x.map(fn (v : Int) { v * 7 })
 assert_eq!(y, Ok(42))
 ```

## map\_err

```moonbit
:::source,moonbitlang/core/result/result.mbt,52:::fn map_err[T, E, F](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E], f : (E) -> F) -> <a href="moonbitlang/core/result#Result">Result</a>[T, F]
```

 Maps the value of a Result if it is `Err` into another, otherwise returns the `Ok` value unchanged.

 #### Example

 ```
 let x: Result[Int, String] = Err("error")
 let y = x.map_err(fn (v : String) { v + "!" })
 assert_eq!(y, Err("error!"))
 ```

## ok

```moonbit
:::source,moonbitlang/core/result/result.mbt,97:::fn ok[T, E](value : T) -> <a href="moonbitlang/core/result#Result">Result</a>[T, E]
```

 Create an `Ok` of type `T`.

 #### Example

 ```
 let x: Result[String, Unit] = Ok("yes")
 assert_true!(x.is_ok())
 ```

## or

```moonbit
:::source,moonbitlang/core/result/result.mbt,145:::fn or[T, E](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E], default : T) -> T
```

 Return the inner `Ok` value, if it exists, otherwise return the provided default.

 #### Example

 ```
 let x: Result[Int, String] = Ok(6)
 let y = x.or(0)
 assert_eq!(y, 6)
 ```

## or\_else

```moonbit
:::source,moonbitlang/core/result/result.mbt,173:::fn or_else[T, E](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E], default : () -> T) -> T
```

 Return the inner `Ok` value, if it exists, otherwise return the provided default.

 Default is lazily evaluated.
 #### Example

 ```
 let x: Result[Int, String] = Ok(6)
 let y = x.or_else(fn() { 0 })
 assert_eq!(y, 6)
 ```

## to\_option

```moonbit
:::source,moonbitlang/core/result/result.mbt,286:::fn to_option[T, E](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E]) -> T?
```

 Converts a `Result` to an `Option`.

 Converts `Ok` to `Some` and `Err` to `None`.

 #### Example

 ```
 let x: Result[Int, String] = Ok(6)
 let y = x.to_option()
 assert_eq!(y, Some(6))
 ```

## unwrap

```moonbit
:::source,moonbitlang/core/result/result.mbt,333:::fn unwrap[T, E](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E]) -> T
```


## unwrap\_or\_error

```moonbit
:::source,moonbitlang/core/result/result.mbt,359:::fn unwrap_or_error[T, E : <a href="moonbitlang/core/error#Error">Error</a>](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E]) -> T!E
```


## wrap0

```moonbit
:::source,moonbitlang/core/result/result.mbt,382:::fn wrap0[T, E : <a href="moonbitlang/core/error#Error">Error</a>](f~ : () -> T!E) -> <a href="moonbitlang/core/result#Result">Result</a>[T, E]
```


## wrap1

```moonbit
:::source,moonbitlang/core/result/result.mbt,391:::fn wrap1[T, A, E : <a href="moonbitlang/core/error#Error">Error</a>](f~ : (A) -> T!E, a : A) -> <a href="moonbitlang/core/result#Result">Result</a>[T, E]
```


## wrap2

```moonbit
:::source,moonbitlang/core/result/result.mbt,400:::fn wrap2[T, A, B, E : <a href="moonbitlang/core/error#Error">Error</a>](f~ : (A, B) -> T!E, a : A, b : B) -> <a href="moonbitlang/core/result#Result">Result</a>[T, E]
```


## Result


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/result/result.mbt,304:::impl[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, E : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for <a href="moonbitlang/core/result#Result">Result</a>[T, E]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/result/result.mbt,304:::fn compare[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, E : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E], other : <a href="moonbitlang/core/result#Result">Result</a>[T, E]) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/result/result.mbt,413:::impl[T : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, E : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for <a href="moonbitlang/core/result#Result">Result</a>[T, E]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/result/result.mbt,416:::fn arbitrary[T : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, E : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>](size : Int, rs : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[T, E]
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### bind
  ```moonbit
  :::source,moonbitlang/core/result/result.mbt,229:::fn <a href="moonbitlang/core/result#Result">Result</a>::bind[T, E, U](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E], g : (T) -> <a href="moonbitlang/core/result#Result">Result</a>[U, E]) -> <a href="moonbitlang/core/result#Result">Result</a>[U, E]
  ```
  > 
  >  Binds a result to a function that returns another result.
  > 
  >  #### Example
  > 
  >  ```
  >  let x: Result[Int, String] = Ok(6)
  >  let y = x.bind(fn(v : Int) { Ok(v * 7) })
  >  assert_eq!(y, Ok(42))
  >  ```
- #### flatten
  ```moonbit
  :::source,moonbitlang/core/result/result.mbt,202:::fn <a href="moonbitlang/core/result#Result">Result</a>::flatten[T, E](self : <a href="moonbitlang/core/result#Result">Result</a>[<a href="moonbitlang/core/result#Result">Result</a>[T, E], E]) -> <a href="moonbitlang/core/result#Result">Result</a>[T, E]
  ```
  > 
  >  Flatten a `Result` of `Result` into a single `Result`.
  > 
  >  If the outer `Result` is an `Ok`, the inner `Result` is returned. If the outer `Result` is an `Err`, the inner `Result` is ignored and the `Err` is returned.
  > 
  >  #### Example
  > 
  >  ```
  >  let x: Result[Result[Int, String], String] = Ok(Ok(6))
  >  let y = x.flatten()
  >  assert_eq!(y, Ok(6))
  >  ```
- #### fold
  ```moonbit
  :::source,moonbitlang/core/result/result.mbt,257:::fn <a href="moonbitlang/core/result#Result">Result</a>::fold[T, E, V](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E], ok : (T) -> V, err : (E) -> V) -> V
  ```
  > 
  >  Folds a `Result` into a single value.
  > 
  >  If the `Result` is an `Ok`, the `ok` function is applied to the value. If the `Result` is an `Err`, the `err` function is applied to the value.
  >  #### Example
  > 
  >  ```
  >  let x = Ok(6)
  >  let y = x.fold(fn(v : Int) -> Int { v * 7 }, fn(_e : String) -> Int { 0 })
  >  assert_eq!(y, 42)
  >  ```
- #### is\_err
  ```moonbit
  :::source,moonbitlang/core/result/result.mbt,123:::fn <a href="moonbitlang/core/result#Result">Result</a>::is_err[T, E](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E]) -> Bool
  ```
  > 
  >  Check if a `Result` is an `Err`.
- #### is\_ok
  ```moonbit
  :::source,moonbitlang/core/result/result.mbt,109:::fn <a href="moonbitlang/core/result#Result">Result</a>::is_ok[T, E](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E]) -> Bool
  ```
  > 
  >  Check if a `Result` is an `Ok`.
- #### map
  ```moonbit
  :::source,moonbitlang/core/result/result.mbt,25:::fn <a href="moonbitlang/core/result#Result">Result</a>::map[T, E, U](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E], f : (T) -> U) -> <a href="moonbitlang/core/result#Result">Result</a>[U, E]
  ```
  > 
  >  Maps the value of a Result if it is `Ok` into another, otherwise returns the `Err` value unchanged.
  > 
  >  #### Example
  > 
  >  ```
  >  let x: Result[Int, Unit] = Ok(6)
  >  let y = x.map(fn (v : Int) { v * 7 })
  >  assert_eq!(y, Ok(42))
  >  ```
- #### map\_err
  ```moonbit
  :::source,moonbitlang/core/result/result.mbt,52:::fn <a href="moonbitlang/core/result#Result">Result</a>::map_err[T, E, F](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E], f : (E) -> F) -> <a href="moonbitlang/core/result#Result">Result</a>[T, F]
  ```
  > 
  >  Maps the value of a Result if it is `Err` into another, otherwise returns the `Ok` value unchanged.
  > 
  >  #### Example
  > 
  >  ```
  >  let x: Result[Int, String] = Err("error")
  >  let y = x.map_err(fn (v : String) { v + "!" })
  >  assert_eq!(y, Err("error!"))
  >  ```
- #### or
  ```moonbit
  :::source,moonbitlang/core/result/result.mbt,145:::fn <a href="moonbitlang/core/result#Result">Result</a>::or[T, E](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E], default : T) -> T
  ```
  > 
  >  Return the inner `Ok` value, if it exists, otherwise return the provided default.
  > 
  >  #### Example
  > 
  >  ```
  >  let x: Result[Int, String] = Ok(6)
  >  let y = x.or(0)
  >  assert_eq!(y, 6)
  >  ```
- #### or\_else
  ```moonbit
  :::source,moonbitlang/core/result/result.mbt,173:::fn <a href="moonbitlang/core/result#Result">Result</a>::or_else[T, E](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E], default : () -> T) -> T
  ```
  > 
  >  Return the inner `Ok` value, if it exists, otherwise return the provided default.
  > 
  >  Default is lazily evaluated.
  >  #### Example
  > 
  >  ```
  >  let x: Result[Int, String] = Ok(6)
  >  let y = x.or_else(fn() { 0 })
  >  assert_eq!(y, 6)
  >  ```
- #### to\_option
  ```moonbit
  :::source,moonbitlang/core/result/result.mbt,286:::fn <a href="moonbitlang/core/result#Result">Result</a>::to_option[T, E](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E]) -> T?
  ```
  > 
  >  Converts a `Result` to an `Option`.
  > 
  >  Converts `Ok` to `Some` and `Err` to `None`.
  > 
  >  #### Example
  > 
  >  ```
  >  let x: Result[Int, String] = Ok(6)
  >  let y = x.to_option()
  >  assert_eq!(y, Some(6))
  >  ```
- #### unwrap
  ```moonbit
  :::source,moonbitlang/core/result/result.mbt,333:::fn <a href="moonbitlang/core/result#Result">Result</a>::unwrap[T, E](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E]) -> T
  ```
  > 
- #### unwrap\_or\_error
  ```moonbit
  :::source,moonbitlang/core/result/result.mbt,359:::fn <a href="moonbitlang/core/result#Result">Result</a>::unwrap_or_error[T, E : <a href="moonbitlang/core/error#Error">Error</a>](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E]) -> T!E
  ```
  > 
