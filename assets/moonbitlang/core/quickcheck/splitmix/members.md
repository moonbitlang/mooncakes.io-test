# Documentation
|Type|description|
|---|---|
|[RandomState](#RandomState)||

|Value|description|
|---|---|
|[clone](#clone)||
|[new](#new)||
|[next](#next)||
|[next\_double](#next_double)||
|[next\_float](#next_float)||
|[next\_int](#next_int)||
|[next\_int64](#next_int64)||
|[next\_positive\_int](#next_positive_int)||
|[next\_two\_uint](#next_two_uint)||
|[next\_uint](#next_uint)||
|[next\_uint64](#next_uint64)||
|[split](#split)||

## RandomState

```moonbit
:::source,moonbitlang/core/quickcheck/splitmix/random.mbt,16:::type RandomState
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/quickcheck/splitmix/random.mbt,19:::impl <a href="moonbitlang/core/builtin#Default">Default</a> for <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/quickcheck/splitmix/random.mbt,19:::fn default() -> <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>
    ```
    > automatically derived
- ```moonbit
  :::source,moonbitlang/core/quickcheck/splitmix/random.mbt,19:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/quickcheck/splitmix/random.mbt,19:::fn output(<a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### clone
  ```moonbit
  :::source,moonbitlang/core/quickcheck/splitmix/random.mbt,43:::fn <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>::clone(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>
  ```
  > 
  >  Clone a RandomState.
- #### new
  ```moonbit
  :::source,moonbitlang/core/quickcheck/splitmix/random.mbt,37:::fn <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>::new(seed~ : UInt64 = ..) -> <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>
  ```
  >  @alert deprecated "use `@splitmix.new` instead"
- #### next
  ```moonbit
  :::source,moonbitlang/core/quickcheck/splitmix/random.mbt,49:::fn <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>::next(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> Unit
  ```
  > 
  >  Skip the next random number.
- #### next\_double
  ```moonbit
  :::source,moonbitlang/core/quickcheck/splitmix/random.mbt,106:::fn <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>::next_double(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> Double
  ```
  > 
  >  Get the next random number as a double in \[0, 1\]
- #### next\_float
  ```moonbit
  :::source,moonbitlang/core/quickcheck/splitmix/random.mbt,99:::fn <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>::next_float(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> Float
  ```
  > 
  >  Get the next random number as a float in \[0, 1\]
- #### next\_int
  ```moonbit
  :::source,moonbitlang/core/quickcheck/splitmix/random.mbt,82:::fn <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>::next_int(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> Int
  ```
  > 
  >  Get the next random number as a 32-bit signed integer.
- #### next\_int64
  ```moonbit
  :::source,moonbitlang/core/quickcheck/splitmix/random.mbt,69:::fn <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>::next_int64(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> Int64
  ```
  > 
  >  Get the next random number as a 64-bit signed integer.
- #### next\_positive\_int
  ```moonbit
  :::source,moonbitlang/core/quickcheck/splitmix/random.mbt,88:::fn <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>::next_positive_int(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> Int
  ```
  > 
  >  Get the next random number as a positive 32-bit signed integer.
- #### next\_two\_uint
  ```moonbit
  :::source,moonbitlang/core/quickcheck/splitmix/random.mbt,75:::fn <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>::next_two_uint(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> (UInt, UInt)
  ```
  > 
  >  Get the next two random number as 32-bit signed integers.
- #### next\_uint
  ```moonbit
  :::source,moonbitlang/core/quickcheck/splitmix/random.mbt,63:::fn <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>::next_uint(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> UInt
  ```
  > 
  >  Get the next random number as a 32-bit unsigned integer.
- #### next\_uint64
  ```moonbit
  :::source,moonbitlang/core/quickcheck/splitmix/random.mbt,55:::fn <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>::next_uint64(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> UInt64
  ```
  > 
  >  Get the next random number as a 64-bit unsigned integer.
- #### split
  ```moonbit
  :::source,moonbitlang/core/quickcheck/splitmix/random.mbt,113:::fn <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>::split(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>
  ```
  > 
  >  Generates an independent random number generator.

## clone

```moonbit
:::source,moonbitlang/core/quickcheck/splitmix/random.mbt,43:::fn clone(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>
```

 Clone a RandomState.

## new

```moonbit
:::source,moonbitlang/core/quickcheck/splitmix/random.mbt,32:::fn new(seed~ : UInt64 = ..) -> <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>
```

 Create a new RandomState from an optional seed.

## next

```moonbit
:::source,moonbitlang/core/quickcheck/splitmix/random.mbt,49:::fn next(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> Unit
```

 Skip the next random number.

## next\_double

```moonbit
:::source,moonbitlang/core/quickcheck/splitmix/random.mbt,106:::fn next_double(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> Double
```

 Get the next random number as a double in \[0, 1\]

## next\_float

```moonbit
:::source,moonbitlang/core/quickcheck/splitmix/random.mbt,99:::fn next_float(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> Float
```

 Get the next random number as a float in \[0, 1\]

## next\_int

```moonbit
:::source,moonbitlang/core/quickcheck/splitmix/random.mbt,82:::fn next_int(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> Int
```

 Get the next random number as a 32-bit signed integer.

## next\_int64

```moonbit
:::source,moonbitlang/core/quickcheck/splitmix/random.mbt,69:::fn next_int64(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> Int64
```

 Get the next random number as a 64-bit signed integer.

## next\_positive\_int

```moonbit
:::source,moonbitlang/core/quickcheck/splitmix/random.mbt,88:::fn next_positive_int(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> Int
```

 Get the next random number as a positive 32-bit signed integer.

## next\_two\_uint

```moonbit
:::source,moonbitlang/core/quickcheck/splitmix/random.mbt,75:::fn next_two_uint(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> (UInt, UInt)
```

 Get the next two random number as 32-bit signed integers.

## next\_uint

```moonbit
:::source,moonbitlang/core/quickcheck/splitmix/random.mbt,63:::fn next_uint(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> UInt
```

 Get the next random number as a 32-bit unsigned integer.

## next\_uint64

```moonbit
:::source,moonbitlang/core/quickcheck/splitmix/random.mbt,55:::fn next_uint64(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> UInt64
```

 Get the next random number as a 64-bit unsigned integer.

## split

```moonbit
:::source,moonbitlang/core/quickcheck/splitmix/random.mbt,113:::fn split(self : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>) -> <a href="moonbitlang/core/quickcheck/splitmix#RandomState">RandomState</a>
```

 Generates an independent random number generator.
