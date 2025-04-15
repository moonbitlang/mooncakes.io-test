# Documentation
|Type|description|
|---|---|
|[Double](#Double)||

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
|[exp](#exp)||
|[expm1](#expm1)||
|[floor](#floor)||
|[from\_int](#from_int)||
|[hypot](#hypot)||
|[infinity](#infinity)||
|[is\_close](#is_close)||
|[is\_inf](#is_inf)||
|[is\_nan](#is_nan)||
|[is\_neg\_inf](#is_neg_inf)||
|[is\_pos\_inf](#is_pos_inf)||
|[ln](#ln)||
|[ln\_1p](#ln_1p)||
|[log10](#log10)||
|[log2](#log2)||
|[max\_value](#max_value)||
|[min\_positive](#min_positive)||
|[min\_value](#min_value)||
|[neg\_infinity](#neg_infinity)||
|[not\_a\_number](#not_a_number)||
|[pow](#pow)||
|[round](#round)||
|[signum](#signum)||
|[sin](#sin)||
|[sinh](#sinh)||
|[tan](#tan)||
|[tanh](#tanh)||
|[to\_be\_bytes](#to_be_bytes)||
|[to\_le\_bytes](#to_le_bytes)||
|[to\_string](#to_string)||
|[to\_uint](#to_uint)||
|[trunc](#trunc)||

## abs

```moonbit
:::source,moonbitlang/core/double/double.mbt,81:::fn abs(self : Double) -> Double
```

 Returns the absolute value of a double-precision floating-point number.

 Parameters:

 * `value` : The double-precision floating-point number to compute the
   absolute value of.

 Returns the absolute value of the input number. For any input `x`, the result
is equivalent to `if x < 0.0 { -x } else { x }`.

 Example:

 ```moonbit
 test "abs" {
   inspect!((-2.5).abs(), content="2.5")
   inspect!(3.14.abs(), content="3.14")
   inspect!(0.0.abs(), content="0")
 }
 ```

## acos

```moonbit
:::source,moonbitlang/core/double/trig_nonjs.mbt,898:::fn acos(self : Double) -> Double
```

 Calculates the arccosine of a number.

 Parameters:

 * `x` : The number for which to calculate the arccosine.

 Returns the arccosine of the number `x`.

 * Returns NaN if the input is NaN.
 * Returns NaN if the input is less than -1 or greater than 1.

 Example:

 ```moonbit
 test "acos" {
   inspect!(0.0.acos(), content="1.5707963267948966")
   inspect!(1.0.acos(), content="0")
   inspect!((-1.0).acos(), content="3.141592653589793")
   inspect!(@double.not_a_number.acos(), content="NaN")
   inspect!(@double.infinity.acos(), content="NaN")
   inspect!(@double.neg_infinity.acos(), content="NaN")
 }
 ```

## acosh

```moonbit
:::source,moonbitlang/core/double/hyperbolic_nonjs.mbt,304:::fn acosh(self : Double) -> Double
```

 Calculates the inverse hyperbolic cosine of a number.

 Parameters:

 * `self` : The number for which to calculate the inverse hyperbolic cosine.

 Returns the inverse hyperbolic cosine of `self`.

 Special cases:

 * Returns `NaN` if `self` is less than `1`.
 * Returns `NaN` if `self` is `NaN`.
 * Returns `0` if `self` is `1`.
 * Returns `infinity` if `self` is `infinity` (Positive infinity).

 Example

 ```moonbit
 test "acosh" {
   inspect!(1.0.acosh(), content="0")
   inspect!(2.0.acosh(), content="1.3169578969248166")
   inspect!(1000.0.acosh(), content="7.600902209541989")
   inspect!(@double.not_a_number.acosh(), content="NaN")
   inspect!(@double.infinity.acosh(), content="Infinity")
   inspect!((-1.0).acosh(), content="NaN")
   inspect!((-2.0).acosh(), content="NaN")
   inspect!(@double.neg_infinity.acosh(), content="NaN")
 }
 ```

## asin

```moonbit
:::source,moonbitlang/core/double/trig_nonjs.mbt,816:::fn asin(self : Double) -> Double
```

 Calculates the arcsine of a number. Handles special cases and edge conditions
according to IEEE 754 standards.

 Parameters:

 * `x` : The number for which to calculate the arcsine.

 Returns the arcsine of the number `x`.

 * Returns NaN if the input is NaN.
 * Returns NaN if the input is less than -1 or greater than 1.

 Example:

 ```moonbit
 test "asin" {
   inspect!(0.0.asin(), content="0")
   inspect!(1.0.asin(), content="1.5707963267948966")
   inspect!((-1.0).asin(), content="-1.5707963267948966")
   inspect!(@double.not_a_number.asin(), content="NaN")
   inspect!(@double.infinity.asin(), content="NaN")
   inspect!(@double.neg_infinity.asin(), content="NaN")
 }
 ```

## asinh

```moonbit
:::source,moonbitlang/core/double/hyperbolic_nonjs.mbt,244:::fn asinh(self : Double) -> Double
```

 Calculates the inverse hyperbolic sine of a number.

 Parameters:

 * `self` : The number for which to calculate the inverse hyperbolic sine.

 Returns the inverse hyperbolic sine of `self`.

 Special cases:

 * Returns `NaN` if `self` is `NaN`
 * Returns `infinity` if `self` is `infinity`

 Example

 ```moonbit
 test "asinh" {
   inspect!(0.0.asinh(), content="0")
   inspect!((-0.0).asinh(), content="0")
   inspect!(1.0.asinh(), content="0.881373587019543")
   inspect!(2.0.asinh(), content="1.4436354751788103")
   inspect!(1000.0.asinh(), content="7.600902709541988")
   inspect!((-1000.0).asinh(), content="-7.600902709541988")
   inspect!(@double.not_a_number.asinh(), content="NaN")
   inspect!(@double.infinity.asinh(), content="Infinity")
   inspect!(@double.neg_infinity.asinh(), content="-Infinity")
 }
 ```

## atan

```moonbit
:::source,moonbitlang/core/double/trig_nonjs.mbt,978:::fn atan(self : Double) -> Double
```

 Calculates the arctangent of a number.

 Parameters:

 * `x` : The number for which to calculate the arctangent.

 Returns the arctangent of the number `x`.

 Example:

 * Returns NaN if the input is NaN.

 ```moonbit
 test "atan" {
   inspect!(0.0.atan(), content="0")
   inspect!(1.0.atan(), content="0.7853981633974483")
   inspect!((-1.0).atan(), content="-0.7853981633974483")
   inspect!(@double.not_a_number.atan(), content="NaN")
   inspect!(@double.infinity.atan(), content="1.5707963267948966")
   inspect!(@double.neg_infinity.atan(), content="-1.5707963267948966")
 }
 ```

## atan2

```moonbit
:::source,moonbitlang/core/double/trig_nonjs.mbt,1088:::fn atan2(self : Double, x : Double) -> Double
```

 Calculates the arctangent of the quotient of two numbers.

 Parameters:

 * `self` : The numerator of the quotient.
 * `x` : The denominator of the quotient.

 Returns the arctangent of the quotient `self / x`.

 * Returns NaN if self or x is NaN.

 Example:

 ```moonbit
 test "atan2" {
   inspect!(0.0.atan2(-1.0), content="3.141592653589793")
   inspect!(1.0.atan2(0.0), content="1.5707963267948966")
   inspect!(1.0.atan2(1.0), content="0.7853981633974483")
   inspect!(@double.not_a_number.atan2(1.0), content="NaN")
   inspect!(1.0.atan2(not_a_number), content="NaN")
   inspect!(@double.infinity.atan2(1.0), content="1.5707963267948966")
   inspect!(1.0.atan2(infinity), content="0")
   inspect!(@double.neg_infinity.atan2(1.0), content="-1.5707963267948966")
   inspect!(1.0.atan2(@double.neg_infinity), content="3.141592653589793")
   inspect!(@double.infinity.atan2(@double.infinity), content="0.7853981633974483")
   inspect!(@double.neg_infinity.atan2(@double.neg_infinity), content="-2.356194490192345")
   inspect!(@double.infinity.atan2(@double.neg_infinity), content="2.356194490192345")
   inspect!(@double.neg_infinity.atan2(@double.infinity), content="-0.7853981633974483")
 }
 ```

## atanh

```moonbit
:::source,moonbitlang/core/double/hyperbolic_nonjs.mbt,355:::fn atanh(self : Double) -> Double
```

 Calculates the inverse hyperbolic tangent of a number.

 Parameters:

 * `self` : The number for which to calculate the inverse hyperbolic tangent.

 Returns the inverse hyperbolic tangent of `self`.

 Special cases:

 * Returns `NaN` if `self` is less than `-1` or greater than `1`.
 * Returns `infinity` if `self` is `1`.
 * Returns `-infinity` if `self` is `-1`.

 Example

 ```moonbit
 test "atanh" {
   inspect!(0.0.atanh(), content="0")
   inspect!((-0.0).atanh(), content="0")
   inspect!(0.5.atanh(), content="0.5493061443340548")
   inspect!((-0.5).atanh(), content="-0.5493061443340548")
   inspect!(1.0.atanh(), content="Infinity")
   inspect!((-1.0).atanh(), content="-Infinity")
   inspect!(1.5.atanh(), content="NaN")
   inspect!(@double.not_a_number.atanh(), content="NaN")
   inspect!(@double.infinity.atanh(), content="NaN")
   inspect!(@double.neg_infinity.atanh(), content="NaN")
 }
 ```

## cbrt

```moonbit
:::source,moonbitlang/core/double/cbrt_nonjs.mbt,57:::fn cbrt(self : Double) -> Double
```

 Calculates the cube root of a number.

 Parameters:

 * `self` : The number for which to calculate the cube root.

 Returns the cube root of `self`.

 Special Cases:

 * Return `NaN` if `self` is `NaN`.
 * Return `±0` if `self` is `±0`.
 * Return `Infinity` if `self` is `Infinity`.
 * Return `-Infinity` if `self` is `-Infinity`.

 Example

 ```moonbit
 test "cbrt" {
   inspect!(1.0.cbrt(), content="1")
   inspect!(3.0.cbrt(), content="1.4422495703074083")
   inspect!((-3.0).cbrt(), content="-1.4422495703074083")
   inspect!(10.0.cbrt(), content="2.154434690031884")
   inspect!(1000.0.cbrt(), content="10")
   inspect!(@double.not_a_number.cbrt(), content="NaN")
   inspect!(@double.infinity, content="Infinity")
   inspect!(@double.neg_infinity, content="-Infinity")
 }
 ```

## ceil

```moonbit
:::source,moonbitlang/core/double/round_wasm.mbt,54:::fn ceil(self : Double) -> Double
```

 Returns the smallest integer greater than or equal to the given number.

 Parameters:

 * `self` : The floating point number to find the ceiling of.

 Returns the ceiling value of the input number.

 Example:

 ```moonbit
 test "ceil" {
   inspect!(3.7.ceil(), content="4")
   inspect!((-3.7).ceil(), content="-3")
   inspect!(42.0.ceil(), content="42")
 }
 ```

## cos

```moonbit
:::source,moonbitlang/core/double/trig_nonjs.mbt,734:::fn cos(self : Double) -> Double
```

 Calculates the cosine of a number in radians. Handles special cases and edge
conditions according to IEEE 754 standards.

 Parameters:

 * `x` : The angle in radians for which to calculate the cosine.

 Returns the cosine of the angle `x`.

 Example:

 ```moonbit
 test "cos" {
   inspect!(0.0.cos(), content="1")
   inspect!(2.5.cos(), content="-0.8011436155469337")
   inspect!((-3.141592653589793).cos(), content="-1") // -pi
   inspect!((-5.0).cos(), content="0.28366218546322625")
   inspect!(31415926535897.9323846.cos(), content="0.9999992690101899")
   inspect!(@double.not_a_number.cos(), content="NaN")
   inspect!(@double.infinity.cos(), content="NaN")
   inspect!(@double.neg_infinity.cos(), content="NaN")
 }
 ```

## cosh

```moonbit
:::source,moonbitlang/core/double/hyperbolic_nonjs.mbt,121:::fn cosh(self : Double) -> Double
```

 Calculates the hyperbolic cosine of a number.

 Parameters:

 * `self` : The number for which to calculate the hyperbolic cosine.

 Returns the hyperbolic cosine of `self`.

 Special cases:

 * Returns `infinity` if `self` is `infinity`
 * Returns `NaN` if `self` is `NaN`

 Example

 ```moonbit
 test "cosh" {
   inspect!(0.0.cosh(), content="1")
   inspect!((-0.0).cosh(), content="1")
   inspect!(1.0.cosh(), content="1.5430806348152437")
   inspect!(2.0.cosh(), content="3.7621956910836314")
   inspect!(1000.0.cosh(), content="Infinity")
   inspect!((-1000.0).cosh(), content="Infinity")
   inspect!(@double.not_a_number.cosh(), content="NaN")
   inspect!(@double.infinity.cosh(), content="Infinity")
   inspect!(@double.neg_infinity.cosh(), content="Infinity")
 }
 ```

## exp

```moonbit
:::source,moonbitlang/core/double/exp_nonjs.mbt,54:::fn exp(self : Double) -> Double
```

 Computes `e` raised to the power of a given number.

 Parameters:

 * `self` : The exponent value to compute `e^x`.

 Returns the value of `e^x`, where `e` is Euler's number (approximately
2\.71828).

 Special cases:

 * Returns `x` if `x` is `infinity` (positive infinity)
 * Returns `0` if `x` is negative infinity
 * Returns `NaN` if `x` is `NaN`
 * Returns `1` if `x` is `0`

 Example:

 ```moonbit
 test "exp" {
   inspect!(0.0.exp(), content="1")
   inspect!(1.0.exp(), content="2.718281828459045")
   inspect!((-1.0).exp(), content="0.36787944117144233")
   inspect!(not_a_number.exp().is_nan(), content="true")
 }
 ```

## expm1

```moonbit
:::source,moonbitlang/core/double/exp_nonjs.mbt,192:::fn expm1(self : Double) -> Double
```

 Calculates exp(x) - 1 accurately even when x is close to zero.

 Parameters:

 * `self` : The exponent.

 Returns e raised to the power of `self`, minus 1.

 Special Cases:

 * Returns NaN if `self` is NaN.
 * Returns -1 if `self` is negative infinity.
 * Returns `Infinity` if `self` is positive infinity.

 Example

 ```moonbit
 test "expm1" {
   inspect!(0.0.expm1(), content="0")
   inspect!(1.0.expm1(), content="1.718281828459045")
   inspect!(2.0.expm1(), content="6.38905609893065")
   inspect!((-1.0).expm1(), content="-0.6321205588285577")
   inspect!((-2.0).expm1(), content="-0.8646647167633873")
   inspect!(@double.not_a_number.expm1(), content="NaN")
   inspect!(@double.infinity.expm1(), content="Infinity")
   inspect!(@double.neg_infinity.expm1(), content="-1")
 }
 ```

## floor

```moonbit
:::source,moonbitlang/core/double/round_wasm.mbt,75:::fn floor(self : Double) -> Double
```

 Returns the largest integer less than or equal to the given number.

 Parameters:

 * `number` : A floating-point number to be rounded down.

 Returns a double-precision floating-point number representing the largest
integer less than or equal to the input.

 Example:

 ```moonbit
 test "floor" {
   inspect!(3.7.floor(), content="3")
   inspect!((-3.7).floor(), content="-4")
   inspect!(0.0.floor(), content="0")
 }
 ```

## from\_int

```moonbit
:::source,moonbitlang/core/double/double.mbt,57:::fn from_int(i : Int) -> Double
```

 same as Double::from\_int\`

## hypot

```moonbit
:::source,moonbitlang/core/double/hypot_nonjs.mbt,49:::fn hypot(self : Double, y : Double) -> Double
```

 Calculates the the square root of the sum of the squares of its arguments.

 Parameters:

 * `self` : The number to be used as the first argument.
 * `y` : The number to be used as the second argument.

 Returns the hypotenuse of a right-angled triangle whose legs are `self` and `y`.

 Example:

 ```moonbit
 test "hypot" {
   inspect!(3.0.hypot(4.0), content="5")
   inspect!(5.0.hypot(12.0), content="13")
   inspect!(8.0.hypot(15.0), content="17")
   inspect!(7.0.hypot(24.0), content="25")
   inspect!(@double.not_a_number.hypot(1.0), content="NaN")
   inspect!(1.0.hypot(@double.not_a_number), content="NaN")
   inspect!(@double.infinity.hypot(1.0), content="Infinity")
   inspect!(1.0.hypot(@double.infinity), content="Infinity")
   inspect!(@double.neg_infinity.hypot(1.0), content="Infinity")
   inspect!(1.0.hypot(@double.neg_infinity), content="Infinity")
 }
 ```

## infinity

```moonbit
:::source,moonbitlang/core/double/double.mbt,19:::let infinity : Double
```


## is\_close

```moonbit
:::source,moonbitlang/core/double/double.mbt,379:::fn is_close(self : Double, other : Double, relative_tolerance~ : Double = .., absolute_tolerance~ : Double = ..) -> Bool
```

 Determines whether two floating-point numbers are approximately equal within
specified tolerances.
The implementation follows the algorithm described in PEP 485 for Python's
`math.isclose()`.

 Parameters:

 * `self` : The first floating-point number to compare.
 * `other` : The second floating-point number to compare.
 * `relative_tolerance` : The relative tolerance for the comparison. Must be
   non-negative. Defaults to 1e-9.
 * `absolute_tolerance` : The absolute tolerance for the comparison. Must be
   non-negative. Defaults to 0.0.

 Returns whether the two numbers are considered approximately equal. Returns
`true` if the numbers are exactly equal or if they are within either the
relative or absolute tolerance. Returns `false` if either number is infinite.

 Example:

 ```moonbit
 test "is_close" {
   let x = 1.0
   let y = 1.000000001
   inspect!(x.is_close(y), content="false")
   inspect!(x.is_close(y, relative_tolerance=1.0e-10), content="false")
   inspect!(infinity.is_close(infinity), content="true")
 }
 ```

## is\_inf

```moonbit
:::source,moonbitlang/core/double/double.mbt,198:::fn is_inf(self : Double) -> Bool
```

 Checks whether a double-precision floating-point number represents positive
or negative infinity.

 Parameters:

 * `value` : The double-precision floating-point number to check.

 Returns `true` if the value is either positive or negative infinity, `false`
otherwise.

 Example:

 ```moonbit
 test "is_inf" {
   inspect!(infinity.is_inf(), content="true")
   inspect!(neg_infinity.is_inf(), content="true")
   inspect!(42.0.is_inf(), content="false")
 }
 ```

## is\_nan

```moonbit
:::source,moonbitlang/core/double/double.mbt,173:::fn is_nan(self : Double) -> Bool
```

 Checks whether a double-precision floating-point number represents a "Not a
Number" (NaN) value.

 Parameters:

 * `number` : A double-precision floating-point value to be checked.

 Returns `true` if the number is NaN, `false` otherwise.

 Example:

 ```moonbit
 test "is_nan" {
   inspect!(not_a_number.is_nan(), content="true")
   inspect!(42.0.is_nan(), content="false")
   inspect!((0.0 / 0.0).is_nan(), content="true")
 }
 ```

## is\_neg\_inf

```moonbit
:::source,moonbitlang/core/double/double.mbt,242:::fn is_neg_inf(self : Double) -> Bool
```

 Checks whether a double-precision floating-point number is negative infinity.

 Parameters:

 * `self` : The double-precision floating-point number to check.

 Returns a boolean value indicating whether the number is negative infinity.

 Example:

 ```moonbit
 test "is_neg_inf" {
   inspect!((-1.0 / 0.0).is_neg_inf(), content="true")
   inspect!(42.0.is_neg_inf(), content="false")
   inspect!((1.0 / 0.0).is_neg_inf(), content="false") // positive infinity
 }
 ```

## is\_pos\_inf

```moonbit
:::source,moonbitlang/core/double/double.mbt,220:::fn is_pos_inf(self : Double) -> Bool
```

 Checks whether a double-precision floating-point number is positive infinity.

 Parameters:

 * `value` : The double-precision floating-point number to check.

 Returns `true` if the number is positive infinity, `false` otherwise.

 Example:

 ```moonbit
 test "is_pos_inf" {
   inspect!(infinity.is_pos_inf(), content="true")
   inspect!(neg_infinity.is_pos_inf(), content="false")
   inspect!(42.0.is_pos_inf(), content="false")
 }
 ```

## ln

```moonbit
:::source,moonbitlang/core/double/log_nonjs.mbt,106:::fn ln(self : Double) -> Double
```

 Calculates the natural logarithm of a double-precision floating-point number.

 Parameters:

 * `self`: The input number.

 Returns the natural logarithm of the input number, with the following special
cases:

 * Returns NaN if the input is NaN or negative
 * Returns negative infinity if the input is zero
 * Returns the input if it is positive infinity

 Example:

 ```moonbit
 test "ln" {
   inspect!(2.0.ln(), content="0.6931471805599453")
   inspect!(1.0.ln(), content="0")
   inspect!((-1.0).ln(), content="NaN")
   inspect!(0.0.ln(), content="-Infinity")
 }
 ```

## ln\_1p

```moonbit
:::source,moonbitlang/core/double/log_nonjs.mbt,228:::fn ln_1p(self : Double) -> Double
```

 Calculates ln(1 + x) accurately even when x is close to zero.

 Parameters:

 * `self` : The number to which 1 is added before calculating the logarithm.

 Returns the natural logarithm of 1 + `self`.

 Special Cases:

 * Returns `NaN` if `self` is `NaN` or less than -1.
 * Returns `-Infinity` if `self` is -1.
 * Returns `+Infinity` if `self` is `+Infinity`.

 Example:

 ```moonbit
 test "ln_1p" {
   inspect!(0.0.ln_1p(), content="0")
   inspect!(1.0.ln_1p(), content="0.6931471805599453")
   inspect!(2.0.ln_1p(), content="1.0986122886681096")
   inspect!(@double.not_a_number.ln_1p(), content="NaN")
   inspect!((-1.0).ln_1p(), content="-Infinity")
   inspect!((-2.0).ln_1p(), content="NaN")
   inspect!(@double.infinity.ln_1p(), content="Infinity")
   inspect!(@double.neg_infinity.ln_1p(), content="NaN")
 }
 ```

## log10

```moonbit
:::source,moonbitlang/core/double/log_nonjs.mbt,178:::fn log10(self : Double) -> Double
```

 Calculates the base-10 logarithm of a double-precision floating-point number.

 Parameters:

 * `self` : The double-precision floating-point number to calculate the
   logarithm of.

 Returns a double-precision floating-point number representing the base-10
logarithm of the input.

 Example:

 ```moonbit
 test "log10" {
   inspect!(0.1.log10(), content="-1")
   inspect!(1.0.log10(), content="0")
   inspect!(10.0.log10(), content="1")
   inspect!(100.0.log10(), content="2")
   inspect!(15.0.log10(), content="1.1760912590556813")
 }
 ```

## log2

```moonbit
:::source,moonbitlang/core/double/log_nonjs.mbt,148:::fn log2(self : Double) -> Double
```

 Calculates the base-2 logarithm of a double-precision floating-point number.

 Parameters:

 * `x` : A double-precision floating-point number.

 Returns the base-2 logarithm of the input number.

 Example:

 ```moonbit
 test "log2" {
   inspect!(2.0.log2(), content="1")
   inspect!(0.5.log2(), content="-1")
   inspect!(3.0.log2(), content="1.584962500721156")
 }
 ```

## max\_value

```moonbit
:::source,moonbitlang/core/double/double.mbt,25:::let max_value : Double
```


## min\_positive

```moonbit
:::source,moonbitlang/core/double/double.mbt,31:::let min_positive : Double
```


## min\_value

```moonbit
:::source,moonbitlang/core/double/double.mbt,28:::let min_value : Double
```


## neg\_infinity

```moonbit
:::source,moonbitlang/core/double/double.mbt,22:::let neg_infinity : Double
```


## not\_a\_number

```moonbit
:::source,moonbitlang/core/double/double.mbt,16:::let not_a_number : Double
```


## pow

```moonbit
:::source,moonbitlang/core/double/pow_nonjs.mbt,135:::fn pow(self : Double, other : Double) -> Double
```

 Calculates the power of a number by raising the base to the specified
exponent. Handles special cases and edge conditions according to IEEE 754
standards.

 Parameters:

 * `base` : The base number to be raised to a power.
 * `exponent` : The power to raise the base number to.

 Returns the result of raising `base` to the power of `exponent`.

 Example:

 ```moonbit
 test "pow" {
   let x = 2.0
   inspect!(x.pow(3.0), content="8")
   inspect!(x.pow(0.5), content="1.4142135623730951")
   inspect!(x.pow(0.0), content="1")
   inspect!((-1.0).pow(2.0), content="1")
   inspect!(0.0.pow(0.0), content="1")
   inspect!(infinity.pow(-1.0), content="0")
 }
 ```

## round

```moonbit
:::source,moonbitlang/core/double/round_wasm.mbt,98:::fn round(self : Double) -> Double
```

 Rounds a floating-point number to the nearest integer using "round half up"
rule. In this rule, when a number is halfway between two integers (like 3.5),
it is rounded up to the next integer.

 Parameters:

 * `value` : The floating-point number to be rounded.

 Returns the rounded value as a double-precision floating-point number.

 Example:

 ```moonbit
 test "round" {
   inspect!(3.7.round(), content="4")
   inspect!(3.2.round(), content="3")
   inspect!(3.5.round(), content="4")
   inspect!((-3.5).round(), content="-3")
 }
 ```

## signum

```moonbit
:::source,moonbitlang/core/double/double.mbt,88:::fn signum(self : Double) -> Double
```

 Returns the sign of the double.
 - If the double is positive, returns 1.0.
 - If the double is negative, returns -1.0.
 - Otherwise, returns the double itself (0.0, -0.0 and NaN).

## sin

```moonbit
:::source,moonbitlang/core/double/trig_nonjs.mbt,691:::fn sin(self : Double) -> Double
```

 Calculates the sine of a number in radians. Handles special cases and edge
conditions according to IEEE 754 standards.

 Parameters:

 * `x` : The angle in radians for which to calculate the sine.

 Returns the sine of the angle `x`.

 Example:

 ```moonbit
 test "sin" {
   inspect!(0.0.sin(), content="0")
   inspect!(1.570796326794897.sin(), content="1") // pi / 2
   inspect!(2.0.sin(), content="0.9092974268256817")
   inspect!(-5.0.sin(), content="0.9589242746631385")
   inspect!(31415926535897.9323846.sin(), content="0.0012091232715481885")
   inspect!(@double.not_a_number.sin(), content="NaN")
   inspect!(@double.infinity.sin(), content="NaN")
   inspect!(@double.neg_infinity.sin(), content="NaN")
 }
 ```

## sinh

```moonbit
:::source,moonbitlang/core/double/hyperbolic_nonjs.mbt,61:::fn sinh(self : Double) -> Double
```

 Calculates the hyperbolic sine of a number.

 Parameters:

 * `self` : The number for which to calculate the hyperbolic sine.

 Returns the hyperbolic sine of `self`.

 Special cases:

 * Returns `infinity` if `self` is `infinity`
 * Returns `NaN` if `self` is `NaN`

 Example:

 ```moonbit
 test "sinh" {
   inspect!(0.0.sinh(), content="0")
   inspect!((-0.0).sinh(), content="0")
   inspect!(1.0.sinh(), content="1.1752011936438014")
   inspect!(2.0.sinh(), content="3.626860407847019")
   inspect!(1000.0.sinh(), content="Infinity")
   inspect!((-1000.0).sinh(), content="-Infinity")
   inspect!(@double.not_a_number.sinh(), content="NaN")
   inspect!(@double.infinity.sinh(), content="Infinity")
   inspect!(@double.neg_infinity.sinh(), content="-Infinity")
 }
 ```

## tan

```moonbit
:::source,moonbitlang/core/double/trig_nonjs.mbt,777:::fn tan(self : Double) -> Double
```

 Calculates the tangent of a number in radians. Handles special cases and edge
conditions according to IEEE 754 standards.

 Parameters:

 * `x` : The angle in radians for which to calculate the tangent.

 Returns the tangent of the angle `x`.

 Example:

 ```moonbit
 test "tan" {
   inspect!(0.0.tan(), content="0")
   inspect!(0.7853981633974483.tan(), content="0.9999999999999999")
   inspect!(4.0.tan(), content="1.1578212823495777")
   inspect!(5.0.tan(), content="-3.380515006246586")
   inspect!(31415926535897.9323846.tan(), content="0.0012091241554056254")
   inspect!(@double.not_a_number.tan(), content="NaN")
   inspect!(@double.infinity.tan(), content="NaN")
   inspect!(@double.neg_infinity.tan(), content="NaN")
 }
 ```

## tanh

```moonbit
:::source,moonbitlang/core/double/hyperbolic_nonjs.mbt,183:::fn tanh(self : Double) -> Double
```

 Calculates the hyperbolic tangent of a number.

 Parameters:

 * `self` : The number for which to calculate the hyperbolic tangent.

 Returns the hyperbolic tangent of `self`.

 Special cases:

 * Returns `NaN` if `self` is `NaN`
 * Returns `1` if `self` is `infinity`
 * Returns `-1` if `self` is `-infinity`

 Example

 ```moobit
 test "tanh" {
   inspect!(0.0.tanh(), content="0")
   inspect!((-0.0).tanh(), content="0")
   inspect!(1.0.tanh(), content="0.7615941559557649")
   inspect!(2.0.tanh(), content="0.9640275800758169")
   inspect!(1000.0.tanh(), content="1")
   inspect!((-1000.0).tanh(), content="-1")
   inspect!(@double.not_a_number.tanh(), content="NaN")
   inspect!(@double.infinity.tanh(), content="1")
   inspect!(@double.neg_infinity.tanh(), content="-1")
 }
 ```

## to\_be\_bytes

```moonbit
:::source,moonbitlang/core/double/double.mbt,423:::fn to_be_bytes(self : Double) -> Bytes
```

 Converts a double-precision floating-point number to a sequence of bytes in
big-endian byte order (most significant byte first).

 Parameters:

 * `self` : The double-precision floating-point number to be converted.

 Returns a sequence of 8 bytes representing the double-precision
floating-point number in big-endian byte order.

 Example:

 ```moonbit
 test "to_be_bytes" {
   let d = 1.0
   inspect!(d.to_be_bytes(), content=
   #|b"\x3f\xf0\x00\x00\x00\x00\x00\x00"
 )
 }
 ```

## to\_le\_bytes

```moonbit
:::source,moonbitlang/core/double/double.mbt,448:::fn to_le_bytes(self : Double) -> Bytes
```

 Converts a double-precision floating-point number to a sequence of bytes in
little-endian order (least significant byte first).

 Parameters:

 * `self` : A double-precision floating-point number to be converted.

 Returns a sequence of 8 bytes representing the double-precision
floating-point number in little-endian order.

 Example:

 ```moonbit
 test "to_le_bytes" {
   let d = 1.0
   inspect!(d.to_le_bytes(), content=
   #|b"\x00\x00\x00\x00\x00\x00\xf0\x3f"
 )
 }
 ```

## to\_string

```moonbit
:::source,moonbitlang/core/double/double.mbt,340:::fn to_string(self : Double) -> String
```

 Converts a double-precision floating-point number to its string
representation.

 Parameters:

 * `self`: The double-precision floating-point number to be converted.

 Returns a string representation of the double-precision floating-point
number.

 Example:

 ```moonbit
 test "Double::to_string" {
   inspect!(42.0.to_string(), content="42")
   inspect!(3.14159.to_string(), content="3.14159")
   inspect!((-0.0).to_string(), content="0")
   inspect!(not_a_number.to_string(), content="NaN")
 }
 ```


## to\_uint

```moonbit
:::source,moonbitlang/core/double/to_uint_wasm.mbt,44:::fn to_uint(self : Double) -> UInt
```

 Converts a double-precision floating-point number to a 32-bit unsigned
integer. Handles special cases including NaN and numbers outside the valid
`UInt` range.

 Parameters:

 * `self` : The double-precision floating-point number to be converted.

 Returns an 32-bit unsigned integer value according to the following rules:

 * Returns 0 if the input is NaN
 * Returns `@uint.max_value` (4294967295U) if the input is greater than or
   equal to `@uint.max_value`
 * Returns `@uint.min_value` (0U) if the input is less than or equal
   to `@uint.min_value`
 * Otherwise returns the integer part of the input by truncating towards zero

 Example:

 ```moonbit
 test "Double::to_uint/normal" {
   inspect!(42.0.to_uint(), content="42")
   inspect!((-42.5).to_uint(), content="0")
   inspect!((0.0 / 0.0).to_uint(), content="0") // NaN
   inspect!((1.0 / 0.0).to_uint(), content="4294967295") // Infinity
   inspect!((-1.0 / 0.0).to_uint(), content="0") // -Infinity
 }
 ```

## trunc

```moonbit
:::source,moonbitlang/core/double/round_wasm.mbt,34:::fn trunc(self : Double) -> Double
```

 Returns an integer value by discarding the decimal part of the floating-point
number (truncation toward zero).

 Parameters:

 * `self` : The floating-point number to be truncated.

 Returns a floating-point number representing the integer part of the input.

 Example:

 ```moonbit
 test "trunc" {
   inspect!(3.7.trunc(), content="3")
   inspect!((-3.7).trunc(), content="-3")
   inspect!(0.0.trunc(), content="0")
 }
 ```

## Double


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/double/double.mbt,308:::impl <a href="moonbitlang/core/builtin#Hash">Hash</a> for Double
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/double/double.mbt,308:::fn hash(self : Double) -> Int
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/core/double/double.mbt,313:::fn hash_combine(self : Double, hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/double/mod_nonjs.mbt,39:::impl <a href="moonbitlang/core/builtin#Mod">Mod</a> for Double
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/double/mod_nonjs.mbt,39:::fn op_mod(self : Double, other : Double) -> Double
    ```
    > 
    >  Calculates the floating-point remainder when `dividend` is divided by
    > `divisor`. Returns NaN if either operand is NaN, or if `dividend` is
    > infinity, or if `divisor` is zero.
    > 
    >  Parameters:
    > 
    >  * `dividend` : The floating-point number to be divided.
    >  * `divisor` : The floating-point number used to divide the `dividend`.
    > 
    >  Returns the remainder of the division. The result has the same sign as the
    > `dividend` and has an absolute value less than the absolute value of
    > `divisor`.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "op_mod" {
    >    inspect!(5.0.op_mod(3.0), content="2")
    >    inspect!((-5.0).op_mod(3.0), content="-2")
    >    inspect!(5.0.op_mod(not_a_number), content="NaN")
    >    inspect!(infinity.op_mod(3.0), content="NaN")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/double/double.mbt,345:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for Double
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/double/double.mbt,345:::fn output(self : Double, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### abs
  ```moonbit
  :::source,moonbitlang/core/double/double.mbt,81:::fn <a href="moonbitlang/core/double#Double">Double</a>::abs(self : Double) -> Double
  ```
  > 
  >  Returns the absolute value of a double-precision floating-point number.
  > 
  >  Parameters:
  > 
  >  * `value` : The double-precision floating-point number to compute the
  >    absolute value of.
  > 
  >  Returns the absolute value of the input number. For any input `x`, the result
  > is equivalent to `if x < 0.0 { -x } else { x }`.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "abs" {
  >    inspect!((-2.5).abs(), content="2.5")
  >    inspect!(3.14.abs(), content="3.14")
  >    inspect!(0.0.abs(), content="0")
  >  }
  >  ```
- #### acos
  ```moonbit
  :::source,moonbitlang/core/double/trig_nonjs.mbt,898:::fn <a href="moonbitlang/core/double#Double">Double</a>::acos(self : Double) -> Double
  ```
  > 
  >  Calculates the arccosine of a number.
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
  >    inspect!(0.0.acos(), content="1.5707963267948966")
  >    inspect!(1.0.acos(), content="0")
  >    inspect!((-1.0).acos(), content="3.141592653589793")
  >    inspect!(@double.not_a_number.acos(), content="NaN")
  >    inspect!(@double.infinity.acos(), content="NaN")
  >    inspect!(@double.neg_infinity.acos(), content="NaN")
  >  }
  >  ```
- #### acosh
  ```moonbit
  :::source,moonbitlang/core/double/hyperbolic_nonjs.mbt,304:::fn <a href="moonbitlang/core/double#Double">Double</a>::acosh(self : Double) -> Double
  ```
  > 
  >  Calculates the inverse hyperbolic cosine of a number.
  > 
  >  Parameters:
  > 
  >  * `self` : The number for which to calculate the inverse hyperbolic cosine.
  > 
  >  Returns the inverse hyperbolic cosine of `self`.
  > 
  >  Special cases:
  > 
  >  * Returns `NaN` if `self` is less than `1`.
  >  * Returns `NaN` if `self` is `NaN`.
  >  * Returns `0` if `self` is `1`.
  >  * Returns `infinity` if `self` is `infinity` (Positive infinity).
  > 
  >  Example
  > 
  >  ```moonbit
  >  test "acosh" {
  >    inspect!(1.0.acosh(), content="0")
  >    inspect!(2.0.acosh(), content="1.3169578969248166")
  >    inspect!(1000.0.acosh(), content="7.600902209541989")
  >    inspect!(@double.not_a_number.acosh(), content="NaN")
  >    inspect!(@double.infinity.acosh(), content="Infinity")
  >    inspect!((-1.0).acosh(), content="NaN")
  >    inspect!((-2.0).acosh(), content="NaN")
  >    inspect!(@double.neg_infinity.acosh(), content="NaN")
  >  }
  >  ```
- #### asin
  ```moonbit
  :::source,moonbitlang/core/double/trig_nonjs.mbt,816:::fn <a href="moonbitlang/core/double#Double">Double</a>::asin(self : Double) -> Double
  ```
  > 
  >  Calculates the arcsine of a number. Handles special cases and edge conditions
  > according to IEEE 754 standards.
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
  >    inspect!(0.0.asin(), content="0")
  >    inspect!(1.0.asin(), content="1.5707963267948966")
  >    inspect!((-1.0).asin(), content="-1.5707963267948966")
  >    inspect!(@double.not_a_number.asin(), content="NaN")
  >    inspect!(@double.infinity.asin(), content="NaN")
  >    inspect!(@double.neg_infinity.asin(), content="NaN")
  >  }
  >  ```
- #### asinh
  ```moonbit
  :::source,moonbitlang/core/double/hyperbolic_nonjs.mbt,244:::fn <a href="moonbitlang/core/double#Double">Double</a>::asinh(self : Double) -> Double
  ```
  > 
  >  Calculates the inverse hyperbolic sine of a number.
  > 
  >  Parameters:
  > 
  >  * `self` : The number for which to calculate the inverse hyperbolic sine.
  > 
  >  Returns the inverse hyperbolic sine of `self`.
  > 
  >  Special cases:
  > 
  >  * Returns `NaN` if `self` is `NaN`
  >  * Returns `infinity` if `self` is `infinity`
  > 
  >  Example
  > 
  >  ```moonbit
  >  test "asinh" {
  >    inspect!(0.0.asinh(), content="0")
  >    inspect!((-0.0).asinh(), content="0")
  >    inspect!(1.0.asinh(), content="0.881373587019543")
  >    inspect!(2.0.asinh(), content="1.4436354751788103")
  >    inspect!(1000.0.asinh(), content="7.600902709541988")
  >    inspect!((-1000.0).asinh(), content="-7.600902709541988")
  >    inspect!(@double.not_a_number.asinh(), content="NaN")
  >    inspect!(@double.infinity.asinh(), content="Infinity")
  >    inspect!(@double.neg_infinity.asinh(), content="-Infinity")
  >  }
  >  ```
- #### atan
  ```moonbit
  :::source,moonbitlang/core/double/trig_nonjs.mbt,978:::fn <a href="moonbitlang/core/double#Double">Double</a>::atan(self : Double) -> Double
  ```
  > 
  >  Calculates the arctangent of a number.
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
  >    inspect!(0.0.atan(), content="0")
  >    inspect!(1.0.atan(), content="0.7853981633974483")
  >    inspect!((-1.0).atan(), content="-0.7853981633974483")
  >    inspect!(@double.not_a_number.atan(), content="NaN")
  >    inspect!(@double.infinity.atan(), content="1.5707963267948966")
  >    inspect!(@double.neg_infinity.atan(), content="-1.5707963267948966")
  >  }
  >  ```
- #### atan2
  ```moonbit
  :::source,moonbitlang/core/double/trig_nonjs.mbt,1088:::fn <a href="moonbitlang/core/double#Double">Double</a>::atan2(self : Double, x : Double) -> Double
  ```
  > 
  >  Calculates the arctangent of the quotient of two numbers.
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
  >    inspect!(0.0.atan2(-1.0), content="3.141592653589793")
  >    inspect!(1.0.atan2(0.0), content="1.5707963267948966")
  >    inspect!(1.0.atan2(1.0), content="0.7853981633974483")
  >    inspect!(@double.not_a_number.atan2(1.0), content="NaN")
  >    inspect!(1.0.atan2(not_a_number), content="NaN")
  >    inspect!(@double.infinity.atan2(1.0), content="1.5707963267948966")
  >    inspect!(1.0.atan2(infinity), content="0")
  >    inspect!(@double.neg_infinity.atan2(1.0), content="-1.5707963267948966")
  >    inspect!(1.0.atan2(@double.neg_infinity), content="3.141592653589793")
  >    inspect!(@double.infinity.atan2(@double.infinity), content="0.7853981633974483")
  >    inspect!(@double.neg_infinity.atan2(@double.neg_infinity), content="-2.356194490192345")
  >    inspect!(@double.infinity.atan2(@double.neg_infinity), content="2.356194490192345")
  >    inspect!(@double.neg_infinity.atan2(@double.infinity), content="-0.7853981633974483")
  >  }
  >  ```
- #### atanh
  ```moonbit
  :::source,moonbitlang/core/double/hyperbolic_nonjs.mbt,355:::fn <a href="moonbitlang/core/double#Double">Double</a>::atanh(self : Double) -> Double
  ```
  > 
  >  Calculates the inverse hyperbolic tangent of a number.
  > 
  >  Parameters:
  > 
  >  * `self` : The number for which to calculate the inverse hyperbolic tangent.
  > 
  >  Returns the inverse hyperbolic tangent of `self`.
  > 
  >  Special cases:
  > 
  >  * Returns `NaN` if `self` is less than `-1` or greater than `1`.
  >  * Returns `infinity` if `self` is `1`.
  >  * Returns `-infinity` if `self` is `-1`.
  > 
  >  Example
  > 
  >  ```moonbit
  >  test "atanh" {
  >    inspect!(0.0.atanh(), content="0")
  >    inspect!((-0.0).atanh(), content="0")
  >    inspect!(0.5.atanh(), content="0.5493061443340548")
  >    inspect!((-0.5).atanh(), content="-0.5493061443340548")
  >    inspect!(1.0.atanh(), content="Infinity")
  >    inspect!((-1.0).atanh(), content="-Infinity")
  >    inspect!(1.5.atanh(), content="NaN")
  >    inspect!(@double.not_a_number.atanh(), content="NaN")
  >    inspect!(@double.infinity.atanh(), content="NaN")
  >    inspect!(@double.neg_infinity.atanh(), content="NaN")
  >  }
  >  ```
- #### cbrt
  ```moonbit
  :::source,moonbitlang/core/double/cbrt_nonjs.mbt,57:::fn <a href="moonbitlang/core/double#Double">Double</a>::cbrt(self : Double) -> Double
  ```
  > 
  >  Calculates the cube root of a number.
  > 
  >  Parameters:
  > 
  >  * `self` : The number for which to calculate the cube root.
  > 
  >  Returns the cube root of `self`.
  > 
  >  Special Cases:
  > 
  >  * Return `NaN` if `self` is `NaN`.
  >  * Return `±0` if `self` is `±0`.
  >  * Return `Infinity` if `self` is `Infinity`.
  >  * Return `-Infinity` if `self` is `-Infinity`.
  > 
  >  Example
  > 
  >  ```moonbit
  >  test "cbrt" {
  >    inspect!(1.0.cbrt(), content="1")
  >    inspect!(3.0.cbrt(), content="1.4422495703074083")
  >    inspect!((-3.0).cbrt(), content="-1.4422495703074083")
  >    inspect!(10.0.cbrt(), content="2.154434690031884")
  >    inspect!(1000.0.cbrt(), content="10")
  >    inspect!(@double.not_a_number.cbrt(), content="NaN")
  >    inspect!(@double.infinity, content="Infinity")
  >    inspect!(@double.neg_infinity, content="-Infinity")
  >  }
  >  ```
- #### ceil
  ```moonbit
  :::source,moonbitlang/core/double/round_wasm.mbt,54:::fn <a href="moonbitlang/core/double#Double">Double</a>::ceil(self : Double) -> Double
  ```
  > 
  >  Returns the smallest integer greater than or equal to the given number.
  > 
  >  Parameters:
  > 
  >  * `self` : The floating point number to find the ceiling of.
  > 
  >  Returns the ceiling value of the input number.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "ceil" {
  >    inspect!(3.7.ceil(), content="4")
  >    inspect!((-3.7).ceil(), content="-3")
  >    inspect!(42.0.ceil(), content="42")
  >  }
  >  ```
- #### cos
  ```moonbit
  :::source,moonbitlang/core/double/trig_nonjs.mbt,734:::fn <a href="moonbitlang/core/double#Double">Double</a>::cos(self : Double) -> Double
  ```
  > 
  >  Calculates the cosine of a number in radians. Handles special cases and edge
  > conditions according to IEEE 754 standards.
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
  >    inspect!(0.0.cos(), content="1")
  >    inspect!(2.5.cos(), content="-0.8011436155469337")
  >    inspect!((-3.141592653589793).cos(), content="-1") // -pi
  >    inspect!((-5.0).cos(), content="0.28366218546322625")
  >    inspect!(31415926535897.9323846.cos(), content="0.9999992690101899")
  >    inspect!(@double.not_a_number.cos(), content="NaN")
  >    inspect!(@double.infinity.cos(), content="NaN")
  >    inspect!(@double.neg_infinity.cos(), content="NaN")
  >  }
  >  ```
- #### cosh
  ```moonbit
  :::source,moonbitlang/core/double/hyperbolic_nonjs.mbt,121:::fn <a href="moonbitlang/core/double#Double">Double</a>::cosh(self : Double) -> Double
  ```
  > 
  >  Calculates the hyperbolic cosine of a number.
  > 
  >  Parameters:
  > 
  >  * `self` : The number for which to calculate the hyperbolic cosine.
  > 
  >  Returns the hyperbolic cosine of `self`.
  > 
  >  Special cases:
  > 
  >  * Returns `infinity` if `self` is `infinity`
  >  * Returns `NaN` if `self` is `NaN`
  > 
  >  Example
  > 
  >  ```moonbit
  >  test "cosh" {
  >    inspect!(0.0.cosh(), content="1")
  >    inspect!((-0.0).cosh(), content="1")
  >    inspect!(1.0.cosh(), content="1.5430806348152437")
  >    inspect!(2.0.cosh(), content="3.7621956910836314")
  >    inspect!(1000.0.cosh(), content="Infinity")
  >    inspect!((-1000.0).cosh(), content="Infinity")
  >    inspect!(@double.not_a_number.cosh(), content="NaN")
  >    inspect!(@double.infinity.cosh(), content="Infinity")
  >    inspect!(@double.neg_infinity.cosh(), content="Infinity")
  >  }
  >  ```
- #### exp
  ```moonbit
  :::source,moonbitlang/core/double/exp_nonjs.mbt,54:::fn <a href="moonbitlang/core/double#Double">Double</a>::exp(self : Double) -> Double
  ```
  > 
  >  Computes `e` raised to the power of a given number.
  > 
  >  Parameters:
  > 
  >  * `self` : The exponent value to compute `e^x`.
  > 
  >  Returns the value of `e^x`, where `e` is Euler's number (approximately
  > 2\.71828).
  > 
  >  Special cases:
  > 
  >  * Returns `x` if `x` is `infinity` (positive infinity)
  >  * Returns `0` if `x` is negative infinity
  >  * Returns `NaN` if `x` is `NaN`
  >  * Returns `1` if `x` is `0`
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "exp" {
  >    inspect!(0.0.exp(), content="1")
  >    inspect!(1.0.exp(), content="2.718281828459045")
  >    inspect!((-1.0).exp(), content="0.36787944117144233")
  >    inspect!(not_a_number.exp().is_nan(), content="true")
  >  }
  >  ```
- #### expm1
  ```moonbit
  :::source,moonbitlang/core/double/exp_nonjs.mbt,192:::fn <a href="moonbitlang/core/double#Double">Double</a>::expm1(self : Double) -> Double
  ```
  > 
  >  Calculates exp(x) - 1 accurately even when x is close to zero.
  > 
  >  Parameters:
  > 
  >  * `self` : The exponent.
  > 
  >  Returns e raised to the power of `self`, minus 1.
  > 
  >  Special Cases:
  > 
  >  * Returns NaN if `self` is NaN.
  >  * Returns -1 if `self` is negative infinity.
  >  * Returns `Infinity` if `self` is positive infinity.
  > 
  >  Example
  > 
  >  ```moonbit
  >  test "expm1" {
  >    inspect!(0.0.expm1(), content="0")
  >    inspect!(1.0.expm1(), content="1.718281828459045")
  >    inspect!(2.0.expm1(), content="6.38905609893065")
  >    inspect!((-1.0).expm1(), content="-0.6321205588285577")
  >    inspect!((-2.0).expm1(), content="-0.8646647167633873")
  >    inspect!(@double.not_a_number.expm1(), content="NaN")
  >    inspect!(@double.infinity.expm1(), content="Infinity")
  >    inspect!(@double.neg_infinity.expm1(), content="-1")
  >  }
  >  ```
- #### floor
  ```moonbit
  :::source,moonbitlang/core/double/round_wasm.mbt,75:::fn <a href="moonbitlang/core/double#Double">Double</a>::floor(self : Double) -> Double
  ```
  > 
  >  Returns the largest integer less than or equal to the given number.
  > 
  >  Parameters:
  > 
  >  * `number` : A floating-point number to be rounded down.
  > 
  >  Returns a double-precision floating-point number representing the largest
  > integer less than or equal to the input.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "floor" {
  >    inspect!(3.7.floor(), content="3")
  >    inspect!((-3.7).floor(), content="-4")
  >    inspect!(0.0.floor(), content="0")
  >  }
  >  ```
- #### from\_int
  ```moonbit
  :::source,moonbitlang/core/double/double.mbt,51:::fn <a href="moonbitlang/core/double#Double">Double</a>::from_int(i : Int) -> Double
  ```
  > 
  >  Converts an integer to a double-precision floating-point number.
  > 
  >  Parameters:
  > 
  >  * `integer` : The integer value to be converted.
  > 
  >  Returns a double-precision floating-point number representing the given
  > integer value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Double::from_int" {
  >    inspect!(@double.from_int(42), content="42")
  >    inspect!(@double.from_int(-1), content="-1")
  >  }
  >  ```
- #### hypot
  ```moonbit
  :::source,moonbitlang/core/double/hypot_nonjs.mbt,49:::fn <a href="moonbitlang/core/double#Double">Double</a>::hypot(self : Double, y : Double) -> Double
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
  >    inspect!(3.0.hypot(4.0), content="5")
  >    inspect!(5.0.hypot(12.0), content="13")
  >    inspect!(8.0.hypot(15.0), content="17")
  >    inspect!(7.0.hypot(24.0), content="25")
  >    inspect!(@double.not_a_number.hypot(1.0), content="NaN")
  >    inspect!(1.0.hypot(@double.not_a_number), content="NaN")
  >    inspect!(@double.infinity.hypot(1.0), content="Infinity")
  >    inspect!(1.0.hypot(@double.infinity), content="Infinity")
  >    inspect!(@double.neg_infinity.hypot(1.0), content="Infinity")
  >    inspect!(1.0.hypot(@double.neg_infinity), content="Infinity")
  >  }
  >  ```
- #### inf
  ```moonbit
  :::source,moonbitlang/core/double/double.mbt,124:::fn <a href="moonbitlang/core/double#Double">Double</a>::inf(sign : Int) -> Double
  ```
  > 
  >  Returns positive infinity if sign \>= 0, negative infinity if sign \< 0.
- #### is\_close
  ```moonbit
  :::source,moonbitlang/core/double/double.mbt,379:::fn <a href="moonbitlang/core/double#Double">Double</a>::is_close(self : Double, other : Double, relative_tolerance~ : Double = .., absolute_tolerance~ : Double = ..) -> Bool
  ```
  > 
  >  Determines whether two floating-point numbers are approximately equal within
  > specified tolerances.
  > The implementation follows the algorithm described in PEP 485 for Python's
  > `math.isclose()`.
  > 
  >  Parameters:
  > 
  >  * `self` : The first floating-point number to compare.
  >  * `other` : The second floating-point number to compare.
  >  * `relative_tolerance` : The relative tolerance for the comparison. Must be
  >    non-negative. Defaults to 1e-9.
  >  * `absolute_tolerance` : The absolute tolerance for the comparison. Must be
  >    non-negative. Defaults to 0.0.
  > 
  >  Returns whether the two numbers are considered approximately equal. Returns
  > `true` if the numbers are exactly equal or if they are within either the
  > relative or absolute tolerance. Returns `false` if either number is infinite.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "is_close" {
  >    let x = 1.0
  >    let y = 1.000000001
  >    inspect!(x.is_close(y), content="false")
  >    inspect!(x.is_close(y, relative_tolerance=1.0e-10), content="false")
  >    inspect!(infinity.is_close(infinity), content="true")
  >  }
  >  ```
- #### is\_inf
  ```moonbit
  :::source,moonbitlang/core/double/double.mbt,198:::fn <a href="moonbitlang/core/double#Double">Double</a>::is_inf(self : Double) -> Bool
  ```
  > 
  >  Checks whether a double-precision floating-point number represents positive
  > or negative infinity.
  > 
  >  Parameters:
  > 
  >  * `value` : The double-precision floating-point number to check.
  > 
  >  Returns `true` if the value is either positive or negative infinity, `false`
  > otherwise.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "is_inf" {
  >    inspect!(infinity.is_inf(), content="true")
  >    inspect!(neg_infinity.is_inf(), content="true")
  >    inspect!(42.0.is_inf(), content="false")
  >  }
  >  ```
- #### is\_nan
  ```moonbit
  :::source,moonbitlang/core/double/double.mbt,173:::fn <a href="moonbitlang/core/double#Double">Double</a>::is_nan(self : Double) -> Bool
  ```
  > 
  >  Checks whether a double-precision floating-point number represents a "Not a
  > Number" (NaN) value.
  > 
  >  Parameters:
  > 
  >  * `number` : A double-precision floating-point value to be checked.
  > 
  >  Returns `true` if the number is NaN, `false` otherwise.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "is_nan" {
  >    inspect!(not_a_number.is_nan(), content="true")
  >    inspect!(42.0.is_nan(), content="false")
  >    inspect!((0.0 / 0.0).is_nan(), content="true")
  >  }
  >  ```
- #### is\_neg\_inf
  ```moonbit
  :::source,moonbitlang/core/double/double.mbt,242:::fn <a href="moonbitlang/core/double#Double">Double</a>::is_neg_inf(self : Double) -> Bool
  ```
  > 
  >  Checks whether a double-precision floating-point number is negative infinity.
  > 
  >  Parameters:
  > 
  >  * `self` : The double-precision floating-point number to check.
  > 
  >  Returns a boolean value indicating whether the number is negative infinity.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "is_neg_inf" {
  >    inspect!((-1.0 / 0.0).is_neg_inf(), content="true")
  >    inspect!(42.0.is_neg_inf(), content="false")
  >    inspect!((1.0 / 0.0).is_neg_inf(), content="false") // positive infinity
  >  }
  >  ```
- #### is\_pos\_inf
  ```moonbit
  :::source,moonbitlang/core/double/double.mbt,220:::fn <a href="moonbitlang/core/double#Double">Double</a>::is_pos_inf(self : Double) -> Bool
  ```
  > 
  >  Checks whether a double-precision floating-point number is positive infinity.
  > 
  >  Parameters:
  > 
  >  * `value` : The double-precision floating-point number to check.
  > 
  >  Returns `true` if the number is positive infinity, `false` otherwise.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "is_pos_inf" {
  >    inspect!(infinity.is_pos_inf(), content="true")
  >    inspect!(neg_infinity.is_pos_inf(), content="false")
  >    inspect!(42.0.is_pos_inf(), content="false")
  >  }
  >  ```
- #### ln
  ```moonbit
  :::source,moonbitlang/core/double/log_nonjs.mbt,106:::fn <a href="moonbitlang/core/double#Double">Double</a>::ln(self : Double) -> Double
  ```
  > 
  >  Calculates the natural logarithm of a double-precision floating-point number.
  > 
  >  Parameters:
  > 
  >  * `self`: The input number.
  > 
  >  Returns the natural logarithm of the input number, with the following special
  > cases:
  > 
  >  * Returns NaN if the input is NaN or negative
  >  * Returns negative infinity if the input is zero
  >  * Returns the input if it is positive infinity
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "ln" {
  >    inspect!(2.0.ln(), content="0.6931471805599453")
  >    inspect!(1.0.ln(), content="0")
  >    inspect!((-1.0).ln(), content="NaN")
  >    inspect!(0.0.ln(), content="-Infinity")
  >  }
  >  ```
- #### ln\_1p
  ```moonbit
  :::source,moonbitlang/core/double/log_nonjs.mbt,228:::fn <a href="moonbitlang/core/double#Double">Double</a>::ln_1p(self : Double) -> Double
  ```
  > 
  >  Calculates ln(1 + x) accurately even when x is close to zero.
  > 
  >  Parameters:
  > 
  >  * `self` : The number to which 1 is added before calculating the logarithm.
  > 
  >  Returns the natural logarithm of 1 + `self`.
  > 
  >  Special Cases:
  > 
  >  * Returns `NaN` if `self` is `NaN` or less than -1.
  >  * Returns `-Infinity` if `self` is -1.
  >  * Returns `+Infinity` if `self` is `+Infinity`.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "ln_1p" {
  >    inspect!(0.0.ln_1p(), content="0")
  >    inspect!(1.0.ln_1p(), content="0.6931471805599453")
  >    inspect!(2.0.ln_1p(), content="1.0986122886681096")
  >    inspect!(@double.not_a_number.ln_1p(), content="NaN")
  >    inspect!((-1.0).ln_1p(), content="-Infinity")
  >    inspect!((-2.0).ln_1p(), content="NaN")
  >    inspect!(@double.infinity.ln_1p(), content="Infinity")
  >    inspect!(@double.neg_infinity.ln_1p(), content="NaN")
  >  }
  >  ```
- #### log10
  ```moonbit
  :::source,moonbitlang/core/double/log_nonjs.mbt,178:::fn <a href="moonbitlang/core/double#Double">Double</a>::log10(self : Double) -> Double
  ```
  > 
  >  Calculates the base-10 logarithm of a double-precision floating-point number.
  > 
  >  Parameters:
  > 
  >  * `self` : The double-precision floating-point number to calculate the
  >    logarithm of.
  > 
  >  Returns a double-precision floating-point number representing the base-10
  > logarithm of the input.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "log10" {
  >    inspect!(0.1.log10(), content="-1")
  >    inspect!(1.0.log10(), content="0")
  >    inspect!(10.0.log10(), content="1")
  >    inspect!(100.0.log10(), content="2")
  >    inspect!(15.0.log10(), content="1.1760912590556813")
  >  }
  >  ```
- #### log2
  ```moonbit
  :::source,moonbitlang/core/double/log_nonjs.mbt,148:::fn <a href="moonbitlang/core/double#Double">Double</a>::log2(self : Double) -> Double
  ```
  > 
  >  Calculates the base-2 logarithm of a double-precision floating-point number.
  > 
  >  Parameters:
  > 
  >  * `x` : A double-precision floating-point number.
  > 
  >  Returns the base-2 logarithm of the input number.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "log2" {
  >    inspect!(2.0.log2(), content="1")
  >    inspect!(0.5.log2(), content="-1")
  >    inspect!(3.0.log2(), content="1.584962500721156")
  >  }
  >  ```
- #### min\_normal
  ```moonbit
  :::source,moonbitlang/core/double/double.mbt,150:::fn <a href="moonbitlang/core/double#Double">Double</a>::min_normal() -> Double
  ```
  > 
  >  Returns the smallest positive normal value of a double-precision
  > floating-point number.
  > 
  >  Returns a `Double` value that represents the smallest positive normal number
  > that can be represented by a double-precision floating-point number
  > (approximately 2.2250738585072014e-308).
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Double::min_normal" {
  >    inspect!(@double.min_positive, content="2.2250738585072014e-308")
  >  }
  >  ```
  > 
- #### nan
  ```moonbit
  :::source,moonbitlang/core/double/double.mbt,116:::fn <a href="moonbitlang/core/double#Double">Double</a>::nan() -> Double
  ```
  > 
  >  \[DEPRECATED\] Returns a "not-a-number" (NaN) value.
  > 
  >  This function is deprecated. Use `@double.not_a_number` instead.
  > 
  >  Returns a double-precision floating-point NaN value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Double::nan" {
  >    let nan = @double.not_a_number
  >    inspect!(nan.is_nan(), content="true")
  >  }
  >  ```
  > 
- #### pow
  ```moonbit
  :::source,moonbitlang/core/double/pow_nonjs.mbt,135:::fn <a href="moonbitlang/core/double#Double">Double</a>::pow(self : Double, other : Double) -> Double
  ```
  > 
  >  Calculates the power of a number by raising the base to the specified
  > exponent. Handles special cases and edge conditions according to IEEE 754
  > standards.
  > 
  >  Parameters:
  > 
  >  * `base` : The base number to be raised to a power.
  >  * `exponent` : The power to raise the base number to.
  > 
  >  Returns the result of raising `base` to the power of `exponent`.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "pow" {
  >    let x = 2.0
  >    inspect!(x.pow(3.0), content="8")
  >    inspect!(x.pow(0.5), content="1.4142135623730951")
  >    inspect!(x.pow(0.0), content="1")
  >    inspect!((-1.0).pow(2.0), content="1")
  >    inspect!(0.0.pow(0.0), content="1")
  >    inspect!(infinity.pow(-1.0), content="0")
  >  }
  >  ```
- #### round
  ```moonbit
  :::source,moonbitlang/core/double/round_wasm.mbt,98:::fn <a href="moonbitlang/core/double#Double">Double</a>::round(self : Double) -> Double
  ```
  > 
  >  Rounds a floating-point number to the nearest integer using "round half up"
  > rule. In this rule, when a number is halfway between two integers (like 3.5),
  > it is rounded up to the next integer.
  > 
  >  Parameters:
  > 
  >  * `value` : The floating-point number to be rounded.
  > 
  >  Returns the rounded value as a double-precision floating-point number.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "round" {
  >    inspect!(3.7.round(), content="4")
  >    inspect!(3.2.round(), content="3")
  >    inspect!(3.5.round(), content="4")
  >    inspect!((-3.5).round(), content="-3")
  >  }
  >  ```
- #### signum
  ```moonbit
  :::source,moonbitlang/core/double/double.mbt,88:::fn <a href="moonbitlang/core/double#Double">Double</a>::signum(self : Double) -> Double
  ```
  > 
  >  Returns the sign of the double.
  >  - If the double is positive, returns 1.0.
  >  - If the double is negative, returns -1.0.
  >  - Otherwise, returns the double itself (0.0, -0.0 and NaN).
- #### sin
  ```moonbit
  :::source,moonbitlang/core/double/trig_nonjs.mbt,691:::fn <a href="moonbitlang/core/double#Double">Double</a>::sin(self : Double) -> Double
  ```
  > 
  >  Calculates the sine of a number in radians. Handles special cases and edge
  > conditions according to IEEE 754 standards.
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
  >    inspect!(0.0.sin(), content="0")
  >    inspect!(1.570796326794897.sin(), content="1") // pi / 2
  >    inspect!(2.0.sin(), content="0.9092974268256817")
  >    inspect!(-5.0.sin(), content="0.9589242746631385")
  >    inspect!(31415926535897.9323846.sin(), content="0.0012091232715481885")
  >    inspect!(@double.not_a_number.sin(), content="NaN")
  >    inspect!(@double.infinity.sin(), content="NaN")
  >    inspect!(@double.neg_infinity.sin(), content="NaN")
  >  }
  >  ```
- #### sinh
  ```moonbit
  :::source,moonbitlang/core/double/hyperbolic_nonjs.mbt,61:::fn <a href="moonbitlang/core/double#Double">Double</a>::sinh(self : Double) -> Double
  ```
  > 
  >  Calculates the hyperbolic sine of a number.
  > 
  >  Parameters:
  > 
  >  * `self` : The number for which to calculate the hyperbolic sine.
  > 
  >  Returns the hyperbolic sine of `self`.
  > 
  >  Special cases:
  > 
  >  * Returns `infinity` if `self` is `infinity`
  >  * Returns `NaN` if `self` is `NaN`
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "sinh" {
  >    inspect!(0.0.sinh(), content="0")
  >    inspect!((-0.0).sinh(), content="0")
  >    inspect!(1.0.sinh(), content="1.1752011936438014")
  >    inspect!(2.0.sinh(), content="3.626860407847019")
  >    inspect!(1000.0.sinh(), content="Infinity")
  >    inspect!((-1000.0).sinh(), content="-Infinity")
  >    inspect!(@double.not_a_number.sinh(), content="NaN")
  >    inspect!(@double.infinity.sinh(), content="Infinity")
  >    inspect!(@double.neg_infinity.sinh(), content="-Infinity")
  >  }
  >  ```
- #### tan
  ```moonbit
  :::source,moonbitlang/core/double/trig_nonjs.mbt,777:::fn <a href="moonbitlang/core/double#Double">Double</a>::tan(self : Double) -> Double
  ```
  > 
  >  Calculates the tangent of a number in radians. Handles special cases and edge
  > conditions according to IEEE 754 standards.
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
  >    inspect!(0.0.tan(), content="0")
  >    inspect!(0.7853981633974483.tan(), content="0.9999999999999999")
  >    inspect!(4.0.tan(), content="1.1578212823495777")
  >    inspect!(5.0.tan(), content="-3.380515006246586")
  >    inspect!(31415926535897.9323846.tan(), content="0.0012091241554056254")
  >    inspect!(@double.not_a_number.tan(), content="NaN")
  >    inspect!(@double.infinity.tan(), content="NaN")
  >    inspect!(@double.neg_infinity.tan(), content="NaN")
  >  }
  >  ```
- #### tanh
  ```moonbit
  :::source,moonbitlang/core/double/hyperbolic_nonjs.mbt,183:::fn <a href="moonbitlang/core/double#Double">Double</a>::tanh(self : Double) -> Double
  ```
  > 
  >  Calculates the hyperbolic tangent of a number.
  > 
  >  Parameters:
  > 
  >  * `self` : The number for which to calculate the hyperbolic tangent.
  > 
  >  Returns the hyperbolic tangent of `self`.
  > 
  >  Special cases:
  > 
  >  * Returns `NaN` if `self` is `NaN`
  >  * Returns `1` if `self` is `infinity`
  >  * Returns `-1` if `self` is `-infinity`
  > 
  >  Example
  > 
  >  ```moobit
  >  test "tanh" {
  >    inspect!(0.0.tanh(), content="0")
  >    inspect!((-0.0).tanh(), content="0")
  >    inspect!(1.0.tanh(), content="0.7615941559557649")
  >    inspect!(2.0.tanh(), content="0.9640275800758169")
  >    inspect!(1000.0.tanh(), content="1")
  >    inspect!((-1000.0).tanh(), content="-1")
  >    inspect!(@double.not_a_number.tanh(), content="NaN")
  >    inspect!(@double.infinity.tanh(), content="1")
  >    inspect!(@double.neg_infinity.tanh(), content="-1")
  >  }
  >  ```
- #### to\_be\_bytes
  ```moonbit
  :::source,moonbitlang/core/double/double.mbt,423:::fn <a href="moonbitlang/core/double#Double">Double</a>::to_be_bytes(self : Double) -> Bytes
  ```
  > 
  >  Converts a double-precision floating-point number to a sequence of bytes in
  > big-endian byte order (most significant byte first).
  > 
  >  Parameters:
  > 
  >  * `self` : The double-precision floating-point number to be converted.
  > 
  >  Returns a sequence of 8 bytes representing the double-precision
  > floating-point number in big-endian byte order.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "to_be_bytes" {
  >    let d = 1.0
  >    inspect!(d.to_be_bytes(), content=
  >    #|b"\x3f\xf0\x00\x00\x00\x00\x00\x00"
  >  )
  >  }
  >  ```
- #### to\_le\_bytes
  ```moonbit
  :::source,moonbitlang/core/double/double.mbt,448:::fn <a href="moonbitlang/core/double#Double">Double</a>::to_le_bytes(self : Double) -> Bytes
  ```
  > 
  >  Converts a double-precision floating-point number to a sequence of bytes in
  > little-endian order (least significant byte first).
  > 
  >  Parameters:
  > 
  >  * `self` : A double-precision floating-point number to be converted.
  > 
  >  Returns a sequence of 8 bytes representing the double-precision
  > floating-point number in little-endian order.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "to_le_bytes" {
  >    let d = 1.0
  >    inspect!(d.to_le_bytes(), content=
  >    #|b"\x00\x00\x00\x00\x00\x00\xf0\x3f"
  >  )
  >  }
  >  ```
- #### to\_string
  ```moonbit
  :::source,moonbitlang/core/double/double.mbt,340:::fn <a href="moonbitlang/core/double#Double">Double</a>::to_string(self : Double) -> String
  ```
  > 
  >  Converts a double-precision floating-point number to its string
  > representation.
  > 
  >  Parameters:
  > 
  >  * `self`: The double-precision floating-point number to be converted.
  > 
  >  Returns a string representation of the double-precision floating-point
  > number.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Double::to_string" {
  >    inspect!(42.0.to_string(), content="42")
  >    inspect!(3.14159.to_string(), content="3.14159")
  >    inspect!((-0.0).to_string(), content="0")
  >    inspect!(not_a_number.to_string(), content="NaN")
  >  }
  >  ```
  > 
- #### to\_uint
  ```moonbit
  :::source,moonbitlang/core/double/to_uint_wasm.mbt,44:::fn <a href="moonbitlang/core/double#Double">Double</a>::to_uint(self : Double) -> UInt
  ```
  > 
  >  Converts a double-precision floating-point number to a 32-bit unsigned
  > integer. Handles special cases including NaN and numbers outside the valid
  > `UInt` range.
  > 
  >  Parameters:
  > 
  >  * `self` : The double-precision floating-point number to be converted.
  > 
  >  Returns an 32-bit unsigned integer value according to the following rules:
  > 
  >  * Returns 0 if the input is NaN
  >  * Returns `@uint.max_value` (4294967295U) if the input is greater than or
  >    equal to `@uint.max_value`
  >  * Returns `@uint.min_value` (0U) if the input is less than or equal
  >    to `@uint.min_value`
  >  * Otherwise returns the integer part of the input by truncating towards zero
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Double::to_uint/normal" {
  >    inspect!(42.0.to_uint(), content="42")
  >    inspect!((-42.5).to_uint(), content="0")
  >    inspect!((0.0 / 0.0).to_uint(), content="0") // NaN
  >    inspect!((1.0 / 0.0).to_uint(), content="4294967295") // Infinity
  >    inspect!((-1.0 / 0.0).to_uint(), content="0") // -Infinity
  >  }
  >  ```
- #### trunc
  ```moonbit
  :::source,moonbitlang/core/double/round_wasm.mbt,34:::fn <a href="moonbitlang/core/double#Double">Double</a>::trunc(self : Double) -> Double
  ```
  > 
  >  Returns an integer value by discarding the decimal part of the floating-point
  > number (truncation toward zero).
  > 
  >  Parameters:
  > 
  >  * `self` : The floating-point number to be truncated.
  > 
  >  Returns a floating-point number representing the integer part of the input.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "trunc" {
  >    inspect!(3.7.trunc(), content="3")
  >    inspect!((-3.7).trunc(), content="-3")
  >    inspect!(0.0.trunc(), content="0")
  >  }
  >  ```
