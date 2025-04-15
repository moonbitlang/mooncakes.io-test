# Documentation
|Type|description|
|---|---|
|[Tuple7](#Tuple7)||
|[Tuple6](#Tuple6)||
|[Tuple5](#Tuple5)||
|[Tuple4](#Tuple4)||
|[Tuple3](#Tuple3)||
|[Tuple2](#Tuple2)||

|Value|description|
|---|---|
|[curry](#curry)||
|[fst](#fst)||
|[map\_both](#map_both)||
|[map\_fst](#map_fst)||
|[map\_snd](#map_snd)||
|[pair](#pair)||
|[snd](#snd)||
|[swap](#swap)||
|[uncurry](#uncurry)||

## curry

```moonbit
:::source,moonbitlang/core/tuple/tuple.mbt,118:::fn curry[T, U, V](f : (T, U) -> V) -> ((T) -> ((U) -> V))
```

 Curry a function.

 #### Example
 ```
 let add = fn(x : Int, y : Int) -> Int { x + y }
 let curried_add = @tuple.curry(add)
 assert_eq!(curried_add(1)(2), 3)
 ```

## fst

```moonbit
:::source,moonbitlang/core/tuple/tuple.mbt,36:::fn fst[T, U](tuple : (T, U)) -> T
```

 Get the first element of a tuple.

 #### Example
 ```
 let tuple = (1, 2)
 let x = @tuple.fst(tuple)
 assert_eq!(x, 1)
 ```

## map\_both

```moonbit
:::source,moonbitlang/core/tuple/tuple.mbt,88:::fn map_both[T, U, V, W](f : (T) -> U, g : (V) -> W, tuple : (T, V)) -> (U, W)
```

 Map a function over both elements of a tuple.

 #### Example
 ```
 let tuple = (1, 2)
 let mapped = @tuple.map_both(fn(x : Int) -> Int { x + 1 }, fn(x : Int) -> Int { x - 1 }, tuple)
 assert_eq!(mapped, (2, 1))
 ```

## map\_fst

```moonbit
:::source,moonbitlang/core/tuple/tuple.mbt,62:::fn map_fst[T, U, V](f : (T) -> U, tuple : (T, V)) -> (U, V)
```

 Map a function over the first element of a tuple.

 #### Example
 ```
 let tuple = (1, 2)
 let mapped = @tuple.map_fst(fn(x : Int) -> Int { x + 1 }, tuple)
 assert_eq!(mapped, (2, 2))
 ```

## map\_snd

```moonbit
:::source,moonbitlang/core/tuple/tuple.mbt,75:::fn map_snd[T, U, V](f : (T) -> U, tuple : (V, T)) -> (V, U)
```

 Map a function over the second element of a tuple.

 #### Example
 ```
 let tuple = (1, 2)
 let mapped = @tuple.map_snd(fn(x : Int) -> Int { x + 1 }, tuple)
 assert_eq!(mapped, (1, 3))
 ```

## pair

```moonbit
:::source,moonbitlang/core/tuple/tuple.mbt,23:::fn pair[T, U](x : T, y : U) -> (T, U)
```

 Create a tuple with two elements.

 #### Example
 ```
 let tuple = @tuple.pair(1, 2)
 assert_eq!(tuple, (1, 2))
 ```

## snd

```moonbit
:::source,moonbitlang/core/tuple/tuple.mbt,49:::fn snd[T, U](tuple : (T, U)) -> U
```

 Get the second element of a tuple.

 #### Example
 ```
 let tuple = (1, 2)
 let y = @tuple.snd(tuple)
 assert_eq!(y, 2)
 ```

## swap

```moonbit
:::source,moonbitlang/core/tuple/tuple.mbt,105:::fn swap[T, U](tuple : (T, U)) -> (U, T)
```

 Swap the elements of a tuple.

 #### Example
 ```
 let tuple = (1, 2)
 let swapped = @tuple.swap(tuple)
 assert_eq!(swapped, (2, 1))
 ```

## uncurry

```moonbit
:::source,moonbitlang/core/tuple/tuple.mbt,131:::fn uncurry[T, U, V](f : (T) -> ((U) -> V)) -> ((T, U) -> V)
```

 Uncurry a function.

 #### Example
 ```
 let add = fn(x : Int) -> (Int) -> Int { fn(y : Int) -> Int { x + y } }
 let uncurried_add = @tuple.uncurry(add)
 assert_eq!(uncurried_add(1, 2), 3)
 ```

## Tuple7


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/tuple/tuple_arbitrary.mbt,77:::impl[A : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, B : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, C : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, D : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, E : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, F : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, G : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for (A, B, C, D, E, F, G)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/tuple/tuple_arbitrary.mbt,85:::fn arbitrary[A : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, B : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, C : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, D : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, E : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, F : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, G : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>](size : Int, r0 : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> (A, B, C, D, E, F, G)
    ```
    > 

## Tuple6


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/tuple/tuple_arbitrary.mbt,63:::impl[A : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, B : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, C : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, D : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, E : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, F : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for (A, B, C, D, E, F)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/tuple/tuple_arbitrary.mbt,70:::fn arbitrary[A : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, B : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, C : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, D : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, E : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, F : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>](size : Int, r0 : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> (A, B, C, D, E, F)
    ```
    > 

## Tuple5


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/tuple/tuple_arbitrary.mbt,50:::impl[A : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, B : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, C : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, D : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, E : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for (A, B, C, D, E)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/tuple/tuple_arbitrary.mbt,56:::fn arbitrary[A : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, B : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, C : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, D : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, E : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>](size : Int, r0 : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> (A, B, C, D, E)
    ```
    > 

## Tuple4


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/tuple/tuple_arbitrary.mbt,38:::impl[A : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, B : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, C : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, D : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for (A, B, C, D)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/tuple/tuple_arbitrary.mbt,43:::fn arbitrary[A : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, B : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, C : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, D : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>](size : Int, r0 : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> (A, B, C, D)
    ```
    > 

## Tuple3


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/tuple/tuple_arbitrary.mbt,28:::impl[A : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, B : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, C : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for (A, B, C)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/tuple/tuple_arbitrary.mbt,28:::fn arbitrary[A : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, B : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, C : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>](size : Int, r0 : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> (A, B, C)
    ```
    > 

## Tuple2


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/tuple/tuple_arbitrary.mbt,19:::impl[A : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, B : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>] <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for (A, B)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/tuple/tuple_arbitrary.mbt,19:::fn arbitrary[A : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>, B : <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a>](size : Int, r0 : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> (A, B)
    ```
    > 
