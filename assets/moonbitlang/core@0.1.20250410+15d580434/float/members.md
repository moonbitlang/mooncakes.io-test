# Documentation
|Type|description|
|---|---|
|[Float](#Float)||

|Value|description|
|---|---|
|[abs](#abs)||
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
|[default](#default)||
|[exp](#exp)||
|[expm1](#expm1)||
|[floor](#floor)||
|[hypot](#hypot)||
|[infinity](#infinity)||
|[is\_inf](#is_inf)||
|[is\_nan](#is_nan)||
|[is\_neg\_inf](#is_neg_inf)||
|[is\_pos\_inf](#is_pos_inf)||
|[ln](#ln)||
|[ln\_1p](#ln_1p)||
|[max\_value](#max_value)||
|[min\_positive](#min_positive)||
|[min\_value](#min_value)||
|[neg\_infinity](#neg_infinity)||
|[not\_a\_number](#not_a_number)||
|[pow](#pow)||
|[round](#round)||
|[sin](#sin)||
|[sinh](#sinh)||
|[tan](#tan)||
|[tanh](#tanh)||
|[to\_be\_bytes](#to_be_bytes)||
|[to\_int](#to_int)||
|[to\_le\_bytes](#to_le_bytes)||
|[trunc](#trunc)||

## abs

```moonbit
:::source,moonbitlang/core/float/float.mbt,128:::fn abs(self : Float) -> Float
```

 Returns the absolute value of a floating-point number.

 Parameters:

 * `self` : A floating-point number.

 Returns the absolute value of the input number. For positive numbers and
zero, returns the number unchanged. For negative numbers, returns the
negation of the number. For NaN, returns NaN.

 Example:

 ```moonbit
 test "Float::abs" {
   inspect!((1.5 : Float).abs(), content="1.5")
   inspect!((-1.5 : Float).abs(), content="1.5")
   inspect!((0.0 : Float).abs(), content="0")
   inspect!((-0.0 : Float).abs(), content="0")
   inspect!(@float.not_a_number.abs().is_nan(), content="true")
 }
 ```

## acos

```moonbit
:::source,moonbitlang/core/float/trig.mbt,142:::fn acos(self : Float) -> Float
```

 Calculates the arccosine of a floating-point number.

 Parameters:

 * `x` : The number for which to calculate the arccosine.

 Returns the arccosine of the number `x`.

 * Returns NaN if the input is NaN.
 * Returns NaN if the input is less than -1 or greater than 1.

 Example:

 ```moonbit
 test "acos" {
   inspect!((0.0 : Float).acos(), content="1.5707963705062866")
   inspect!((1.0 : Float).acos(), content="0")
   inspect!((-1.0 : Float).acos(), content="3.1415927410125732")
   inspect!(@float.not_a_number.acos(), content="NaN")
   inspect!(@float.infinity.acos(), content="NaN")
   inspect!(@float.neg_infinity.acos(), content="NaN")
 }
 ```

## acosh

```moonbit
:::source,moonbitlang/core/float/hyperbolic.mbt,177:::fn acosh(self : Float) -> Float
```

 Calculates the inverse hyperbolic cosine of a number.

 Parameters:

 * `x` : The number for which to calculate the inverse hyperbolic cosine.

 Returns the inverse hyperbolic cosine of `x`.

 Special cases:

 * Returns `NaN` if `x` is less than `1`.
 * Returns `NaN` if `x` is `NaN`.
 * Returns `0` if `x` is `1`.
 * Returns `infinity` if `x` is `infinity` (Positive infinity).

 Example

 ```moonbit
 test "acosh" {
   inspect!((1.0 : Float).acosh(), content="0")
   inspect!((2.0 : Float).acosh(), content="1.316957950592041")
   inspect!((1000.0 : Float).acosh(), content="7.600902080535889")
   inspect!((-1.0 : Float).acosh(), content="NaN")
   inspect!((-2.0 : Float).acosh(), content="NaN")
   inspect!(@float.not_a_number.acosh(), content="NaN")
   inspect!(@float.infinity.acosh(), content="Infinity")
   inspect!(@float.neg_infinity.acosh(), content="NaN")
 }
 ```

## asin

```moonbit
:::source,moonbitlang/core/float/trig.mbt,114:::fn asin(self : Float) -> Float
```

 Calculates the arcsine of a floating-point number.

 Parameters:

 * `x` : The number for which to calculate the arcsine.

 Returns the arcsine of the number `x`.

 * Returns NaN if the input is NaN.
 * Returns NaN if the input is less than -1 or greater than 1.

 Example:

 ```moonbit
 test "asin" {
   inspect!((0.0 : Float).asin(), content="0")
   inspect!((1.0 : Float).asin(), content="1.5707963705062866")
   inspect!((-1.0 : Float).asin(), content="-1.5707963705062866")
   inspect!(@float.not_a_number.asin(), content="NaN")
   inspect!(@float.infinity.asin(), content="NaN")
   inspect!(@float.neg_infinity.asin(), content="NaN")
 }
 ```

## asinh

```moonbit
:::source,moonbitlang/core/float/hyperbolic.mbt,143:::fn asinh(self : Float) -> Float
```

 Calculates the inverse hyperbolic sine of a number.

 Parameters:

 * `x` : The number for which to calculate the inverse hyperbolic sine.

 Returns the inverse hyperbolic sine of `x`.

 Special cases:

 * Returns `NaN` if `x` is `NaN`
 * Returns `infinity` if `x` is `infinity`

 Example

 ```moonbit
 test "asinh" {
   inspect!((0.0 : Float).asinh(), content="0")
   inspect!((-0.0 : Float).asinh(), content="0")
   inspect!((1.0 : Float).asinh(), content="0.8813735842704773")
   inspect!((2.0 : Float).asinh(), content="1.4436354637145996")
   inspect!((1000.0 : Float).asinh(), content="7.600902557373047")
   inspect!(@float.not_a_number.asinh(), content="NaN")
   inspect!(@float.infinity.asinh(), content="Infinity")
   inspect!(@float.neg_infinity.asinh(), content="-Infinity")
 }
 ```

## atan

```moonbit
:::source,moonbitlang/core/float/trig.mbt,169:::fn atan(self : Float) -> Float
```

 Calculates the arctangent of a floating-point number.

 Parameters:

 * `x` : The number for which to calculate the arctangent.

 Returns the arctangent of the number `x`.

 Example:

 * Returns NaN if the input is NaN.

 ```moonbit
 test "atan" {
   inspect!((0.0 : Float).atan(), content="0")
   inspect!((1.0 : Float).atan(), content="0.7853981852531433")
   inspect!((-1.0 : Float).atan(), content="-0.7853981852531433")
   inspect!(@float.not_a_number.atan(), content="NaN")
   inspect!(@float.infinity.atan(), content="1.5707963705062866")
   inspect!(@float.neg_infinity.atan(), content="-1.5707963705062866")
 }
 ```

## atan2

```moonbit
:::source,moonbitlang/core/float/trig.mbt,204:::fn atan2(self : Float, other : Float) -> Float
```

 Calculates the arctangent of the quotient of two floating-point numbers.

 Parameters:

 * `self` : The numerator of the quotient.
 * `x` : The denominator of the quotient.

 Returns the arctangent of the quotient `self / x`.

 * Returns NaN if self or x is NaN.

 Example:

 ```moonbit
 test "atan2" {
   inspect!((0.0 : Float).atan2(-1.0), content="3.1415927410125732")
   inspect!((1.0 : Float).atan2(0.0), content="1.5707963705062866")
   inspect!((1.0 : Float).atan2(1.0), content="0.7853981852531433")
   inspect!(@float.not_a_number.atan2(1.0), content="NaN")
   inspect!((1.0 : Float).atan2(not_a_number), content="NaN")
   inspect!(@float.infinity.atan2(1.0), content="1.5707963705062866")
   inspect!((1.0 : Float).atan2(infinity), content="0")
   inspect!(@float.neg_infinity.atan2(1.0), content="-1.5707963705062866")
   inspect!((1.0 : Float).atan2(@float.neg_infinity), content="3.1415927410125732")
   inspect!(@float.infinity.atan2(@float.infinity), content="0.7853981852531433")
   inspect!(@float.neg_infinity.atan2(@float.neg_infinity), content="-2.356194496154785")
   inspect!(@float.infinity.atan2(@float.neg_infinity), content="2.356194496154785")
   inspect!(@float.neg_infinity.atan2(@float.infinity), content="-0.7853981852531433")
 }
 ```

## atanh

```moonbit
:::source,moonbitlang/core/float/hyperbolic.mbt,212:::fn atanh(self : Float) -> Float
```

 Calculates the inverse hyperbolic tangent of a number.

 Parameters:

 * `x` : The number for which to calculate the inverse hyperbolic tangent.

 Returns the inverse hyperbolic tangent of `x`.

 Special cases:

 * Returns `NaN` if `x` is less than `-1` or greater than `1`.
 * Returns `infinity` if `x` is `1`.
 * Returns `-infinity` if `x` is `-1`.

 Example

 ```moonbit
 test "atanh" {
   inspect!((0.0 : Float).atanh(), content="0")
   inspect!((-0.0 : Float).atanh(), content="0")
   inspect!((0.5 : Float).atanh(), content="0.5493061542510986")
   inspect!((-0.5 : Float).atanh(), content="-0.5493061542510986")
   inspect!((1.0 : Float).atanh(), content="Infinity")
   inspect!((-1.0 : Float).atanh(), content="-Infinity")
   inspect!((1.5 : Float).atanh(), content="NaN")
   inspect!(@float.not_a_number.atanh(), content="NaN")
   inspect!(@float.infinity.atanh(), content="NaN")
   inspect!(@float.neg_infinity.atanh(), content="NaN")
 }
 ```

## cbrt

```moonbit
:::source,moonbitlang/core/float/cbrt.mbt,44:::fn cbrt(self : Float) -> Float
```

 Calculates the cube root of a number.

 Parameters:

 * `x` : The number for which to calculate the cube root.

 Returns the cube root of `x`.

 Special Cases:

 * Return `NaN` if `x` is `NaN`.
 * Return `±0` if `x` is `±0`.
 * Return `Infinity` if `x` is `Infinity`.
 * Return `-Infinity` if `x` is `-Infinity`.

 Example

 ```moonbit
 test "cbrt" {
  inspect!((0 : Float).cbrt(), content="0")
  inspect!((1 : Float).cbrt(), content="1")
  inspect!((8 : Float).cbrt(), content="2")
  inspect!((-8 : Float).cbrt(), content="-2")
  inspect!(@float.not_a_number.cbrt(), content="NaN")
  inspect!(@float.infinity.cbrt(), content="Infinity")
  inspect!(@float.neg_infinity.cbrt(), content="-Infinity")
 }
 ```

## ceil

```moonbit
:::source,moonbitlang/core/float/round_wasm.mbt,59:::fn ceil(self : Float) -> Float
```

 Returns the smallest integer greater than or equal to the given
floating-point number.

 Parameters:

 * `self` : The floating-point number to round up.

 Returns the ceiling value of the input as a `Float`.

 Example:

 ```moonbit
 test "ceil" {
   inspect!((1.4 : Float).ceil(), content="2")
   inspect!((1.0 : Float).ceil(), content="1")
   inspect!((-1.4 : Float).ceil(), content="-1")
 }
 ```

## cos

```moonbit
:::source,moonbitlang/core/float/trig.mbt,61:::fn cos(self : Float) -> Float
```

 Calculates the cosine of a floating-point number in radians.

 Parameters:

 * `x` : The angle in radians for which to calculate the cosine.

 Returns the cosine of the angle `x`.

 Example:

 ```moonbit
 test "cos" {
   inspect!((0.0 : Float).cos(), content="1")
   inspect!((2.0 : Float).cos(), content="-0.416146844625473")
   inspect!((-5.0 : Float).cos(), content="0.28366219997406006")
   inspect!(@float.not_a_number.cos(), content="NaN")
   inspect!(@float.infinity.cos(), content="NaN")
   inspect!(@float.neg_infinity.cos(), content="NaN")
 }
 ```

## cosh

```moonbit
:::source,moonbitlang/core/float/hyperbolic.mbt,77:::fn cosh(self : Float) -> Float
```

 Calculates the hyperbolic cosine of a number.

 Parameters:

 * `x` : The number for which to calculate the hyperbolic cosine.

 Returns the hyperbolic cosine of `x`.

 Special cases:

 * Returns `infinity` if `x` is `infinity`
 * Returns `NaN` if `x` is `NaN`

 Example

 ```moonbit
 test "cosh" {
   inspect!((0.0 : Float).cosh(), content="1")
   inspect!((-0.0).cosh(), content="1")
   inspect!((1.0 : Float).cosh(), content="1.5430806875228882")
   inspect!((2.0: Float).cosh(), content="3.762195587158203")
   inspect!((1000.0: Float).cosh(), content="Infinity")
   inspect!((-1000.0 : Float).cosh(), content="Infinity")
   inspect!(@float.not_a_number.cosh(), content="NaN")
   inspect!(@float.infinity.cosh(), content="Infinity")
   inspect!(@float.neg_infinity.cosh(), content="Infinity")
 }
 ```

## default

```moonbit
:::source,moonbitlang/core/float/float.mbt,179:::fn default() -> Float
```

 Returns the default value for `Float` type, which is `0.0`.

 Returns a float value of `0.0`.

 Example:

 ```moonbit
 test "default" {
   inspect!(@float.default(), content="0")
 }
 ```

## exp

```moonbit
:::source,moonbitlang/core/float/exp.mbt,91:::fn exp(self : Float) -> Float
```

 Calculates the exponential function e^x for a given floating-point number.

 Parameters:

 * `x` : A floating-point number for which to calculate e^x.

 Returns the value of e raised to the power of x (e^x).

 Example:

 ```moonbit
 test "exp" {
   inspect!((0.0 : Float).exp(), content="1")
   inspect!((1.0 : Float).exp(), content="2.7182817459106445")
   inspect!(@float.neg_infinity.exp(), content="0")
 }
 ```

## expm1

```moonbit
:::source,moonbitlang/core/float/exp.mbt,152:::fn expm1(self : Float) -> Float
```

 Calculates exp(x) - 1 accurately even when x is close to zero.

 Parameters:

 * `x` : The exponent.

 Returns e raised to the power of `x`, minus 1.

 Special Cases:

 * Returns NaN if `x` is NaN.
 * Returns -1 if `x` is negative infinity.
 * Returns `Infinity` if `x` is positive infinity.

 Example

 ```moonbit
 test "expm1" {
  inspect!((0 : Float).expm1(), content="0")
  inspect!((1 : Float).expm1(), content="1.718281865119934")
  inspect!((-1 : Float).expm1(), content="-0.6321205496788025")
  inspect!(@float.not_a_number.expm1(), content="NaN")
  inspect!(@float.infinity.expm1(), content="Infinity")
  inspect!(@float.neg_infinity.expm1(), content="-1")
 }
 ```

## floor

```moonbit
:::source,moonbitlang/core/float/round_wasm.mbt,80:::fn floor(self : Float) -> Float
```

 Returns the largest integer less than or equal to the given floating-point
number.

 Parameters:

 * `number` : The floating-point number to be rounded down.

 Returns a floating-point number representing the largest integer less than or
equal to the input.

 Example:

 ```moonbit
 test "floor" {
   inspect!((3.7 : Float).floor(), content="3")
   inspect!((-3.7 : Float).floor(), content="-4")
 }
 ```

## hypot

```moonbit
:::source,moonbitlang/core/float/hypot.mbt,41:::fn hypot(self : Float, y : Float) -> Float
```

 Calculates the the square root of the sum of the squares of its arguments.

 Parameters:

 * `self` : The number to be used as the first argument.
 * `y` : The number to be used as the second argument.

 Returns the hypotenuse of a right-angled triangle whose legs are `self` and `y`.

 Example:

 ```moonbit
 test "hypot" {
   inspect!((3.0 : Float).hypot(4.0), content="5")
   inspect!((5.0 : Float).hypot(12.0), content="13")
   inspect!((8.0 : Float).hypot(15.0), content="17")
   inspect!((7.0 : Float).hypot(24.0), content="25")
   inspect!(@float.not_a_number.hypot(1.0), content="NaN")
   inspect!((1.0 : Float).hypot(@float.not_a_number), content="NaN")
   inspect!(@float.infinity.hypot(1.0), content="Infinity")
   inspect!((1.0 : Float).hypot(@float.infinity), content="Infinity")
   inspect!(@float.neg_infinity.hypot(1.0), content="Infinity")
   inspect!((1.0 : Float).hypot(@float.neg_infinity), content="Infinity")
 }
 ```

## infinity

```moonbit
:::source,moonbitlang/core/float/float.mbt,46:::let infinity : Float
```

 Represents positive infinity as a floating-point value.

 Returns a constant value representing positive infinity in IEEE 754
single-precision floating-point format (0x7F800000).

 Example:

 ```moonbit
 test "infinity" {
   inspect!(@float.infinity.is_pos_inf(), content="true")
   inspect!(@float.infinity > 1.0, content="true")
 }
 ```

## is\_inf

```moonbit
:::source,moonbitlang/core/float/float.mbt,298:::fn is_inf(self : Float) -> Bool
```

 Determines if the floating-point number is positive or negative infinity.

 Parameters:

 * `self` : The floating-point number to be checked.

 Returns a boolean value indicating whether the number is positive or negative
infinity.

 Example:

 ```moonbit
 test "Float::is_inf" {
   inspect!(@float.infinity.is_inf(), content="true")
   inspect!(@float.neg_infinity.is_inf(), content="true")
   inspect!((1.0 : Float).is_inf(), content="false")
 }
 ```

## is\_nan

```moonbit
:::source,moonbitlang/core/float/float.mbt,364:::fn is_nan(self : Float) -> Bool
```

 Determines if the floating-point number is NaN (Not a Number).

 Parameters:

 * `self` : The floating-point number to be checked.

 Returns a boolean value indicating whether the number is NaN.

 Example:

 ```moonbit
 test "Float::is_nan" {
   inspect!(@float.not_a_number.is_nan(), content="true")
   inspect!((1.0 : Float).is_nan(), content="false")
   inspect!(@float.infinity.is_nan(), content="false")
 }
 ```

## is\_neg\_inf

```moonbit
:::source,moonbitlang/core/float/float.mbt,342:::fn is_neg_inf(self : Float) -> Bool
```

 Determines if the floating-point number is negative infinity.

 Parameters:

 * `self` : The floating-point number to be checked.

 Returns a boolean value indicating whether the number is negative infinity.

 Example:

 ```moonbit
 test "Float::is_neg_inf" {
   inspect!(@float.neg_infinity.is_neg_inf(), content="true")
   inspect!((1.0 : Float).is_neg_inf(), content="false")
   inspect!(@float.infinity.is_neg_inf(), content="false")
 }
 ```

## is\_pos\_inf

```moonbit
:::source,moonbitlang/core/float/float.mbt,320:::fn is_pos_inf(self : Float) -> Bool
```

 Determines if the floating-point number is positive infinity.

 Parameters:

 * `self` : The floating-point number to be checked.

 Returns a boolean value indicating whether the number is positive infinity.

 Example:

 ```moonbit
 test "Float::is_pos_inf" {
   inspect!(@float.infinity.is_pos_inf(), content="true")
   inspect!((1.0 : Float).is_pos_inf(), content="false")
   inspect!(@float.neg_infinity.is_pos_inf(), content="false")
 }
 ```

## ln

```moonbit
:::source,moonbitlang/core/float/log.mbt,75:::fn ln(self : Float) -> Float
```

 Calculates the natural logarithm of a floating-point number.

 Parameters:

 * `value` : The floating-point number to calculate the natural logarithm of.

 Returns the natural logarithm of the input value. Special cases are handled
as follows:

 * Returns `0.0` when the input is `1.0`
 * Returns `neg_infinity` when the input is `0.0`
 * Returns `not_a_number` when the input is negative
 * Returns `infinity` when the input is `infinity`
 * Returns `not_a_number` when the input is `not_a_number`

 Example:

 ```moonbit
 test "ln" {
   inspect!((1.0 : Float).ln(), content="0")
   inspect!((2.718281828459045 : Float).ln(), content="0.9999999403953552")
   inspect!((0.0 : Float).ln(), content="-Infinity")
 }
 ```

## ln\_1p

```moonbit
:::source,moonbitlang/core/float/log.mbt,137:::fn ln_1p(self : Float) -> Float
```

 Calculates ln(1 + x) accurately even when x is close to zero.

 Parameters:

 * `x` : The number to which 1 is added before calculating the logarithm.

 Returns the natural logarithm of 1 + `x`.

 Special Cases:

 * Returns `NaN` if `x` is `NaN` or less than -1.
 * Returns `-Infinity` if `x` is -1.
 * Returns `+Infinity` if `x` is `+Infinity`.

 Example:

 ```moonbit
 test "ln_1p" {
   inspect!((0 : Float).ln_1p(), content="0")
   inspect!((1 : Float).ln_1p(), content="0.6931471824645996")
   inspect!((-1 : Float).ln_1p(), content="-Infinity")
   inspect!((-2 : Float).ln_1p(), content="NaN")
   inspect!(@float.not_a_number.ln_1p(), content="NaN")
   inspect!(@float.infinity.ln_1p(), content="Infinity")
   inspect!(@float.neg_infinity.ln_1p(), content="NaN")
 }
 ```

## max\_value

```moonbit
:::source,moonbitlang/core/float/float.mbt,77:::let max_value : Float
```

 Represents the maximum finite value of a 32-bit floating-point number, which
is approximately 3.4028235e+38.

 Example:

 ```moonbit
 test "max_value" {
   inspect!(@float.max_value < @float.infinity, content="true")
   inspect!(@float.max_value > 0.0, content="true")
 }
 ```

## min\_positive

```moonbit
:::source,moonbitlang/core/float/float.mbt,104:::let min_positive : Float
```

 Represents the smallest positive normalized floating-point number that can be
represented by the Float type (approximately 1.17549435e-38).

 Example:

 ```moonbit
 test "min_positive" {
   inspect!(@float.min_positive > 0.0, content="true")
   inspect!(@float.min_positive < 1.2e-38, content="true")
 }
 ```

## min\_value

```moonbit
:::source,moonbitlang/core/float/float.mbt,90:::let min_value : Float
```

 Represents the smallest finite negative Float value (-3.4028235e+38).

 Example:

 ```moonbit
 test "min_value" {
   inspect!(@float.min_value < -1.0, content="true")
   inspect!(@float.min_value > @float.neg_infinity, content="true")
 }
 ```

## neg\_infinity

```moonbit
:::source,moonbitlang/core/float/float.mbt,63:::let neg_infinity : Float
```

 Represents negative infinity for 32-bit floating-point numbers. This constant
has a mathematical value of -∞ and follows the IEEE 754 standard for
floating-point arithmetic.

 Returns a `Float` value representing negative infinity.

 Example:

 ```moonbit
 test "neg_infinity" {
   inspect!(@float.neg_infinity.is_neg_inf(), content="true")
   inspect!(@float.neg_infinity < (-1.0 : Float), content="true")
 }
 ```

## not\_a\_number

```moonbit
:::source,moonbitlang/core/float/float.mbt,30:::let not_a_number : Float
```

 Represents the Not a Number (NaN) value in floating-point arithmetic. NaN is
used to represent undefined or unrepresentable values, such as the result of
0\.0/0.0.

 Returns a special floating-point value that represents NaN.

 Example:

 ```moonbit
 test "not_a_number" {
   inspect!(@float.not_a_number.is_nan(), content="true")
   inspect!(@float.not_a_number + 1.0, content="NaN")
 }
 ```

## pow

```moonbit
:::source,moonbitlang/core/float/pow.mbt,35:::fn pow(self : Float, other : Float) -> Float
```

 Calculates the power of a floating-point number raised to another
floating-point number.

 Parameters:

 * `base` : The base number to be raised to a power.
 * `exponent` : The power to which the base number is raised.

 Returns the result of raising `base` to the power of `exponent`.

 Example:

 ```moonbit
 test "pow" {
   inspect!((2.0 : Float).pow(3.0), content="8")
   inspect!((4.0 : Float).pow(0.5), content="2")
   inspect!((1.0 : Float).pow(-1.0), content="1")
 }
 ```

## round

```moonbit
:::source,moonbitlang/core/float/round_wasm.mbt,103:::fn round(self : Float) -> Float
```

 Rounds a floating-point number to the nearest integer value. If the
fractional part is exactly 0.5, rounds up to the nearest integer (ties to
ceiling).

 Parameters:

 * `self` : The floating-point number to be rounded.

 Returns the rounded value as a float.

 Example:

 ```moonbit
 test "round" {
   inspect!((1.4 : Float).round(), content="1")
   inspect!((1.5 : Float).round(), content="2")
   inspect!((1.6 : Float).round(), content="2")
   inspect!((-1.5 : Float).round(), content="-1")
 }
 ```

## sin

```moonbit
:::source,moonbitlang/core/float/trig.mbt,36:::fn sin(self : Float) -> Float
```

 Calculates the sine of a floating-point number in radians.

 Parameters:

 * `x` : The angle in radians for which to calculate the sine.

 Returns the sine of the angle `x`.

 Example:

 ```moonbit
 test "sin" {
   inspect!((0.0 : Float).sin(), content="0")
   inspect!((2.0 : Float).sin(), content="0.9092974066734314")
   inspect!((-5.0 : Float).sin(), content="0.9589242935180664")
   inspect!(@float.not_a_number.sin(), content="NaN")
   inspect!(@float.infinity.sin(), content="NaN")
   inspect!(@float.neg_infinity.sin(), content="NaN")
 }
 ```

## sinh

```moonbit
:::source,moonbitlang/core/float/hyperbolic.mbt,44:::fn sinh(self : Float) -> Float
```

 Calculates the hyperbolic sine of a number.

 Parameters:

 * `x` : The number for which to calculate the hyperbolic sine.

 Returns the hyperbolic sine of `x`.

 Special cases:

 * Returns `infinity` if `x` is `infinity`
 * Returns `NaN` if `x` is `NaN`

 Example:

 ```moonbit
 test "sinh" {
   inspect!((0.0 : Float).sinh(), content="0")
   inspect!((-0.0 : Float).sinh(), content="0")
   inspect!((1.0 : Float).sinh(), content="1.175201177597046")
   inspect!((2.0 : Float).sinh(), content="3.6268603801727295")
   inspect!((1000.0 : Float).sinh(), content="Infinity")
   inspect!((-1000.0 : Float).sinh(), content="-Infinity")
   inspect!(@float.not_a_number.sinh(), content="NaN")
   inspect!(@float.infinity.sinh(), content="Infinity")
   inspect!(@float.neg_infinity.sinh(), content="-Infinity")
 }
 ```

## tan

```moonbit
:::source,moonbitlang/core/float/trig.mbt,86:::fn tan(self : Float) -> Float
```

 Calculates the tangent of a floating-point number in radians.

 Parameters:

 * `x` : The angle in radians for which to calculate the tangent.

 Returns the tangent of the angle `x`.

 Example:

 ```moonbit
 test "tan" {
   inspect!((0.0 : Float).tan(), content="0")
   inspect!((2.0 : Float).tan(), content="-2.185039758682251")
   inspect!((-5.0 : Float).tan(), content="3.3805150985717773")
   inspect!(@float.not_a_number.tan(), content="NaN")
   inspect!(@float.infinity.tan(), content="NaN")
   inspect!(@float.neg_infinity.tan(), content="NaN")
 }
 ```

## tanh

```moonbit
:::source,moonbitlang/core/float/hyperbolic.mbt,111:::fn tanh(self : Float) -> Float
```

 Calculates the hyperbolic tangent of a number.

 Parameters:

 * `x` : The number for which to calculate the hyperbolic tangent.

 Returns the hyperbolic tangent of `x`.

 Special cases:

 * Returns `NaN` if `x` is `NaN`
 * Returns `1` if `x` is `infinity`
 * Returns `-1` if `x` is `-infinity`

 Example

 ```moobit
 test "tanh" {
   inspect!((0.0 : Float).tanh(), content="0")
   inspect!((-0.0 : Float).tanh(), content="0")
   inspect!((1.0 : Float).tanh(), content="0.7615941559557649")
   inspect!((2.0 : Float).tanh(), content="0.9640275800758169")
   inspect!((1000.0 : Float).tanh(), content="1")
   inspect!((-1000.0 : Float).tanh(), content="-1")
   inspect!(@float.not_a_number.tanh(), content="NaN")
   inspect!(@float.infinity.tanh(), content="1")
   inspect!(@float.neg_infinity.tanh(), content="-1")
 }
 ```

## to\_be\_bytes

```moonbit
:::source,moonbitlang/core/float/float.mbt,251:::fn to_be_bytes(self : Float) -> Bytes
```

 Converts a floating-point number to a sequence of bytes in big-endian byte
order. In big-endian order, the most significant byte is stored at the lowest
memory address.

 Parameters:

 * `float` : The floating-point number to be converted.

 Returns a sequence of 4 bytes representing the floating-point number in IEEE
754 single-precision format with big-endian byte order.

 Example:

 ```moonbit
 test "Float::to_be_bytes" {
   let x : Float = 1.0
   inspect!(x.to_be_bytes(), content=
   #|b"\x3f\x80\x00\x00"
 )
 }
 ```

## to\_int

```moonbit
:::source,moonbitlang/core/float/to_int_wasm.mbt,40:::fn to_int(self : Float) -> Int
```

 Converts a floating-point number to an integer, with proper handling of
special cases such as NaN and values outside the range of 32-bit integers.

 Parameters:

 * `self` : The floating-point number to be converted.

 Returns an integer representation of the float value. Specifically:
 * `0` for `@float.not_a_number` (NaN),
 * `@int.max_value` (2147483647) for values greater than `@int.max_value`,
 * `@int.min_value` (-2147483648) for values less than `@int.min_value`.
 * truncated (towards zero) integer value for other cases.

 Examples:

 ```moonbit
 test "Float::to_int/normal" {
   inspect!((1.5 : Float).to_int(), content="1")
   inspect!((-1.5 : Float).to_int(), content="-1")
   inspect!(@float.not_a_number.to_int(), content="0")
   inspect!(@float.infinity.to_int(), content="2147483647")
   inspect!(@float.neg_infinity.to_int(), content="-2147483648")
 }
 ```

## to\_le\_bytes

```moonbit
:::source,moonbitlang/core/float/float.mbt,275:::fn to_le_bytes(self : Float) -> Bytes
```

 Converts a floating-point number to its binary representation in
little-endian byte order.

 Parameters:

 * `float` : The floating-point number to be converted.

 Returns a sequence of bytes representing the float value in little-endian
order (least significant byte first).

 Example:

 ```moonbit
 test "to_le_bytes" {
   let f : Float = 1.0
   let bytes = f.to_le_bytes()
   inspect!(bytes.length(), content="4")
 }
 ```

## trunc

```moonbit
:::source,moonbitlang/core/float/round_wasm.mbt,38:::fn trunc(self : Float) -> Float
```

 Returns the nearest integer value not greater in magnitude than the given
floating-point number.

 Removes the fractional part of the floating-point number, effectively
truncating towards zero. For example, `1.9` becomes `1.0`, and `-1.9` becomes
`-1.0`.

 Parameters:

 * `self` : The floating-point number to truncate.

 Returns the truncated floating-point number.

 Example:

 ```moonbit
 test "Float::trunc" {
   inspect!((1.9 : Float).trunc(), content="1")
   inspect!((-1.9 : Float).trunc(), content="-1")
   inspect!((0.1 : Float).trunc(), content="0")
 }
 ```

## Float


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/float/float.mbt,163:::impl <a href="moonbitlang/core/builtin#Default">Default</a> for Float
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/float/float.mbt,163:::fn default() -> Float
    ```
    > 
    >  Returns a default value for the `Float` type, which is `0.0`.
    > 
    >  Returns a `Float` value initialized to zero.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Float::default" {
    >    inspect!(Float::default(), content="0")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/float/float.mbt,203:::impl <a href="moonbitlang/core/builtin#Hash">Hash</a> for Float
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/float/float.mbt,203:::fn hash(self : Float) -> Int
    ```
    > 
    >  Computes a hash value for a floating-point number by first converting it to
    > its integer representation and then applying the standard integer hashing
    > function.
    > 
    >  Parameters:
    > 
    >  * `value` : The floating-point number to be hashed.
    > 
    >  Returns an integer hash value for the given floating-point number.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Float::hash" {
    >    let f : Float = 3.14
    >    let h = Hash::hash(f)
    >    inspect!(h != 0, content="true")
    >  }
    >  ```
  * ```moonbit
    :::source,moonbitlang/core/float/float.mbt,225:::fn hash_combine(self : Float, hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
    >  Combines the hash value of a floating-point number with an existing hasher.
    > 
    >  Parameters:
    > 
    >  * `self` : The floating-point number to be hashed.
    >  * `hasher` : The hasher object to combine the hash value with.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Float::hash_combine" {
    >    let x : Float = 3.14
    >    let y : Float = 3.14
    >    // Same values should produce same hash combinations
    >    inspect!(Hash::hash(x) == Hash::hash(y), content="true")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/float/mod.mbt,33:::impl <a href="moonbitlang/core/builtin#Mod">Mod</a> for Float
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/float/mod.mbt,33:::fn op_mod(self : Float, other : Float) -> Float
    ```
    > 
    >  Calculates the modulo operation between two floating-point numbers.
    > 
    >  Parameters:
    > 
    >  * `self` : The dividend floating-point number.
    >  * `other` : The divisor floating-point number.
    > 
    >  Returns the remainder of the division of `self` by `other`.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "op_mod" {
    >    inspect!((5.7 : Float).op_mod(2.0), content="1.6999998092651367")
    >    inspect!((-5.7 : Float).op_mod(2.0), content="-1.6999998092651367")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/float/float.mbt,147:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for Float
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/float/float.mbt,147:::fn output(self : Float, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
    >  Converts a floating-point number to its string representation.
    > 
    >  Parameters:
    > 
    >  * `self` : The floating-point number to be converted.
    >  * `logger` : The logger to write the string representation to.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Float::output" {
    >    let f : Float = 3.14
    >    let s = f.to_double().to_string()
    >    inspect!(s, content="3.140000104904175")
    >  }
    >  ```

#### mooncakes-io-method-mark-Methods
- #### abs
  ```moonbit
  :::source,moonbitlang/core/float/float.mbt,128:::fn <a href="moonbitlang/core/float#Float">Float</a>::abs(self : Float) -> Float
  ```
  > 
  >  Returns the absolute value of a floating-point number.
  > 
  >  Parameters:
  > 
  >  * `self` : A floating-point number.
  > 
  >  Returns the absolute value of the input number. For positive numbers and
  > zero, returns the number unchanged. For negative numbers, returns the
  > negation of the number. For NaN, returns NaN.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Float::abs" {
  >    inspect!((1.5 : Float).abs(), content="1.5")
  >    inspect!((-1.5 : Float).abs(), content="1.5")
  >    inspect!((0.0 : Float).abs(), content="0")
  >    inspect!((-0.0 : Float).abs(), content="0")
  >    inspect!(@float.not_a_number.abs().is_nan(), content="true")
  >  }
  >  ```
- #### acos
  ```moonbit
  :::source,moonbitlang/core/float/trig.mbt,142:::fn <a href="moonbitlang/core/float#Float">Float</a>::acos(self : Float) -> Float
  ```
  > 
  >  Calculates the arccosine of a floating-point number.
  > 
  >  Parameters:
  > 
  >  * `x` : The number for which to calculate the arccosine.
  > 
  >  Returns the arccosine of the number `x`.
  > 
  >  * Returns NaN if the input is NaN.
  >  * Returns NaN if the input is less than -1 or greater than 1.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "acos" {
  >    inspect!((0.0 : Float).acos(), content="1.5707963705062866")
  >    inspect!((1.0 : Float).acos(), content="0")
  >    inspect!((-1.0 : Float).acos(), content="3.1415927410125732")
  >    inspect!(@float.not_a_number.acos(), content="NaN")
  >    inspect!(@float.infinity.acos(), content="NaN")
  >    inspect!(@float.neg_infinity.acos(), content="NaN")
  >  }
  >  ```
- #### acosh
  ```moonbit
  :::source,moonbitlang/core/float/hyperbolic.mbt,177:::fn <a href="moonbitlang/core/float#Float">Float</a>::acosh(self : Float) -> Float
  ```
  > 
  >  Calculates the inverse hyperbolic cosine of a number.
  > 
  >  Parameters:
  > 
  >  * `x` : The number for which to calculate the inverse hyperbolic cosine.
  > 
  >  Returns the inverse hyperbolic cosine of `x`.
  > 
  >  Special cases:
  > 
  >  * Returns `NaN` if `x` is less than `1`.
  >  * Returns `NaN` if `x` is `NaN`.
  >  * Returns `0` if `x` is `1`.
  >  * Returns `infinity` if `x` is `infinity` (Positive infinity).
  > 
  >  Example
  > 
  >  ```moonbit
  >  test "acosh" {
  >    inspect!((1.0 : Float).acosh(), content="0")
  >    inspect!((2.0 : Float).acosh(), content="1.316957950592041")
  >    inspect!((1000.0 : Float).acosh(), content="7.600902080535889")
  >    inspect!((-1.0 : Float).acosh(), content="NaN")
  >    inspect!((-2.0 : Float).acosh(), content="NaN")
  >    inspect!(@float.not_a_number.acosh(), content="NaN")
  >    inspect!(@float.infinity.acosh(), content="Infinity")
  >    inspect!(@float.neg_infinity.acosh(), content="NaN")
  >  }
  >  ```
- #### asin
  ```moonbit
  :::source,moonbitlang/core/float/trig.mbt,114:::fn <a href="moonbitlang/core/float#Float">Float</a>::asin(self : Float) -> Float
  ```
  > 
  >  Calculates the arcsine of a floating-point number.
  > 
  >  Parameters:
  > 
  >  * `x` : The number for which to calculate the arcsine.
  > 
  >  Returns the arcsine of the number `x`.
  > 
  >  * Returns NaN if the input is NaN.
  >  * Returns NaN if the input is less than -1 or greater than 1.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "asin" {
  >    inspect!((0.0 : Float).asin(), content="0")
  >    inspect!((1.0 : Float).asin(), content="1.5707963705062866")
  >    inspect!((-1.0 : Float).asin(), content="-1.5707963705062866")
  >    inspect!(@float.not_a_number.asin(), content="NaN")
  >    inspect!(@float.infinity.asin(), content="NaN")
  >    inspect!(@float.neg_infinity.asin(), content="NaN")
  >  }
  >  ```
- #### asinh
  ```moonbit
  :::source,moonbitlang/core/float/hyperbolic.mbt,143:::fn <a href="moonbitlang/core/float#Float">Float</a>::asinh(self : Float) -> Float
  ```
  > 
  >  Calculates the inverse hyperbolic sine of a number.
  > 
  >  Parameters:
  > 
  >  * `x` : The number for which to calculate the inverse hyperbolic sine.
  > 
  >  Returns the inverse hyperbolic sine of `x`.
  > 
  >  Special cases:
  > 
  >  * Returns `NaN` if `x` is `NaN`
  >  * Returns `infinity` if `x` is `infinity`
  > 
  >  Example
  > 
  >  ```moonbit
  >  test "asinh" {
  >    inspect!((0.0 : Float).asinh(), content="0")
  >    inspect!((-0.0 : Float).asinh(), content="0")
  >    inspect!((1.0 : Float).asinh(), content="0.8813735842704773")
  >    inspect!((2.0 : Float).asinh(), content="1.4436354637145996")
  >    inspect!((1000.0 : Float).asinh(), content="7.600902557373047")
  >    inspect!(@float.not_a_number.asinh(), content="NaN")
  >    inspect!(@float.infinity.asinh(), content="Infinity")
  >    inspect!(@float.neg_infinity.asinh(), content="-Infinity")
  >  }
  >  ```
- #### atan
  ```moonbit
  :::source,moonbitlang/core/float/trig.mbt,169:::fn <a href="moonbitlang/core/float#Float">Float</a>::atan(self : Float) -> Float
  ```
  > 
  >  Calculates the arctangent of a floating-point number.
  > 
  >  Parameters:
  > 
  >  * `x` : The number for which to calculate the arctangent.
  > 
  >  Returns the arctangent of the number `x`.
  > 
  >  Example:
  > 
  >  * Returns NaN if the input is NaN.
  > 
  >  ```moonbit
  >  test "atan" {
  >    inspect!((0.0 : Float).atan(), content="0")
  >    inspect!((1.0 : Float).atan(), content="0.7853981852531433")
  >    inspect!((-1.0 : Float).atan(), content="-0.7853981852531433")
  >    inspect!(@float.not_a_number.atan(), content="NaN")
  >    inspect!(@float.infinity.atan(), content="1.5707963705062866")
  >    inspect!(@float.neg_infinity.atan(), content="-1.5707963705062866")
  >  }
  >  ```
- #### atan2
  ```moonbit
  :::source,moonbitlang/core/float/trig.mbt,204:::fn <a href="moonbitlang/core/float#Float">Float</a>::atan2(self : Float, other : Float) -> Float
  ```
  > 
  >  Calculates the arctangent of the quotient of two floating-point numbers.
  > 
  >  Parameters:
  > 
  >  * `self` : The numerator of the quotient.
  >  * `x` : The denominator of the quotient.
  > 
  >  Returns the arctangent of the quotient `self / x`.
  > 
  >  * Returns NaN if self or x is NaN.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "atan2" {
  >    inspect!((0.0 : Float).atan2(-1.0), content="3.1415927410125732")
  >    inspect!((1.0 : Float).atan2(0.0), content="1.5707963705062866")
  >    inspect!((1.0 : Float).atan2(1.0), content="0.7853981852531433")
  >    inspect!(@float.not_a_number.atan2(1.0), content="NaN")
  >    inspect!((1.0 : Float).atan2(not_a_number), content="NaN")
  >    inspect!(@float.infinity.atan2(1.0), content="1.5707963705062866")
  >    inspect!((1.0 : Float).atan2(infinity), content="0")
  >    inspect!(@float.neg_infinity.atan2(1.0), content="-1.5707963705062866")
  >    inspect!((1.0 : Float).atan2(@float.neg_infinity), content="3.1415927410125732")
  >    inspect!(@float.infinity.atan2(@float.infinity), content="0.7853981852531433")
  >    inspect!(@float.neg_infinity.atan2(@float.neg_infinity), content="-2.356194496154785")
  >    inspect!(@float.infinity.atan2(@float.neg_infinity), content="2.356194496154785")
  >    inspect!(@float.neg_infinity.atan2(@float.infinity), content="-0.7853981852531433")
  >  }
  >  ```
- #### atanh
  ```moonbit
  :::source,moonbitlang/core/float/hyperbolic.mbt,212:::fn <a href="moonbitlang/core/float#Float">Float</a>::atanh(self : Float) -> Float
  ```
  > 
  >  Calculates the inverse hyperbolic tangent of a number.
  > 
  >  Parameters:
  > 
  >  * `x` : The number for which to calculate the inverse hyperbolic tangent.
  > 
  >  Returns the inverse hyperbolic tangent of `x`.
  > 
  >  Special cases:
  > 
  >  * Returns `NaN` if `x` is less than `-1` or greater than `1`.
  >  * Returns `infinity` if `x` is `1`.
  >  * Returns `-infinity` if `x` is `-1`.
  > 
  >  Example
  > 
  >  ```moonbit
  >  test "atanh" {
  >    inspect!((0.0 : Float).atanh(), content="0")
  >    inspect!((-0.0 : Float).atanh(), content="0")
  >    inspect!((0.5 : Float).atanh(), content="0.5493061542510986")
  >    inspect!((-0.5 : Float).atanh(), content="-0.5493061542510986")
  >    inspect!((1.0 : Float).atanh(), content="Infinity")
  >    inspect!((-1.0 : Float).atanh(), content="-Infinity")
  >    inspect!((1.5 : Float).atanh(), content="NaN")
  >    inspect!(@float.not_a_number.atanh(), content="NaN")
  >    inspect!(@float.infinity.atanh(), content="NaN")
  >    inspect!(@float.neg_infinity.atanh(), content="NaN")
  >  }
  >  ```
- #### cbrt
  ```moonbit
  :::source,moonbitlang/core/float/cbrt.mbt,44:::fn <a href="moonbitlang/core/float#Float">Float</a>::cbrt(self : Float) -> Float
  ```
  > 
  >  Calculates the cube root of a number.
  > 
  >  Parameters:
  > 
  >  * `x` : The number for which to calculate the cube root.
  > 
  >  Returns the cube root of `x`.
  > 
  >  Special Cases:
  > 
  >  * Return `NaN` if `x` is `NaN`.
  >  * Return `±0` if `x` is `±0`.
  >  * Return `Infinity` if `x` is `Infinity`.
  >  * Return `-Infinity` if `x` is `-Infinity`.
  > 
  >  Example
  > 
  >  ```moonbit
  >  test "cbrt" {
  >   inspect!((0 : Float).cbrt(), content="0")
  >   inspect!((1 : Float).cbrt(), content="1")
  >   inspect!((8 : Float).cbrt(), content="2")
  >   inspect!((-8 : Float).cbrt(), content="-2")
  >   inspect!(@float.not_a_number.cbrt(), content="NaN")
  >   inspect!(@float.infinity.cbrt(), content="Infinity")
  >   inspect!(@float.neg_infinity.cbrt(), content="-Infinity")
  >  }
  >  ```
- #### ceil
  ```moonbit
  :::source,moonbitlang/core/float/round_wasm.mbt,59:::fn <a href="moonbitlang/core/float#Float">Float</a>::ceil(self : Float) -> Float
  ```
  > 
  >  Returns the smallest integer greater than or equal to the given
  > floating-point number.
  > 
  >  Parameters:
  > 
  >  * `self` : The floating-point number to round up.
  > 
  >  Returns the ceiling value of the input as a `Float`.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "ceil" {
  >    inspect!((1.4 : Float).ceil(), content="2")
  >    inspect!((1.0 : Float).ceil(), content="1")
  >    inspect!((-1.4 : Float).ceil(), content="-1")
  >  }
  >  ```
- #### cos
  ```moonbit
  :::source,moonbitlang/core/float/trig.mbt,61:::fn <a href="moonbitlang/core/float#Float">Float</a>::cos(self : Float) -> Float
  ```
  > 
  >  Calculates the cosine of a floating-point number in radians.
  > 
  >  Parameters:
  > 
  >  * `x` : The angle in radians for which to calculate the cosine.
  > 
  >  Returns the cosine of the angle `x`.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "cos" {
  >    inspect!((0.0 : Float).cos(), content="1")
  >    inspect!((2.0 : Float).cos(), content="-0.416146844625473")
  >    inspect!((-5.0 : Float).cos(), content="0.28366219997406006")
  >    inspect!(@float.not_a_number.cos(), content="NaN")
  >    inspect!(@float.infinity.cos(), content="NaN")
  >    inspect!(@float.neg_infinity.cos(), content="NaN")
  >  }
  >  ```
- #### cosh
  ```moonbit
  :::source,moonbitlang/core/float/hyperbolic.mbt,77:::fn <a href="moonbitlang/core/float#Float">Float</a>::cosh(self : Float) -> Float
  ```
  > 
  >  Calculates the hyperbolic cosine of a number.
  > 
  >  Parameters:
  > 
  >  * `x` : The number for which to calculate the hyperbolic cosine.
  > 
  >  Returns the hyperbolic cosine of `x`.
  > 
  >  Special cases:
  > 
  >  * Returns `infinity` if `x` is `infinity`
  >  * Returns `NaN` if `x` is `NaN`
  > 
  >  Example
  > 
  >  ```moonbit
  >  test "cosh" {
  >    inspect!((0.0 : Float).cosh(), content="1")
  >    inspect!((-0.0).cosh(), content="1")
  >    inspect!((1.0 : Float).cosh(), content="1.5430806875228882")
  >    inspect!((2.0: Float).cosh(), content="3.762195587158203")
  >    inspect!((1000.0: Float).cosh(), content="Infinity")
  >    inspect!((-1000.0 : Float).cosh(), content="Infinity")
  >    inspect!(@float.not_a_number.cosh(), content="NaN")
  >    inspect!(@float.infinity.cosh(), content="Infinity")
  >    inspect!(@float.neg_infinity.cosh(), content="Infinity")
  >  }
  >  ```
- #### exp
  ```moonbit
  :::source,moonbitlang/core/float/exp.mbt,91:::fn <a href="moonbitlang/core/float#Float">Float</a>::exp(self : Float) -> Float
  ```
  > 
  >  Calculates the exponential function e^x for a given floating-point number.
  > 
  >  Parameters:
  > 
  >  * `x` : A floating-point number for which to calculate e^x.
  > 
  >  Returns the value of e raised to the power of x (e^x).
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "exp" {
  >    inspect!((0.0 : Float).exp(), content="1")
  >    inspect!((1.0 : Float).exp(), content="2.7182817459106445")
  >    inspect!(@float.neg_infinity.exp(), content="0")
  >  }
  >  ```
- #### expm1
  ```moonbit
  :::source,moonbitlang/core/float/exp.mbt,152:::fn <a href="moonbitlang/core/float#Float">Float</a>::expm1(self : Float) -> Float
  ```
  > 
  >  Calculates exp(x) - 1 accurately even when x is close to zero.
  > 
  >  Parameters:
  > 
  >  * `x` : The exponent.
  > 
  >  Returns e raised to the power of `x`, minus 1.
  > 
  >  Special Cases:
  > 
  >  * Returns NaN if `x` is NaN.
  >  * Returns -1 if `x` is negative infinity.
  >  * Returns `Infinity` if `x` is positive infinity.
  > 
  >  Example
  > 
  >  ```moonbit
  >  test "expm1" {
  >   inspect!((0 : Float).expm1(), content="0")
  >   inspect!((1 : Float).expm1(), content="1.718281865119934")
  >   inspect!((-1 : Float).expm1(), content="-0.6321205496788025")
  >   inspect!(@float.not_a_number.expm1(), content="NaN")
  >   inspect!(@float.infinity.expm1(), content="Infinity")
  >   inspect!(@float.neg_infinity.expm1(), content="-1")
  >  }
  >  ```
- #### floor
  ```moonbit
  :::source,moonbitlang/core/float/round_wasm.mbt,80:::fn <a href="moonbitlang/core/float#Float">Float</a>::floor(self : Float) -> Float
  ```
  > 
  >  Returns the largest integer less than or equal to the given floating-point
  > number.
  > 
  >  Parameters:
  > 
  >  * `number` : The floating-point number to be rounded down.
  > 
  >  Returns a floating-point number representing the largest integer less than or
  > equal to the input.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "floor" {
  >    inspect!((3.7 : Float).floor(), content="3")
  >    inspect!((-3.7 : Float).floor(), content="-4")
  >  }
  >  ```
- #### hypot
  ```moonbit
  :::source,moonbitlang/core/float/hypot.mbt,41:::fn <a href="moonbitlang/core/float#Float">Float</a>::hypot(self : Float, y : Float) -> Float
  ```
  > 
  >  Calculates the the square root of the sum of the squares of its arguments.
  > 
  >  Parameters:
  > 
  >  * `self` : The number to be used as the first argument.
  >  * `y` : The number to be used as the second argument.
  > 
  >  Returns the hypotenuse of a right-angled triangle whose legs are `self` and `y`.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "hypot" {
  >    inspect!((3.0 : Float).hypot(4.0), content="5")
  >    inspect!((5.0 : Float).hypot(12.0), content="13")
  >    inspect!((8.0 : Float).hypot(15.0), content="17")
  >    inspect!((7.0 : Float).hypot(24.0), content="25")
  >    inspect!(@float.not_a_number.hypot(1.0), content="NaN")
  >    inspect!((1.0 : Float).hypot(@float.not_a_number), content="NaN")
  >    inspect!(@float.infinity.hypot(1.0), content="Infinity")
  >    inspect!((1.0 : Float).hypot(@float.infinity), content="Infinity")
  >    inspect!(@float.neg_infinity.hypot(1.0), content="Infinity")
  >    inspect!((1.0 : Float).hypot(@float.neg_infinity), content="Infinity")
  >  }
  >  ```
- #### is\_inf
  ```moonbit
  :::source,moonbitlang/core/float/float.mbt,298:::fn <a href="moonbitlang/core/float#Float">Float</a>::is_inf(self : Float) -> Bool
  ```
  > 
  >  Determines if the floating-point number is positive or negative infinity.
  > 
  >  Parameters:
  > 
  >  * `self` : The floating-point number to be checked.
  > 
  >  Returns a boolean value indicating whether the number is positive or negative
  > infinity.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Float::is_inf" {
  >    inspect!(@float.infinity.is_inf(), content="true")
  >    inspect!(@float.neg_infinity.is_inf(), content="true")
  >    inspect!((1.0 : Float).is_inf(), content="false")
  >  }
  >  ```
- #### is\_nan
  ```moonbit
  :::source,moonbitlang/core/float/float.mbt,364:::fn <a href="moonbitlang/core/float#Float">Float</a>::is_nan(self : Float) -> Bool
  ```
  > 
  >  Determines if the floating-point number is NaN (Not a Number).
  > 
  >  Parameters:
  > 
  >  * `self` : The floating-point number to be checked.
  > 
  >  Returns a boolean value indicating whether the number is NaN.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Float::is_nan" {
  >    inspect!(@float.not_a_number.is_nan(), content="true")
  >    inspect!((1.0 : Float).is_nan(), content="false")
  >    inspect!(@float.infinity.is_nan(), content="false")
  >  }
  >  ```
- #### is\_neg\_inf
  ```moonbit
  :::source,moonbitlang/core/float/float.mbt,342:::fn <a href="moonbitlang/core/float#Float">Float</a>::is_neg_inf(self : Float) -> Bool
  ```
  > 
  >  Determines if the floating-point number is negative infinity.
  > 
  >  Parameters:
  > 
  >  * `self` : The floating-point number to be checked.
  > 
  >  Returns a boolean value indicating whether the number is negative infinity.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Float::is_neg_inf" {
  >    inspect!(@float.neg_infinity.is_neg_inf(), content="true")
  >    inspect!((1.0 : Float).is_neg_inf(), content="false")
  >    inspect!(@float.infinity.is_neg_inf(), content="false")
  >  }
  >  ```
- #### is\_pos\_inf
  ```moonbit
  :::source,moonbitlang/core/float/float.mbt,320:::fn <a href="moonbitlang/core/float#Float">Float</a>::is_pos_inf(self : Float) -> Bool
  ```
  > 
  >  Determines if the floating-point number is positive infinity.
  > 
  >  Parameters:
  > 
  >  * `self` : The floating-point number to be checked.
  > 
  >  Returns a boolean value indicating whether the number is positive infinity.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Float::is_pos_inf" {
  >    inspect!(@float.infinity.is_pos_inf(), content="true")
  >    inspect!((1.0 : Float).is_pos_inf(), content="false")
  >    inspect!(@float.neg_infinity.is_pos_inf(), content="false")
  >  }
  >  ```
- #### ln
  ```moonbit
  :::source,moonbitlang/core/float/log.mbt,75:::fn <a href="moonbitlang/core/float#Float">Float</a>::ln(self : Float) -> Float
  ```
  > 
  >  Calculates the natural logarithm of a floating-point number.
  > 
  >  Parameters:
  > 
  >  * `value` : The floating-point number to calculate the natural logarithm of.
  > 
  >  Returns the natural logarithm of the input value. Special cases are handled
  > as follows:
  > 
  >  * Returns `0.0` when the input is `1.0`
  >  * Returns `neg_infinity` when the input is `0.0`
  >  * Returns `not_a_number` when the input is negative
  >  * Returns `infinity` when the input is `infinity`
  >  * Returns `not_a_number` when the input is `not_a_number`
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "ln" {
  >    inspect!((1.0 : Float).ln(), content="0")
  >    inspect!((2.718281828459045 : Float).ln(), content="0.9999999403953552")
  >    inspect!((0.0 : Float).ln(), content="-Infinity")
  >  }
  >  ```
- #### ln\_1p
  ```moonbit
  :::source,moonbitlang/core/float/log.mbt,137:::fn <a href="moonbitlang/core/float#Float">Float</a>::ln_1p(self : Float) -> Float
  ```
  > 
  >  Calculates ln(1 + x) accurately even when x is close to zero.
  > 
  >  Parameters:
  > 
  >  * `x` : The number to which 1 is added before calculating the logarithm.
  > 
  >  Returns the natural logarithm of 1 + `x`.
  > 
  >  Special Cases:
  > 
  >  * Returns `NaN` if `x` is `NaN` or less than -1.
  >  * Returns `-Infinity` if `x` is -1.
  >  * Returns `+Infinity` if `x` is `+Infinity`.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "ln_1p" {
  >    inspect!((0 : Float).ln_1p(), content="0")
  >    inspect!((1 : Float).ln_1p(), content="0.6931471824645996")
  >    inspect!((-1 : Float).ln_1p(), content="-Infinity")
  >    inspect!((-2 : Float).ln_1p(), content="NaN")
  >    inspect!(@float.not_a_number.ln_1p(), content="NaN")
  >    inspect!(@float.infinity.ln_1p(), content="Infinity")
  >    inspect!(@float.neg_infinity.ln_1p(), content="NaN")
  >  }
  >  ```
- #### pow
  ```moonbit
  :::source,moonbitlang/core/float/pow.mbt,35:::fn <a href="moonbitlang/core/float#Float">Float</a>::pow(self : Float, other : Float) -> Float
  ```
  > 
  >  Calculates the power of a floating-point number raised to another
  > floating-point number.
  > 
  >  Parameters:
  > 
  >  * `base` : The base number to be raised to a power.
  >  * `exponent` : The power to which the base number is raised.
  > 
  >  Returns the result of raising `base` to the power of `exponent`.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "pow" {
  >    inspect!((2.0 : Float).pow(3.0), content="8")
  >    inspect!((4.0 : Float).pow(0.5), content="2")
  >    inspect!((1.0 : Float).pow(-1.0), content="1")
  >  }
  >  ```
- #### round
  ```moonbit
  :::source,moonbitlang/core/float/round_wasm.mbt,103:::fn <a href="moonbitlang/core/float#Float">Float</a>::round(self : Float) -> Float
  ```
  > 
  >  Rounds a floating-point number to the nearest integer value. If the
  > fractional part is exactly 0.5, rounds up to the nearest integer (ties to
  > ceiling).
  > 
  >  Parameters:
  > 
  >  * `self` : The floating-point number to be rounded.
  > 
  >  Returns the rounded value as a float.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "round" {
  >    inspect!((1.4 : Float).round(), content="1")
  >    inspect!((1.5 : Float).round(), content="2")
  >    inspect!((1.6 : Float).round(), content="2")
  >    inspect!((-1.5 : Float).round(), content="-1")
  >  }
  >  ```
- #### sin
  ```moonbit
  :::source,moonbitlang/core/float/trig.mbt,36:::fn <a href="moonbitlang/core/float#Float">Float</a>::sin(self : Float) -> Float
  ```
  > 
  >  Calculates the sine of a floating-point number in radians.
  > 
  >  Parameters:
  > 
  >  * `x` : The angle in radians for which to calculate the sine.
  > 
  >  Returns the sine of the angle `x`.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "sin" {
  >    inspect!((0.0 : Float).sin(), content="0")
  >    inspect!((2.0 : Float).sin(), content="0.9092974066734314")
  >    inspect!((-5.0 : Float).sin(), content="0.9589242935180664")
  >    inspect!(@float.not_a_number.sin(), content="NaN")
  >    inspect!(@float.infinity.sin(), content="NaN")
  >    inspect!(@float.neg_infinity.sin(), content="NaN")
  >  }
  >  ```
- #### sinh
  ```moonbit
  :::source,moonbitlang/core/float/hyperbolic.mbt,44:::fn <a href="moonbitlang/core/float#Float">Float</a>::sinh(self : Float) -> Float
  ```
  > 
  >  Calculates the hyperbolic sine of a number.
  > 
  >  Parameters:
  > 
  >  * `x` : The number for which to calculate the hyperbolic sine.
  > 
  >  Returns the hyperbolic sine of `x`.
  > 
  >  Special cases:
  > 
  >  * Returns `infinity` if `x` is `infinity`
  >  * Returns `NaN` if `x` is `NaN`
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "sinh" {
  >    inspect!((0.0 : Float).sinh(), content="0")
  >    inspect!((-0.0 : Float).sinh(), content="0")
  >    inspect!((1.0 : Float).sinh(), content="1.175201177597046")
  >    inspect!((2.0 : Float).sinh(), content="3.6268603801727295")
  >    inspect!((1000.0 : Float).sinh(), content="Infinity")
  >    inspect!((-1000.0 : Float).sinh(), content="-Infinity")
  >    inspect!(@float.not_a_number.sinh(), content="NaN")
  >    inspect!(@float.infinity.sinh(), content="Infinity")
  >    inspect!(@float.neg_infinity.sinh(), content="-Infinity")
  >  }
  >  ```
- #### tan
  ```moonbit
  :::source,moonbitlang/core/float/trig.mbt,86:::fn <a href="moonbitlang/core/float#Float">Float</a>::tan(self : Float) -> Float
  ```
  > 
  >  Calculates the tangent of a floating-point number in radians.
  > 
  >  Parameters:
  > 
  >  * `x` : The angle in radians for which to calculate the tangent.
  > 
  >  Returns the tangent of the angle `x`.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "tan" {
  >    inspect!((0.0 : Float).tan(), content="0")
  >    inspect!((2.0 : Float).tan(), content="-2.185039758682251")
  >    inspect!((-5.0 : Float).tan(), content="3.3805150985717773")
  >    inspect!(@float.not_a_number.tan(), content="NaN")
  >    inspect!(@float.infinity.tan(), content="NaN")
  >    inspect!(@float.neg_infinity.tan(), content="NaN")
  >  }
  >  ```
- #### tanh
  ```moonbit
  :::source,moonbitlang/core/float/hyperbolic.mbt,111:::fn <a href="moonbitlang/core/float#Float">Float</a>::tanh(self : Float) -> Float
  ```
  > 
  >  Calculates the hyperbolic tangent of a number.
  > 
  >  Parameters:
  > 
  >  * `x` : The number for which to calculate the hyperbolic tangent.
  > 
  >  Returns the hyperbolic tangent of `x`.
  > 
  >  Special cases:
  > 
  >  * Returns `NaN` if `x` is `NaN`
  >  * Returns `1` if `x` is `infinity`
  >  * Returns `-1` if `x` is `-infinity`
  > 
  >  Example
  > 
  >  ```moobit
  >  test "tanh" {
  >    inspect!((0.0 : Float).tanh(), content="0")
  >    inspect!((-0.0 : Float).tanh(), content="0")
  >    inspect!((1.0 : Float).tanh(), content="0.7615941559557649")
  >    inspect!((2.0 : Float).tanh(), content="0.9640275800758169")
  >    inspect!((1000.0 : Float).tanh(), content="1")
  >    inspect!((-1000.0 : Float).tanh(), content="-1")
  >    inspect!(@float.not_a_number.tanh(), content="NaN")
  >    inspect!(@float.infinity.tanh(), content="1")
  >    inspect!(@float.neg_infinity.tanh(), content="-1")
  >  }
  >  ```
- #### to\_be\_bytes
  ```moonbit
  :::source,moonbitlang/core/float/float.mbt,251:::fn <a href="moonbitlang/core/float#Float">Float</a>::to_be_bytes(self : Float) -> Bytes
  ```
  > 
  >  Converts a floating-point number to a sequence of bytes in big-endian byte
  > order. In big-endian order, the most significant byte is stored at the lowest
  > memory address.
  > 
  >  Parameters:
  > 
  >  * `float` : The floating-point number to be converted.
  > 
  >  Returns a sequence of 4 bytes representing the floating-point number in IEEE
  > 754 single-precision format with big-endian byte order.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Float::to_be_bytes" {
  >    let x : Float = 1.0
  >    inspect!(x.to_be_bytes(), content=
  >    #|b"\x3f\x80\x00\x00"
  >  )
  >  }
  >  ```
- #### to\_int
  ```moonbit
  :::source,moonbitlang/core/float/to_int_wasm.mbt,40:::fn <a href="moonbitlang/core/float#Float">Float</a>::to_int(self : Float) -> Int
  ```
  > 
  >  Converts a floating-point number to an integer, with proper handling of
  > special cases such as NaN and values outside the range of 32-bit integers.
  > 
  >  Parameters:
  > 
  >  * `self` : The floating-point number to be converted.
  > 
  >  Returns an integer representation of the float value. Specifically:
  >  * `0` for `@float.not_a_number` (NaN),
  >  * `@int.max_value` (2147483647) for values greater than `@int.max_value`,
  >  * `@int.min_value` (-2147483648) for values less than `@int.min_value`.
  >  * truncated (towards zero) integer value for other cases.
  > 
  >  Examples:
  > 
  >  ```moonbit
  >  test "Float::to_int/normal" {
  >    inspect!((1.5 : Float).to_int(), content="1")
  >    inspect!((-1.5 : Float).to_int(), content="-1")
  >    inspect!(@float.not_a_number.to_int(), content="0")
  >    inspect!(@float.infinity.to_int(), content="2147483647")
  >    inspect!(@float.neg_infinity.to_int(), content="-2147483648")
  >  }
  >  ```
- #### to\_le\_bytes
  ```moonbit
  :::source,moonbitlang/core/float/float.mbt,275:::fn <a href="moonbitlang/core/float#Float">Float</a>::to_le_bytes(self : Float) -> Bytes
  ```
  > 
  >  Converts a floating-point number to its binary representation in
  > little-endian byte order.
  > 
  >  Parameters:
  > 
  >  * `float` : The floating-point number to be converted.
  > 
  >  Returns a sequence of bytes representing the float value in little-endian
  > order (least significant byte first).
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "to_le_bytes" {
  >    let f : Float = 1.0
  >    let bytes = f.to_le_bytes()
  >    inspect!(bytes.length(), content="4")
  >  }
  >  ```
- #### trunc
  ```moonbit
  :::source,moonbitlang/core/float/round_wasm.mbt,38:::fn <a href="moonbitlang/core/float#Float">Float</a>::trunc(self : Float) -> Float
  ```
  > 
  >  Returns the nearest integer value not greater in magnitude than the given
  > floating-point number.
  > 
  >  Removes the fractional part of the floating-point number, effectively
  > truncating towards zero. For example, `1.9` becomes `1.0`, and `-1.9` becomes
  > `-1.0`.
  > 
  >  Parameters:
  > 
  >  * `self` : The floating-point number to truncate.
  > 
  >  Returns the truncated floating-point number.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Float::trunc" {
  >    inspect!((1.9 : Float).trunc(), content="1")
  >    inspect!((-1.9 : Float).trunc(), content="-1")
  >    inspect!((0.1 : Float).trunc(), content="0")
  >  }
  >  ```
