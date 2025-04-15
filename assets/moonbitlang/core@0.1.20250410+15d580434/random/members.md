# Documentation
|Type|description|
|---|---|
|[Rand](#Rand)||

|Value|description|
|---|---|
|[double](#double)||
|[float](#float)||
|[int](#int)||
|[int64](#int64)||
|[new](#new)||
|[shuffle](#shuffle)||
|[uint](#uint)||
|[uint64](#uint64)||

## Rand

```moonbit
:::source,moonbitlang/core/random/random.mbt,17:::type Rand
```

 Currently we only support \[chacha8\] as the source of randomness.

#### mooncakes-io-method-mark-Methods
- #### double
  ```moonbit
  :::source,moonbitlang/core/random/random.mbt,158:::fn <a href="moonbitlang/core/random#Rand">Rand</a>::double(self : <a href="moonbitlang/core/random#Rand">Rand</a>) -> Double
  ```
  > 
  >  \[double\] returns a pseudo-random 64-bit Double in the range \[0.0, 1.0)
- #### float
  ```moonbit
  :::source,moonbitlang/core/random/random.mbt,172:::fn <a href="moonbitlang/core/random#Rand">Rand</a>::float(self : <a href="moonbitlang/core/random#Rand">Rand</a>) -> Float
  ```
  > 
  >  \[float\] returns a pseudo-random 32-bit Float in the range \[0.0, 1.0)
- #### int
  ```moonbit
  :::source,moonbitlang/core/random/random.mbt,63:::fn <a href="moonbitlang/core/random#Rand">Rand</a>::int(self : <a href="moonbitlang/core/random#Rand">Rand</a>, limit~ : Int = ..) -> Int
  ```
  > 
  >  \[int\] Return a non-negative pseudo-random 31-bit integer as an Int in the range \[0, 2^31) or \[0, limit) if limit is provided.
  > 
  >  #### Arguments
  > 
  >  * `limit` - The upper bound (exclusive) of the random number to be generated (Optional).
  >    When limit is 0, the range is \[0, 2^31).
- #### int64
  ```moonbit
  :::source,moonbitlang/core/random/random.mbt,79:::fn <a href="moonbitlang/core/random#Rand">Rand</a>::int64(self : <a href="moonbitlang/core/random#Rand">Rand</a>, limit~ : Int64 = ..) -> Int64
  ```
  > 
  >  \[int64\] returns a non-negative pseudo-random 63-bit integer as an Int64 in the range \[0, 2^63)
  > 
  >  #### Arguments
  > 
  >  * `limit` - The upper bound (exclusive) of the random number to be generated (Optional).
  >    When limit is 0, the range is \[0, 2^63).
- #### new
  ```moonbit
  :::source,moonbitlang/core/random/random.mbt,33:::fn <a href="moonbitlang/core/random#Rand">Rand</a>::new(seed~ : Bytes = ..) -> <a href="moonbitlang/core/random#Rand">Rand</a>
  ```
  >  @alert deprecated "use `@random.new` instead"
- #### shuffle
  ```moonbit
  :::source,moonbitlang/core/random/random.mbt,249:::fn <a href="moonbitlang/core/random#Rand">Rand</a>::shuffle(self : <a href="moonbitlang/core/random#Rand">Rand</a>, limit : Int, swap : (Int, Int) -> Unit) -> Unit
  ```
  > 
  >  \[shuffle\] shuffles the first n elements of an array using the Fisher-Yates shuffle algorithm.
  > @alert unsafe "Panics if limit is negative"
  > 
  >  #### Example
  >  ```
  >  let r = @random.new()
  >  let a = [1, 2, 3, 4, 5]
  >  r.shuffle(
  >    a.length(),
  >    fn(i : Int, j : Int) {
  >      let t = a[i]
  >      a[i] = a[j]
  >      a[j] = t
  >    },
  >  )
  >  ```
- #### uint
  ```moonbit
  :::source,moonbitlang/core/random/random.mbt,97:::fn <a href="moonbitlang/core/random#Rand">Rand</a>::uint(self : <a href="moonbitlang/core/random#Rand">Rand</a>, limit~ : UInt = ..) -> UInt
  ```
  > 
  >  \[uint\] returns a non-negative pseudo-random 32-bit integer as a Uint in the range \[0, 2^32) or \[0, limit) if limit is provided.
  > 
  >  #### Arguments
  > 
  >  * `limit` - The upper bound (exclusive) of the random number to be generated (Optional).
  >    When limit is 0, the range is \[0, 2^32).
- #### uint64
  ```moonbit
  :::source,moonbitlang/core/random/random.mbt,123:::fn <a href="moonbitlang/core/random#Rand">Rand</a>::uint64(self : <a href="moonbitlang/core/random#Rand">Rand</a>, limit~ : UInt64 = ..) -> UInt64
  ```
  > 
  >  \[uint64\] returns a non-negative pseudo-random 64-bit integer as a Uint64 in the range \[0, 2^64) or \[0, limit) if limit is provided.
  > 
  >  #### Arguments
  > 
  >  * `limit` - The upper bound (exclusive) of the random number to be generated (Optional).
  >    When limit is 0, the range is \[0, 2^64).

## double

```moonbit
:::source,moonbitlang/core/random/random.mbt,158:::fn double(self : <a href="moonbitlang/core/random#Rand">Rand</a>) -> Double
```

 \[double\] returns a pseudo-random 64-bit Double in the range \[0.0, 1.0)

## float

```moonbit
:::source,moonbitlang/core/random/random.mbt,172:::fn float(self : <a href="moonbitlang/core/random#Rand">Rand</a>) -> Float
```

 \[float\] returns a pseudo-random 32-bit Float in the range \[0.0, 1.0)

## int

```moonbit
:::source,moonbitlang/core/random/random.mbt,63:::fn int(self : <a href="moonbitlang/core/random#Rand">Rand</a>, limit~ : Int = ..) -> Int
```

 \[int\] Return a non-negative pseudo-random 31-bit integer as an Int in the range \[0, 2^31) or \[0, limit) if limit is provided.

 #### Arguments

 * `limit` - The upper bound (exclusive) of the random number to be generated (Optional).
   When limit is 0, the range is \[0, 2^31).

## int64

```moonbit
:::source,moonbitlang/core/random/random.mbt,79:::fn int64(self : <a href="moonbitlang/core/random#Rand">Rand</a>, limit~ : Int64 = ..) -> Int64
```

 \[int64\] returns a non-negative pseudo-random 63-bit integer as an Int64 in the range \[0, 2^63)

 #### Arguments

 * `limit` - The upper bound (exclusive) of the random number to be generated (Optional).
   When limit is 0, the range is \[0, 2^63).

## new

```moonbit
:::source,moonbitlang/core/random/random.mbt,24:::fn new(seed~ : Bytes = ..) -> <a href="moonbitlang/core/random#Rand">Rand</a>
```

 Create a new random number generator with \[seed\].
@alert unsafe "Panic if seed is not 32 bytes long"

## shuffle

```moonbit
:::source,moonbitlang/core/random/random.mbt,249:::fn shuffle(self : <a href="moonbitlang/core/random#Rand">Rand</a>, limit : Int, swap : (Int, Int) -> Unit) -> Unit
```

 \[shuffle\] shuffles the first n elements of an array using the Fisher-Yates shuffle algorithm.
@alert unsafe "Panics if limit is negative"

 #### Example
 ```
 let r = @random.new()
 let a = [1, 2, 3, 4, 5]
 r.shuffle(
   a.length(),
   fn(i : Int, j : Int) {
     let t = a[i]
     a[i] = a[j]
     a[j] = t
   },
 )
 ```

## uint

```moonbit
:::source,moonbitlang/core/random/random.mbt,97:::fn uint(self : <a href="moonbitlang/core/random#Rand">Rand</a>, limit~ : UInt = ..) -> UInt
```

 \[uint\] returns a non-negative pseudo-random 32-bit integer as a Uint in the range \[0, 2^32) or \[0, limit) if limit is provided.

 #### Arguments

 * `limit` - The upper bound (exclusive) of the random number to be generated (Optional).
   When limit is 0, the range is \[0, 2^32).

## uint64

```moonbit
:::source,moonbitlang/core/random/random.mbt,123:::fn uint64(self : <a href="moonbitlang/core/random#Rand">Rand</a>, limit~ : UInt64 = ..) -> UInt64
```

 \[uint64\] returns a non-negative pseudo-random 64-bit integer as a Uint64 in the range \[0, 2^64) or \[0, limit) if limit is provided.

 #### Arguments

 * `limit` - The upper bound (exclusive) of the random number to be generated (Optional).
   When limit is 0, the range is \[0, 2^64).
