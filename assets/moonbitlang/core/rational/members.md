# Documentation
|Type|description|
|---|---|
|[RationalError](#RationalError)||
|[T](#T)||

|Value|description|
|---|---|
|[abs](#abs)||
|[ceil](#ceil)||
|[floor](#floor)||
|[fract](#fract)||
|[from\_double](#from_double)||
|[is\_integer](#is_integer)||
|[neg](#neg)||
|[new](#new)||
|[reciprocal](#reciprocal)||
|[to\_double](#to_double)||
|[trunc](#trunc)||

## RationalError

```moonbit
:::source,moonbitlang/core/rational/rational.mbt,167:::pub(all) type! RationalError String

```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/rational/rational.mbt,177:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/rational#RationalError">RationalError</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/rational/rational.mbt,177:::fn op_equal(self : <a href="moonbitlang/core/rational#RationalError">RationalError</a>, other : <a href="moonbitlang/core/rational#RationalError">RationalError</a>) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/rational/rational.mbt,170:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/rational#RationalError">RationalError</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/rational/rational.mbt,170:::fn output(self : <a href="moonbitlang/core/rational#RationalError">RationalError</a>, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 

## T

```moonbit
:::source,moonbitlang/core/rational/rational.mbt,25:::type T
```

 Rational number type.

 Invariants:
 - The denominator is always positive.
 - The numerator and denominator are always coprime.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/rational/rational.mbt,69:::impl <a href="moonbitlang/core/builtin#Add">Add</a> for <a href="moonbitlang/core/rational#T">T</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/rational/rational.mbt,69:::fn op_add(self : <a href="moonbitlang/core/rational#T">T</a>, other : <a href="moonbitlang/core/rational#T">T</a>) -> <a href="moonbitlang/core/rational#T">T</a>
    ```
    > 
    >  NOTE: we don't check overflow here, to align with the `op_add` of `Int64`.
    > TODO: add a `checked_add` method.
- ```moonbit
  :::source,moonbitlang/core/rational/rational.mbt,137:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for <a href="moonbitlang/core/rational#T">T</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/rational/rational.mbt,137:::fn compare(self : <a href="moonbitlang/core/rational#T">T</a>, other : <a href="moonbitlang/core/rational#T">T</a>) -> Int
    ```
    > 
    >  Compares two rational numbers.
- ```moonbit
  :::source,moonbitlang/core/rational/rational.mbt,93:::impl <a href="moonbitlang/core/builtin#Div">Div</a> for <a href="moonbitlang/core/rational#T">T</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/rational/rational.mbt,93:::fn op_div(self : <a href="moonbitlang/core/rational#T">T</a>, other : <a href="moonbitlang/core/rational#T">T</a>) -> <a href="moonbitlang/core/rational#T">T</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/rational/rational.mbt,131:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/rational#T">T</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/rational/rational.mbt,131:::fn op_equal(self : <a href="moonbitlang/core/rational#T">T</a>, other : <a href="moonbitlang/core/rational#T">T</a>) -> Bool
    ```
    > 
    >  Equal to operator for rational numbers.
- ```moonbit
  :::source,moonbitlang/core/rational/rational.mbt,85:::impl <a href="moonbitlang/core/builtin#Mul">Mul</a> for <a href="moonbitlang/core/rational#T">T</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/rational/rational.mbt,85:::fn op_mul(self : <a href="moonbitlang/core/rational#T">T</a>, other : <a href="moonbitlang/core/rational#T">T</a>) -> <a href="moonbitlang/core/rational#T">T</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/rational/rational.mbt,305:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/rational#T">T</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/rational/rational.mbt,305:::fn output(self : <a href="moonbitlang/core/rational#T">T</a>, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/rational/rational.mbt,77:::impl <a href="moonbitlang/core/builtin#Sub">Sub</a> for <a href="moonbitlang/core/rational#T">T</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/rational/rational.mbt,77:::fn op_sub(self : <a href="moonbitlang/core/rational#T">T</a>, other : <a href="moonbitlang/core/rational#T">T</a>) -> <a href="moonbitlang/core/rational#T">T</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/rational/rational.mbt,318:::impl <a href="moonbitlang/core/quickcheck#Arbitrary">@moonbitlang/core/quickcheck.Arbitrary</a> for <a href="moonbitlang/core/rational#T">T</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/rational/rational.mbt,318:::fn arbitrary(size : Int, rs : <a href="moonbitlang/core/quickcheck/splitmix#RandomState">@moonbitlang/core/quickcheck/splitmix.RandomState</a>) -> <a href="moonbitlang/core/rational#T">T</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### abs
  ```moonbit
  :::source,moonbitlang/core/rational/rational.mbt,125:::fn <a href="moonbitlang/core/rational#T">T</a>::abs(self : <a href="moonbitlang/core/rational#T">T</a>) -> <a href="moonbitlang/core/rational#T">T</a>
  ```
  > 
  >  Returns the absolute value of a rational number.
- #### ceil
  ```moonbit
  :::source,moonbitlang/core/rational/rational.mbt,265:::fn <a href="moonbitlang/core/rational#T">T</a>::ceil(self : <a href="moonbitlang/core/rational#T">T</a>) -> Int64
  ```
  > 
  >  Ceils a rational number towards positive infinity.
- #### floor
  ```moonbit
  :::source,moonbitlang/core/rational/rational.mbt,277:::fn <a href="moonbitlang/core/rational#T">T</a>::floor(self : <a href="moonbitlang/core/rational#T">T</a>) -> Int64
  ```
  > 
  >  Floors a rational number towards negative infinity.
- #### fract
  ```moonbit
  :::source,moonbitlang/core/rational/rational.mbt,300:::fn <a href="moonbitlang/core/rational#T">T</a>::fract(self : <a href="moonbitlang/core/rational#T">T</a>) -> <a href="moonbitlang/core/rational#T">T</a>
  ```
  > 
  >  Fractional part of a rational number.
  > Same as `self - self.trunc()`.
- #### from\_double
  ```moonbit
  :::source,moonbitlang/core/rational/deprecated.mbt,25:::fn <a href="moonbitlang/core/rational#T">T</a>::from_double(value : Double) -> <a href="moonbitlang/core/rational#T">T</a>!<a href="moonbitlang/core/rational#RationalError">RationalError</a>
  ```
  > 
- #### is\_integer
  ```moonbit
  :::source,moonbitlang/core/rational/rational.mbt,332:::fn <a href="moonbitlang/core/rational#T">T</a>::is_integer(self : <a href="moonbitlang/core/rational#T">T</a>) -> Bool
  ```
  > 
- #### neg
  ```moonbit
  :::source,moonbitlang/core/rational/rational.mbt,119:::fn <a href="moonbitlang/core/rational#T">T</a>::neg(self : <a href="moonbitlang/core/rational#T">T</a>) -> <a href="moonbitlang/core/rational#T">T</a>
  ```
  > 
  >  Returns the negation of a rational number.
- #### new
  ```moonbit
  :::source,moonbitlang/core/rational/deprecated.mbt,18:::fn <a href="moonbitlang/core/rational#T">T</a>::new(numerator : Int64, denominator : Int64) -> <a href="moonbitlang/core/rational#T">T</a>?
  ```
  > 
- #### reciprocal
  ```moonbit
  :::source,moonbitlang/core/rational/rational.mbt,109:::fn <a href="moonbitlang/core/rational#T">T</a>::reciprocal(self : <a href="moonbitlang/core/rational#T">T</a>) -> <a href="moonbitlang/core/rational#T">T</a>
  ```
  > 
  >  Returns the reciprocal of a rational number.
- #### to\_double
  ```moonbit
  :::source,moonbitlang/core/rational/rational.mbt,151:::fn <a href="moonbitlang/core/rational#T">T</a>::to_double(self : <a href="moonbitlang/core/rational#T">T</a>) -> Double
  ```
  > 
  >  Returns the approximate double value of a rational number.
- #### trunc
  ```moonbit
  :::source,moonbitlang/core/rational/rational.mbt,289:::fn <a href="moonbitlang/core/rational#T">T</a>::trunc(self : <a href="moonbitlang/core/rational#T">T</a>) -> Int64
  ```
  > 
  >  Rounds a rational number towards zero.

## abs

```moonbit
:::source,moonbitlang/core/rational/rational.mbt,125:::fn abs(self : <a href="moonbitlang/core/rational#T">T</a>) -> <a href="moonbitlang/core/rational#T">T</a>
```

 Returns the absolute value of a rational number.

## ceil

```moonbit
:::source,moonbitlang/core/rational/rational.mbt,265:::fn ceil(self : <a href="moonbitlang/core/rational#T">T</a>) -> Int64
```

 Ceils a rational number towards positive infinity.

## floor

```moonbit
:::source,moonbitlang/core/rational/rational.mbt,277:::fn floor(self : <a href="moonbitlang/core/rational#T">T</a>) -> Int64
```

 Floors a rational number towards negative infinity.

## fract

```moonbit
:::source,moonbitlang/core/rational/rational.mbt,300:::fn fract(self : <a href="moonbitlang/core/rational#T">T</a>) -> <a href="moonbitlang/core/rational#T">T</a>
```

 Fractional part of a rational number.
Same as `self - self.trunc()`.

## from\_double

```moonbit
:::source,moonbitlang/core/rational/rational.mbt,188:::fn from_double(value : Double) -> <a href="moonbitlang/core/rational#T">T</a>!<a href="moonbitlang/core/rational#RationalError">RationalError</a>
```

 Returns the approximate rational value of a double.

## is\_integer

```moonbit
:::source,moonbitlang/core/rational/rational.mbt,332:::fn is_integer(self : <a href="moonbitlang/core/rational#T">T</a>) -> Bool
```


## neg

```moonbit
:::source,moonbitlang/core/rational/rational.mbt,119:::fn neg(self : <a href="moonbitlang/core/rational#T">T</a>) -> <a href="moonbitlang/core/rational#T">T</a>
```

 Returns the negation of a rational number.

## new

```moonbit
:::source,moonbitlang/core/rational/rational.mbt,42:::fn new(numerator : Int64, denominator : Int64) -> <a href="moonbitlang/core/rational#T">T</a>?
```

 Creates a rational number.

## reciprocal

```moonbit
:::source,moonbitlang/core/rational/rational.mbt,109:::fn reciprocal(self : <a href="moonbitlang/core/rational#T">T</a>) -> <a href="moonbitlang/core/rational#T">T</a>
```

 Returns the reciprocal of a rational number.

## to\_double

```moonbit
:::source,moonbitlang/core/rational/rational.mbt,151:::fn to_double(self : <a href="moonbitlang/core/rational#T">T</a>) -> Double
```

 Returns the approximate double value of a rational number.

## trunc

```moonbit
:::source,moonbitlang/core/rational/rational.mbt,289:::fn trunc(self : <a href="moonbitlang/core/rational#T">T</a>) -> Int64
```

 Rounds a rational number towards zero.
