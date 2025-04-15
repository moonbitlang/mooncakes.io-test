# Documentation
|Value|description|
|---|---|
|[PI](#PI)||
|[acos](#acos)||
|[acosh](#acosh)||
|[asin](#asin)||
|[asinh](#asinh)||
|[atan](#atan)||
|[atan2](#atan2)||
|[atanh](#atanh)||
|[cbrt](#cbrt)||
|[ceil](#ceil)||
|[cos](#cos)||
|[cosh](#cosh)||
|[exp](#exp)||
|[expm1](#expm1)||
|[floor](#floor)||
|[hypot](#hypot)||
|[ln](#ln)||
|[ln\_1p](#ln_1p)||
|[log10](#log10)||
|[log2](#log2)||
|[maximum](#maximum)||
|[minimum](#minimum)||
|[pi](#pi)||
|[round](#round)||
|[sin](#sin)||
|[sinh](#sinh)||
|[tan](#tan)||
|[tanh](#tanh)||
|[trunc](#trunc)||

## PI

```moonbit
:::source,moonbitlang/core/math/trigonometric.mbt,16:::let PI : Double
```


## acos

```moonbit
:::source,moonbitlang/core/math/trigonometric.mbt,48:::fn acos(x : Double) -> Double
```


## acosh

```moonbit
:::source,moonbitlang/core/math/hyperbolic.mbt,36:::fn acosh(x : Double) -> Double
```


## asin

```moonbit
:::source,moonbitlang/core/math/trigonometric.mbt,43:::fn asin(x : Double) -> Double
```


## asinh

```moonbit
:::source,moonbitlang/core/math/hyperbolic.mbt,31:::fn asinh(x : Double) -> Double
```


## atan

```moonbit
:::source,moonbitlang/core/math/trigonometric.mbt,38:::fn atan(x : Double) -> Double
```


## atan2

```moonbit
:::source,moonbitlang/core/math/trigonometric.mbt,53:::fn atan2(y : Double, x : Double) -> Double
```


## atanh

```moonbit
:::source,moonbitlang/core/math/hyperbolic.mbt,41:::fn atanh(x : Double) -> Double
```


## cbrt

```moonbit
:::source,moonbitlang/core/math/algebraic.mbt,64:::fn cbrt(x : Double) -> Double
```

 Calculates the cube root of a number.

 #### Examples

 ```
 assert_eq!(@math.cbrt(1), 1)
 assert_eq!(@math.cbrt(27), 3)
 assert_eq!(@math.cbrt(125), 5)
 assert_eq!(@math.cbrt(1000), 10)
 ```

## ceil

```moonbit
:::source,moonbitlang/core/math/round.mbt,27:::fn ceil(input : Double) -> Double
```


## cos

```moonbit
:::source,moonbitlang/core/math/trigonometric.mbt,28:::fn cos(x : Double) -> Double
```


## cosh

```moonbit
:::source,moonbitlang/core/math/hyperbolic.mbt,21:::fn cosh(x : Double) -> Double
```


## exp

```moonbit
:::source,moonbitlang/core/math/exp.mbt,16:::fn exp(input : Double) -> Double
```


## expm1

```moonbit
:::source,moonbitlang/core/math/exp.mbt,21:::fn expm1(input : Double) -> Double
```


## floor

```moonbit
:::source,moonbitlang/core/math/round.mbt,41:::fn floor(input : Double) -> Double
```


## hypot

```moonbit
:::source,moonbitlang/core/math/algebraic.mbt,78:::fn hypot(x : Double, y : Double) -> Double
```

 Returns the hypotenuse of a right-angled triangle whose legs are `x` and `y`.

 #### Examples

 ```
 assert_eq!(@math.hypot(3, 4), 5)
 assert_eq!(@math.hypot(5, 12), 13)
 assert_eq!(@math.hypot(8, 15), 17)
 ```

## ln

```moonbit
:::source,moonbitlang/core/math/log.mbt,31:::fn ln(input : Double) -> Double
```

 Calculates the natural logarithm (base e) of the input.

 Parameters:

 - `input` : The floating-point number for which to calculate the natural
   logarithm.

 Returns the natural logarithm of the input.

 Examples:

 ```
 assert_eq!(ln(1.0), 0.0)
 assert_eq!(ln(0.5), -0.6931471805599453)
 ```

## ln\_1p

```moonbit
:::source,moonbitlang/core/math/log.mbt,86:::fn ln_1p(input : Double) -> Double
```

 Calculates ln(1 + x) accurately even when x is close to zero.

 Parameters:

 * `input` : The number to which 1 is added before calculating the logarithm.

 Returns the natural logarithm of 1 + `input`.

 Special Cases:

 * Returns `NaN` if `x` is `NaN` or less than -1.
 * Returns `-Infinity` if `x` is -1.
 * Returns `+Infinity` if `x` is `+Infinity`.

## log10

```moonbit
:::source,moonbitlang/core/math/log.mbt,68:::fn log10(input : Double) -> Double
```

 Calculates the base-10 logarithm of the input number.

 Parameters:

 - `input` : The floating-point number for which to calculate the logarithm.

 Returns the base-10 logarithm of the input number.

 Example:

 ```
 assert_eq!(log10(100.0), 2.0)
 ```

## log2

```moonbit
:::source,moonbitlang/core/math/log.mbt,50:::fn log2(input : Double) -> Double
```

 Calculates the base-2 logarithm of the input number.

 Parameters:

 - `input` : The floating-point number for which the logarithm is to be
   calculated.

 Returns the base-2 logarithm of the input number.

 Example:

 ```
 assert_eq!(log2(8.0), 3.0)
 ```

## maximum

```moonbit
:::source,moonbitlang/core/math/algebraic.mbt,26:::fn maximum[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](x : T, y : T) -> T
```

 Compares and returns the maximum of two values.

 Returns the second argument if the comparison determines them to be equal.

 #### Examples

 ```
 assert_eq!(@math.maximum(1, 2), 2)
 assert_eq!(@math.maximum(2, 2), 2)
 ```

## minimum

```moonbit
:::source,moonbitlang/core/math/algebraic.mbt,45:::fn minimum[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](x : T, y : T) -> T
```

 Compares and returns the minimum of two values.

 Returns the first argument if the comparison determines them to be equal.

 #### Examples

 ```
 assert_eq!(@math.minimum(1, 2), 1)
 assert_eq!(@math.minimum(2, 2), 2)
 ```

## pi

```moonbit
:::source,moonbitlang/core/math/trigonometric.mbt,20:::let pi : Double
```

@alert deprecated "Use `PI` instead"

## round

```moonbit
:::source,moonbitlang/core/math/round.mbt,16:::fn round(input : Double) -> Double
```


## sin

```moonbit
:::source,moonbitlang/core/math/trigonometric.mbt,23:::fn sin(x : Double) -> Double
```


## sinh

```moonbit
:::source,moonbitlang/core/math/hyperbolic.mbt,16:::fn sinh(x : Double) -> Double
```


## tan

```moonbit
:::source,moonbitlang/core/math/trigonometric.mbt,33:::fn tan(x : Double) -> Double
```


## tanh

```moonbit
:::source,moonbitlang/core/math/hyperbolic.mbt,26:::fn tanh(x : Double) -> Double
```


## trunc

```moonbit
:::source,moonbitlang/core/math/round.mbt,55:::fn trunc(input : Double) -> Double
```

