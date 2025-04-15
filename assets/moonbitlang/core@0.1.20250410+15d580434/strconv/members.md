# Documentation
|Trait|description|
|---|---|
|[@moonbitlang/core/strconv.FromStr](#@moonbitlang/core/strconv.FromStr)||

|Type|description|
|---|---|
|[Decimal](#Decimal)||
|[StrConvError](#StrConvError)||

|Value|description|
|---|---|
|[parse](#parse)||
|[parse\_bool](#parse_bool)||
|[parse\_decimal](#parse_decimal)| @alert deprecated "use \`@strconv.parse\_double\` instead"|
|[parse\_double](#parse_double)||
|[parse\_int](#parse_int)||
|[parse\_int64](#parse_int64)||
|[parse\_uint](#parse_uint)||
|[parse\_uint64](#parse_uint64)||
|[shift](#shift)||
|[to\_double](#to_double)| @alert deprecated "use \`@strconv.parse\_double\` instead to avoid using this method."|

## @moonbitlang/core/strconv.FromStr

```moonbit
:::source,moonbitlang/core/strconv/traits.mbt,22:::pub(open) trait @moonbitlang/core/strconv.FromStr {
  from_string(String) -> Self!<a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/strconv/traits.mbt,27:::impl <a href="moonbitlang/core/strconv#FromStr">FromStr</a> for Bool
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/strconv/traits.mbt,27:::fn from_string(str : String) -> Bool!<a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/strconv/traits.mbt,32:::impl <a href="moonbitlang/core/strconv#FromStr">FromStr</a> for Int
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/strconv/traits.mbt,32:::fn from_string(str : String) -> Int!<a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/strconv/traits.mbt,37:::impl <a href="moonbitlang/core/strconv#FromStr">FromStr</a> for Int64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/strconv/traits.mbt,37:::fn from_string(str : String) -> Int64!<a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/strconv/traits.mbt,42:::impl <a href="moonbitlang/core/strconv#FromStr">FromStr</a> for UInt
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/strconv/traits.mbt,42:::fn from_string(str : String) -> UInt!<a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/strconv/traits.mbt,47:::impl <a href="moonbitlang/core/strconv#FromStr">FromStr</a> for UInt64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/strconv/traits.mbt,47:::fn from_string(str : String) -> UInt64!<a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/strconv/traits.mbt,52:::impl <a href="moonbitlang/core/strconv#FromStr">FromStr</a> for Double
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/strconv/traits.mbt,52:::fn from_string(str : String) -> Double!<a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>
    ```
    > 

## Decimal

```moonbit
:::source,moonbitlang/core/strconv/decimal.mbt,23:::type Decimal
```

 High Precision Decimal structure for "Simple Decimal Conversion" algorithm.
Developed by Ken. Thompson, Russ Cox, Robert Griesemer, Nigel Tao.
 
 reference:
 - <https://nigeltao.github.io/blog/2020/parse-number-f64-simple.html>
 - <https://nigeltao.github.io/blog/2020/eisel-lemire.html>
   @alert deprecated "Decimal will be changed to private. Use `@strconv.parse_double` instead"

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/strconv/decimal.mbt,576:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/strconv#Decimal">Decimal</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/strconv/decimal.mbt,576:::fn output(self : <a href="moonbitlang/core/strconv#Decimal">Decimal</a>, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### from\_int64
  ```moonbit
  :::source,moonbitlang/core/strconv/decimal.mbt,64:::fn <a href="moonbitlang/core/strconv#Decimal">Decimal</a>::from_int64(v : Int64) -> <a href="moonbitlang/core/strconv#Decimal">Decimal</a>
  ```
  > 
  >  Create a decimal with an Int64 value.
- #### new
  ```moonbit
  :::source,moonbitlang/core/strconv/decimal.mbt,46:::fn <a href="moonbitlang/core/strconv#Decimal">Decimal</a>::new() -> <a href="moonbitlang/core/strconv#Decimal">Decimal</a>
  ```
  > 
  >  Create a zero decimal.
- #### parse\_decimal
  ```moonbit
  :::source,moonbitlang/core/strconv/decimal.mbt,160:::fn <a href="moonbitlang/core/strconv#Decimal">Decimal</a>::parse_decimal(str : String) -> <a href="moonbitlang/core/strconv#Decimal">Decimal</a>!<a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>
  ```
  >  @alert deprecated "use `@strconv.parse_double` instead"
- #### shift
  ```moonbit
  :::source,moonbitlang/core/strconv/decimal.mbt,259:::fn <a href="moonbitlang/core/strconv#Decimal">Decimal</a>::shift(self : <a href="moonbitlang/core/strconv#Decimal">Decimal</a>, s : Int) -> Unit
  ```
  > 
  >  Binary shift left (s \> 0) or right (s \< 0).
  > The shift count must not larger than the max\_shift to avoid overflow.
- #### to\_double
  ```moonbit
  :::source,moonbitlang/core/strconv/decimal.mbt,167:::fn <a href="moonbitlang/core/strconv#Decimal">Decimal</a>::to_double(self : <a href="moonbitlang/core/strconv#Decimal">Decimal</a>) -> Double!<a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>
  ```
  >  @alert deprecated "use `@strconv.parse_double` instead to avoid using this method."

## StrConvError

```moonbit
:::source,moonbitlang/core/strconv/errors.mbt,16:::pub(all) type! StrConvError String

```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/strconv/errors.mbt,19:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/strconv/errors.mbt,19:::fn output(self : <a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 

## parse

```moonbit
:::source,moonbitlang/core/strconv/traits.mbt,57:::fn parse[A : <a href="moonbitlang/core/strconv#FromStr">FromStr</a>](str : String) -> A!<a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>
```


## parse\_bool

```moonbit
:::source,moonbitlang/core/strconv/bool.mbt,17:::fn parse_bool(str : String) -> Bool!<a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>
```

 Parse a string and return the represented boolean value or an error.

## parse\_decimal

```moonbit
:::source,moonbitlang/core/strconv/decimal.mbt,74:::fn parse_decimal(str : String) -> <a href="moonbitlang/core/strconv#Decimal">Decimal</a>!<a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>
```
 @alert deprecated "use `@strconv.parse_double` instead"

## parse\_double

```moonbit
:::source,moonbitlang/core/strconv/double.mbt,70:::fn parse_double(str : String) -> Double!<a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>
```

 Parse a string into a double precision floating point number. The string
must contain at least one of:
 - An integer part (decimal digits)
 - A decimal point followed by a fractional part (decimal digits)
 - An exponent part ('e' or 'E' followed by an optional sign and decimal digits)

 The string may optionally start with a sign ('+' or '-').
For readability, underscores may appear between digits.

 Examples:
 ```
 inspect!(parse_double!("123"), content="123")
 inspect!(parse_double!("12.34"), content="12.34")
 inspect!(parse_double!(".123"), content="0.123")
 inspect!(parse_double!("1e5"), content="100000")
 inspect!(parse_double!("1.2e-3"), content="0.0012")
 inspect!(parse_double!("1_234.5"), content="1234.5")
 ```

 An exponent value exp scales the mantissa (significand) by 10^exp.
For example, "1.23e2" represents 1.23 × 10² = 123.

## parse\_int

```moonbit
:::source,moonbitlang/core/strconv/int.mbt,138:::fn parse_int(str : String, base~ : Int = ..) -> Int!<a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>
```

 Parse a string in the given base (0, 2 to 36), return a Int number or an error.
If the `~base` argument is 0, the base will be inferred by the prefix.

## parse\_int64

```moonbit
:::source,moonbitlang/core/strconv/int.mbt,86:::fn parse_int64(str : String, base~ : Int = ..) -> Int64!<a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>
```

 Parses a string into an Int64 number using the specified base, or returns an error.
The base must be 0 or between 2 and 36 (inclusive). If base is 0, it will be
inferred from the string prefix:
   - "0x" or "0X" for base 16 (hex)
   - "0o" or "0O" for base 8 (octal)
   - "0b" or "0B" for base 2 (binary)
   - Default is base 10 (decimal)
     For readability, underscores may appear after base prefixes or between digits.
     These underscores do not affect the value.
     Examples:
 ```
 inspect!(parse_int64!("123"), content="123")
 inspect!(parse_int64!("0xff", base=0), content="255") 
 inspect!(parse_int64!("0o10"), content="8")
 inspect!(parse_int64!("0b1010"), content="10")
 inspect!(parse_int64!("1_234"), content="1234")
 inspect!(parse_int64!("-123"), content="-123")
 inspect!(parse_int64!("ff", base=16), content="255")
 inspect!(parse_int64!("zz", base=36), content="1295")
 ```
 

## parse\_uint

```moonbit
:::source,moonbitlang/core/strconv/uint.mbt,91:::fn parse_uint(str : String, base~ : Int = ..) -> UInt!<a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>
```

 Parse a string in the given base (0, 2 to 36), return an UInt number or an error.
If the `~base` argument is 0, the base will be inferred by the prefix.

## parse\_uint64

```moonbit
:::source,moonbitlang/core/strconv/uint.mbt,42:::fn parse_uint64(str : String, base~ : Int = ..) -> UInt64!<a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>
```

 Parses a string into a UInt64 number using the specified base, or returns an error.
The base must be 0 or between 2 and 36 (inclusive). If base is 0, it will be
inferred from the string prefix:
   - "0x" or "0X" for base 16 (hex)
   - "0o" or "0O" for base 8 (octal)
   - "0b" or "0B" for base 2 (binary)
   - Default is base 10 (decimal)
     For readability, underscores may appear after base prefixes or between digits.
     These underscores do not affect the value.
     Examples:
 ```
 inspect!(parse_uint64!("123"), content="123")
 inspect!(parse_uint64!("0xff", base=0), content="255")
 inspect!(parse_uint64!("0o10"), content="8")
 inspect!(parse_uint64!("0b1010"), content="10")
 inspect!(parse_uint64!("1_234"), content="1234")
 inspect!(parse_uint64!("ff", base=16), content="255")
 inspect!(parse_uint64!("zz", base=36), content="1295")
 ```
 

## shift

```moonbit
:::source,moonbitlang/core/strconv/decimal.mbt,259:::fn shift(self : <a href="moonbitlang/core/strconv#Decimal">Decimal</a>, s : Int) -> Unit
```

 Binary shift left (s \> 0) or right (s \< 0).
The shift count must not larger than the max\_shift to avoid overflow.

## to\_double

```moonbit
:::source,moonbitlang/core/strconv/decimal.mbt,167:::fn to_double(self : <a href="moonbitlang/core/strconv#Decimal">Decimal</a>) -> Double!<a href="moonbitlang/core/strconv#StrConvError">StrConvError</a>
```
 @alert deprecated "use `@strconv.parse_double` instead to avoid using this method."
