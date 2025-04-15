# Documentation
|Trait|description|
|---|---|
|[Add](#Add)||
|[BitAnd](#BitAnd)||
|[BitOr](#BitOr)||
|[BitXOr](#BitXOr)||
|[Compare](#Compare)||
|[Default](#Default)||
|[Div](#Div)||
|[Eq](#Eq)||
|[Hash](#Hash)||
|[Logger](#Logger)||
|[Mod](#Mod)||
|[Mul](#Mul)||
|[Neg](#Neg)||
|[Shl](#Shl)||
|[Show](#Show)||
|[Shr](#Shr)||
|[Sub](#Sub)||
|[ToJson](#ToJson)||

|Type|description|
|---|---|
|[ArgsLoc](#ArgsLoc)||
|[Array](#Array)||
|[ArrayView](#ArrayView)||
|[BigInt](#BigInt)||
|[Failure](#Failure)||
|[Hasher](#Hasher)||
|[InspectError](#InspectError)||
|[Iter](#Iter)||
|[Iter2](#Iter2)||
|[IterResult](#IterResult)||
|[Json](#Json)||
|[Map](#Map)||
|[Set](#Set)||
|[SnapshotError](#SnapshotError)||
|[SourceLoc](#SourceLoc)||
|[StringBuilder](#StringBuilder)||
|[UninitializedArray](#UninitializedArray)||
|[Logger](#Logger)||
|[Bytes](#Bytes)||
|[FixedArray](#FixedArray)||
|[Option](#Option)||
|[String](#String)||
|[Double](#Double)||
|[Float](#Float)||
|[UInt64](#UInt64)||
|[UInt16](#UInt16)||
|[UInt](#UInt)||
|[Int64](#Int64)||
|[Int16](#Int16)||
|[Int](#Int)||
|[Char](#Char)||
|[Byte](#Byte)||
|[Bool](#Bool)||

|Value|description|
|---|---|
|[abort](#abort)||
|[assert\_eq](#assert_eq)||
|[assert\_false](#assert_false)||
|[assert\_not\_eq](#assert_not_eq)||
|[assert\_true](#assert_true)||
|[dump](#dump)||
|[fail](#fail)||
|[ignore](#ignore)||
|[inspect](#inspect)||
|[not](#not)||
|[op\_ge](#op_ge)||
|[op\_gt](#op_gt)||
|[op\_le](#op_le)||
|[op\_lt](#op_lt)||
|[op\_notequal](#op_notequal)||
|[panic](#panic)||
|[physical\_equal](#physical_equal)||
|[println](#println)||
|[repr](#repr)||

## Add

```moonbit
:::source,moonbitlang/core/builtin/operators.mbt,17:::pub(open) trait Add {
  op_add(Self, Self) -> Self
}
```

 types implementing this trait can use the `+` operator

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/byte.mbt,94:::impl <a href="moonbitlang/core/builtin#Add">Add</a> for Byte
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/byte.mbt,94:::fn op_add(self : Byte, that : Byte) -> Byte
    ```
    > 
    >  Adds two `Byte` values together and returns the result as a `Byte`.
    > 
    >  Parameters:
    > 
    >  - `byte1` : The first `Byte` value to be added.
    >  - `byte2` : The second `Byte` value to be added.
    > 
    >  Returns the sum of `byte1` and `byte2` as a `Byte`.
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,260:::impl <a href="moonbitlang/core/builtin#Add">Add</a> for Int
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,260:::fn op_add(self : Int, other : Int) -> Int
    ```
    > 
    >  Adds two 32-bit signed integers. Performs two's complement arithmetic, which
    > means the operation will wrap around if the result exceeds the range of a
    > 32-bit integer.
    > 
    >  Parameters:
    > 
    >  * `self` : The first integer operand.
    >  * `other` : The second integer operand.
    > 
    >  Returns a new integer that is the sum of the two operands. If the
    > mathematical sum exceeds the range of a 32-bit integer (-2,147,483,648 to
    > 2,147,483,647), the result wraps around according to two's complement rules.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int::op_add" {
    >    inspect!(42 + 1, content="43")
    >    inspect!(2147483647 + 1, content="-2147483648") // Overflow wraps around to minimum value
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,60:::impl <a href="moonbitlang/core/builtin#Add">Add</a> for Int64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,60:::fn op_add(self : Int64, other : Int64) -> Int64
    ```
    > 
    >  Adds two 64-bit integers together. Performs overflow checking and wrapping
    > according to two's complement arithmetic.
    > 
    >  Parameters:
    > 
    >  * `self` : The first 64-bit integer operand.
    >  * `other` : The second 64-bit integer operand to add to the first.
    > 
    >  Returns a new 64-bit integer representing the sum of the two operands.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int64::op_add" {
    >    let a = 9223372036854775807L // Int64 maximum value
    >    let b = 1L
    >    inspect!(a + b, content="-9223372036854775808") // Wraps around to minimum value
    >    inspect!(42L + -42L, content="0")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1992:::impl <a href="moonbitlang/core/builtin#Add">Add</a> for UInt
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,1992:::fn op_add(self : UInt, other : UInt) -> UInt
    ```
    > 
    >  Performs addition between two unsigned 32-bit integers. If the result
    > overflows, it wraps around according to the rules of modular arithmetic
    > (2^32).
    > 
    >  Parameters:
    > 
    >  * `self` : The first unsigned 32-bit integer operand.
    >  * `other` : The second unsigned 32-bit integer operand to be added.
    > 
    >  Returns the sum of the two unsigned integers, wrapped around if necessary.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt::op_add" {
    >    let a = 42U
    >    let b = 100U
    >    inspect!(a + b, content="142")
    >  
    >    // Demonstrate overflow behavior
    >    let max = 4294967295U // UInt::max_value
    >    inspect!(max + 1U, content="0")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1193:::impl <a href="moonbitlang/core/builtin#Add">Add</a> for UInt64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1193:::fn op_add(self : UInt64, other : UInt64) -> UInt64
    ```
    > 
    >  Adds two 64-bit unsigned integers. This is the implementation of the `+`
    > operator for `UInt64`.
    > 
    >  Parameters:
    > 
    >  * `self` : The first unsigned 64-bit integer operand.
    >  * `other` : The second unsigned 64-bit integer operand.
    > 
    >  Returns the sum of the two unsigned 64-bit integers. If the result overflows,
    > it wraps around modulo 2^64.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt64::op_add" {
    >    let a = 42UL
    >    let b = 100UL
    >    inspect!(a + b, content="142")
    >  
    >    // Demonstrate overflow behavior
    >    let max = 18446744073709551615UL
    >    inspect!(max + 1UL, content="0")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2629:::impl <a href="moonbitlang/core/builtin#Add">Add</a> for Float
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,2629:::fn op_add(self : Float, other : Float) -> Float
    ```
    > 
    >  Performs addition between two single-precision floating-point numbers.
    > 
    >  Parameters:
    > 
    >  * `self` : The first floating-point operand.
    >  * `other` : The second floating-point operand to be added to the first
    >    operand.
    > 
    >  Returns a single-precision floating-point number representing the sum of the
    > two operands.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Float::op_add" {
    >    let a = 3.14.to_float()
    >    let b = 2.86.to_float()
    >    let sum = a + b
    >    inspect!(sum.to_double(), content="6")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,951:::impl <a href="moonbitlang/core/builtin#Add">Add</a> for Double
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,951:::fn op_add(self : Double, other : Double) -> Double
    ```
    > 
    >  Adds two double-precision floating-point numbers together following IEEE 754
    > standards.
    > 
    >  Parameters:
    > 
    >  * `self` : The first double-precision floating-point number.
    >  * `other` : The second double-precision floating-point number to add.
    > 
    >  Returns the sum of the two numbers. Special cases follow IEEE 754 rules:
    > 
    >  * If either operand is NaN, returns NaN
    >  * If adding +∞ and -∞, returns NaN
    >  * If adding ±∞ with any finite number, returns ±∞
    >  * If adding +0.0 and -0.0, returns +0.0
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Double::op_add" {
    >    inspect!(2.5 + 3.7, content="6.2")
    >    inspect!(1.0 / 0.0 + -1.0 / 0.0, content="NaN") // Infinity + -Infinity = NaN
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1835:::impl <a href="moonbitlang/core/builtin#Add">Add</a> for String
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,1835:::fn op_add(self : String, other : String) -> String
    ```
    > 
    >  Concatenates two strings, creating a new string that contains all characters
    > from the first string followed by all characters from the second string.
    > 
    >  Parameters:
    > 
    >  * `self` : The first string to concatenate.
    >  * `other` : The second string to concatenate.
    > 
    >  Returns a new string containing the concatenation of both input strings.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "String::op_add" {
    >    let hello = "Hello"
    >    let world = " World!"
    >    inspect!(hello + world, content="Hello World!")
    >    inspect!("" + "abc", content="abc") // concatenating with empty string
    >  }
    >  ```

## BitAnd

```moonbit
:::source,moonbitlang/core/builtin/operators.mbt,53:::pub(open) trait BitAnd {
  land(Self, Self) -> Self
}
```

 types implementing this trait can use the `&` operator

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/byte.mbt,247:::impl <a href="moonbitlang/core/builtin#BitAnd">BitAnd</a> for Byte
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/byte.mbt,247:::fn land(self : Byte, that : Byte) -> Byte
    ```
    > 
    >  Performs a bitwise AND operation between two `Byte` values.
    > 
    >  Parameters:
    > 
    >  - `byte1` : The first `Byte` value to perform the bitwise AND operation with.
    >  - `byte2` : The second `Byte` value to perform the bitwise AND operation
    >    with.
    > 
    >  Returns the result of the bitwise AND operation as a `Byte`.
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,215:::impl <a href="moonbitlang/core/builtin#BitAnd">BitAnd</a> for Int64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,215:::fn land(self : Int64, other : Int64) -> Int64
    ```
    > 
    >  Performs a bitwise AND operation between two 64-bit signed integers.
    > 
    >  Parameters:
    > 
    >  * `self` : The first 64-bit integer operand.
    >  * `other` : The second 64-bit integer operand.
    > 
    >  Returns a 64-bit integer where each bit is set to 1 if and only if the
    > corresponding bits in both operands are 1.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int64::land" {
    >    let a = 0xFF00FF00L
    >    let b = 0x0F0F0F0FL
    >    inspect!(a & b, content="251662080") // 0x0F000F00
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1373:::impl <a href="moonbitlang/core/builtin#BitAnd">BitAnd</a> for UInt64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1373:::fn land(self : UInt64, other : UInt64) -> UInt64
    ```
    > 
    >  Performs a bitwise AND operation between two unsigned 64-bit integers.
    > 
    >  Parameters:
    > 
    >  * `self` : The first unsigned 64-bit integer operand.
    >  * `other` : The second unsigned 64-bit integer operand.
    > 
    >  Returns the result of performing a bitwise AND operation on the two operands.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt64::land" {
    >    let a = 0xF0F0F0F0F0F0F0F0UL
    >    let b = 0xFF00FF00FF00FF00UL
    >    inspect!(a & b, content="17294086455919964160") // 0xF000F000F000F000
    >  }
    >  ```

## BitOr

```moonbit
:::source,moonbitlang/core/builtin/operators.mbt,59:::pub(open) trait BitOr {
  lor(Self, Self) -> Self
}
```

 types implementing this trait can use the `|` operator

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/byte.mbt,260:::impl <a href="moonbitlang/core/builtin#BitOr">BitOr</a> for Byte
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/byte.mbt,260:::fn lor(self : Byte, that : Byte) -> Byte
    ```
    > 
    >  Performs a bitwise OR operation between two `Byte` values.
    > 
    >  Parameters:
    > 
    >  - `self` : The first `Byte` value.
    >  - `that` : The second `Byte` value.
    > 
    >  Returns a new `Byte` value resulting from the bitwise OR operation.
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,237:::impl <a href="moonbitlang/core/builtin#BitOr">BitOr</a> for Int64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,237:::fn lor(self : Int64, other : Int64) -> Int64
    ```
    > 
    >  Performs a bitwise OR operation between two 64-bit integers.
    > 
    >  Parameters:
    > 
    >  * `self` : The first 64-bit integer operand.
    >  * `other` : The second 64-bit integer operand.
    > 
    >  Returns a new 64-bit integer where each bit is set to 1 if at least one of
    > the corresponding bits in either operand is 1.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int64::lor" {
    >    let a = 0xFF00L // 1111_1111_0000_0000
    >    let b = 0x0FF0L // 0000_1111_1111_0000
    >    inspect!(a | b, content="65520") // 1111_1111_1111_0000 = 65520
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1395:::impl <a href="moonbitlang/core/builtin#BitOr">BitOr</a> for UInt64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1395:::fn lor(self : UInt64, other : UInt64) -> UInt64
    ```
    > 
    >  Performs a bitwise OR operation between two unsigned 64-bit integers.
    > 
    >  Parameters:
    > 
    >  * `self` : The first unsigned 64-bit integer operand.
    >  * `other` : The second unsigned 64-bit integer operand.
    > 
    >  Returns a new `UInt64` value with bits set to 1 where either or both operands
    > have bits set to 1, and 0 where both operands have bits set to 0.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt64::lor" {
    >    let a = 0xF0F0F0F0UL
    >    let b = 0x0F0F0F0FUL
    >    inspect!(a | b, content="4294967295") // All bits set to 1
    >  }
    >  ```

## BitXOr

```moonbit
:::source,moonbitlang/core/builtin/operators.mbt,65:::pub(open) trait BitXOr {
  lxor(Self, Self) -> Self
}
```

 types implementing this trait can use the `^` operator

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/byte.mbt,273:::impl <a href="moonbitlang/core/builtin#BitXOr">BitXOr</a> for Byte
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/byte.mbt,273:::fn lxor(self : Byte, that : Byte) -> Byte
    ```
    > 
    >  Performs a bitwise XOR operation between two `Byte` values.
    > 
    >  Parameters:
    > 
    >  - `self` : The first `Byte` value.
    >  - `that` : The second `Byte` value.
    > 
    >  Returns the result of the bitwise XOR operation as a `Byte`.
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,262:::impl <a href="moonbitlang/core/builtin#BitXOr">BitXOr</a> for Int64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,262:::fn lxor(self : Int64, other : Int64) -> Int64
    ```
    > 
    >  Performs a bitwise XOR operation between two 64-bit integers. Each bit of the
    > result is set to 1 if the corresponding bits of the operands are different,
    > and 0 if they are the same.
    > 
    >  Parameters:
    > 
    >  * `self` : The first 64-bit integer operand.
    >  * `other` : The second 64-bit integer operand.
    > 
    >  Returns a new 64-bit integer containing the result of the bitwise XOR
    > operation.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int64::lxor" {
    >    let a = 0xF0F0F0F0F0F0F0F0L
    >    let b = 0x0F0F0F0F0F0F0F0FL
    >    inspect!(a ^ b, content="-1") // All bits set to 1
    >    inspect!(a ^ a, content="0") // XOR with self gives 0
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1419:::impl <a href="moonbitlang/core/builtin#BitXOr">BitXOr</a> for UInt64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1419:::fn lxor(self : UInt64, other : UInt64) -> UInt64
    ```
    > 
    >  Performs a bitwise XOR operation between two unsigned 64-bit integers. For
    > each bit position, the result is 1 if the bits at that position in the two
    > operands are different, and 0 if they are the same.
    > 
    >  Parameters:
    > 
    >  * `self` : The first unsigned 64-bit integer operand.
    >  * `other` : The second unsigned 64-bit integer operand.
    > 
    >  Returns a new `UInt64` value representing the bitwise XOR of the two
    > operands.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt64::lxor" {
    >    let a = 0xF0F0F0F0UL
    >    let b = 0x0F0F0F0FUL
    >    inspect!(a ^ b, content="4294967295") // 0xFFFFFFFF
    >  }
    >  ```

## Compare

```moonbit
:::source,moonbitlang/core/builtin/traits.mbt,28:::pub(open) trait Compare : <a href="moonbitlang/core/builtin#Eq">Eq</a> {
  compare(Self, Self) -> Int
}
```

 Trait for types whose elements are ordered

 The return value of \[compare\] is:
 - zero, if the two arguments are equal
 - negative, if the first argument is smaller
 - positive, if the first argument is greater

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,195:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for Bool
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,195:::fn compare(self : Bool, other : Bool) -> Int
    ```
    > 
    >  Compares two boolean values and returns their relative order. The comparison
    > follows the rule that `false` is less than `true`.
    > 
    >  Parameters:
    > 
    >  * `self` : The first boolean value to compare.
    >  * `other` : The second boolean value to compare against.
    > 
    >  Returns an integer indicating the relative order:
    > 
    >  * A negative value if `self` is `false` and `other` is `true`
    >  * Zero if `self` equals `other`
    >  * A positive value if `self` is `true` and `other` is `false`
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Bool::compare" {
    >    inspect!(true.compare(false), content="1") // true > false
    >    inspect!(false.compare(true), content="-1") // false < true
    >    inspect!(true.compare(true), content="0") // true = true
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/byte.mbt,125:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for Byte
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/byte.mbt,125:::fn compare(self : Byte, that : Byte) -> Int
    ```
    > 
    >  Compares two `Byte` values and returns an integer indicating their relative
    > order.
    > 
    >  Parameters:
    > 
    >  - `byte1` : The first `Byte` value to compare.
    >  - `byte2` : The second `Byte` value to compare.
    > 
    >  Returns an integer where:
    >  - A value less than 0 indicates that `byte1` is less than `byte2`.
    >  - A value of 0 indicates that `byte1` is equal to `byte2`.
    >  - A value greater than 0 indicates that `byte1` is greater than `byte2`.
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1288:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for Char
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,1288:::fn compare(self : Char, other : Char) -> Int
    ```
    > 
    >  Compares two characters based on their Unicode code points. Returns a
    > negative value if the first character comes before the second, zero if they
    > are equal, and a positive value if the first character comes after the
    > second.
    > 
    >  Parameters:
    > 
    >  * `self` : The first character to compare.
    >  * `other` : The second character to compare against.
    > 
    >  Returns an integer indicating the relative ordering:
    > 
    >  * A negative value if `self` is less than `other`
    >  * Zero if `self` equals `other`
    >  * A positive value if `self` is greater than `other`
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Char::compare" {
    >    inspect!('a'.compare('b'), content="-1")
    >    inspect!('b'.compare('a'), content="1")
    >    inspect!('a'.compare('a'), content="0")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,749:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for Int
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,749:::fn compare(self : Int, other : Int) -> Int
    ```
    > 
    >  Compares two integers and returns their relative order.
    > 
    >  Parameters:
    > 
    >  * `self` : The first integer to compare.
    >  * `other` : The second integer to compare against.
    > 
    >  Returns an integer indicating the relative order:
    > 
    >  * A negative value if `self` is less than `other`
    >  * Zero if `self` equals `other`
    >  * A positive value if `self` is greater than `other`
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int::compare" {
    >    let a = 42
    >    let b = 24
    >    inspect!(a.compare(b), content="1") // 42 > 24
    >    inspect!(b.compare(a), content="-1") // 24 < 42
    >    inspect!(a.compare(a), content="0") // 42 = 42
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,571:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for Int64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,571:::fn compare(self : Int64, other : Int64) -> Int
    ```
    > 
    >  Compares two 64-bit integers and returns their relative order.
    > 
    >  Parameters:
    > 
    >  * `self` : The first 64-bit integer to compare.
    >  * `other` : The second 64-bit integer to compare against.
    > 
    >  Returns an integer indicating the relative order:
    > 
    >  * A negative value if `self` is less than `other`
    >  * Zero if `self` equals `other`
    >  * A positive value if `self` is greater than `other`
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int64::compare" {
    >    let a = 42L
    >    let b = 24L
    >    let c = -42L
    >    inspect!(a.compare(b), content="1") // 42 > 24
    >    inspect!(b.compare(a), content="-1") // 24 < 42
    >    inspect!(c.compare(a), content="-1") // -42 < 42
    >    inspect!(a.compare(a), content="0") // 42 = 42
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2175:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for UInt
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,2175:::fn compare(self : UInt, other : UInt) -> Int
    ```
    > 
    >  Compares two unsigned 32-bit integers and returns their relative order.
    > 
    >  Parameters:
    > 
    >  * `self` : The first unsigned integer to compare.
    >  * `other` : The second unsigned integer to compare against.
    > 
    >  Returns an integer indicating the relative order:
    > 
    >  * A negative value if `self` is less than `other`
    >  * Zero if `self` equals `other`
    >  * A positive value if `self` is greater than `other`
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt::compare" {
    >    let a = 42U
    >    let b = 24U
    >    inspect!(a.compare(b), content="1") // 42 > 24
    >    inspect!(b.compare(a), content="-1") // 24 < 42
    >    inspect!(a.compare(a), content="0") // 42 = 42
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1329:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for UInt64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1329:::fn compare(self : UInt64, other : UInt64) -> Int
    ```
    > 
    >  Compares two unsigned 64-bit integers and determines their relative order.
    > 
    >  Parameters:
    > 
    >  * `self` : The first unsigned 64-bit integer to compare.
    >  * `other` : The second unsigned 64-bit integer to compare.
    > 
    >  Returns an integer indicating the relative order:
    > 
    >  * A negative value if `self` is less than `other`
    >  * Zero if `self` equals `other`
    >  * A positive value if `self` is greater than `other`
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt64::compare" {
    >    let a = 42UL
    >    let b = 24UL
    >    inspect!(a.compare(b), content="1") // 42 > 24
    >    inspect!(b.compare(a), content="-1") // 24 < 42
    >    inspect!(a.compare(a), content="0") // 42 = 42
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2816:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for Float
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,2816:::fn compare(self : Float, other : Float) -> Int
    ```
    > 
    >  Compares two 32-bit floating-point numbers and returns their relative order.
    > 
    >  Parameters:
    > 
    >  * `self` : The first floating-point number to compare.
    >  * `other` : The second floating-point number to compare.
    > 
    >  Returns an integer indicating the relative order:
    > 
    >  * A negative value if `self` is less than `other`
    >  * Zero if `self` equals `other`
    >  * A positive value if `self` is greater than `other`
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Float::compare" {
    >    let a = 3.14
    >    let b = 2.718
    >    inspect!(a.compare(b), content="1") // 3.14 > 2.718
    >    inspect!(b.compare(a), content="-1") // 2.718 < 3.14
    >    inspect!(a.compare(a), content="0") // 3.14 = 3.14
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1142:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for Double
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,1142:::fn compare(self : Double, other : Double) -> Int
    ```
    > 
    >  Compares two double-precision floating-point numbers and returns their
    > relative order. Follows IEEE 754 rules for floating-point comparisons,
    > including handling of special values like NaN.
    > 
    >  Parameters:
    > 
    >  * `self` : The first double-precision floating-point number to compare.
    >  * `other` : The second double-precision floating-point number to compare
    >    against.
    > 
    >  Returns an integer indicating the relative order:
    > 
    >  * A negative value if `self` is less than `other`
    >  * Zero if `self` equals `other`
    >  * A positive value if `self` is greater than `other`
    >  * If either value is NaN, returns an implementation-defined value that is
    >    consistent with total ordering
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Double::compare" {
    >    let a = 3.14
    >    let b = 2.718
    >    inspect!(a.compare(b), content="1") // 3.14 > 2.718
    >    inspect!(b.compare(a), content="-1") // 2.718 < 3.14
    >    inspect!(a.compare(a), content="0") // 3.14 = 3.14
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/bytes.mbt,401:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for Bytes
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/bytes.mbt,401:::fn compare(self : Bytes, other : Bytes) -> Int
    ```
    > 
    >  Compares two byte sequences lexicographically. First compares the lengths of
    > the sequences, then compares bytes pairwise until a difference is found or
    > all bytes have been compared.
    > 
    >  Parameters:
    > 
    >  * `self` : The first byte sequence to compare.
    >  * `other` : The second byte sequence to compare.
    > 
    >  Returns an integer indicating the relative order:
    > 
    >  * A negative value if `self` is less than `other`
    >  * Zero if `self` equals `other`
    >  * A positive value if `self` is greater than `other`
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Bytes::compare" {
    >    let a = b"\x01\x02\x03"
    >    let b = b"\x01\x02\x04"
    >    inspect!(a.compare(b), content="-1") // a < b
    >    inspect!(b.compare(a), content="1") // b > a
    >    inspect!(a.compare(a), content="0") // a = a
    >  }
    >  
    >  test "Bytes::compare/different_lengths" {
    >    let a = b"\x01\x02"
    >    let b = b"\x01\x02\x03"
    >    inspect!(a.compare(b), content="-1") // shorter sequence is less
    >    inspect!(b.compare(a), content="1") // longer sequence is greater
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_compare.mbt,16:::impl[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for (T0, T1)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_compare.mbt,16:::fn compare[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1), other : (T0, T1)) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_compare.mbt,26:::impl[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for (T0, T1, T2)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_compare.mbt,26:::fn compare[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2), other : (T0, T1, T2)) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_compare.mbt,38:::impl[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for (T0, T1, T2, T3)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_compare.mbt,43:::fn compare[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3), other : (T0, T1, T2, T3)) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_compare.mbt,54:::impl[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for (T0, T1, T2, T3, T4)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_compare.mbt,60:::fn compare[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4), other : (T0, T1, T2, T3, T4)) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_compare.mbt,73:::impl[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for (T0, T1, T2, T3, T4, T5)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_compare.mbt,80:::fn compare[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5), other : (T0, T1, T2, T3, T4, T5)) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_compare.mbt,98:::impl[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for (T0, T1, T2, T3, T4, T5, T6)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_compare.mbt,106:::fn compare[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6), other : (T0, T1, T2, T3, T4, T5, T6)) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_compare.mbt,126:::impl[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for (T0, T1, T2, T3, T4, T5, T6, T7)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_compare.mbt,135:::fn compare[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7), other : (T0, T1, T2, T3, T4, T5, T6, T7)) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_compare.mbt,157:::impl[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_compare.mbt,167:::fn compare[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8), other : (T0, T1, T2, T3, T4, T5, T6, T7, T8)) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_compare.mbt,191:::impl[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_compare.mbt,202:::fn compare[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9), other : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9)) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_compare.mbt,228:::impl[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_compare.mbt,240:::fn compare[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10), other : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10)) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_compare.mbt,268:::impl[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_compare.mbt,281:::fn compare[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11), other : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11)) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_compare.mbt,311:::impl[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T12 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_compare.mbt,325:::fn compare[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T12 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12), other : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12)) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_compare.mbt,357:::impl[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T12 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T13 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_compare.mbt,372:::fn compare[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T12 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T13 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13), other : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13)) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_compare.mbt,406:::impl[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T12 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T13 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T14 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13, T14)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_compare.mbt,422:::fn compare[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T12 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T13 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T14 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13, T14), other : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13, T14)) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_compare.mbt,458:::impl[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T12 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T13 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T14 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T15 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13, T14, T15)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_compare.mbt,475:::fn compare[T0 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T12 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T13 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T14 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, T15 : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13, T14, T15), other : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13, T14, T15)) -> Int
    ```
    > 

## Default

```moonbit
:::source,moonbitlang/core/builtin/traits.mbt,46:::pub(open) trait Default {
  default() -> Self
}
```

 Trait for types with a default value

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,210:::impl <a href="moonbitlang/core/builtin#Default">Default</a> for Bool
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,210:::fn default() -> Bool
    ```
    > 
    >  Returns the default value for the `Bool` type, which is `false`.
    > 
    >  Returns a `Bool` value that represents the default state of a boolean value.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Bool::default" {
    >    let b : Bool = Bool::default()
    >    inspect!(b, content="false")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/byte.mbt,221:::impl <a href="moonbitlang/core/builtin#Default">Default</a> for Byte
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/byte.mbt,221:::fn default() -> Byte
    ```
    > 
    >  Returns the default value for a `Byte`, which is `b'\x00'`.
    > 
    >  Parameters:
    > 
    >  - None
    > 
    >  Returns the default `Byte` value, which is `b'\x00'`.
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1303:::impl <a href="moonbitlang/core/builtin#Default">Default</a> for Char
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,1303:::fn default() -> Char
    ```
    > 
    >  Returns the default value for the `Char` type, which is the null character
    > (`'\x00'`).
    > 
    >  Returns a `Char` value representing the null character.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Char::default" {
    >    assert_true!(Char::default().to_string() == "\x00")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,796:::impl <a href="moonbitlang/core/builtin#Default">Default</a> for Int
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,796:::fn default() -> Int
    ```
    > 
    >  Returns the default value for integers, which is 0.
    > 
    >  Returns an integer value of 0.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int::default" {
    >    let x : Int = Int::default()
    >    inspect!(x, content="0")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,585:::impl <a href="moonbitlang/core/builtin#Default">Default</a> for Int64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,585:::fn default() -> Int64
    ```
    > 
    >  Returns the default value for `Int64` type, which is zero (0L).
    > 
    >  Returns a 64-bit signed integer with value 0.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int64::default" {
    >    inspect!(Int64::default(), content="0")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/uint64.mbt,16:::impl <a href="moonbitlang/core/builtin#Default">Default</a> for UInt64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/uint64.mbt,16:::fn default() -> UInt64
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1156:::impl <a href="moonbitlang/core/builtin#Default">Default</a> for Double
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,1156:::fn default() -> Double
    ```
    > 
    >  Returns the default value for double-precision floating-point numbers (0.0).
    > 
    >  Returns a `Double` value initialized to 0.0.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Double::default" {
    >    inspect!(Double::default(), content="0")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/fixedarray.mbt,100:::impl[X] <a href="moonbitlang/core/builtin#Default">Default</a> for <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/fixedarray.mbt,100:::fn default[X]() -> <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[X]
    ```
    > 
    >  Returns an empty fixed-size array of the specified type.
    > 
    >  Parameters:
    > 
    >  * `X` : The type parameter specifying the element type of the array.
    > 
    >  Returns an empty fixed-size array of type `FixedArray[X]`.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "FixedArray::default" {
    >    let arr : FixedArray[Int] = FixedArray::default()
    >    inspect!(arr.length(), content="0")
    >    inspect!(arr.is_empty(), content="true")
    >  }
    >  ```

## Div

```moonbit
:::source,moonbitlang/core/builtin/operators.mbt,35:::pub(open) trait Div {
  op_div(Self, Self) -> Self
}
```

 types implementing this trait can use the `/` operator

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/byte.mbt,68:::impl <a href="moonbitlang/core/builtin#Div">Div</a> for Byte
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/byte.mbt,68:::fn op_div(self : Byte, that : Byte) -> Byte
    ```
    > 
    >  Performs division operation between two bytes by converting them to integers,
    > performing the division, and converting the result back to a byte.
    > 
    >  Parameters:
    > 
    >  * `self` : The dividend byte value.
    >  * `that` : The divisor byte value.
    > 
    >  Returns the quotient of the division as a byte.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Byte::op_div" {
    >    let a = b'\xFF' // 255
    >    let b = b'\x03' // 3
    >    inspect!(a / b, content="b'\\x55'") // 255 / 3 = 85 (0x55)
    >  }
    >  
    >  test "panic Byte::op_div/division_by_zero" {
    >    let a = b'\x01'
    >    let b = b'\x00'
    >    ignore(a / b) // Division by zero
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,338:::impl <a href="moonbitlang/core/builtin#Div">Div</a> for Int
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,338:::fn op_div(self : Int, other : Int) -> Int
    ```
    > 
    >  Performs integer division between two 32-bit integers. The result is
    > truncated towards zero (rounds down for positive numbers and up for negative
    > numbers).
    > 
    >  Parameters:
    > 
    >  * `dividend` : The first integer operand to be divided.
    >  * `divisor` : The second integer operand that divides the dividend.
    > 
    >  Returns the quotient of the division operation.
    > 
    >  Throws a panic if `divisor` is zero.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int::op_div" {
    >    inspect!(10 / 3, content="3") // truncates towards zero
    >    inspect!(-10 / 3, content="-3")
    >    inspect!(10 / -3, content="-3")
    >  }
    >  
    >  test "panic Int::op_div/division_by_zero" {
    >    ignore(42 / 0) // Panics with division by zero
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,141:::impl <a href="moonbitlang/core/builtin#Div">Div</a> for Int64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,141:::fn op_div(self : Int64, other : Int64) -> Int64
    ```
    > 
    >  Performs integer division between two 64-bit integers. Truncates the result
    > towards zero.
    > 
    >  Parameters:
    > 
    >  * `self` : The dividend (the number to be divided).
    >  * `other` : The divisor (the number to divide by).
    > 
    >  Returns the quotient of the division.
    > 
    >  Throws a panic if `other` is zero.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int64::op_div" {
    >    let a = 42L
    >    let b = 5L
    >    inspect!(a / b, content="8")
    >    let c = -42L
    >    let d = 5L
    >    inspect!(c / d, content="-8")
    >  }
    >  
    >  test "panic Int64::op_div/division_by_zero" {
    >    let a = 42L
    >    ignore(a / 0L) // Division by zero
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2074:::impl <a href="moonbitlang/core/builtin#Div">Div</a> for UInt
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,2074:::fn op_div(self : UInt, other : UInt) -> UInt
    ```
    > 
    >  Performs division between two unsigned 32-bit integers. The operation follows
    > standard unsigned integer division rules, where the result is truncated
    > towards zero.
    > 
    >  Parameters:
    > 
    >  * `self` : The dividend (the number to be divided).
    >  * `other` : The divisor (the number to divide by).
    > 
    >  Returns an unsigned 32-bit integer representing the quotient of the division.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt::op_div" {
    >    let a = 42U
    >    let b = 5U
    >    inspect!(a / b, content="8") // Using infix operator
    >  }
    >  
    >  test "panic UInt::op_div/division_by_zero" {
    >    let a = 42U
    >    ignore(a / 0U) // Throws runtime error: division by zero
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1273:::impl <a href="moonbitlang/core/builtin#Div">Div</a> for UInt64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1273:::fn op_div(self : UInt64, other : UInt64) -> UInt64
    ```
    > 
    >  Performs division operation between two unsigned 64-bit integers.
    > 
    >  Parameters:
    > 
    >  * `self` : The dividend unsigned 64-bit integer.
    >  * `other` : The divisor unsigned 64-bit integer.
    > 
    >  Returns the quotient of dividing the dividend by the divisor.
    > 
    >  Throws a runtime error if `other` is zero.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt64::op_div" {
    >    let a = 100UL
    >    let b = 20UL
    >    inspect!(a / b, content="5") // Using infix operator
    >  }
    >  
    >  test "panic UInt64::op_div/division_by_zero" {
    >    let a = 42UL
    >    ignore(a / 0UL) // Throws runtime error: division by zero
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2706:::impl <a href="moonbitlang/core/builtin#Div">Div</a> for Float
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,2706:::fn op_div(self : Float, other : Float) -> Float
    ```
    > 
    >  Performs division between two 32-bit floating-point numbers according to IEEE
    > 754 rules.
    > 
    >  Parameters:
    > 
    >  * `self` : The dividend floating-point number.
    >  * `other` : The divisor floating-point number.
    > 
    >  Returns a new floating-point number representing the quotient of the
    > division. Special cases follow IEEE 754 rules:
    > 
    >  * Division by zero returns infinity (with the appropriate sign)
    >  * Division of zero by zero returns NaN
    >  * Division of infinity by infinity returns NaN
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Float::op_div" {
    >    let a = 6.0.to_float()
    >    let b = 2.0.to_float()
    >    let result = (a / b).to_double()
    >    inspect!(result, content="3")
    >    inspect!((0.0.to_float() / 0.0.to_float()).to_double(), content="NaN")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1034:::impl <a href="moonbitlang/core/builtin#Div">Div</a> for Double
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,1034:::fn op_div(self : Double, other : Double) -> Double
    ```
    > 
    >  Performs division between two double-precision floating-point numbers.
    > Follows IEEE 754 standard for floating-point arithmetic, including handling
    > of special cases like division by zero (returns infinity) and operations
    > involving NaN.
    > 
    >  Parameters:
    > 
    >  * `self` : The dividend (numerator) in the division operation.
    >  * `other` : The divisor (denominator) in the division operation.
    > 
    >  Returns the result of dividing `self` by `other`. Special cases follow IEEE
    > 754:
    > 
    >  * Division by zero returns positive or negative infinity based on the
    >    dividend's sign
    >  * Operations involving NaN return NaN
    >  * Division of infinity by infinity returns NaN
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Double::op_div" {
    >    inspect!(6.0 / 2.0, content="3")
    >    inspect!(-6.0 / 2.0, content="-3")
    >    inspect!(1.0 / 0.0, content="Infinity")
    >  }
    >  ```

## Eq

```moonbit
:::source,moonbitlang/core/builtin/traits.mbt,17:::pub(open) trait Eq {
  op_equal(Self, Self) -> Bool
}
```

 Trait for types whose elements can test for equality

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/unit.mbt,16:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for Unit
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/unit.mbt,16:::fn op_equal(self : Unit, _other : Unit) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,135:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for Bool
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,135:::fn op_equal(self : Bool, other : Bool) -> Bool
    ```
    > 
    >  Compares two boolean values for equality.
    > 
    >  Parameters:
    > 
    >  * `self` : The first boolean value to compare.
    >  * `other` : The second boolean value to compare.
    > 
    >  Returns `true` if both boolean values are equal (either both `true` or both
    > `false`), `false` otherwise.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Bool::op_equal" {
    >    inspect!(true == true, content="true")
    >    inspect!(false == true, content="false")
    >    inspect!(true == false, content="false")
    >    inspect!(false == false, content="true")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/byte.mbt,81:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for Byte
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/byte.mbt,81:::fn op_equal(self : Byte, that : Byte) -> Bool
    ```
    > 
    >  Compares two `Byte` values for equality.
    > 
    >  Parameters:
    > 
    >  - `self` : The first `Byte` value to compare.
    >  - `that` : The second `Byte` value to compare.
    > 
    >  Returns `true` if the two `Byte` values are equal, otherwise `false`.
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1260:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for Char
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,1260:::fn op_equal(self : Char, other : Char) -> Bool
    ```
    > 
    >  Compares two characters for equality.
    > 
    >  Parameters:
    > 
    >  * `self` : The first character to compare.
    >  * `other` : The second character to compare.
    > 
    >  Returns `true` if both characters represent the same Unicode code point,
    > `false` otherwise.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Char::op_equal" {
    >    let a = 'A'
    >    let b = 'A'
    >    let c = 'B'
    >    inspect!(a == b, content="true")
    >    inspect!(a == c, content="false")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,722:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for Int
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,722:::fn op_equal(self : Int, other : Int) -> Bool
    ```
    > 
    >  Compares two integers for equality.
    > 
    >  Parameters:
    > 
    >  * `self` : The first integer to compare.
    >  * `other` : The second integer to compare.
    > 
    >  Returns `true` if both integers have the same value, `false` otherwise.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int::op_equal" {
    >    inspect!(42 == 42, content="true")
    >    inspect!(42 == -42, content="false")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,542:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for Int64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,542:::fn op_equal(self : Int64, other : Int64) -> Bool
    ```
    > 
    >  Tests if two 64-bit integers are equal.
    > 
    >  Parameters:
    > 
    >  * `self` : The first 64-bit integer to compare.
    >  * `other` : The second 64-bit integer to compare.
    > 
    >  Returns `true` if both integers are equal, `false` otherwise.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int64::op_equal" {
    >    let a = 42L
    >    let b = 42L
    >    let c = -42L
    >    inspect!(a == b, content="true")
    >    inspect!(a == c, content="false")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2126:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for UInt
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,2126:::fn op_equal(self : UInt, other : UInt) -> Bool
    ```
    > 
    >  Compares two unsigned 32-bit integers for equality.
    > 
    >  Parameters:
    > 
    >  * `self` : The first unsigned integer operand.
    >  * `other` : The second unsigned integer operand to compare with.
    > 
    >  Returns `true` if both integers have the same value, `false` otherwise.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt::op_equal" {
    >    let a = 42U
    >    let b = 42U
    >    let c = 24U
    >    inspect!(a == b, content="true")
    >    inspect!(a == c, content="false")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1352:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for UInt64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1352:::fn op_equal(self : UInt64, other : UInt64) -> Bool
    ```
    > 
    >  Compares two unsigned 64-bit integers for equality.
    > 
    >  Parameters:
    > 
    >  * `self` : The first unsigned 64-bit integer to compare.
    >  * `other` : The second unsigned 64-bit integer to compare.
    > 
    >  Returns `true` if both integers have the same value, `false` otherwise.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt64::op_equal" {
    >    let a = 42UL
    >    let b = 42UL
    >    let c = 24UL
    >    inspect!(a == b, content="true")
    >    inspect!(a == c, content="false")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2762:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for Float
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,2762:::fn op_equal(self : Float, other : Float) -> Bool
    ```
    > 
    >  Tests two floating-point numbers for equality. Follows IEEE 754 equality
    > comparison rules, where NaN values are not equal to any value, including
    > themselves.
    > 
    >  Parameters:
    > 
    >  * `self` : The first floating-point number to compare.
    >  * `other` : The second floating-point number to compare.
    > 
    >  Returns `true` if both numbers are equal, `false` otherwise. Note that `-0.0`
    > and `+0.0` are considered equal.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Float::op_equal" {
    >    let x = 3.14
    >    let y = 3.14
    >    let z = 0.0 / 0.0 // NaN
    >    inspect!(x == y, content="true")
    >    inspect!(z == z, content="false") // NaN is not equal to itself
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1086:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for Double
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,1086:::fn op_equal(self : Double, other : Double) -> Bool
    ```
    > 
    >  Compares two double-precision floating-point numbers for equality following
    > IEEE 754 rules. Returns `true` if both numbers are equal, including when both
    > are `NaN`. Note that this differs from the standard IEEE 754 behavior where
    > `NaN` is not equal to any value, including itself.
    > 
    >  Parameters:
    > 
    >  * `self` : The first double-precision floating-point number to compare.
    >  * `other` : The second double-precision floating-point number to compare.
    > 
    >  Returns `true` if both numbers are equal, `false` otherwise.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Double::op_equal" {
    >    let a = 3.14
    >    let b = 3.14
    >    let c = 2.718
    >    inspect!(a == b, content="true")
    >    inspect!(a == c, content="false")
    >    let nan = 0.0 / 0.0 // NaN
    >    inspect!(nan == nan, content="false") // Note: NaN equals itself in MoonBit
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1859:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for String
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,1859:::fn op_equal(self : String, other : String) -> Bool
    ```
    > 
    >  Tests whether two strings are equal by comparing their characters.
    > 
    >  Parameters:
    > 
    >  * `self` : The first string to compare.
    >  * `other` : The second string to compare.
    > 
    >  Returns `true` if both strings contain exactly the same sequence of
    > characters, `false` otherwise.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "String::op_equal" {
    >    let str1 = "hello"
    >    let str2 = "hello"
    >    let str3 = "world"
    >    inspect!(str1 == str2, content="true")
    >    inspect!(str1 == str3, content="false")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/option.mbt,16:::impl[X : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for X?
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/option.mbt,16:::fn op_equal[X : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : X?, other : X?) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/result.mbt,16:::impl[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>, E : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/result#Result">Result</a>[T, E]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/result.mbt,16:::fn op_equal[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>, E : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E], other : <a href="moonbitlang/core/result#Result">Result</a>[T, E]) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/bytes.mbt,352:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for Bytes
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/bytes.mbt,352:::fn op_equal(self : Bytes, other : Bytes) -> Bool
    ```
    > 
    >  Compares two byte sequences for equality. Returns true only if both sequences
    > have the same length and contain identical bytes in the same order.
    > 
    >  Parameters:
    > 
    >  * `self` : The first byte sequence to compare.
    >  * `other` : The second byte sequence to compare.
    > 
    >  Returns `true` if the byte sequences are equal, `false` otherwise.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Bytes::op_equal" {
    >    let bytes1 = b"\x01\x02\x03"
    >    let bytes2 = b"\x01\x02\x03"
    >    let bytes3 = b"\x01\x02\x04"
    >    inspect!(bytes1 == bytes2, content="true")
    >    inspect!(bytes1 == bytes3, content="false")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_eq.mbt,16:::impl[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for (T0, T1)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_eq.mbt,16:::fn op_equal[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1), other : (T0, T1)) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_eq.mbt,24:::impl[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for (T0, T1, T2)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_eq.mbt,24:::fn op_equal[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2), other : (T0, T1, T2)) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_eq.mbt,32:::impl[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for (T0, T1, T2, T3)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_eq.mbt,32:::fn op_equal[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3), other : (T0, T1, T2, T3)) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_eq.mbt,43:::impl[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for (T0, T1, T2, T3, T4)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_eq.mbt,49:::fn op_equal[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4), other : (T0, T1, T2, T3, T4)) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_eq.mbt,58:::impl[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for (T0, T1, T2, T3, T4, T5)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_eq.mbt,65:::fn op_equal[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5), other : (T0, T1, T2, T3, T4, T5)) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_eq.mbt,78:::impl[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for (T0, T1, T2, T3, T4, T5, T6)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_eq.mbt,86:::fn op_equal[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6), other : (T0, T1, T2, T3, T4, T5, T6)) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_eq.mbt,100:::impl[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for (T0, T1, T2, T3, T4, T5, T6, T7)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_eq.mbt,109:::fn op_equal[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7), other : (T0, T1, T2, T3, T4, T5, T6, T7)) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_eq.mbt,124:::impl[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_eq.mbt,134:::fn op_equal[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8), other : (T0, T1, T2, T3, T4, T5, T6, T7, T8)) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_eq.mbt,150:::impl[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_eq.mbt,161:::fn op_equal[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9), other : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9)) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_eq.mbt,178:::impl[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_eq.mbt,190:::fn op_equal[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10), other : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10)) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_eq.mbt,208:::impl[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_eq.mbt,221:::fn op_equal[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11), other : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11)) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_eq.mbt,240:::impl[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T12 : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_eq.mbt,254:::fn op_equal[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T12 : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12), other : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12)) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_eq.mbt,274:::impl[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T12 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T13 : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_eq.mbt,289:::fn op_equal[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T12 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T13 : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13), other : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13)) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_eq.mbt,310:::impl[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T12 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T13 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T14 : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13, T14)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_eq.mbt,326:::fn op_equal[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T12 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T13 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T14 : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13, T14), other : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13, T14)) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_eq.mbt,348:::impl[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T12 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T13 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T14 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T15 : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13, T14, T15)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_eq.mbt,365:::fn op_equal[T0 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T1 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T2 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T3 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T4 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T5 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T6 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T7 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T8 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T9 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T10 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T11 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T12 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T13 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T14 : <a href="moonbitlang/core/builtin#Eq">Eq</a>, T15 : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13, T14, T15), other : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13, T14, T15)) -> Bool
    ```
    > 

## Hash

```moonbit
:::source,moonbitlang/core/builtin/traits.mbt,34:::pub(open) trait Hash {
  hash_combine(Self, <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
  hash(Self) -> Int = _
}
```

 Trait for types that can be hashed

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/byte.mbt,186:::impl <a href="moonbitlang/core/builtin#Hash">Hash</a> for Byte
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/byte.mbt,186:::fn hash(self : Byte) -> Int
    ```
    > 
    >  Implements the `Hash` trait for `Byte` type by converting the byte to an
    > integer and using it as the hash value.
    > 
    >  Parameters:
    > 
    >  * `self` : The byte value to be hashed.
    > 
    >  Returns an integer representing the hash value of the byte.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Byte::hash" {
    >    let b = b'\x42'
    >    inspect!(Hash::hash(b), content="66") // ASCII value of 'B'
    >  }
    >  ```
  * ```moonbit
    :::source,moonbitlang/core/builtin/byte.mbt,209:::fn hash_combine(self : Byte, hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
    >  Implements the `Hash` trait for `Byte` type by providing a `hash_combine`
    > method that combines a byte value with a hasher.
    > 
    >  Parameters:
    > 
    >  * `self` : The byte value to be hashed.
    >  * `hasher` : The hasher object that will be used to combine the byte value
    >    into its internal state.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Byte::hash_combine" {
    >    let hasher = Hasher::new()
    >    hasher.combine_byte(b'\xFF')
    >    inspect!(hasher.finalize(), content="1955036104")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,510:::impl <a href="moonbitlang/core/builtin#Hash">Hash</a> for Int
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/hasher.mbt,510:::fn hash(self : Int) -> Int
    ```
    > 
    >  Implements the `Hash` trait for integer values using a combination of shifts
    > and multiplications to produce a well-distributed hash value. Based on the
    > hash algorithm from hash-prospector
    > (https://github.com/skeeto/hash-prospector).
    > 
    >  Parameters:
    > 
    >  * `integer` : The integer value to be hashed. The value will be reinterpreted
    >    as an unsigned integer before hashing to ensure consistent behavior across
    >    positive and negative values.
    > 
    >  Returns a 32-bit hash value derived from the input integer.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int::hash" {
    >    let x = 42
    >    inspect!(Hash::hash(x), content="-1704501356")
    >    let y = -42
    >    inspect!(Hash::hash(y), content="1617647962")
    >  }
    >  ```
    >  TODO: This implementation is **different** from the default implementation of the hash trait.
    > So it will be replaced with the default implementation in the future **(breaking change)**,
    > and users should not rely on this particular hash value
    >  ```moonbit
    >  test {
    >    let x = 42
    >    assert_not_eq!(Hash::hash(x),Hasher::new()..combine(x).finalize())
    >  }
    >  ```
  * ```moonbit
    :::source,moonbitlang/core/builtin/hasher.mbt,541:::fn hash_combine(self : Int, hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
    >  Implements hash combination for integers by combining the integer value with
    > a hasher. This implementation ensures that integers can be used as keys in
    > hash-based collections like hash maps and hash sets.
    > 
    >  Parameters:
    > 
    >  * `self` : The integer value to be hashed.
    >  * `hasher` : A `Hasher` object that accumulates the hash value.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int::hash_combine" {
    >    let hasher = Hasher::new()
    >    hasher.combine_int(42)
    >    inspect!(hasher.finalize(), content="1161967057")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,565:::impl <a href="moonbitlang/core/builtin#Hash">Hash</a> for UInt
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/hasher.mbt,565:::fn hash_combine(self : UInt, hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
    >  Combines the hash value of an unsigned integer with a hasher object. This is
    > useful when you need to hash a data structure that contains unsigned
    > integers.
    > 
    >  Parameters:
    > 
    >  * `value` : The unsigned integer to be combined with the hasher.
    >  * `hasher` : The hasher object that will incorporate the hash value of the
    >    unsigned integer.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt::hash_combine" {
    >    let hasher = Hasher::new()
    >    hasher.combine_uint(42U)
    >    inspect!(hasher.finalize(), content="1161967057")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,587:::impl <a href="moonbitlang/core/builtin#Hash">Hash</a> for UInt64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/hasher.mbt,587:::fn hash_combine(self : UInt64, hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
    >  Implements the `Hash` trait for `UInt64` by combining the hash value of an
    > unsigned 64-bit integer into a hasher.
    > 
    >  Parameters:
    > 
    >  * `self` : The unsigned 64-bit integer value to be hashed.
    >  * `hasher` : The hasher object used to compute the combined hash value.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt64::hash_combine" {
    >    let hasher = Hasher::new()
    >    hasher.combine_uint64(42UL)
    >    inspect!(hasher.finalize(), content="-1962516083")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,473:::impl <a href="moonbitlang/core/builtin#Hash">Hash</a> for String
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/hasher.mbt,473:::fn hash_combine(self : String, hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
    >  Implements the `Hash` trait for `String` type, providing a method to combine
    > a string's hash value with a hasher's state.
    > 
    >  Parameters:
    > 
    >  * `self` : The string value to be hashed.
    >  * `hasher` : The hasher object that will be updated with the string's hash
    >    value.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "String::hash" {
    >    let s1 = "hello"
    >    let s2 = "hello"
    >    let s3 = "world"
    >    inspect!(Hash::hash(s1) == Hash::hash(s2), content="true")
    >    inspect!(Hash::hash(s1) == Hash::hash(s3), content="false")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,614:::impl[X : <a href="moonbitlang/core/builtin#Hash">Hash</a>] <a href="moonbitlang/core/builtin#Hash">Hash</a> for X?
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/hasher.mbt,614:::fn hash_combine[X : <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : X?, hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
    >  Implements the `Hash` trait for `Option` types, allowing them to be used as
    > keys in hash-based collections.
    > 
    >  Parameters:
    > 
    >  * `self` : The `Option` value to be hashed.
    >  * `hasher` : The hasher object that accumulates the hash state.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Option::hash_combine" {
    >    let hasher = Hasher::new()
    >    let some_value : Int? = Some(42)
    >    let none_value : Int? = None
    >    hasher.combine(some_value)
    >    inspect!(hasher.finalize(), content="2103260413")
    >    let hasher2 = Hasher::new()
    >    hasher2.combine(none_value)
    >    inspect!(hasher2.finalize(), content="148298089")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,644:::impl[T : <a href="moonbitlang/core/builtin#Hash">Hash</a>, E : <a href="moonbitlang/core/builtin#Hash">Hash</a>] <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="moonbitlang/core/result#Result">Result</a>[T, E]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/hasher.mbt,644:::fn hash_combine[T : <a href="moonbitlang/core/builtin#Hash">Hash</a>, E : <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E], hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
    >  Implements the `Hash` trait for `Result` type, allowing `Result` values to be
    > used in hash-based collections.
    > 
    >  Parameters:
    > 
    >  * `self` : The `Result` value to be hashed.
    >  * `hasher` : The hasher object to which the hash value will be combined.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Result::hash_combine" {
    >    let hasher = Hasher::new()
    >    let ok_result : Result[Int, String] = Ok(42)
    >    let err_result : Result[Int, String] = Err("error")
    >    hasher.combine(ok_result)
    >    inspect!(hasher.finalize(), content="-1948635851")
    >    let hasher = Hasher::new()
    >    hasher.combine(err_result)
    >    inspect!(hasher.finalize(), content="1953766574")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_hash.mbt,16:::impl[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>, B : <a href="moonbitlang/core/builtin#Hash">Hash</a>] <a href="moonbitlang/core/builtin#Hash">Hash</a> for (A, B)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_hash.mbt,16:::fn hash_combine[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>, B : <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : (A, B), hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_hash.mbt,22:::impl[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>, B : <a href="moonbitlang/core/builtin#Hash">Hash</a>, C : <a href="moonbitlang/core/builtin#Hash">Hash</a>] <a href="moonbitlang/core/builtin#Hash">Hash</a> for (A, B, C)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_hash.mbt,22:::fn hash_combine[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>, B : <a href="moonbitlang/core/builtin#Hash">Hash</a>, C : <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : (A, B, C), hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_hash.mbt,31:::impl[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>, B : <a href="moonbitlang/core/builtin#Hash">Hash</a>, C : <a href="moonbitlang/core/builtin#Hash">Hash</a>, D : <a href="moonbitlang/core/builtin#Hash">Hash</a>] <a href="moonbitlang/core/builtin#Hash">Hash</a> for (A, B, C, D)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_hash.mbt,31:::fn hash_combine[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>, B : <a href="moonbitlang/core/builtin#Hash">Hash</a>, C : <a href="moonbitlang/core/builtin#Hash">Hash</a>, D : <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : (A, B, C, D), hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_hash.mbt,40:::impl[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>, B : <a href="moonbitlang/core/builtin#Hash">Hash</a>, C : <a href="moonbitlang/core/builtin#Hash">Hash</a>, D : <a href="moonbitlang/core/builtin#Hash">Hash</a>, E : <a href="moonbitlang/core/builtin#Hash">Hash</a>] <a href="moonbitlang/core/builtin#Hash">Hash</a> for (A, B, C, D, E)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_hash.mbt,46:::fn hash_combine[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>, B : <a href="moonbitlang/core/builtin#Hash">Hash</a>, C : <a href="moonbitlang/core/builtin#Hash">Hash</a>, D : <a href="moonbitlang/core/builtin#Hash">Hash</a>, E : <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : (A, B, C, D, E), hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_hash.mbt,52:::impl[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>, B : <a href="moonbitlang/core/builtin#Hash">Hash</a>, C : <a href="moonbitlang/core/builtin#Hash">Hash</a>, D : <a href="moonbitlang/core/builtin#Hash">Hash</a>, E : <a href="moonbitlang/core/builtin#Hash">Hash</a>, F : <a href="moonbitlang/core/builtin#Hash">Hash</a>] <a href="moonbitlang/core/builtin#Hash">Hash</a> for (A, B, C, D, E, F)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_hash.mbt,59:::fn hash_combine[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>, B : <a href="moonbitlang/core/builtin#Hash">Hash</a>, C : <a href="moonbitlang/core/builtin#Hash">Hash</a>, D : <a href="moonbitlang/core/builtin#Hash">Hash</a>, E : <a href="moonbitlang/core/builtin#Hash">Hash</a>, F : <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : (A, B, C, D, E, F), hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_hash.mbt,65:::impl[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>, B : <a href="moonbitlang/core/builtin#Hash">Hash</a>, C : <a href="moonbitlang/core/builtin#Hash">Hash</a>, D : <a href="moonbitlang/core/builtin#Hash">Hash</a>, E : <a href="moonbitlang/core/builtin#Hash">Hash</a>, F : <a href="moonbitlang/core/builtin#Hash">Hash</a>, G : <a href="moonbitlang/core/builtin#Hash">Hash</a>] <a href="moonbitlang/core/builtin#Hash">Hash</a> for (A, B, C, D, E, F, G)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_hash.mbt,73:::fn hash_combine[A : <a href="moonbitlang/core/builtin#Hash">Hash</a>, B : <a href="moonbitlang/core/builtin#Hash">Hash</a>, C : <a href="moonbitlang/core/builtin#Hash">Hash</a>, D : <a href="moonbitlang/core/builtin#Hash">Hash</a>, E : <a href="moonbitlang/core/builtin#Hash">Hash</a>, F : <a href="moonbitlang/core/builtin#Hash">Hash</a>, G : <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : (A, B, C, D, E, F, G), hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 

## Logger

```moonbit
:::source,moonbitlang/core/builtin/traits.mbt,52:::pub(open) trait Logger {
  write_string(Self, String) -> Unit
  write_substring(Self, String, Int, Int) -> Unit
  write_char(Self, Char) -> Unit = _
}
```

 Trait for a logger, where debug logs can be written into

## Mod

```moonbit
:::source,moonbitlang/core/builtin/operators.mbt,47:::pub(open) trait Mod {
  op_mod(Self, Self) -> Self
}
```

 types implementing this trait can use the `%` operator

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,366:::impl <a href="moonbitlang/core/builtin#Mod">Mod</a> for Int
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,366:::fn op_mod(self : Int, other : Int) -> Int
    ```
    > 
    >  Calculates the remainder of dividing one integer by another. The result
    > follows the formula `dividend - (dividend / divisor) * divisor`, maintaining
    > the same sign as the dividend.
    > 
    >  Parameters:
    > 
    >  * `self` : The dividend (the number being divided).
    >  * `other` : The divisor (the number to divide by).
    > 
    >  Returns the remainder of the division. If `other` is 0, the behavior is
    > undefined.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int::op_mod" {
    >    inspect!(7 % 3, content="1")
    >    inspect!(-7 % 3, content="-1")
    >    inspect!(7 % -3, content="1")
    >  }
    >  
    >  test "panic Int::op_mod/division_by_zero" {
    >    ignore(7 % 0) // Panics with division by zero
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,170:::impl <a href="moonbitlang/core/builtin#Mod">Mod</a> for Int64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,170:::fn op_mod(self : Int64, other : Int64) -> Int64
    ```
    > 
    >  Calculates the remainder of the division between two 64-bit integers. The
    > result follows the formula `self - (self / other) * other`, maintaining the
    > same sign as the dividend.
    > 
    >  Parameters:
    > 
    >  * `self` : The dividend 64-bit integer.
    >  * `other` : The divisor 64-bit integer.
    > 
    >  Returns the remainder of the division.
    > 
    >  Throws a panic if `other` is zero.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int64::op_mod" {
    >    inspect!(7L % 3L, content="1")
    >    inspect!(-7L % 3L, content="-1")
    >    inspect!(7L % -3L, content="1")
    >  }
    >  
    >  test "panic Int64::op_mod/division_by_zero" {
    >    ignore(7L % 0L) // Panics with division by zero
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2103:::impl <a href="moonbitlang/core/builtin#Mod">Mod</a> for UInt
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,2103:::fn op_mod(self : UInt, other : UInt) -> UInt
    ```
    > 
    >  Calculates the remainder of dividing one unsigned integer by another.
    > 
    >  Parameters:
    > 
    >  * `self` : The unsigned integer dividend.
    >  * `other` : The unsigned integer divisor.
    > 
    >  Returns the remainder of the division operation.
    > 
    >  Throws a panic if `other` is zero.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt::op_mod" {
    >    let a = 17U
    >    let b = 5U
    >    inspect!(a % b, content="2") // 17 divided by 5 gives quotient 3 and remainder 2
    >    inspect!(7U % 4U, content="3")
    >  }
    >  
    >  test "panic UInt::op_mod/division_by_zero" {
    >    let a = 42U
    >    ignore(a % 0U) // Panics: division by zero
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1302:::impl <a href="moonbitlang/core/builtin#Mod">Mod</a> for UInt64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1302:::fn op_mod(self : UInt64, other : UInt64) -> UInt64
    ```
    > 
    >  Calculates the remainder of dividing one unsigned 64-bit integer by another.
    > 
    >  Parameters:
    > 
    >  * `self` : The dividend unsigned 64-bit integer.
    >  * `other` : The divisor unsigned 64-bit integer.
    > 
    >  Returns the remainder of the division operation.
    > 
    >  Throws a panic if the divisor is zero.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt64::op_mod" {
    >    let a = 17UL
    >    let b = 5UL
    >    inspect!(a % b, content="2") // 17 divided by 5 gives quotient 3 and remainder 2
    >    inspect!(7UL % 4UL, content="3")
    >  }
    >  
    >  test "panic UInt64::op_mod/division_by_zero" {
    >    let a = 42UL
    >    ignore(a % 0UL) // Panics: division by zero
    >  }
    >  ```

## Mul

```moonbit
:::source,moonbitlang/core/builtin/operators.mbt,29:::pub(open) trait Mul {
  op_mul(Self, Self) -> Self
}
```

 types implementing this trait can use the `*` operator

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/byte.mbt,38:::impl <a href="moonbitlang/core/builtin#Mul">Mul</a> for Byte
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/byte.mbt,38:::fn op_mul(self : Byte, that : Byte) -> Byte
    ```
    > 
    >  Performs multiplication between two byte values. The result is truncated to
    > fit within the byte range.
    > 
    >  Parameters:
    > 
    >  * `self` : The first byte operand in the multiplication.
    >  * `that` : The second byte operand in the multiplication.
    > 
    >  Returns the product of the two bytes, truncated to fit within the byte range
    > (0-255).
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Byte::op_mul" {
    >    let a = b'\x02'
    >    let b = b'\x03'
    >    inspect!(a * b, content="b'\\x06'") // 2 * 3 = 6
    >    let c = b'\xFF'
    >    inspect!(c * c, content="b'\\x01'") // 255 * 255 = 65025, truncated to 1
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,309:::impl <a href="moonbitlang/core/builtin#Mul">Mul</a> for Int
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,309:::fn op_mul(self : Int, other : Int) -> Int
    ```
    > 
    >  Multiplies two 32-bit integers. This is the implementation of the `*`
    > operator for `Int`.
    > 
    >  Parameters:
    > 
    >  * `self` : The first integer operand.
    >  * `other` : The second integer operand.
    > 
    >  Returns the product of the two integers. If the result overflows the range of
    > `Int`, it wraps around according to two's complement arithmetic.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int::op_mul" {
    >    inspect!(42 * 2, content="84")
    >    inspect!(-10 * 3, content="-30")
    >    let max = 2147483647 // Int.max_value
    >    inspect!(max * 2, content="-2") // Overflow wraps around
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,109:::impl <a href="moonbitlang/core/builtin#Mul">Mul</a> for Int64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,109:::fn op_mul(self : Int64, other : Int64) -> Int64
    ```
    > 
    >  Multiplies two 64-bit integers.
    > 
    >  Parameters:
    > 
    >  * `self` : The first 64-bit integer operand.
    >  * `other` : The second 64-bit integer operand.
    > 
    >  Returns the product of the two 64-bit integers. If the result overflows the
    > range of `Int64`, it will be truncated according to two's complement
    > arithmetic.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int64::op_mul" {
    >    let a = 42L
    >    let b = 100L
    >    inspect!(a * b, content="4200")
    >    let c = -42L
    >    inspect!(c * b, content="-4200")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2046:::impl <a href="moonbitlang/core/builtin#Mul">Mul</a> for UInt
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,2046:::fn op_mul(self : UInt, other : UInt) -> UInt
    ```
    > 
    >  Performs multiplication between two unsigned 32-bit integers. The result
    > wraps around if it exceeds the maximum value of `UInt`.
    > 
    >  Parameters:
    > 
    >  * `self` : The first unsigned integer operand.
    >  * `other` : The second unsigned integer operand.
    > 
    >  Returns the product of the two unsigned integers. If the result exceeds the
    > maximum value of `UInt` (4294967295), it wraps around to the corresponding
    > value modulo 2^32.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt::op_mul" {
    >    let a = 3U
    >    let b = 4U
    >    inspect!(a * b, content="12")
    >    let max = 4294967295U
    >    inspect!(max * 2U, content="4294967294") // Wraps around to max * 2 % 2^32
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1245:::impl <a href="moonbitlang/core/builtin#Mul">Mul</a> for UInt64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1245:::fn op_mul(self : UInt64, other : UInt64) -> UInt64
    ```
    > 
    >  Performs multiplication between two unsigned 64-bit integers.
    > 
    >  Parameters:
    > 
    >  * `self` : The first unsigned 64-bit integer operand.
    >  * `other` : The second unsigned 64-bit integer operand.
    > 
    >  Returns the product of the two unsigned 64-bit integers. The result wraps
    > around if it exceeds the maximum value of `UInt64`.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt64::op_mul" {
    >    let a = 2UL
    >    let b = 3UL
    >    inspect!(a * b, content="6")
    >  
    >    // Demonstrate wrapping behavior
    >    let max = 18446744073709551615UL
    >    inspect!(max * 2UL, content="18446744073709551614") // Wraps around to max - 1
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2677:::impl <a href="moonbitlang/core/builtin#Mul">Mul</a> for Float
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,2677:::fn op_mul(self : Float, other : Float) -> Float
    ```
    > 
    >  Performs multiplication between two single-precision floating-point numbers
    > according to IEEE 754 rules.
    > 
    >  Parameters:
    > 
    >  * `self` : The first floating-point number operand.
    >  * `other` : The second floating-point number operand to multiply with the
    >    first.
    > 
    >  Returns a single-precision floating-point number that is the product of the
    > two operands.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Float::op_mul" {
    >    let x = Int::to_float(2)
    >    let y = Int::to_float(3)
    >    let z = x * y
    >    inspect!(z.to_double(), content="6")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1004:::impl <a href="moonbitlang/core/builtin#Mul">Mul</a> for Double
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,1004:::fn op_mul(self : Double, other : Double) -> Double
    ```
    > 
    >  Multiplies two double-precision floating-point numbers. This is the
    > implementation of the `*` operator for `Double` type.
    > 
    >  Parameters:
    > 
    >  * `self` : The first double-precision floating-point operand.
    >  * `other` : The second double-precision floating-point operand.
    > 
    >  Returns a new double-precision floating-point number representing the product
    > of the two operands. Special cases follow IEEE 754 standard:
    > 
    >  * If either operand is NaN, returns NaN
    >  * If one operand is infinity and the other is zero, returns NaN
    >  * If one operand is infinity and the other is a non-zero finite number,
    >    returns infinity with the appropriate sign
    >  * If both operands are infinity, returns infinity with the appropriate sign
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Double::op_mul" {
    >    inspect!(2.5 * 2.0, content="5")
    >    inspect!(-2.0 * 3.0, content="-6")
    >    let nan = 0.0 / 0.0 // NaN
    >    inspect!(nan * 1.0, content="NaN")
    >  }
    >  ```

## Neg

```moonbit
:::source,moonbitlang/core/builtin/operators.mbt,41:::pub(open) trait Neg {
  op_neg(Self) -> Self
}
```

 types implementing this trait can use the unary `-` operator

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,236:::impl <a href="moonbitlang/core/builtin#Neg">Neg</a> for Int
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,236:::fn op_neg(self : Int) -> Int
    ```
    > 
    >  Performs arithmetic negation on an integer value, returning its additive
    > inverse.
    > 
    >  Parameters:
    > 
    >  * `self` : The integer value to negate.
    > 
    >  Returns the negation of the input value. For all inputs except
    > `Int::min_value()`, returns the value with opposite sign. When the input is
    > `Int::min_value()`, returns `Int::min_value()` due to two's complement
    > representation.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int::op_neg" {
    >    inspect!(-42, content="-42")
    >    inspect!(42, content="42")
    >    inspect!(--2147483647, content="2147483647") // negating near min value
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,37:::impl <a href="moonbitlang/core/builtin#Neg">Neg</a> for Int64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,37:::fn op_neg(self : Int64) -> Int64
    ```
    > 
    >  Performs unary negation on a 64-bit signed integer, returning its arithmetic
    > inverse.
    > 
    >  Parameters:
    > 
    >  * `value` : The 64-bit signed integer to negate.
    > 
    >  Returns the arithmetic negation of the input value. For all inputs except
    > `Int64::min_value()`, returns the value with opposite sign. When the input is
    > `Int64::min_value()`, returns `Int64::min_value()` due to two's complement
    > representation.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int64::op_neg" {
    >    inspect!(-42L, content="-42")
    >    inspect!(--42L, content="42")
    >    inspect!(-9223372036854775808L, content="-9223372036854775808") // negating min value
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2605:::impl <a href="moonbitlang/core/builtin#Neg">Neg</a> for Float
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,2605:::fn op_neg(self : Float) -> Float
    ```
    > 
    >  Performs unary negation on a 32-bit floating-point number. Returns the
    > arithmetic inverse of the operand.
    > 
    >  Parameters:
    > 
    >  * `self` : The floating-point number to negate.
    > 
    >  Returns a new floating-point number with the same magnitude but opposite sign
    > as the input. Special cases:
    > 
    >  * Negating NaN returns NaN
    >  * Negating +0.0 returns -0.0
    >  * Negating -0.0 returns +0.0
    >  * Negating +Infinity returns -Infinity
    >  * Negating -Infinity returns +Infinity
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Float::op_neg" {
    >    let f = 3.14.to_float()
    >    inspect!((-f).to_double(), content="-3.140000104904175")
    >    let zero = 0.0.to_float()
    >    inspect!((-zero).to_double(), content="0")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,925:::impl <a href="moonbitlang/core/builtin#Neg">Neg</a> for Double
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,925:::fn op_neg(self : Double) -> Double
    ```
    > 
    >  Negates a double-precision floating-point number. For non-NaN inputs, changes
    > the sign of the number. For NaN inputs, returns NaN.
    > 
    >  Parameters:
    > 
    >  * `number` : The double-precision floating-point number to negate.
    > 
    >  Returns a new double-precision floating-point number that is the negation of
    > the input number.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Double::op_neg" {
    >    inspect!(-42.0, content="-42")
    >    inspect!(--42.0, content="42")
    >    inspect!(-(0.0 / 0.0), content="NaN") // Negating NaN returns NaN
    >  }
    >  ```

## Shl

```moonbit
:::source,moonbitlang/core/builtin/operators.mbt,71:::pub(open) trait Shl {
  op_shl(Self, Int) -> Self
}
```

 types implementing this trait can use the `<<` operator

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/byte.mbt,300:::impl <a href="moonbitlang/core/builtin#Shl">Shl</a> for Byte
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/byte.mbt,300:::fn op_shl(self : Byte, count : Int) -> Byte
    ```
    > 
    >  Shifts the bits of the `Byte` value to the left by the specified number of
    > positions.
    > 
    >  Parameters:
    > 
    >  - `byte_value` : The `Byte` value whose bits are to be shifted.
    >  - `shift_count` : The number of bit positions to shift the `byte_value` to
    >    the left.
    > 
    >  Returns the resulting `Byte` value after the shift operation.
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,485:::impl <a href="moonbitlang/core/builtin#Shl">Shl</a> for Int
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,485:::fn op_shl(self : Int, other : Int) -> Int
    ```
    > 
    >  Performs a left shift operation on a 32-bit integer. Shifts each bit in the
    > integer to the left by the specified number of positions, filling the
    > rightmost positions with zeros.
    > 
    >  Parameters:
    > 
    >  * `self` : The integer value to be shifted.
    >  * `shift` : The number of positions to shift. Must be a non-negative value
    >    less than 32. Values outside this range will be masked with `& 31`.
    > 
    >  Returns a new integer with bits shifted left by the specified number of
    > positions. For each position shifted, the rightmost bit is filled with 0, and
    > the leftmost bit is discarded.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int::op_shl" {
    >    let x = 1
    >    inspect!(x << 3, content="8") // Binary: 1 -> 1000
    >    let y = -4
    >    inspect!(y << 2, content="-16") // Binary: 100 -> 10000
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,421:::impl <a href="moonbitlang/core/builtin#Shl">Shl</a> for Int64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,421:::fn op_shl(self : Int64, other : Int) -> Int64
    ```
    > 
    >  Performs a left shift operation on a 64-bit integer value. Shifts the bits of
    > the first operand to the left by the number of positions specified by the
    > second operand. The rightmost positions are filled with zeros.
    > 
    >  Parameters:
    > 
    >  * `self` : The 64-bit integer value to be shifted.
    >  * `shift` : The number of positions to shift the bits to the left. Must be
    >    non-negative and less than 64.
    > 
    >  Returns a new `Int64` value representing the result of the left shift
    > operation.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int64::op_shl" {
    >    let n = 1L
    >    inspect!(n << 3, content="8") // 1 shifted left by 3 positions becomes 8
    >    let m = -4L
    >    inspect!(m << 2, content="-16") // -4 shifted left by 2 positions becomes -16
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2401:::impl <a href="moonbitlang/core/builtin#Shl">Shl</a> for UInt
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,2401:::fn op_shl(self : UInt, shift : Int) -> UInt
    ```
    > 
    >  Performs a left shift operation on an unsigned 32-bit integer. Each bit in
    > the integer is shifted left by the specified number of positions, and zeros
    > are filled in from the right.
    > 
    >  Parameters:
    > 
    >  * `self` : The unsigned 32-bit integer to be shifted.
    >  * `shift` : The number of positions to shift. Only the least significant 5
    >    bits are used, effectively making the shift count always between 0 and 31.
    > 
    >  Returns a new unsigned 32-bit integer that is the result of shifting `self`
    > left by `shift` positions.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt::op_shl" {
    >    let x = 1U
    >    inspect!(x << 3, content="8") // Binary: 1 -> 1000
    >    let y = 0xFFFFFFFFU
    >    inspect!(y << 16, content="4294901760") // All bits after position 16 are discarded
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1569:::impl <a href="moonbitlang/core/builtin#Shl">Shl</a> for UInt64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1569:::fn op_shl(self : UInt64, shift : Int) -> UInt64
    ```
    > 
    >  Performs a bitwise left shift operation on an unsigned 64-bit integer.
    > 
    >  Parameters:
    > 
    >  * `self` : The unsigned 64-bit integer to be shifted.
    >  * `shift` : The number of positions to shift the bits to the left. Must be
    >    between 0 and 63 inclusive, values outside this range will be masked with `&
    >    63`.
    > 
    >  Returns the result of shifting `self` left by `shift` positions. For each
    > position shifted, the rightmost bit is filled with 0, and the leftmost bit is
    > discarded.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt64::op_shl" {
    >    let x = 1UL
    >    inspect!(x << 3, content="8") // 1 shifted left by 3 positions becomes 8
    >    inspect!(x << 63, content="9223372036854775808") // 1 shifted left by 63 positions
    >  }
    >  ```

## Show

```moonbit
:::source,moonbitlang/core/builtin/traits.mbt,65:::pub(open) trait Show {
  output(Self, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
  to_string(Self) -> String = _
}
```

 Trait for types that can be converted to `String`

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/show.mbt,16:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for Unit
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,16:::fn output(_self : Unit, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/show.mbt,21:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for Bool
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,21:::fn output(self : Bool, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/show.mbt,50:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for Byte
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,50:::fn output(self : Byte, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/show.mbt,209:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for Char
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,214:::fn output(self : Char, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,209:::fn to_string(self : Char) -> String
    ```
    > 
    >  Convert Char to String
    > @intrinsic %char.to\_string
- ```moonbit
  :::source,moonbitlang/core/builtin/to_string.mbt,38:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for Int
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,30:::fn output(self : Int, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/to_string.mbt,38:::fn to_string(self : Int) -> String
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/to_string.mbt,79:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for Int16
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,55:::fn output(self : Int16, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/to_string.mbt,79:::fn to_string(self : Int16) -> String
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/to_string.mbt,26:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for Int64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,35:::fn output(self : Int64, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/to_string.mbt,26:::fn to_string(self : Int64) -> String
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/to_string.mbt,50:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for UInt
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,40:::fn output(self : UInt, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/to_string.mbt,50:::fn to_string(self : UInt) -> String
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/to_string.mbt,89:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for UInt16
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,60:::fn output(self : UInt16, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/to_string.mbt,89:::fn to_string(self : UInt16) -> String
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/to_string.mbt,69:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for UInt64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,45:::fn output(self : UInt64, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/to_string.mbt,69:::fn to_string(self : UInt64) -> String
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/show.mbt,96:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for String
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,96:::fn output(self : String, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,155:::fn to_string(self : String) -> String
    ```
    > 
    >  This is different from `Show::output`,
    > here it returns the original string without escaping.
    > The rationale is in string interpolation,
    > we want to show the original string, not the escaped one.
    >  #### Examples
    >  
    >  ```
    >  let str = "Hello \n"
    >  inspect!(str.to_string(), content="Hello \n")
    >  inspect!(str.escape(), content="\"Hello \\n\"")
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/show.mbt,175:::impl[X : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for X?
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,175:::fn output[X : <a href="moonbitlang/core/builtin#Show">Show</a>](self : X?, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/show.mbt,184:::impl[T : <a href="moonbitlang/core/builtin#Show">Show</a>, E : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/result#Result">Result</a>[T, E]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,184:::fn output[T : <a href="moonbitlang/core/builtin#Show">Show</a>, E : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/result#Result">Result</a>[T, E], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/show.mbt,197:::impl[X : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,197:::fn output[X : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[X], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/show.mbt,82:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for Bytes
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,82:::fn output(self : Bytes, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/show.mbt,192:::impl[X : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/ref#Ref">Ref</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,192:::fn output[X : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/ref#Ref">Ref</a>[X], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_show.mbt,16:::impl[A : <a href="moonbitlang/core/builtin#Show">Show</a>, B : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for (A, B)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_show.mbt,16:::fn output[A : <a href="moonbitlang/core/builtin#Show">Show</a>, B : <a href="moonbitlang/core/builtin#Show">Show</a>](self : (A, B), logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_show.mbt,27:::impl[A : <a href="moonbitlang/core/builtin#Show">Show</a>, B : <a href="moonbitlang/core/builtin#Show">Show</a>, C : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for (A, B, C)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_show.mbt,27:::fn output[A : <a href="moonbitlang/core/builtin#Show">Show</a>, B : <a href="moonbitlang/core/builtin#Show">Show</a>, C : <a href="moonbitlang/core/builtin#Show">Show</a>](self : (A, B, C), logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_show.mbt,43:::impl[A : <a href="moonbitlang/core/builtin#Show">Show</a>, B : <a href="moonbitlang/core/builtin#Show">Show</a>, C : <a href="moonbitlang/core/builtin#Show">Show</a>, D : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for (A, B, C, D)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_show.mbt,43:::fn output[A : <a href="moonbitlang/core/builtin#Show">Show</a>, B : <a href="moonbitlang/core/builtin#Show">Show</a>, C : <a href="moonbitlang/core/builtin#Show">Show</a>, D : <a href="moonbitlang/core/builtin#Show">Show</a>](self : (A, B, C, D), logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_show.mbt,61:::impl[A : <a href="moonbitlang/core/builtin#Show">Show</a>, B : <a href="moonbitlang/core/builtin#Show">Show</a>, C : <a href="moonbitlang/core/builtin#Show">Show</a>, D : <a href="moonbitlang/core/builtin#Show">Show</a>, E : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for (A, B, C, D, E)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_show.mbt,67:::fn output[A : <a href="moonbitlang/core/builtin#Show">Show</a>, B : <a href="moonbitlang/core/builtin#Show">Show</a>, C : <a href="moonbitlang/core/builtin#Show">Show</a>, D : <a href="moonbitlang/core/builtin#Show">Show</a>, E : <a href="moonbitlang/core/builtin#Show">Show</a>](self : (A, B, C, D, E), logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_show.mbt,84:::impl[A : <a href="moonbitlang/core/builtin#Show">Show</a>, B : <a href="moonbitlang/core/builtin#Show">Show</a>, C : <a href="moonbitlang/core/builtin#Show">Show</a>, D : <a href="moonbitlang/core/builtin#Show">Show</a>, E : <a href="moonbitlang/core/builtin#Show">Show</a>, F : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for (A, B, C, D, E, F)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_show.mbt,91:::fn output[A : <a href="moonbitlang/core/builtin#Show">Show</a>, B : <a href="moonbitlang/core/builtin#Show">Show</a>, C : <a href="moonbitlang/core/builtin#Show">Show</a>, D : <a href="moonbitlang/core/builtin#Show">Show</a>, E : <a href="moonbitlang/core/builtin#Show">Show</a>, F : <a href="moonbitlang/core/builtin#Show">Show</a>](self : (A, B, C, D, E, F), logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_show.mbt,110:::impl[A : <a href="moonbitlang/core/builtin#Show">Show</a>, B : <a href="moonbitlang/core/builtin#Show">Show</a>, C : <a href="moonbitlang/core/builtin#Show">Show</a>, D : <a href="moonbitlang/core/builtin#Show">Show</a>, E : <a href="moonbitlang/core/builtin#Show">Show</a>, F : <a href="moonbitlang/core/builtin#Show">Show</a>, G : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for (A, B, C, D, E, F, G)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_show.mbt,118:::fn output[A : <a href="moonbitlang/core/builtin#Show">Show</a>, B : <a href="moonbitlang/core/builtin#Show">Show</a>, C : <a href="moonbitlang/core/builtin#Show">Show</a>, D : <a href="moonbitlang/core/builtin#Show">Show</a>, E : <a href="moonbitlang/core/builtin#Show">Show</a>, F : <a href="moonbitlang/core/builtin#Show">Show</a>, G : <a href="moonbitlang/core/builtin#Show">Show</a>](self : (A, B, C, D, E, F, G), logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_show.mbt,139:::impl[T0 : <a href="moonbitlang/core/builtin#Show">Show</a>, T1 : <a href="moonbitlang/core/builtin#Show">Show</a>, T2 : <a href="moonbitlang/core/builtin#Show">Show</a>, T3 : <a href="moonbitlang/core/builtin#Show">Show</a>, T4 : <a href="moonbitlang/core/builtin#Show">Show</a>, T5 : <a href="moonbitlang/core/builtin#Show">Show</a>, T6 : <a href="moonbitlang/core/builtin#Show">Show</a>, T7 : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for (T0, T1, T2, T3, T4, T5, T6, T7)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_show.mbt,148:::fn output[T0 : <a href="moonbitlang/core/builtin#Show">Show</a>, T1 : <a href="moonbitlang/core/builtin#Show">Show</a>, T2 : <a href="moonbitlang/core/builtin#Show">Show</a>, T3 : <a href="moonbitlang/core/builtin#Show">Show</a>, T4 : <a href="moonbitlang/core/builtin#Show">Show</a>, T5 : <a href="moonbitlang/core/builtin#Show">Show</a>, T6 : <a href="moonbitlang/core/builtin#Show">Show</a>, T7 : <a href="moonbitlang/core/builtin#Show">Show</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7), logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_show.mbt,171:::impl[T0 : <a href="moonbitlang/core/builtin#Show">Show</a>, T1 : <a href="moonbitlang/core/builtin#Show">Show</a>, T2 : <a href="moonbitlang/core/builtin#Show">Show</a>, T3 : <a href="moonbitlang/core/builtin#Show">Show</a>, T4 : <a href="moonbitlang/core/builtin#Show">Show</a>, T5 : <a href="moonbitlang/core/builtin#Show">Show</a>, T6 : <a href="moonbitlang/core/builtin#Show">Show</a>, T7 : <a href="moonbitlang/core/builtin#Show">Show</a>, T8 : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_show.mbt,181:::fn output[T0 : <a href="moonbitlang/core/builtin#Show">Show</a>, T1 : <a href="moonbitlang/core/builtin#Show">Show</a>, T2 : <a href="moonbitlang/core/builtin#Show">Show</a>, T3 : <a href="moonbitlang/core/builtin#Show">Show</a>, T4 : <a href="moonbitlang/core/builtin#Show">Show</a>, T5 : <a href="moonbitlang/core/builtin#Show">Show</a>, T6 : <a href="moonbitlang/core/builtin#Show">Show</a>, T7 : <a href="moonbitlang/core/builtin#Show">Show</a>, T8 : <a href="moonbitlang/core/builtin#Show">Show</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8), logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_show.mbt,206:::impl[T0 : <a href="moonbitlang/core/builtin#Show">Show</a>, T1 : <a href="moonbitlang/core/builtin#Show">Show</a>, T2 : <a href="moonbitlang/core/builtin#Show">Show</a>, T3 : <a href="moonbitlang/core/builtin#Show">Show</a>, T4 : <a href="moonbitlang/core/builtin#Show">Show</a>, T5 : <a href="moonbitlang/core/builtin#Show">Show</a>, T6 : <a href="moonbitlang/core/builtin#Show">Show</a>, T7 : <a href="moonbitlang/core/builtin#Show">Show</a>, T8 : <a href="moonbitlang/core/builtin#Show">Show</a>, T9 : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_show.mbt,217:::fn output[T0 : <a href="moonbitlang/core/builtin#Show">Show</a>, T1 : <a href="moonbitlang/core/builtin#Show">Show</a>, T2 : <a href="moonbitlang/core/builtin#Show">Show</a>, T3 : <a href="moonbitlang/core/builtin#Show">Show</a>, T4 : <a href="moonbitlang/core/builtin#Show">Show</a>, T5 : <a href="moonbitlang/core/builtin#Show">Show</a>, T6 : <a href="moonbitlang/core/builtin#Show">Show</a>, T7 : <a href="moonbitlang/core/builtin#Show">Show</a>, T8 : <a href="moonbitlang/core/builtin#Show">Show</a>, T9 : <a href="moonbitlang/core/builtin#Show">Show</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9), logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_show.mbt,244:::impl[T0 : <a href="moonbitlang/core/builtin#Show">Show</a>, T1 : <a href="moonbitlang/core/builtin#Show">Show</a>, T2 : <a href="moonbitlang/core/builtin#Show">Show</a>, T3 : <a href="moonbitlang/core/builtin#Show">Show</a>, T4 : <a href="moonbitlang/core/builtin#Show">Show</a>, T5 : <a href="moonbitlang/core/builtin#Show">Show</a>, T6 : <a href="moonbitlang/core/builtin#Show">Show</a>, T7 : <a href="moonbitlang/core/builtin#Show">Show</a>, T8 : <a href="moonbitlang/core/builtin#Show">Show</a>, T9 : <a href="moonbitlang/core/builtin#Show">Show</a>, T10 : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_show.mbt,256:::fn output[T0 : <a href="moonbitlang/core/builtin#Show">Show</a>, T1 : <a href="moonbitlang/core/builtin#Show">Show</a>, T2 : <a href="moonbitlang/core/builtin#Show">Show</a>, T3 : <a href="moonbitlang/core/builtin#Show">Show</a>, T4 : <a href="moonbitlang/core/builtin#Show">Show</a>, T5 : <a href="moonbitlang/core/builtin#Show">Show</a>, T6 : <a href="moonbitlang/core/builtin#Show">Show</a>, T7 : <a href="moonbitlang/core/builtin#Show">Show</a>, T8 : <a href="moonbitlang/core/builtin#Show">Show</a>, T9 : <a href="moonbitlang/core/builtin#Show">Show</a>, T10 : <a href="moonbitlang/core/builtin#Show">Show</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10), logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_show.mbt,285:::impl[T0 : <a href="moonbitlang/core/builtin#Show">Show</a>, T1 : <a href="moonbitlang/core/builtin#Show">Show</a>, T2 : <a href="moonbitlang/core/builtin#Show">Show</a>, T3 : <a href="moonbitlang/core/builtin#Show">Show</a>, T4 : <a href="moonbitlang/core/builtin#Show">Show</a>, T5 : <a href="moonbitlang/core/builtin#Show">Show</a>, T6 : <a href="moonbitlang/core/builtin#Show">Show</a>, T7 : <a href="moonbitlang/core/builtin#Show">Show</a>, T8 : <a href="moonbitlang/core/builtin#Show">Show</a>, T9 : <a href="moonbitlang/core/builtin#Show">Show</a>, T10 : <a href="moonbitlang/core/builtin#Show">Show</a>, T11 : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_show.mbt,298:::fn output[T0 : <a href="moonbitlang/core/builtin#Show">Show</a>, T1 : <a href="moonbitlang/core/builtin#Show">Show</a>, T2 : <a href="moonbitlang/core/builtin#Show">Show</a>, T3 : <a href="moonbitlang/core/builtin#Show">Show</a>, T4 : <a href="moonbitlang/core/builtin#Show">Show</a>, T5 : <a href="moonbitlang/core/builtin#Show">Show</a>, T6 : <a href="moonbitlang/core/builtin#Show">Show</a>, T7 : <a href="moonbitlang/core/builtin#Show">Show</a>, T8 : <a href="moonbitlang/core/builtin#Show">Show</a>, T9 : <a href="moonbitlang/core/builtin#Show">Show</a>, T10 : <a href="moonbitlang/core/builtin#Show">Show</a>, T11 : <a href="moonbitlang/core/builtin#Show">Show</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11), logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_show.mbt,329:::impl[T0 : <a href="moonbitlang/core/builtin#Show">Show</a>, T1 : <a href="moonbitlang/core/builtin#Show">Show</a>, T2 : <a href="moonbitlang/core/builtin#Show">Show</a>, T3 : <a href="moonbitlang/core/builtin#Show">Show</a>, T4 : <a href="moonbitlang/core/builtin#Show">Show</a>, T5 : <a href="moonbitlang/core/builtin#Show">Show</a>, T6 : <a href="moonbitlang/core/builtin#Show">Show</a>, T7 : <a href="moonbitlang/core/builtin#Show">Show</a>, T8 : <a href="moonbitlang/core/builtin#Show">Show</a>, T9 : <a href="moonbitlang/core/builtin#Show">Show</a>, T10 : <a href="moonbitlang/core/builtin#Show">Show</a>, T11 : <a href="moonbitlang/core/builtin#Show">Show</a>, T12 : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_show.mbt,343:::fn output[T0 : <a href="moonbitlang/core/builtin#Show">Show</a>, T1 : <a href="moonbitlang/core/builtin#Show">Show</a>, T2 : <a href="moonbitlang/core/builtin#Show">Show</a>, T3 : <a href="moonbitlang/core/builtin#Show">Show</a>, T4 : <a href="moonbitlang/core/builtin#Show">Show</a>, T5 : <a href="moonbitlang/core/builtin#Show">Show</a>, T6 : <a href="moonbitlang/core/builtin#Show">Show</a>, T7 : <a href="moonbitlang/core/builtin#Show">Show</a>, T8 : <a href="moonbitlang/core/builtin#Show">Show</a>, T9 : <a href="moonbitlang/core/builtin#Show">Show</a>, T10 : <a href="moonbitlang/core/builtin#Show">Show</a>, T11 : <a href="moonbitlang/core/builtin#Show">Show</a>, T12 : <a href="moonbitlang/core/builtin#Show">Show</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12), logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_show.mbt,376:::impl[T0 : <a href="moonbitlang/core/builtin#Show">Show</a>, T1 : <a href="moonbitlang/core/builtin#Show">Show</a>, T2 : <a href="moonbitlang/core/builtin#Show">Show</a>, T3 : <a href="moonbitlang/core/builtin#Show">Show</a>, T4 : <a href="moonbitlang/core/builtin#Show">Show</a>, T5 : <a href="moonbitlang/core/builtin#Show">Show</a>, T6 : <a href="moonbitlang/core/builtin#Show">Show</a>, T7 : <a href="moonbitlang/core/builtin#Show">Show</a>, T8 : <a href="moonbitlang/core/builtin#Show">Show</a>, T9 : <a href="moonbitlang/core/builtin#Show">Show</a>, T10 : <a href="moonbitlang/core/builtin#Show">Show</a>, T11 : <a href="moonbitlang/core/builtin#Show">Show</a>, T12 : <a href="moonbitlang/core/builtin#Show">Show</a>, T13 : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_show.mbt,391:::fn output[T0 : <a href="moonbitlang/core/builtin#Show">Show</a>, T1 : <a href="moonbitlang/core/builtin#Show">Show</a>, T2 : <a href="moonbitlang/core/builtin#Show">Show</a>, T3 : <a href="moonbitlang/core/builtin#Show">Show</a>, T4 : <a href="moonbitlang/core/builtin#Show">Show</a>, T5 : <a href="moonbitlang/core/builtin#Show">Show</a>, T6 : <a href="moonbitlang/core/builtin#Show">Show</a>, T7 : <a href="moonbitlang/core/builtin#Show">Show</a>, T8 : <a href="moonbitlang/core/builtin#Show">Show</a>, T9 : <a href="moonbitlang/core/builtin#Show">Show</a>, T10 : <a href="moonbitlang/core/builtin#Show">Show</a>, T11 : <a href="moonbitlang/core/builtin#Show">Show</a>, T12 : <a href="moonbitlang/core/builtin#Show">Show</a>, T13 : <a href="moonbitlang/core/builtin#Show">Show</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13), logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_show.mbt,426:::impl[T0 : <a href="moonbitlang/core/builtin#Show">Show</a>, T1 : <a href="moonbitlang/core/builtin#Show">Show</a>, T2 : <a href="moonbitlang/core/builtin#Show">Show</a>, T3 : <a href="moonbitlang/core/builtin#Show">Show</a>, T4 : <a href="moonbitlang/core/builtin#Show">Show</a>, T5 : <a href="moonbitlang/core/builtin#Show">Show</a>, T6 : <a href="moonbitlang/core/builtin#Show">Show</a>, T7 : <a href="moonbitlang/core/builtin#Show">Show</a>, T8 : <a href="moonbitlang/core/builtin#Show">Show</a>, T9 : <a href="moonbitlang/core/builtin#Show">Show</a>, T10 : <a href="moonbitlang/core/builtin#Show">Show</a>, T11 : <a href="moonbitlang/core/builtin#Show">Show</a>, T12 : <a href="moonbitlang/core/builtin#Show">Show</a>, T13 : <a href="moonbitlang/core/builtin#Show">Show</a>, T14 : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13, T14)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_show.mbt,442:::fn output[T0 : <a href="moonbitlang/core/builtin#Show">Show</a>, T1 : <a href="moonbitlang/core/builtin#Show">Show</a>, T2 : <a href="moonbitlang/core/builtin#Show">Show</a>, T3 : <a href="moonbitlang/core/builtin#Show">Show</a>, T4 : <a href="moonbitlang/core/builtin#Show">Show</a>, T5 : <a href="moonbitlang/core/builtin#Show">Show</a>, T6 : <a href="moonbitlang/core/builtin#Show">Show</a>, T7 : <a href="moonbitlang/core/builtin#Show">Show</a>, T8 : <a href="moonbitlang/core/builtin#Show">Show</a>, T9 : <a href="moonbitlang/core/builtin#Show">Show</a>, T10 : <a href="moonbitlang/core/builtin#Show">Show</a>, T11 : <a href="moonbitlang/core/builtin#Show">Show</a>, T12 : <a href="moonbitlang/core/builtin#Show">Show</a>, T13 : <a href="moonbitlang/core/builtin#Show">Show</a>, T14 : <a href="moonbitlang/core/builtin#Show">Show</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13, T14), logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_show.mbt,479:::impl[T0 : <a href="moonbitlang/core/builtin#Show">Show</a>, T1 : <a href="moonbitlang/core/builtin#Show">Show</a>, T2 : <a href="moonbitlang/core/builtin#Show">Show</a>, T3 : <a href="moonbitlang/core/builtin#Show">Show</a>, T4 : <a href="moonbitlang/core/builtin#Show">Show</a>, T5 : <a href="moonbitlang/core/builtin#Show">Show</a>, T6 : <a href="moonbitlang/core/builtin#Show">Show</a>, T7 : <a href="moonbitlang/core/builtin#Show">Show</a>, T8 : <a href="moonbitlang/core/builtin#Show">Show</a>, T9 : <a href="moonbitlang/core/builtin#Show">Show</a>, T10 : <a href="moonbitlang/core/builtin#Show">Show</a>, T11 : <a href="moonbitlang/core/builtin#Show">Show</a>, T12 : <a href="moonbitlang/core/builtin#Show">Show</a>, T13 : <a href="moonbitlang/core/builtin#Show">Show</a>, T14 : <a href="moonbitlang/core/builtin#Show">Show</a>, T15 : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13, T14, T15)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_show.mbt,496:::fn output[T0 : <a href="moonbitlang/core/builtin#Show">Show</a>, T1 : <a href="moonbitlang/core/builtin#Show">Show</a>, T2 : <a href="moonbitlang/core/builtin#Show">Show</a>, T3 : <a href="moonbitlang/core/builtin#Show">Show</a>, T4 : <a href="moonbitlang/core/builtin#Show">Show</a>, T5 : <a href="moonbitlang/core/builtin#Show">Show</a>, T6 : <a href="moonbitlang/core/builtin#Show">Show</a>, T7 : <a href="moonbitlang/core/builtin#Show">Show</a>, T8 : <a href="moonbitlang/core/builtin#Show">Show</a>, T9 : <a href="moonbitlang/core/builtin#Show">Show</a>, T10 : <a href="moonbitlang/core/builtin#Show">Show</a>, T11 : <a href="moonbitlang/core/builtin#Show">Show</a>, T12 : <a href="moonbitlang/core/builtin#Show">Show</a>, T13 : <a href="moonbitlang/core/builtin#Show">Show</a>, T14 : <a href="moonbitlang/core/builtin#Show">Show</a>, T15 : <a href="moonbitlang/core/builtin#Show">Show</a>](self : (T0, T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13, T14, T15), logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 

## Shr

```moonbit
:::source,moonbitlang/core/builtin/operators.mbt,77:::pub(open) trait Shr {
  op_shr(Self, Int) -> Self
}
```

 types implementing this trait can use the `>>` operator

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/byte.mbt,315:::impl <a href="moonbitlang/core/builtin#Shr">Shr</a> for Byte
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/byte.mbt,315:::fn op_shr(self : Byte, count : Int) -> Byte
    ```
    > 
    >  Shifts the bits of the `Byte` value to the right by the specified number of
    > positions.
    > 
    >  Parameters:
    > 
    >  - `byte` : The `Byte` value whose bits are to be shifted.
    >  - `count` : The number of bit positions to shift the `byte` value to the
    >    right.
    > 
    >  Returns the resulting `Byte` value after the bitwise right shift operation.
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,512:::impl <a href="moonbitlang/core/builtin#Shr">Shr</a> for Int
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,512:::fn op_shr(self : Int, other : Int) -> Int
    ```
    > 
    >  Performs an arithmetic right shift operation on an integer value. Shifts the
    > bits of the first operand to the right by the number of positions specified
    > by the second operand. The sign bit is preserved and copied to the leftmost
    > positions.
    > 
    >  Parameters:
    > 
    >  * `self` : The integer value to be shifted.
    >  * `shift` : The number of positions to shift the bits to the right. Must be
    >    non-negative.
    > 
    >  Returns an integer representing the result of the arithmetic right shift
    > operation.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int::op_shr" {
    >    let n = -16
    >    inspect!(n >> 2, content="-4") // Sign bit is preserved during shift
    >    let p = 16
    >    inspect!(p >> 2, content="4") // Regular right shift for positive numbers
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,448:::impl <a href="moonbitlang/core/builtin#Shr">Shr</a> for Int64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,448:::fn op_shr(self : Int64, other : Int) -> Int64
    ```
    > 
    >  Performs arithmetic right shift operation on a 64-bit integer value by a
    > specified number of bits. Preserves the sign bit of the original number while
    > shifting its bits right, filling the leftmost positions with copies of the
    > sign bit.
    > 
    >  Parameters:
    > 
    >  * `self` : The 64-bit integer value to be shifted.
    >  * `shift_count` : The number of positions to shift right. Must be
    >    non-negative and less than 64.
    > 
    >  Returns a new `Int64` value that represents the result of shifting `self`
    > right by `shift_count` bits.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int64::op_shr" {
    >    let n = -1024L
    >    inspect!(n >> 3, content="-128") // Preserves sign bit
    >    let p = 1024L
    >    inspect!(p >> 3, content="128") // Regular right shift for positive numbers
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2432:::impl <a href="moonbitlang/core/builtin#Shr">Shr</a> for UInt
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,2432:::fn op_shr(self : UInt, shift : Int) -> UInt
    ```
    > 
    >  Performs a logical right shift operation on an unsigned 32-bit integer. The
    > operation shifts all bits to the right by a specified number of positions,
    > filling the leftmost positions with zeros.
    > 
    >  Parameters:
    > 
    >  * `self` : The unsigned 32-bit integer to be shifted.
    >  * `shift` : The number of positions to shift right. If this value is
    >    negative, the behavior is undefined. Values larger than 31 are masked with `&
    >    31`.
    > 
    >  Returns a new unsigned 32-bit integer containing the result of the right
    > shift operation.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt::op_shr" {
    >    let x = 0xFF000000U
    >    inspect!(x >> 8, content="16711680") // 0x00FF0000
    >    inspect!(x >> 24, content="255") // 0x000000FF
    >  }
    >  
    >  test "UInt::op_shr/large_shift" {
    >    let x = 0xFF000000U
    >    inspect!(x >> 32, content="4278190080") // Same as x >> 0 due to masking
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1595:::impl <a href="moonbitlang/core/builtin#Shr">Shr</a> for UInt64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1595:::fn op_shr(self : UInt64, shift : Int) -> UInt64
    ```
    > 
    >  Performs a logical right shift operation on a 64-bit unsigned integer by a
    > specified number of bits. All bits shifted beyond the least significant bit
    > are discarded, and zeros are shifted in from the most significant bit.
    > 
    >  Parameters:
    > 
    >  * `self` : The 64-bit unsigned integer to be shifted.
    >  * `shift` : The number of positions to shift right. Only the least
    >    significant 6 bits of this value are used, effectively making the shift count
    >    always between 0 and 63.
    > 
    >  Returns a new `UInt64` value representing the result of the right shift
    > operation.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt64::op_shr" {
    >    let x = 0xFF00FF00FF00FF00UL
    >    inspect!(x >> 8, content="71777214294589695") // Shifted right by 8 bits
    >    inspect!(x >> 64, content="18374966859414961920") // Equivalent to x >> 0 due to masking
    >  }
    >  ```

## Sub

```moonbit
:::source,moonbitlang/core/builtin/operators.mbt,23:::pub(open) trait Sub {
  op_sub(Self, Self) -> Self
}
```

 types implementing this trait can use the `-` operator

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/byte.mbt,108:::impl <a href="moonbitlang/core/builtin#Sub">Sub</a> for Byte
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/byte.mbt,108:::fn op_sub(self : Byte, that : Byte) -> Byte
    ```
    > 
    >  Subtracts the second byte from the first byte and returns the result as a
    > byte.
    > 
    >  Parameters:
    > 
    >  - `self` : The byte from which the second byte will be subtracted.
    >  - `that` : The byte to subtract from the first byte.
    > 
    >  Returns the result of the subtraction as a byte.
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,285:::impl <a href="moonbitlang/core/builtin#Sub">Sub</a> for Int
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,285:::fn op_sub(self : Int, other : Int) -> Int
    ```
    > 
    >  Performs subtraction between two 32-bit integers, following standard two's
    > complement arithmetic rules. When the result overflows or underflows, it
    > wraps around within the 32-bit integer range.
    > 
    >  Parameters:
    > 
    >  * `self` : The minuend (the number being subtracted from).
    >  * `other` : The subtrahend (the number to subtract).
    > 
    >  Returns the difference between `self` and `other`.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int::op_sub" {
    >    let a = 42
    >    let b = 10
    >    inspect!(a - b, content="32")
    >    let max = 2147483647 // Int maximum value
    >    inspect!(max - -1, content="-2147483648") // Overflow case
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,84:::impl <a href="moonbitlang/core/builtin#Sub">Sub</a> for Int64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,84:::fn op_sub(self : Int64, other : Int64) -> Int64
    ```
    > 
    >  Performs subtraction between two 64-bit integers.
    > 
    >  Parameters:
    > 
    >  * `self` : The minuend (the number being subtracted from).
    >  * `other` : The subtrahend (the number to subtract).
    > 
    >  Returns the difference between `self` and `other` as a 64-bit integer.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Int64::op_sub" {
    >    let a = 9223372036854775807L // Int64 maximum value
    >    let b = 1L
    >    inspect!(a - b, content="9223372036854775806")
    >    let c = -9223372036854775808L // Int64 minimum value
    >    let d = 1L
    >    inspect!(c - d, content="9223372036854775807")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2020:::impl <a href="moonbitlang/core/builtin#Sub">Sub</a> for UInt
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,2020:::fn op_sub(self : UInt, other : UInt) -> UInt
    ```
    > 
    >  Performs subtraction between two unsigned 32-bit integers. When the result
    > would be negative, the function wraps around using modular arithmetic (2^32).
    > 
    >  Parameters:
    > 
    >  * `self` : The first unsigned 32-bit integer (minuend).
    >  * `other` : The second unsigned 32-bit integer to subtract from the first
    >    (subtrahend).
    > 
    >  Returns a new unsigned 32-bit integer representing the difference between the
    > two numbers. If the result would be negative, it wraps around to a positive
    > number by adding 2^32 repeatedly until the result is in range.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt::op_sub" {
    >    let a = 5U
    >    let b = 3U
    >    inspect!(a - b, content="2")
    >    let c = 3U
    >    let d = 5U
    >    inspect!(c - d, content="4294967294") // wraps around to 2^32 - 2
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1219:::impl <a href="moonbitlang/core/builtin#Sub">Sub</a> for UInt64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1219:::fn op_sub(self : UInt64, other : UInt64) -> UInt64
    ```
    > 
    >  Performs subtraction between two unsigned 64-bit integers. When the result
    > would be negative, the function wraps around using modular arithmetic (2^64).
    > 
    >  Parameters:
    > 
    >  * `self` : The first unsigned 64-bit integer (minuend).
    >  * `other` : The second unsigned 64-bit integer to subtract from the first
    >    (subtrahend).
    > 
    >  Returns the difference between the two numbers, wrapped around if necessary.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "UInt64::op_sub" {
    >    let a = 5UL
    >    let b = 3UL
    >    inspect!(a - b, content="2")
    >    let c = 3UL
    >    let d = 5UL
    >    inspect!(c - d, content="18446744073709551614") // wraps around to 2^64 - 2
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2652:::impl <a href="moonbitlang/core/builtin#Sub">Sub</a> for Float
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,2652:::fn op_sub(self : Float, other : Float) -> Float
    ```
    > 
    >  Performs subtraction between two single-precision floating-point numbers.
    > 
    >  Parameters:
    > 
    >  * `self` : The first floating-point number (minuend).
    >  * `other` : The second floating-point number (subtrahend).
    > 
    >  Returns a new floating-point number representing the difference between
    > `self` and `other`.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Float::op_sub" {
    >    let x = 3.14.to_float()
    >    let y = 1.0.to_float()
    >    let result = x - y
    >    inspect!(result.to_double(), content="2.140000104904175")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,974:::impl <a href="moonbitlang/core/builtin#Sub">Sub</a> for Double
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/intrinsics.mbt,974:::fn op_sub(self : Double, other : Double) -> Double
    ```
    > 
    >  Performs subtraction between two double-precision floating-point numbers.
    > 
    >  Parameters:
    > 
    >  * `self` : The first operand (minuend).
    >  * `other` : The second operand (subtrahend).
    > 
    >  Returns the difference between the two numbers according to IEEE 754
    > double-precision arithmetic rules.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Double::op_sub" {
    >    let a = 5.0
    >    let b = 3.0
    >    inspect!(a - b, content="2")
    >    inspect!(0.0 / 0.0 - 1.0, content="NaN") // NaN - anything = NaN
    >  }
    >  ```

## ToJson

```moonbit
:::source,moonbitlang/core/builtin/json.mbt,159:::pub(open) trait ToJson {
  to_json(Self) -> <a href="moonbitlang/core/json#Json">Json</a>
}
```

 Trait for types that can be converted to `Json`

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,293:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for Unit
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,293:::fn to_json(_self : Unit) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,164:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for Bool
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,164:::fn to_json(self : Bool) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,213:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for Char
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,213:::fn to_json(self : Char) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,173:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for Int
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,173:::fn to_json(self : Int) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,178:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for Int64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,178:::fn to_json(self : Int64) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,183:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for UInt
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,183:::fn to_json(self : UInt) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,188:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for UInt64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,188:::fn to_json(self : UInt64) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,203:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for Float
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,203:::fn to_json(self : Float) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,193:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for Double
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,193:::fn to_json(self : Double) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,208:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for String
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,208:::fn to_json(self : String) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,274:::impl[T : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for T?
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,274:::fn to_json[T : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : T?) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,282:::impl[Ok : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, Err : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="moonbitlang/core/result#Result">Result</a>[Ok, Err]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,282:::fn to_json[Ok : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, Err : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : <a href="moonbitlang/core/result#Result">Result</a>[Ok, Err]) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,228:::impl[X : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,228:::fn to_json[X : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[X]) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_to_json.mbt,16:::impl[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for (A, B)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_to_json.mbt,16:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : (A, B)) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_to_json.mbt,21:::impl[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for (A, B, C)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_to_json.mbt,21:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : (A, B, C)) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_to_json.mbt,28:::impl[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for (A, B, C, D)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_to_json.mbt,28:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : (A, B, C, D)) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_to_json.mbt,35:::impl[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for (A, B, C, D, E)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_to_json.mbt,41:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : (A, B, C, D, E)) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_to_json.mbt,52:::impl[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for (A, B, C, D, E, F)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_to_json.mbt,59:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : (A, B, C, D, E, F)) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_to_json.mbt,71:::impl[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for (A, B, C, D, E, F, G)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_to_json.mbt,79:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : (A, B, C, D, E, F, G)) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_to_json.mbt,92:::impl[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, H : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for (A, B, C, D, E, F, G, H)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_to_json.mbt,101:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, H : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : (A, B, C, D, E, F, G, H)) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_to_json.mbt,115:::impl[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, H : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, I : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for (A, B, C, D, E, F, G, H, I)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_to_json.mbt,125:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, H : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, I : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : (A, B, C, D, E, F, G, H, I)) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_to_json.mbt,140:::impl[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, H : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, I : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, J : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for (A, B, C, D, E, F, G, H, I, J)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_to_json.mbt,151:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, H : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, I : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, J : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : (A, B, C, D, E, F, G, H, I, J)) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_to_json.mbt,167:::impl[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, H : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, I : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, J : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, K : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for (A, B, C, D, E, F, G, H, I, J, K)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_to_json.mbt,179:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, H : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, I : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, J : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, K : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : (A, B, C, D, E, F, G, H, I, J, K)) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_to_json.mbt,196:::impl[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, H : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, I : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, J : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, K : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, L : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for (A, B, C, D, E, F, G, H, I, J, K, L)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_to_json.mbt,209:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, H : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, I : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, J : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, K : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, L : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : (A, B, C, D, E, F, G, H, I, J, K, L)) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_to_json.mbt,227:::impl[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, H : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, I : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, J : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, K : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, L : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, M : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for (A, B, C, D, E, F, G, H, I, J, K, L, M)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_to_json.mbt,241:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, H : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, I : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, J : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, K : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, L : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, M : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : (A, B, C, D, E, F, G, H, I, J, K, L, M)) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_to_json.mbt,260:::impl[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, H : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, I : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, J : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, K : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, L : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, M : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, N : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for (A, B, C, D, E, F, G, H, I, J, K, L, M, N)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_to_json.mbt,275:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, H : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, I : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, J : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, K : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, L : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, M : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, N : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : (A, B, C, D, E, F, G, H, I, J, K, L, M, N)) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_to_json.mbt,295:::impl[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, H : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, I : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, J : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, K : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, L : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, M : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, N : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, O : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for (A, B, C, D, E, F, G, H, I, J, K, L, M, N, O)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_to_json.mbt,311:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, H : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, I : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, J : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, K : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, L : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, M : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, N : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, O : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : (A, B, C, D, E, F, G, H, I, J, K, L, M, N, O)) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/tuple_to_json.mbt,332:::impl[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, H : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, I : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, J : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, K : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, L : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, M : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, N : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, O : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, P : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for (A, B, C, D, E, F, G, H, I, J, K, L, M, N, O, P)
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/tuple_to_json.mbt,349:::fn to_json[A : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, B : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, C : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, D : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, E : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, F : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, G : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, H : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, I : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, J : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, K : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, L : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, M : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, N : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, O : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>, P : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : (A, B, C, D, E, F, G, H, I, J, K, L, M, N, O, P)) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 

## ArgsLoc

```moonbit
:::source,moonbitlang/core/builtin/autoloc.mbt,51:::pub(all) type ArgsLoc <a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a>?]
```

 Represents a type for storing argument locations in source code. It is an
array of optional source locations, where each element corresponds to an
argument's location in the source code. Used internally by the compiler for
error reporting and debugging purposes.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/autoloc.mbt,51:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/builtin#ArgsLoc">ArgsLoc</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/autoloc.mbt,51:::fn output(<a href="moonbitlang/core/builtin#ArgsLoc">ArgsLoc</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### to\_json
  ```moonbit
  :::source,moonbitlang/core/builtin/autoloc.mbt,64:::fn <a href="moonbitlang/core/builtin#ArgsLoc">ArgsLoc</a>::to_json(self : <a href="moonbitlang/core/builtin#ArgsLoc">ArgsLoc</a>) -> String
  ```
  > 
  >  Converts an array of optional source locations to its JSON string
  > representation. Each location in the array is either represented as a string
  > if present, or "null" if absent.
  > 
  >  Parameters:
  > 
  >  * `self` : The array of optional source locations to be converted.
  > 
  >  Returns a JSON array string where each element is either a string
  > representation of a source location or "null".

## Array

```moonbit
:::source,moonbitlang/core/builtin/arraycore_nonjs.mbt,21:::type Array[T]
```

 An `Array` is a collection of values that supports random access and can
grow in size.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,329:::impl[T] <a href="moonbitlang/core/builtin#Add">Add</a> for <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/array.mbt,329:::fn op_add[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], other : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> <a href="moonbitlang/core/array#Array">Array</a>[T]
    ```
    > 
    >  Concatenates two arrays into a new array. The resulting array contains all
    > elements from the first array followed by all elements from the second array.
    > 
    >  Parameters:
    > 
    >  * `self` : The first array to concatenate.
    >  * `other` : The second array to concatenate.
    > 
    >  Returns a new array containing all elements from both arrays in order.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Array::op_add" {
    >    let a = [1, 2, 3]
    >    let b = [4, 5]
    >    inspect!(a + b, content="[1, 2, 3, 4, 5]")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,295:::impl[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/array.mbt,295:::fn compare[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#Array">Array</a>[T], other : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> Int
    ```
    > 
    >  Compares two arrays lexicographically.
    > 
    >  First compares the lengths of the arrays. If they differ, returns -1 if the
    > first array is shorter, 1 if it's longer. If the lengths are equal, compares
    > elements pairwise until a difference is found or all elements have been
    > compared.
    > 
    >  Parameters:
    > 
    >  * `self` : The first array to compare.
    >  * `other` : The second array to compare.
    > 
    >  Returns an integer that indicates the relative order:
    > 
    >  * A negative value if `self` is less than `other`
    >  * Zero if `self` equals `other`
    >  * A positive value if `self` is greater than `other`
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Array::compare" {
    >    let arr1 = [1, 2, 3]
    >    let arr2 = [1, 2, 4]
    >    let arr3 = [1, 2]
    >    inspect!(arr1.compare(arr2), content="-1") // arr1 < arr2
    >    inspect!(arr2.compare(arr1), content="1") // arr2 > arr1
    >    inspect!(arr1.compare(arr3), content="1") // arr1 > arr3 (longer)
    >    inspect!(arr1.compare(arr1), content="0") // arr1 = arr1
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1768:::impl[T] <a href="moonbitlang/core/builtin#Default">Default</a> for <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/array.mbt,1768:::fn default[T]() -> <a href="moonbitlang/core/array#Array">Array</a>[T]
    ```
    > 
    >  Creates a new empty array.
    > 
    >  Returns an empty array of type `Array[T]`.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Array::default" {
    >    let arr : Array[Int] = Array::default()
    >    inspect!(arr.length(), content="0")
    >    inspect!(arr.is_empty(), content="true")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,244:::impl[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/array.mbt,244:::fn op_equal[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#Array">Array</a>[T], other : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> Bool
    ```
    > 
    >  Compares two arrays for equality. Returns true if both arrays have the same
    > length and contain equal elements in the same order.
    > 
    >  Parameters:
    > 
    >  * `self` : The first array to compare.
    >  * `other` : The second array to compare.
    > 
    >  Returns true if the arrays are equal, false otherwise.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Array::op_equal" {
    >    let arr1 = [1, 2, 3]
    >    let arr2 = [1, 2, 3]
    >    let arr3 = [1, 2, 4]
    >    inspect!(arr1 == arr2, content="true")
    >    inspect!(arr1 == arr3, content="false")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,257:::impl[T : <a href="moonbitlang/core/builtin#Hash">Hash</a>] <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/array.mbt,257:::fn hash_combine[T : <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : <a href="moonbitlang/core/array#Array">Array</a>[T], hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/show.mbt,202:::impl[X : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/array#Array">Array</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,202:::fn output[X : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/array#Array">Array</a>[X], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,223:::impl[X : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="moonbitlang/core/array#Array">Array</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,223:::fn to_json[X : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : <a href="moonbitlang/core/array#Array">Array</a>[X]) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### append
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,374:::fn <a href="moonbitlang/core/array#Array">Array</a>::append[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], other : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> Unit
  ```
  > 
  >  Appends all elements from one array to the end of another array. The elements
  > are added in-place, modifying the original array.
  > 
  >  Parameters:
  > 
  >  * `self` : The array to append to.
  >  * `other` : The array whose elements will be appended.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::append" {
  >    let v1 = [1, 2, 3]
  >    let v2 = [4, 5, 6]
  >    v1.append(v2)
  >    inspect!(v1, content="[1, 2, 3, 4, 5, 6]")
  >  }
  >  
  >  test "Array::append/empty" {
  >    let v1 = [1, 2, 3]
  >    let v2 : Array[Int] = []
  >    v1.append(v2)
  >    inspect!(v1, content="[1, 2, 3]")
  >  }
  >  ```
- #### binary\_search
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1019:::fn <a href="moonbitlang/core/array#Array">Array</a>::binary_search[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#Array">Array</a>[T], value : T) -> <a href="moonbitlang/core/result#Result">Result</a>[Int, Int]
  ```
  > 
  >  Performs a binary search on a sorted array to find the index of a given element.
  > 
  >  #### Example
  >  ```
  >  let v = [3, 4, 5]
  >  let result = v.binary_search(3)
  >  assert_eq!(result, Ok(0)) // The element 3 is found at index 0
  >  ```
  > 
  >  #### Arguments
  >  - `self`: The array in which to perform the search.
  >  - `value`: The element to search for in the array.
  > 
  >  #### Returns
  >  - `Result[Int, Int]`:
  >    If the element is found, an `Ok` variant is returned, containing the index of the matching element in the array.
  >    If there are multiple matches, the leftmost match will be returned.
  >    If the element is not found, an `Err` variant is returned, containing the index where the element could be inserted to maintain the sorted order.
  > 
  >  #### Notes
  >  - Ensure that the array is sorted in increasing order before calling this function.
  >  - If the array is not sorted, the returned result is undefined and should not be relied on.
- #### binary\_search\_by
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1098:::fn <a href="moonbitlang/core/array#Array">Array</a>::binary_search_by[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], cmp : (T) -> Int) -> <a href="moonbitlang/core/result#Result">Result</a>[Int, Int]
  ```
  > 
  >  Performs a binary search on a sorted array using a custom comparison
  > function. Returns the position of the matching element if found, or the
  > position where the element could be inserted while maintaining the sorted
  > order.
  > 
  >  Parameters:
  > 
  >  * `array` : The sorted array to search in.
  >  * `comparator` : A function that compares each element with the target value,
  >    returning:
  >   * A negative integer if the element is less than the target
  >   * Zero if the element equals the target
  >   * A positive integer if the element is greater than the target
  > 
  >  Returns a `Result` containing either:
  > 
  >  * `Ok(index)` if a matching element is found at position `index`
  >  * `Err(index)` if no match is found, where `index` is the position where the
  >    element could be inserted
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "binary_search_by" {
  >    let arr = [1, 3, 5, 7, 9]
  >    let find_3 = arr.binary_search_by(fn(x) {
  >      if x < 3 {
  >        -1
  >      } else if x > 3 {
  >        1
  >      } else {
  >        0
  >      }
  >    })
  >    inspect!(find_3, content="Ok(1)")
  >    let find_4 = arr.binary_search_by(fn(x) {
  >      if x < 4 {
  >        -1
  >      } else if x > 4 {
  >        1
  >      } else {
  >        0
  >      }
  >    })
  >    inspect!(find_4, content="Err(2)")
  >  }
  >  ```
  > 
  >  Notes:
  > 
  >  * Assumes the array is sorted according to the ordering implied by the
  >    comparison function
  >  * For multiple matches, returns the leftmost matching position
  >  * Returns an insertion point that maintains the sort order when no match is
  >    found
- #### blit\_to
  ```moonbit
  :::source,moonbitlang/core/builtin/array_block.mbt,142:::fn <a href="moonbitlang/core/array#Array">Array</a>::blit_to[A](self : <a href="moonbitlang/core/array#Array">Array</a>[A], dst : <a href="moonbitlang/core/array#Array">Array</a>[A], len~ : Int, src_offset~ : Int = .., dst_offset~ : Int = ..) -> Unit
  ```
  > 
  >  Copies elements from one array to another array, with support for growing the
  > destination array if needed. The arrays may overlap, in which case the copy
  > is performed in a way that preserves the data.
  > 
  >  Parameters:
  > 
  >  * `source` : The array to copy elements from.
  >  * `destination` : The array to copy elements to. Will be automatically grown
  >    if needed to accommodate the copied elements.
  >  * `length` : The number of elements to copy.
  >  * `source_start` : Starting index in the source array. Defaults to 0.
  >  * `destination_start` : Starting index in the destination array. Defaults to
  >  0. 
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::blit_to/basic" {
  >    let src = [1, 2, 3, 4, 5]
  >    let dst = [0, 0]
  >    src.blit_to(dst, len=3, dst_offset=1)
  >    inspect!(dst, content="[0, 1, 2, 3]")
  >  }
  >  ```
  > 
  >  Panics if:
  > 
  >  * `len` is negative
  >  * `src_offset` is negative
  >  * `dst_offset` is negative
  >  * `dst_offset + len` exceeds the length of destination array
  >  * `src_offset + len` exceeds the length of source array
- #### capacity
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,89:::fn <a href="moonbitlang/core/array#Array">Array</a>::capacity[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> Int
  ```
  > 
  >  Returns the total capacity of the array, which is the number of elements that
  > the array can hold without requiring reallocation of its internal buffer.
  > 
  >  Parameters:
  > 
  >  * `array` : The array whose capacity is to be determined.
  > 
  >  Returns the current capacity of the array as an integer.
  > 
  >  NOTE: The capacity of an array may not be consistent across different backends
  > and/or different versions of the MoonBit compiler/core.
- #### chunk\_by
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1598:::fn <a href="moonbitlang/core/array#Array">Array</a>::chunk_by[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], pred : (T, T) -> Bool) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/core/array#Array">Array</a>[T]]
  ```
  > 
  >  Groups consecutive elements of the array into chunks where adjacent elements
  > satisfy the given predicate function.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to be chunked.
  >  * `predicate` : A function that takes two adjacent elements and returns
  >    `true` if they should be in the same chunk, `false` otherwise.
  > 
  >  Returns an array of arrays, where each inner array is a chunk of consecutive
  > elements that satisfy the predicate with their adjacent elements.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "chunk_by" {
  >    let v = [1, 1, 2, 3, 2, 3, 2, 3, 4]
  >    let chunks = v.chunk_by(fn(x, y) { x <= y })
  >    inspect!(chunks, content="[[1, 1, 2, 3], [2, 3], [2, 3, 4]]")
  >  }
  >  
  >  test "chunk_by/empty" {
  >    let v : Array[Int] = []
  >    inspect!(v.chunk_by(fn(x, y) { x <= y }), content="[]")
  >  }
  >  ```
- #### chunks
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1557:::fn <a href="moonbitlang/core/array#Array">Array</a>::chunks[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], size : Int) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/core/array#Array">Array</a>[T]]
  ```
  > 
  >  Divides an array into smaller arrays (chunks) of the specified size.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to be divided into chunks.
  >  * `size` : The size of each chunk. Must be a positive integer.
  > 
  >  Returns an array of arrays, where each inner array is a chunk containing
  > elements from the original array. If the length of the original array is not
  > divisible by the chunk size, the last chunk will contain fewer elements.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "chunks" {
  >    let arr = [1, 2, 3, 4, 5]
  >    let chunks = arr.chunks(2)
  >    inspect!(chunks, content="[[1, 2], [3, 4], [5]]")
  >  }
  >  
  >  test "chunks/empty" {
  >    let arr : Array[Int] = []
  >    inspect!(arr.chunks(3), content="[]")
  >  }
  >  ```
- #### clear
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,478:::fn <a href="moonbitlang/core/array#Array">Array</a>::clear[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> Unit
  ```
  > 
  >  Clears the array, removing all values.
  > 
  >  This method has no effect on the allocated capacity of the array, only setting the length to 0.
  > 
  >  #### Example
  >  ```
  >  let v = [3, 4, 5]
  >  v.clear()
  >  assert_eq!(v.length(), 0)
  >  ```
- #### contains
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,761:::fn <a href="moonbitlang/core/array#Array">Array</a>::contains[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#Array">Array</a>[T], value : T) -> Bool
  ```
  > 
  >  Checks whether the array contains an element equal to the given value.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to search in.
  >  * `value` : The value to search for.
  > 
  >  Returns `true` if the array contains an element equal to the given value,
  > `false` otherwise.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::contains" {
  >    let arr = [1, 2, 3, 4, 5]
  >    inspect!(arr.contains(3), content="true")
  >    inspect!(arr.contains(6), content="false")
  >  }
  >  
  >  test "Array::contains/empty" {
  >    let arr : Array[Int] = []
  >    inspect!(arr.contains(1), content="false")
  >  }
  >  ```
- #### dedup
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1478:::fn <a href="moonbitlang/core/array#Array">Array</a>::dedup[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> Unit
  ```
  > 
  >  Removes consecutive duplicate elements from an array in-place, using equality
  > comparison. The first occurrence of each element is retained while subsequent
  > equal elements are removed.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to remove duplicates from. Must contain elements that
  >    implement the `Eq` trait for equality comparison.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "dedup" {
  >    let arr = [1, 2, 2, 3, 3, 3, 2]
  >    arr.dedup()
  >    inspect!(arr, content="[1, 2, 3, 2]")
  >  }
  >  
  >  test "dedup/sorted" {
  >    let arr = [1, 2, 2, 2, 3, 3]
  >    arr.dedup()
  >    inspect!(arr, content="[1, 2, 3]")
  >  }
  >  
  >  test "dedup/empty" {
  >    let arr : Array[Int] = []
  >    arr.dedup()
  >    inspect!(arr, content="[]")
  >  }
  >  ```
  > 
  >  Note: For best results when removing all duplicates regardless of position,
  > sort the array before calling this function. When used on an unsorted array,
  > this function only removes consecutive duplicates.
- #### drain
  ```moonbit
  :::source,moonbitlang/core/builtin/arraycore_nonjs.mbt,368:::fn <a href="moonbitlang/core/array#Array">Array</a>::drain[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], begin : Int, end : Int) -> <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  >  Removes the specified range from the array and returns it.
  > 
  >  This functions returns a array range from `begin` to `end` `[begin, end)`
  > 
  >  #### Example
  >  ```
  >  let v = [3, 4, 5]
  >  let vv = v.drain(1, 2) // vv = [4], v = [3, 5]
  >  assert_eq!(vv, [4])
  >  assert_eq!(v, [3, 5])
  >  ```
  >  @alert unsafe "Panic if index is out of bounds."
- #### each
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,404:::fn <a href="moonbitlang/core/array#Array">Array</a>::each[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], f : (T) -> Unit) -> Unit
  ```
  > 
  >  Iterates through each element of the array in order, applying the given
  > function to each element.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to iterate over.
  >  * `function` : A function that takes a single element of type `T` as input
  >    and returns `Unit`. This function is applied to each element of the array in
  >    order.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::each" {
  >    let arr = [1, 2, 3]
  >    let mut sum = 0
  >    arr.each(fn(x) { sum = sum + x })
  >    inspect!(sum, content="6")
  >  }
  >  ```
- #### eachi
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,461:::fn <a href="moonbitlang/core/array#Array">Array</a>::eachi[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], f : (Int, T) -> Unit) -> Unit
  ```
  > 
  >  Iterates over the elements of the array with index.
  > 
  >  #### Example
  >  ```
  >  let v = [3, 4, 5]
  >  let mut sum = 0
  >  v.eachi(fn (i, x) {sum = sum + x + i})
  >  ```
- #### ends\_with
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,835:::fn <a href="moonbitlang/core/array#Array">Array</a>::ends_with[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#Array">Array</a>[T], suffix : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> Bool
  ```
  > 
  >  Tests if an array ends with the given suffix.
  > 
  >  Parameters:
  > 
  >  * `self` : The array to check.
  >  * `suffix` : The array to test against.
  > 
  >  Returns `true` if the array ends with the given suffix, `false` otherwise.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::ends_with/basic" {
  >    let arr = [1, 2, 3, 4, 5]
  >    inspect!(arr.ends_with([4, 5]), content="true")
  >    inspect!(arr.ends_with([3, 4]), content="false")
  >    inspect!(arr.ends_with([]), content="true")
  >  }
  >  
  >  test "Array::ends_with/empty" {
  >    let arr : Array[Int] = []
  >    inspect!(arr.ends_with([]), content="true")
  >    inspect!(arr.ends_with([1]), content="false")
  >  }
  >  ```
- #### extract\_if
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1516:::fn <a href="moonbitlang/core/array#Array">Array</a>::extract_if[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], f : (T) -> Bool) -> <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  >  Extracts elements from an array that satisfy a given predicate function. The
  > extracted elements are removed from the original array and returned as a new
  > array. The relative order of the extracted elements is preserved.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to extract elements from.
  >  * `predicate` : A function that takes an element and returns `true` if the
  >    element should be extracted, `false` otherwise.
  > 
  >  Returns a new array containing all elements that satisfy the predicate
  > function, in the order they appeared in the original array.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "extract_if" {
  >    let arr = [1, 2, 3, 4, 5]
  >    let extracted = arr.extract_if(fn(x) { x % 2 == 0 })
  >    inspect!(extracted, content="[2, 4]")
  >    inspect!(arr, content="[1, 3, 5]")
  >  }
  >  ```
- #### filter
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,571:::fn <a href="moonbitlang/core/array#Array">Array</a>::filter[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], f : (T) -> Bool) -> <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  >  Creates a new array containing all elements from the input array that satisfy
  > the given predicate function.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to filter.
  >  * `predicate` : A function that takes an element and returns a boolean
  >    indicating whether the element should be included in the result.
  > 
  >  Returns a new array containing only the elements for which the predicate
  > function returns `true`. The relative order of the elements is preserved.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::filter" {
  >    let arr = [1, 2, 3, 4, 5]
  >    let evens = arr.filter(fn(x) { x % 2 == 0 })
  >    inspect!(evens, content="[2, 4]")
  >  }
  >  ```
- #### find\_index
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,970:::fn <a href="moonbitlang/core/array#Array">Array</a>::find_index[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], f : (T) -> Bool) -> Int?
  ```
  > 
  >  Searches the array for the first element that satisfies the predicate
  > function.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to search in.
  >  * `predicate` : A function that takes an element and returns a boolean
  >    indicating whether the element satisfies the search condition.
  > 
  >  Returns the index of the first element that satisfies the predicate, or
  > `None` if no such element is found.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "find_index" {
  >    let arr = [1, 2, 3, 4, 5]
  >    inspect!(arr.search_by(fn(x) { x > 3 }), content="Some(3)")
  >    inspect!(arr.search_by(fn(x) { x > 10 }), content="None")
  >  }
  >  ```
  > 
- #### flatten
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1263:::fn <a href="moonbitlang/core/array#Array">Array</a>::flatten[T](self : <a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/core/array#Array">Array</a>[T]]) -> <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  >  Flattens a array of arrays into a array.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  let v = [[3, 4], [5, 6]].flatten()
  >  assert_eq!(v, [3, 4, 5, 6])
  >  ```
- #### fold
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1303:::fn <a href="moonbitlang/core/array#Array">Array</a>::fold[A, B](self : <a href="moonbitlang/core/array#Array">Array</a>[A], init~ : B, f : (B, A) -> B) -> B
  ```
  > 
  >  Fold out values from an array according to certain rules.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  let sum = [1, 2, 3, 4, 5].fold(init=0, fn { sum, elem => sum + elem })
  >  assert_eq!(sum, 15)
  >  ```
- #### fold\_left
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1382:::fn <a href="moonbitlang/core/array#Array">Array</a>::fold_left[T, U](self : <a href="moonbitlang/core/array#Array">Array</a>[T], f : (U, T) -> U, init~ : U) -> U
  ```
  > 
  >  Fold out values from an array according to certain rules.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  let sum = [1, 2, 3, 4, 5].fold(init=0, fn { sum, elem => sum + elem })
  >  assert_eq!(sum, 15)
  >  ```
- #### fold\_lefti
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1416:::fn <a href="moonbitlang/core/array#Array">Array</a>::fold_lefti[T, U](self : <a href="moonbitlang/core/array#Array">Array</a>[T], f : (Int, U, T) -> U, init~ : U) -> U
  ```
  > 
  >  Fold out values from an array according to certain rules with index.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  let sum = [1, 2, 3, 4, 5].foldi(init=0, fn { index, sum, _elem => sum + index })
  >  assert_eq!(sum, 10)
  >  ```
- #### fold\_right
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1397:::fn <a href="moonbitlang/core/array#Array">Array</a>::fold_right[T, U](self : <a href="moonbitlang/core/array#Array">Array</a>[T], f : (U, T) -> U, init~ : U) -> U
  ```
  > 
  >  Fold out values from an array according to certain rules in reversed turn.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  let sum = [1, 2, 3, 4, 5].rev_fold(init=0, fn { sum, elem => sum + elem })
  >  assert_eq!(sum, 15)
  >  ```
- #### fold\_righti
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1435:::fn <a href="moonbitlang/core/array#Array">Array</a>::fold_righti[T, U](self : <a href="moonbitlang/core/array#Array">Array</a>[T], f : (Int, U, T) -> U, init~ : U) -> U
  ```
  > 
  >  Fold out values from an array according to certain rules in reversed turn with index.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  let sum = [1, 2, 3, 4, 5].rev_foldi(init=0, fn { index, sum, _elem => sum + index })
  >  assert_eq!(sum, 10)
  >  ```
- #### foldi
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1337:::fn <a href="moonbitlang/core/array#Array">Array</a>::foldi[A, B](self : <a href="moonbitlang/core/array#Array">Array</a>[A], init~ : B, f : (Int, B, A) -> B) -> B
  ```
  > 
  >  Fold out values from an array according to certain rules with index.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  let sum = [1, 2, 3, 4, 5].foldi(init=0, fn { index, sum, _elem => sum + index })
  >  assert_eq!(sum, 10)
  >  ```
- #### from\_fixed\_array
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,35:::fn <a href="moonbitlang/core/array#Array">Array</a>::from_fixed_array[T](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]) -> <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  >  Creates a new dynamic array from a fixed-size array.
  > 
  >  Parameters:
  > 
  >  * `arr` : The fixed-size array to convert. The elements of this array will be
  >    copied to the new array.
  > 
  >  Returns a new dynamic array containing all elements from the input fixed-size
  > array.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::from_fixed_array" {
  >    let fixed = FixedArray::make(3, 42)
  >    let dynamic = Array::from_fixed_array(fixed)
  >    inspect!(dynamic, content="[42, 42, 42]")
  >  }
  >  ```
- #### get
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,174:::fn <a href="moonbitlang/core/array#Array">Array</a>::get[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], index : Int) -> T?
  ```
  > 
  >  Retrieves the element at the specified index from the array.
  > 
  >  Parameters:
  > 
  >  * `self` : The array to get the element from.
  >  * `index` : The position in the array from which to retrieve the element.
  > 
  >  Returns `Some(element)` if the index is within bounds, or `None` if the index
  > is out of bounds.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::get" {
  >    let arr = [1, 2, 3]
  >    inspect!(arr.get(-1), content="None")
  >    inspect!(arr.get(0), content="Some(1)")
  >    inspect!(arr.get(3), content="None")
  >  }
  >  ```
- #### insert
  ```moonbit
  :::source,moonbitlang/core/builtin/arraycore_nonjs.mbt,392:::fn <a href="moonbitlang/core/array#Array">Array</a>::insert[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], index : Int, value : T) -> Unit
  ```
  > 
  >  Inserts an element at a given index within the array.
  > 
  >  #### Example
  >  ```
  >  [3, 4, 5].insert(1, 6)
  >  ```
  >  @alert unsafe "Panic if index is out of bounds."
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,600:::fn <a href="moonbitlang/core/array#Array">Array</a>::is_empty[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> Bool
  ```
  > 
  >  Tests whether the array contains no elements.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to check.
  > 
  >  Returns `true` if the array has no elements, `false` otherwise.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::is_empty" {
  >    let empty : Array[Int] = []
  >    inspect!(empty.is_empty(), content="true")
  >    let non_empty = [1, 2, 3]
  >    inspect!(non_empty.is_empty(), content="false")
  >  }
  >  ```
- #### is\_sorted
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,632:::fn <a href="moonbitlang/core/array#Array">Array</a>::is_sorted[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> Bool
  ```
  > 
  >  Tests whether the array is sorted in ascending order.
  > 
  >  Parameters:
  > 
  >  * `self` : The array to be tested.
  >  * `T` : The type of elements in the array. Must implement the `Compare`
  >    trait.
  > 
  >  Returns a boolean value indicating whether the array is sorted in ascending
  > order:
  > 
  >  * `true` if the array is empty, contains only one element, or all elements
  >    are in ascending order.
  >  * `false` if any element is greater than the element that follows it.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::is_sorted/basic" {
  >    let ascending = [1, 2, 3, 4, 5]
  >    let descending = [5, 4, 3, 2, 1]
  >    let unsorted = [1, 3, 2, 4, 5]
  >    inspect!(ascending.is_sorted(), content="true")
  >    inspect!(descending.is_sorted(), content="false")
  >    inspect!(unsorted.is_sorted(), content="false")
  >  }
  >  ```
- #### iter
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1679:::fn <a href="moonbitlang/core/array#Array">Array</a>::iter[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
  >  Creates an iterator over the elements of the array.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to create an iterator from.
  > 
  >  Returns an iterator that yields each element of the array in order.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::iter" {
  >    let arr = [1, 2, 3]
  >    let mut sum = 0
  >    arr.iter().each(fn(x) { sum = sum + x })
  >    inspect!(sum, content="6")
  >  }
  >  ```
- #### iter2
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1743:::fn <a href="moonbitlang/core/array#Array">Array</a>::iter2[A](self : <a href="moonbitlang/core/array#Array">Array</a>[A]) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[Int, A]
  ```
  > 
  >  Returns an iterator that provides both indices and values of the array in
  > order.
  > 
  >  Parameters:
  > 
  >  * `self` : The array to iterate over.
  > 
  >  Returns an iterator that yields tuples of index and value pairs, where
  > indices start from 0.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::iter2" {
  >    let arr = [10, 20, 30]
  >    let mut sum = 0
  >    arr.iter2().each(fn(i, x) { sum = sum + i + x })
  >    inspect!(sum, content="63") // (0 + 10) + (1 + 20) + (2 + 30) = 63
  >  }
  >  ```
- #### length
  ```moonbit
  :::source,moonbitlang/core/builtin/arraycore_nonjs.mbt,84:::fn <a href="moonbitlang/core/array#Array">Array</a>::length[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> Int
  ```
  > 
  >  Returns the number of elements in the array.
  > 
  >  Parameters:
  > 
  >  * `array` : The array whose length is to be determined.
  > 
  >  Returns the number of elements in the array as an integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::length" {
  >    let arr = [1, 2, 3]
  >    inspect!(arr.length(), content="3")
  >    let empty : Array[Int] = []
  >    inspect!(empty.length(), content="0")
  >  }
  >  ```
- #### make
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,69:::fn <a href="moonbitlang/core/array#Array">Array</a>::make[T](len : Int, elem : T) -> <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  >  Creates a new array with a specified length and initializes all elements with
  > the given value.
  > 
  >  Parameters:
  > 
  >  * `length` : The length of the array to create. Must be a non-negative
  >    integer.
  >  * `initial_value` : The value used to initialize all elements in the array.
  > 
  >  Returns a new array of type `Array[T]` with `length` elements, where each
  > element is initialized to `initial_value`.
  > 
  >  Throws an error if `length` is negative.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::make" {
  >    let arr = Array::make(3, 42)
  >    inspect!(arr, content="[42, 42, 42]")
  >  }
  >  
  >  test "panic Array::make/negative_length" {
  >    ignore(Array::make(-1, 0))
  >  }
  >  ```
- #### map
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,491:::fn <a href="moonbitlang/core/array#Array">Array</a>::map[T, U](self : <a href="moonbitlang/core/array#Array">Array</a>[T], f : (T) -> U) -> <a href="moonbitlang/core/array#Array">Array</a>[U]
  ```
  > 
  >  Maps a function over the elements of the array.
  > 
  >  #### Example
  >  ```
  >  let v = [3, 4, 5]
  >  let v2 = v.map(fn (x) {x + 1})
  >  assert_eq!(v2, [4, 5, 6])
  >  ```
- #### map\_inplace
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,508:::fn <a href="moonbitlang/core/array#Array">Array</a>::map_inplace[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], f : (T) -> T) -> Unit
  ```
  > 
  >  Maps a function over the elements of the array in place.
  > 
  >  #### Example
  >  ```
  >  let v = [3, 4, 5]
  >  v.map_inplace(fn (x) {x + 1})
  >  assert_eq!(v, [4, 5, 6])
  >  ```
- #### mapi
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,523:::fn <a href="moonbitlang/core/array#Array">Array</a>::mapi[T, U](self : <a href="moonbitlang/core/array#Array">Array</a>[T], f : (Int, T) -> U) -> <a href="moonbitlang/core/array#Array">Array</a>[U]
  ```
  > 
  >  Maps a function over the elements of the array with index.
  > 
  >  #### Example
  >  ```
  >  let v = [3, 4, 5]
  >  let v2 = v.mapi(fn (i, x) {x + i})
  >  assert_eq!(v2, [3, 5, 7])
  >  ```
- #### mapi\_inplace
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,543:::fn <a href="moonbitlang/core/array#Array">Array</a>::mapi_inplace[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], f : (Int, T) -> T) -> Unit
  ```
  > 
  >  Maps a function over the elements of the array with index in place.
  > 
  >  #### Example
  >  ```
  >  let v = [3, 4, 5]
  >  v.mapi_inplace(fn (i, x) {x + i})
  >  assert_eq!(v, [3, 5, 7])
  >  ```
- #### new
  ```moonbit
  :::source,moonbitlang/core/builtin/arraycore_nonjs.mbt,56:::fn <a href="moonbitlang/core/array#Array">Array</a>::new[T](capacity~ : Int = ..) -> <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  >  Creates a new empty array with an optional initial capacity.
  > 
  >  Parameters:
  > 
  >  * `capacity` : The initial capacity of the array. If 0 (default), creates an
  >    array with minimum capacity. Must be non-negative.
  > 
  >  Returns a new empty array of type `Array[T]` with the specified initial
  > capacity.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::new" {
  >    let arr : Array[Int] = Array::new(capacity=10)
  >    inspect!(arr.length(), content="0")
  >    inspect!(arr.capacity(), content="10")
  >  }
  >  
  >  test "Array::new/default" {
  >    let arr : Array[Int] = Array::new()
  >    inspect!(arr.length(), content="0")
  >  }
  >  ```
- #### op\_as\_view
  ```moonbit
  :::source,moonbitlang/core/builtin/arrayview.mbt,243:::fn <a href="moonbitlang/core/array#Array">Array</a>::op_as_view[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], start~ : Int = .., end? : Int) -> <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T]
  ```
  > 
  >  Creates a view of a portion of the array. The view provides read-write access
  > to the underlying array without copying the elements.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to create a view from.
  >  * `start` : The starting index of the view (inclusive). Defaults to 0.
  >  * `end` : The ending index of the view (exclusive). If not provided, defaults
  >    to the length of the array.
  > 
  >  Returns an `ArrayView` that provides a window into the specified portion of
  > the array.
  > 
  >  Throws a panic if the indices are invalid (i.e., `start` is negative, `end`
  > is greater than the array length, or `start` is greater than `end`).
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "op_as_view" {
  >    let arr = [1, 2, 3, 4, 5]
  >    let view = arr[1:4] // Create a view of elements at indices 1, 2, and 3
  >    inspect!(view[0], content="2") // First element of view is arr[1]
  >    inspect!(view.length(), content="3") // View contains 3 elements
  >  }
  >  
  >  test "panic op_as_view/invalid_range" {
  >    let arr = [1, 2, 3]
  >    ignore(arr[2:1]) // Panic: start index greater than end index
  >  }
  >  ```
- #### op\_get
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,147:::fn <a href="moonbitlang/core/array#Array">Array</a>::op_get[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], index : Int) -> T
  ```
  > 
  >  Retrieves an element from the array at the specified index.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to get the element from.
  >  * `index` : The position in the array from which to retrieve the element.
  > 
  >  Returns the element at the specified index.
  > 
  >  Throws a panic if the index is negative or greater than or equal to the
  > length of the array.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::op_get" {
  >    let arr = [1, 2, 3]
  >    inspect!(arr[1], content="2")
  >  }
  >  
  >  test "panic Array::op_get/out_of_bounds" {
  >    let arr = [1, 2, 3]
  >    ignore(arr[3]) // Index out of bounds
  >  }
  >  ```
  > 
  >  @alert unsafe "Panic if index is out of bounds"
- #### op\_set
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,216:::fn <a href="moonbitlang/core/array#Array">Array</a>::op_set[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], index : Int, value : T) -> Unit
  ```
  > 
  >  Sets the element at the specified index in the array to a new value. The
  > original value at that index is overwritten.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to modify.
  >  * `index` : The position in the array where the value will be set.
  >  * `value` : The new value to assign at the specified index.
  > 
  >  Throws an error if `index` is negative or greater than or equal to the length
  > of the array.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::op_set" {
  >    let arr = [1, 2, 3]
  >    arr[1] = 42
  >    inspect!(arr, content="[1, 42, 3]")
  >  }
  >  
  >  test "panic Array::op_set/out_of_bounds" {
  >    let arr = [1, 2, 3]
  >    arr[3] = 42 // Index out of bounds
  >  }
  >  ```
  > 
  >  @alert unsafe "Panic if index is out of bounds."
- #### pop
  ```moonbit
  :::source,moonbitlang/core/builtin/arraycore_nonjs.mbt,270:::fn <a href="moonbitlang/core/array#Array">Array</a>::pop[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> T?
  ```
  > 
  >  Removes the last element from a array and returns it, or `None` if it is empty.
  > 
  >  #### Example
  >  ```
  >  let v = [1, 2, 3]
  >  assert_eq!(v.pop(), Some(3))
  >  assert_eq!(v, [1, 2])
  >  ```
- #### pop\_exn
  ```moonbit
  :::source,moonbitlang/core/builtin/arraycore_nonjs.mbt,286:::fn <a href="moonbitlang/core/array#Array">Array</a>::pop_exn[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> T
  ```
  > 
- #### push
  ```moonbit
  :::source,moonbitlang/core/builtin/arraycore_nonjs.mbt,252:::fn <a href="moonbitlang/core/array#Array">Array</a>::push[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], value : T) -> Unit
  ```
  > 
  >  Adds an element to the end of the array.
  > 
  >  If the array is at capacity, it will be reallocated.
  > 
  >  #### Example
  >  ```
  >  let v = []
  >  v.push(3)
  >  ```
- #### remove
  ```moonbit
  :::source,moonbitlang/core/builtin/arraycore_nonjs.mbt,337:::fn <a href="moonbitlang/core/array#Array">Array</a>::remove[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], index : Int) -> T
  ```
  > 
  >  Remove an element from the array at a given index.
  > 
  >  Removes and returns the element at position index within the array, shifting all elements after it to the left.
  > 
  >  #### Example
  >  ```
  >  let v = [3, 4, 5]
  >  assert_eq!(v.remove(1), 4)
  >  assert_eq!(v, [3, 5])
  >  ```
  >  @alert unsafe "Panic if index is out of bounds."
- #### repeat
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1286:::fn <a href="moonbitlang/core/array#Array">Array</a>::repeat[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], times : Int) -> <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  >  Create a array by repeat a given array for a given times.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  let v = [3, 4].repeat(2)
  >  assert_eq!(v, [3, 4, 3, 4])
  >  ```
- #### reserve\_capacity
  ```moonbit
  :::source,moonbitlang/core/builtin/arraycore_nonjs.mbt,215:::fn <a href="moonbitlang/core/array#Array">Array</a>::reserve_capacity[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], capacity : Int) -> Unit
  ```
  > 
  >  Reserves capacity to ensure that it can hold at least the number of elements
  > specified by the `capacity` argument.
  > 
  >  #### Example
  > 
  >  ```
  >  let v = [1]
  >  v.reserve_capacity(10)
  >  assert_eq!(v.capacity(), 10)
  >  ```
- #### resize
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1241:::fn <a href="moonbitlang/core/array#Array">Array</a>::resize[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], new_len : Int, f : T) -> Unit
  ```
  > 
  >  Resizes an array to a specified length, either by truncating if the new
  > length is smaller, or by appending copies of a default value if the new
  > length is larger.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to be resized.
  >  * `new_length` : The desired length of the array after resizing.
  >  * `default_value` : The value to append when extending the array.
  > 
  >  Throws a panic if `new_length` is negative.
  > 
  >  Examples:
  > 
  >  ```moonbit
  >  test "Array::resize/shrink" {
  >    let arr = [1, 2, 3, 4, 5]
  >    arr.resize(3, 0)
  >    inspect!(arr, content="[1, 2, 3]")
  >  }
  >  
  >  test "Array::resize/extend" {
  >    let arr = [1, 2, 3]
  >    arr.resize(5, 0)
  >    inspect!(arr, content="[1, 2, 3, 0, 0]")
  >  }
  >  
  >  test "panic Array::resize/negative_length" {
  >    let arr = [1, 2, 3]
  >    ignore(arr.resize(-1, 0))
  >  }
  >  ```
  > 
  >  @alert unsafe "Panic if new length is negative."
- #### retain
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1193:::fn <a href="moonbitlang/core/array#Array">Array</a>::retain[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], f : (T) -> Bool) -> Unit
  ```
  > 
  >  Removes all elements from the array that do not satisfy the predicate
  > function, modifying the array in place. The order of remaining elements is
  > preserved.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to be filtered.
  >  * `predicate` : A function that takes an element and returns `true` if the
  >    element should be kept, `false` if it should be removed.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "retain" {
  >    let arr = [1, 2, 3, 4, 5]
  >    arr.retain(fn(x) { x % 2 == 0 })
  >    inspect!(arr, content="[2, 4]")
  >  }
  >  
  >  test "retain/empty_result" {
  >    let arr = [1, 2, 3]
  >    arr.retain(fn(x) { x > 10 })
  >    inspect!(arr, content="[]")
  >  }
  >  
  >  test "retain/keep_all" {
  >    let arr = [1, 2, 3]
  >    arr.retain(fn { _ => true })
  >    inspect!(arr, content="[1, 2, 3]")
  >  }
  >  ```
  >  TODO: perf could be improved
- #### rev
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,694:::fn <a href="moonbitlang/core/array#Array">Array</a>::rev[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  >  Creates a new array with elements in reversed order.
  > 
  >  Parameters:
  > 
  >  * `self` : The array to be reversed.
  > 
  >  Returns a new array containing the same elements as the input array but in
  > reverse order. The original array remains unchanged.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::rev" {
  >    let arr = [1, 2, 3, 4, 5]
  >    inspect!(arr.rev(), content="[5, 4, 3, 2, 1]")
  >    inspect!(arr, content="[1, 2, 3, 4, 5]") // original array unchanged
  >  }
  >  ```
- #### rev\_each
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,428:::fn <a href="moonbitlang/core/array#Array">Array</a>::rev_each[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], f : (T) -> Unit) -> Unit
  ```
  > 
  >  Iterates over the elements of the array in reverse order, applying the given
  > function to each element.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to iterate over.
  >  * `f` : A function that takes an element of type `T` and returns `Unit`. This
  >    function is applied to each element of the array in reverse order.
  > 
  >  Example:
  > 
  >  ```
  >  let v = [3, 4, 5]
  >  let mut sum = 0
  >  v.rev_each(fn(x) { sum = sum - x })
  >  @json.inspect!(sum, content=-12)
  >  ```
- #### rev\_eachi
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,445:::fn <a href="moonbitlang/core/array#Array">Array</a>::rev_eachi[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], f : (Int, T) -> Unit) -> Unit
  ```
  > 
  >  Iterates over the elements of the array with index in reversed order.
  > 
  >  #### Example
  >  ```
  >  let v = [3, 4, 5]
  >  let mut sum = 0
  >  v.rev_eachi(fn(i, x) { sum = sum + x + i })
  >  assert_eq!(sum, 15)
  >  ```
- #### rev\_fold
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1320:::fn <a href="moonbitlang/core/array#Array">Array</a>::rev_fold[A, B](self : <a href="moonbitlang/core/array#Array">Array</a>[A], init~ : B, f : (B, A) -> B) -> B
  ```
  > 
  >  Fold out values from an array according to certain rules in reversed turn.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  let sum = [1, 2, 3, 4, 5].rev_fold(init=0, fn { sum, elem => sum + elem })
  >  assert_eq!(sum, 15)
  >  ```
- #### rev\_foldi
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1358:::fn <a href="moonbitlang/core/array#Array">Array</a>::rev_foldi[A, B](self : <a href="moonbitlang/core/array#Array">Array</a>[A], init~ : B, f : (Int, B, A) -> B) -> B
  ```
  > 
  >  Fold out values from an array according to certain rules in reversed turn with index.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  let sum = [1, 2, 3, 4, 5].rev_foldi(init=0, fn { index, sum, _elem => sum + index })
  >  assert_eq!(sum, 10)
  >  ```
- #### rev\_inplace
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,667:::fn <a href="moonbitlang/core/array#Array">Array</a>::rev_inplace[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> Unit
  ```
  > 
  >  Reverses the order of elements in an array in place, modifying the original
  > array.
  > 
  >  Parameters:
  > 
  >  * `self` : The array to be reversed.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::rev_inplace" {
  >    let arr = [1, 2, 3, 4, 5]
  >    arr.rev_inplace()
  >    inspect!(arr, content="[5, 4, 3, 2, 1]")
  >  }
  >  
  >  test "Array::rev_inplace/empty" {
  >    let arr : Array[Int] = []
  >    arr.rev_inplace()
  >    inspect!(arr, content="[]")
  >  }
  >  ```
- #### rev\_iter
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1711:::fn <a href="moonbitlang/core/array#Array">Array</a>::rev_iter[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
  >  Returns an iterator that yields elements from the array in reverse order,
  > from the last element to the first.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to iterate over in reverse order.
  > 
  >  Returns an iterator that yields each element of the array, starting from the
  > last element and moving towards the first.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::rev_iter" {
  >    let arr = [1, 2, 3]
  >    let result = []
  >    arr.rev_iter().each(fn(x) { result.push(x) })
  >    inspect!(result, content="[3, 2, 1]")
  >  }
  >  ```
- #### search
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,935:::fn <a href="moonbitlang/core/array#Array">Array</a>::search[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#Array">Array</a>[T], value : T) -> Int?
  ```
  > 
  >  Searches for the first occurrence of a value in the array and returns its
  > index.
  > 
  >  Parameters:
  > 
  >  * `self` : The array to search in.
  >  * `value` : The value to search for.
  > 
  >  Returns an `Option` containing the index of the first occurrence of `value`
  > if found, or `None` if the value is not present in the array.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::search" {
  >    let arr = [1, 2, 3, 2, 4]
  >    inspect!(arr.search(2), content="Some(1)") // first occurrence
  >    inspect!(arr.search(5), content="None") // not found
  >  }
  >  ```
- #### search\_by
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,986:::fn <a href="moonbitlang/core/array#Array">Array</a>::search_by[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], f : (T) -> Bool) -> Int?
  ```
  > 
  >  Search the index of the first element that satisfies the predicate.
  > 
  >  #### Example
  > 
  >  ```
  >  let v = [1, 2, 3, 4, 5]
  >  match v.search_by(fn(x) { x == 3 }) {
  >    Some(index) => assert_eq!(index, 2) // 2
  >    None => println("Not found")
  >  }
  >  ```
- #### shrink\_to\_fit
  ```moonbit
  :::source,moonbitlang/core/builtin/arraycore_nonjs.mbt,235:::fn <a href="moonbitlang/core/array#Array">Array</a>::shrink_to_fit[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> Unit
  ```
  > 
  >  Shrinks the capacity of the array as much as possible.
  > 
  >  #### Example
  > 
  >  ```
  >  let v = Array::new(capacity=10)
  >  v.push(1)
  >  v.push(2)
  >  v.push(3)
  >  v.shrink_to_fit()
  >  assert_eq!(v.capacity(), 3)
  >  ```
- #### split
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1645:::fn <a href="moonbitlang/core/array#Array">Array</a>::split[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], pred : (T) -> Bool) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/core/array#Array">Array</a>[T]]
  ```
  > 
  >  Splits an array into chunks using a predicate function. Creates chunks by
  > grouping consecutive elements that do not satisfy the predicate function.
  > Elements that satisfy the predicate function are excluded from the resulting
  > chunks and act as delimiters.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to be split into chunks.
  >  * `predicate` : A function that takes an element and returns `true` if the
  >    element should be used as a delimiter.
  > 
  >  Returns an array of arrays, where each inner array is a chunk of consecutive
  > elements that do not satisfy the predicate.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "split/basic" {
  >    let arr = [1, 0, 2, 0, 3, 0, 4]
  >    inspect!(arr.split(fn(x) { x == 0 }), content="[[1], [2], [3], [4]]")
  >  }
  >  
  >  test "split/empty_chunks" {
  >    let arr = [0, 1, 0, 0, 2, 0]
  >    inspect!(arr.split(fn(x) { x == 0 }), content="[[], [1], [], [2]]")
  >  }
  >  ```
- #### split\_at
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,714:::fn <a href="moonbitlang/core/array#Array">Array</a>::split_at[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], index : Int) -> (<a href="moonbitlang/core/array#Array">Array</a>[T], <a href="moonbitlang/core/array#Array">Array</a>[T])
  ```
  > 
  >  Split the array into two at the given index.
  > 
  >  #### Example
  >  ```
  >  let v = [3, 4, 5]
  >  let (v1, v2) = v.split_at(1)
  >  assert_eq!(v1, [3])
  >  assert_eq!(v2, [4, 5])
  >  ```
  >  TODO: perf could be optimized
  > @alert unsafe "Panic if index is out of bounds."
- #### starts\_with
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,796:::fn <a href="moonbitlang/core/array#Array">Array</a>::starts_with[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#Array">Array</a>[T], prefix : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> Bool
  ```
  > 
  >  Checks if the array begins with all elements of the provided prefix array in
  > order.
  > 
  >  Parameters:
  > 
  >  * `self` : The array to check against.
  >  * `prefix` : The array containing the sequence of elements to look for at the
  >    beginning.
  > 
  >  Returns `true` if the array starts with all elements in `prefix` in the same
  > order, `false` otherwise. An empty prefix array always returns `true`, and a
  > prefix longer than the array always returns `false`.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::starts_with" {
  >    let arr = [1, 2, 3, 4, 5]
  >    inspect!(arr.starts_with([1, 2]), content="true")
  >    inspect!(arr.starts_with([2, 3]), content="false")
  >    inspect!(arr.starts_with([]), content="true")
  >    inspect!(arr.starts_with([1, 2, 3, 4, 5, 6]), content="false")
  >  }
  >  ```
- #### strip\_prefix
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,870:::fn <a href="moonbitlang/core/array#Array">Array</a>::strip_prefix[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#Array">Array</a>[T], prefix : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> <a href="moonbitlang/core/array#Array">Array</a>[T]?
  ```
  > 
  >  Removes a prefix from an array if it exists.
  > 
  >  Parameters:
  > 
  >  * `array` : The array to remove the prefix from.
  >  * `prefix` : The array to be removed from the beginning of `array`.
  > 
  >  Returns `Some(array)` containing the remaining elements after removing the
  > prefix if the array starts with the prefix, or `None` if the array doesn't
  > start with the prefix.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "strip_prefix" {
  >    let arr = [1, 2, 3, 4, 5]
  >    inspect!(arr.strip_prefix([1, 2]), content="Some([3, 4, 5])")
  >    inspect!(arr.strip_prefix([2, 3]), content="None")
  >  }
  >  ```
- #### strip\_suffix
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,900:::fn <a href="moonbitlang/core/array#Array">Array</a>::strip_suffix[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/array#Array">Array</a>[T], suffix : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> <a href="moonbitlang/core/array#Array">Array</a>[T]?
  ```
  > 
  >  Strip a suffix from the array.
  > 
  >  If the array ends with the suffix, return the array before the suffix, otherwise return None.
  > 
  >  #### Example
  >  ```
  >  let v = [3, 4, 5]
  >  let v2 = v.strip_suffix([5])
  >  assert_eq!(v2, Some([3, 4]))
  >  ```
- #### swap
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,1148:::fn <a href="moonbitlang/core/array#Array">Array</a>::swap[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], i : Int, j : Int) -> Unit
  ```
  > 
  >  Swaps the values at two positions in the array.
  > 
  >  Parameters:
  > 
  >  * `array` : The array in which to swap elements.
  >  * `index1` : The index of the first element to be swapped.
  >  * `index2` : The index of the second element to be swapped.
  > 
  >  Throws an error if either index is negative or greater than or equal to the
  > length of the array.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::swap" {
  >    let arr = [1, 2, 3]
  >    arr.swap(0, 2)
  >    inspect!(arr, content="[3, 2, 1]")
  >  }
  >  
  >  test "panic Array::swap/out_of_bounds" {
  >    let arr = [1, 2, 3]
  >    ignore(arr.swap(0, 3)) // Index out of bounds
  >  }
  >  ```
  >  @alert unsafe "Panic if index is out of bounds."
- #### unsafe\_blit
  ```moonbit
  :::source,moonbitlang/core/builtin/array_block.mbt,49:::fn <a href="moonbitlang/core/array#Array">Array</a>::unsafe_blit[A](dst : <a href="moonbitlang/core/array#Array">Array</a>[A], dst_offset : Int, src : <a href="moonbitlang/core/array#Array">Array</a>[A], src_offset : Int, len : Int) -> Unit
  ```
  > 
  >  Copies elements from one array to another array. Works correctly even when
  > the source and destination arrays overlap.
  > 
  >  Parameters:
  > 
  >  * `dst` : The destination array where elements will be copied to.
  >  * `dst_offset` : The starting index in the destination array where elements
  >    should be copied.
  >  * `src` : The source array from which elements will be copied.
  >  * `src_offset` : The starting index in the source array from which elements
  >    should be copied.
  >  * `len` : The number of elements to copy.
  > 
  >  The behavior is undefined if any of the following conditions are met:
  > 
  >  * `len` is negative
  >  * `dst_offset` is negative
  >  * `src_offset` is negative
  >  * `dst_offset + len` exceeds the length of destination array
  >  * `src_offset + len` exceeds the length of source array
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::unsafe_blit" {
  >    let src = [1, 2, 3, 4, 5]
  >    let dst = [0, 0, 0, 0, 0]
  >    Array::unsafe_blit(dst, 1, src, 2, 2)
  >    inspect!(dst, content="[0, 3, 4, 0, 0]")
  >  }
  >  ```
  > 
  >  @alert unsafe "Panic if the indices or length are out of bounds"
- #### unsafe\_blit\_fixed
  ```moonbit
  :::source,moonbitlang/core/builtin/array_block.mbt,93:::fn <a href="moonbitlang/core/array#Array">Array</a>::unsafe_blit_fixed[A](dst : <a href="moonbitlang/core/array#Array">Array</a>[A], dst_offset : Int, src : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A], src_offset : Int, len : Int) -> Unit
  ```
  > 
  >  Copies elements from a fixed-size array to a dynamic array. The arrays may
  > overlap, in which case the copy is performed in a way that preserves the
  > data.
  > 
  >  Parameters:
  > 
  >  * `dst` : The destination dynamic array where elements will be copied to.
  >  * `dst_offset` : The starting index in the destination array where copying
  >    begins.
  >  * `src` : The source fixed-size array from which elements will be copied.
  >  * `src_offset` : The starting index in the source array from which copying
  >    begins.
  >  * `len` : The number of elements to copy.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::unsafe_blit_fixed" {
  >    let src = FixedArray::make(5, 0)
  >    let dst = Array::make(5, 0)
  >    for i in 0..<5 {
  >      src[i] = i + 1
  >    }
  >    Array::unsafe_blit_fixed(dst, 1, src, 0, 2)
  >    inspect!(dst, content="[0, 1, 2, 0, 0]")
  >  }
  >  ```
- #### unsafe\_get
  ```moonbit
  :::source,moonbitlang/core/builtin/array.mbt,114:::fn <a href="moonbitlang/core/array#Array">Array</a>::unsafe_get[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T], idx : Int) -> T
  ```
  > 
  >  Retrieves the element at the specified index from an array without bounds
  > checking.
  > 
  >  Parameters:
  > 
  >  * `array` : The array from which to retrieve the element.
  >  * `index` : The position in the array from which to retrieve the element.
  > 
  >  Returns the element at the specified index.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Array::unsafe_get/basic" {
  >    let arr = [1, 2, 3]
  >    inspect!(arr.unsafe_get(1), content="2")
  >  }
  >  ```
  > 
- #### unsafe\_pop
  ```moonbit
  :::source,moonbitlang/core/builtin/arraycore_nonjs.mbt,315:::fn <a href="moonbitlang/core/array#Array">Array</a>::unsafe_pop[T](self : <a href="moonbitlang/core/array#Array">Array</a>[T]) -> T
  ```
  > 
  >  Removes and returns the last element from the array.
  > 
  >  Parameters:
  > 
  >  * `array` : The array from which to remove and return the last element.
  > 
  >  Returns the last element of the array before removal.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "unsafe_pop" {
  >    let arr = [1, 2, 3]
  >    inspect!(arr.unsafe_pop(), content="3")
  >    inspect!(arr, content="[1, 2]")
  >  }
  >  
  >  test "panic unsafe_pop/empty" {
  >    let arr : Array[Int] = []
  >    ignore(arr.unsafe_pop()) // Panics when array is empty
  >  }
  >  ```
  > 
  >  @alert unsafe "Panic if the array is empty."

## ArrayView

```moonbit
:::source,moonbitlang/core/builtin/arrayview.mbt,27:::type ArrayView[T]
```

 An `ArrayView` represents a view into a section of an array without copying the data.

 #### Example

 ```moonbit
 let arr = [1, 2, 3, 4, 5]
 let view = arr[1:4]  // Creates a view of elements at indices 1,2,3
 assert_eq!(view[0], 2)
 assert_eq!(view.length(), 3)
 ```
 @alert deprecated "use @array.View instead"

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,241:::impl[X : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,241:::fn to_json[X : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[X]) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### length
  ```moonbit
  :::source,moonbitlang/core/builtin/arrayview.mbt,51:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::length[T](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T]) -> Int
  ```
  > 
  >  Returns the length (number of elements) of an array view.
  > 
  >  Parameters:
  > 
  >  * `array_view` : The array view whose length is to be determined.
  > 
  >  Returns an integer representing the number of elements in the array view.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "ArrayView::length" {
  >    let arr = [1, 2, 3, 4, 5]
  >    let view = arr[2:4]
  >    inspect!(view.length(), content="2")
  >  }
  >  ```
- #### op\_as\_view
  ```moonbit
  :::source,moonbitlang/core/builtin/arrayview.mbt,299:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::op_as_view[T](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T], start~ : Int = .., end? : Int) -> <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T]
  ```
  > 
  >  Creates a new view into a portion of the array view.
  > 
  >  Parameters:
  > 
  >  * `self` : The array view to create a new view from.
  >  * `start` : The starting index in the current view (inclusive). Defaults to
  >  0. 
  >  * `end` : The ending index in the current view (exclusive). Defaults to the
  >    length of the current view.
  > 
  >  Returns a new `ArrayView` that provides a window into the specified portion
  > of the original array view. The indices are relative to the start of the
  > current view.
  > 
  >  Throws a panic if:
  > 
  >  * `start` is negative
  >  * `end` is greater than the length of the current view
  >  * `start` is greater than `end`
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "ArrayView::op_as_view" {
  >    let arr = [1, 2, 3, 4, 5]
  >    let view = arr[1:4] // view = [2, 3, 4]
  >    let subview = view[1:2] // subview = [3]
  >    inspect!(subview[0], content="3")
  >  }
  >  ```
  > 
  >  ```moonbit
  >  test "panic ArrayView::op_as_view/invalid_range" {
  >    let arr = [1, 2, 3, 4, 5]
  >    let view = arr[1:4]
  >    ignore(view[2:5]) // Panic: end index out of bounds
  >  }
  >  ```
- #### op\_get
  ```moonbit
  :::source,moonbitlang/core/builtin/arrayview.mbt,85:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::op_get[T](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T], index : Int) -> T
  ```
  > 
  >  Retrieves an element at the specified index from the array view.
  > 
  >  Parameters:
  > 
  >  * `self` : The array view to access.
  >  * `index` : The position in the array view from which to retrieve the
  >    element.
  > 
  >  Returns the element at the specified index.
  > 
  >  Throws a runtime error if the index is out of bounds (less than 0 or greater
  > than or equal to the length of the array view).
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "ArrayView::op_get" {
  >    let arr = [1, 2, 3, 4, 5]
  >    let view = arr[2:4]
  >    inspect!(view[0], content="3")
  >    inspect!(view[1], content="4")
  >  }
  >  
  >  test "panic ArrayView::op_get/out_of_bounds" {
  >    let arr = [1, 2, 3]
  >    let view = arr[1:]
  >    ignore(view[2]) // Index out of bounds
  >  }
  >  ```
- #### op\_set
  ```moonbit
  :::source,moonbitlang/core/builtin/arrayview.mbt,158:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::op_set[T](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T], index : Int, value : T) -> Unit
  ```
  > 
  >  Sets the value at the specified index in the array view.
  > 
  >  Parameters:
  > 
  >  * `array_view` : The array view to modify.
  >  * `index` : The position in the array view where the value will be set.
  >  * `value` : The value to be assigned at the specified index.
  > 
  >  Throws a panic if `index` is negative or greater than or equal to the length
  > of the array view.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "ArrayView::op_set" {
  >    let arr = [1, 2, 3, 4, 5]
  >    let view = arr[1:4] // view contains [2, 3, 4]
  >    view.op_set(1, 42)
  >    inspect!(arr, content="[1, 2, 42, 4, 5]")
  >  }
  >  
  >  test "panic ArrayView::op_set/out_of_bounds" {
  >    let arr = [1, 2, 3]
  >    let view = arr[1:]
  >    ignore(view.op_set(2, 42)) // Index out of bounds
  >  }
  >  ```
  > 
  >  @alert unsafe "Panic if index is out of bounds."
- #### swap
  ```moonbit
  :::source,moonbitlang/core/builtin/arrayview.mbt,200:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::swap[T](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T], i : Int, j : Int) -> Unit
  ```
  > 
  >  Swaps two elements in the array view at the specified indices.
  > 
  >  Parameters:
  > 
  >  * `self` : The array view in which to swap elements.
  >  * `i` : The index of the first element to be swapped.
  >  * `j` : The index of the second element to be swapped.
  > 
  >  Throws a panic if either index is negative or greater than or equal to the
  > length of the array view.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "ArrayView::swap" {
  >    let arr = [1, 2, 3, 4, 5]
  >    let view = arr[1:4] // view = [2, 3, 4]
  >    view.swap(0, 2) // view = [4, 3, 2]
  >    inspect!(view, content="[4, 3, 2]")
  >  }
  >  
  >  test "panic ArrayView::swap/out_of_bounds" {
  >    let view = [1, 2, 3][:]
  >    ignore(view.swap(0, 3)) // Index out of bounds
  >  }
  >  ```
  > 
  >  @alert unsafe "Panic if index is out of bounds"
- #### unsafe\_get
  ```moonbit
  :::source,moonbitlang/core/builtin/arrayview.mbt,124:::fn <a href="moonbitlang/core/array#ArrayView">ArrayView</a>::unsafe_get[T](self : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T], index : Int) -> T
  ```
  > 
  >  Retrieves an element from the array view at the specified index without
  > performing bounds checking.
  > 
  >  Parameters:
  > 
  >  * `array_view` : The array view to retrieve the element from.
  >  * `index` : The position in the array view from which to retrieve the
  >    element.
  > 
  >  Returns the element at the specified index in the array view.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "ArrayView::unsafe_get" {
  >    let arr = [1, 2, 3, 4, 5]
  >    let view = arr[1:4]
  >    inspect!(view.unsafe_get(1), content="3")
  >  }
  >  
  >  test "panic ArrayView::unsafe_get/out_of_bounds" {
  >    let arr = [1, 2, 3]
  >    let view = arr[1:]
  >    ignore(view.unsafe_get(5)) // Index out of bounds
  >  }
  >  ```
  > 

## BigInt

```moonbit
:::source,moonbitlang/core/builtin/bigint_nonjs.mbt,33:::type BigInt
```

 A big integer represented as an array of Int.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,240:::impl <a href="moonbitlang/core/builtin#Add">Add</a> for <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,240:::fn op_add(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, other : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
    ```
    > 
    >  Adds two arbitrary-precision integers. Handles positive and negative numbers
    > correctly by converting subtraction of negative numbers into addition of
    > positive numbers.
    > 
    >  Parameters:
    > 
    >  * `self` : The first big integer to add.
    >  * `other` : The second big integer to add.
    > 
    >  Returns a new `BigInt` that represents the sum of the two input numbers.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "BigInt::op_add" {
    >    let a = 9223372036854775807N // Max value of Int64
    >    let b = 1N
    >    inspect!(a + b, content="9223372036854775808") // Beyond Int64 range
    >    inspect!(-a + -b, content="-9223372036854775808")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,1470:::impl <a href="moonbitlang/core/builtin#BitAnd">BitAnd</a> for <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,1470:::fn land(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, other : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
    ```
    > 
    >  Performs a bitwise AND operation between two arbitrary-precision integers.
    > 
    >  The operation is performed using two's complement representation, which means
    > it handles both positive and negative numbers correctly. For negative
    > numbers, the function first converts them to their two's complement form,
    > performs the AND operation, and then converts the result back if necessary.
    > 
    >  Parameters:
    > 
    >  * `self` : The first arbitrary-precision integer operand.
    >  * `other` : The second arbitrary-precision integer operand.
    > 
    >  Returns a new `BigInt` representing the result of the bitwise AND operation.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "BigInt::land" {
    >    let a = BigInt::from_string("42") // 0b101010
    >    let b = BigInt::from_string("-12") // ~0b1011 + 1
    >    inspect!(a & b, content="32") // 0b100000
    >  }
    >  
    >  test "BigInt::land/negative" {
    >    let a = BigInt::from_string("-8") // ~0b111 + 1
    >    let b = BigInt::from_string("-4") // ~0b11 + 1
    >    inspect!(a & b, content="-8") // ~0b1011 + 1
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,1579:::impl <a href="moonbitlang/core/builtin#BitOr">BitOr</a> for <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,1579:::fn lor(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, other : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
    ```
    > 
    >  Performs a bitwise OR operation between two arbitrary-precision integers,
    > following two's complement representation for negative numbers.
    > 
    >  Parameters:
    > 
    >  * `self` : The first arbitrary-precision integer operand.
    >  * `other` : The second arbitrary-precision integer operand.
    > 
    >  Returns a new `BigInt` representing the result of the bitwise OR operation.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "BigInt::lor" {
    >    let a = BigInt::from_string("42")
    >    let b = BigInt::from_string("-12")
    >    inspect!(a | b, content="-2")
    >    let c = BigInt::from_string("-8")
    >    let d = BigInt::from_string("-4")
    >    inspect!(c | d, content="-4")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,1691:::impl <a href="moonbitlang/core/builtin#BitXOr">BitXOr</a> for <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,1691:::fn lxor(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, other : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
    ```
    > 
    >  Performs a bitwise XOR operation between two `BigInt` values, treating them
    > as two's complement binary numbers.
    > 
    >  Parameters:
    > 
    >  * `self` : The first `BigInt` operand.
    >  * `other` : The second `BigInt` operand.
    > 
    >  Returns a new `BigInt` value representing the bitwise XOR of the two
    > operands.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "BigInt::lxor" {
    >    let a = BigInt::from_string("42")
    >    let b = BigInt::from_string("-7")
    >    inspect!(a ^ b, content="-45")
    >  }
    >  
    >  test "BigInt::lxor/zero" {
    >    let a = BigInt::from_string("42")
    >    inspect!(a ^ a, content="0") // XOR with self gives 0
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,853:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,853:::fn compare(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, other : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>) -> Int
    ```
    > 
    >  Compares two arbitrary-precision integers and returns their relative order.
    > 
    >  Parameters:
    > 
    >  * `self` : The first arbitrary-precision integer to compare.
    >  * `other` : The second arbitrary-precision integer to compare.
    > 
    >  Returns an integer indicating the relative order:
    > 
    >  * A negative value if `self` is less than `other`
    >  * Zero if `self` equals `other`
    >  * A positive value if `self` is greater than `other`
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "BigInt::compare" {
    >    let a = BigInt::from_string("42")
    >    let b = BigInt::from_string("24")
    >    let c = BigInt::from_string("-42")
    >    inspect!(a.compare(b), content="1") // 42 > 24
    >    inspect!(b.compare(a), content="-1") // 24 < 42
    >    inspect!(c.compare(a), content="-1") // -42 < 42
    >    inspect!(a.compare(a), content="0") // 42 = 42
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,461:::impl <a href="moonbitlang/core/builtin#Div">Div</a> for <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,461:::fn op_div(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, other : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
    ```
    > 
    >  Performs division between two arbitrary-precision integers, following
    > standard arithmetic rules for signed division.
    > 
    >  Parameters:
    > 
    >  * `self` : The dividend big integer.
    >  * `other` : The divisor big integer.
    > 
    >  Returns the quotient of the division.
    > 
    >  Throws a panic if the divisor is zero.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "BigInt::op_div" {
    >    let a = BigInt::from_string("100")
    >    let b = BigInt::from_string("20")
    >    inspect!(a / b, content="5")
    >    inspect!(-a / b, content="-5")
    >    inspect!(a / -b, content="-5")
    >    inspect!(-a / -b, content="5")
    >  }
    >  
    >  test "panic BigInt::op_div/division_by_zero" {
    >    let a = BigInt::from_string("100")
    >    let b = BigInt::from_string("0")
    >    ignore(a / b) // Division by zero
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,900:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,900:::fn op_equal(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, other : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>) -> Bool
    ```
    > 
    >  Compares two `BigInt` values for equality. Returns true if both numbers have
    > the same sign and magnitude.
    > 
    >  Parameters:
    > 
    >  * `self` : The first `BigInt` value to compare.
    >  * `other` : The second `BigInt` value to compare.
    > 
    >  Returns `true` if the two `BigInt` values are equal, `false` otherwise.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "BigInt::op_equal" {
    >    let a = 123456789N
    >    let b = 123456789N
    >    let c = -123456789N
    >    inspect!(a == b, content="true")
    >    inspect!(a == c, content="false")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,510:::impl <a href="moonbitlang/core/builtin#Mod">Mod</a> for <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,510:::fn op_mod(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, other : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
    ```
    > 
    >  Calculates the modulo (remainder) of dividing one big integer by another.
    > 
    >  Parameters:
    > 
    >  * `self` : The dividend big integer.
    >  * `other` : The divisor big integer.
    > 
    >  Returns the remainder of the division operation.
    > 
    >  Throws an error if `other` is zero.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "BigInt::op_mod" {
    >    let a = 42N
    >    let b = 5N
    >    inspect!(a % b, content="2")
    >    let c = -42N
    >    let d = -5N
    >    inspect!(c % d, content="-2")
    >  }
    >  
    >  test "panic BigInt::op_mod/divide_by_zero" {
    >    let a = 42N
    >    ignore(a % 0N) // Division by zero
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,364:::impl <a href="moonbitlang/core/builtin#Mul">Mul</a> for <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,364:::fn op_mul(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, other : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
    ```
    > 
    >  Multiplies two arbitrary-precision integers. Uses the most efficient
    > multiplication algorithm based on the size of the operands:
    > 
    >  * Grade school multiplication for small numbers
    >  * Karatsuba multiplication for large numbers
    > 
    >  Parameters:
    > 
    >  * `self` : The first arbitrary-precision integer to multiply.
    >  * `other` : The second arbitrary-precision integer to multiply.
    > 
    >  Returns the product of the two numbers. The sign of the result follows the
    > standard multiplication rules: positive if both operands have the same sign,
    > negative otherwise.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "BigInt::op_mul" {
    >    let a = 12345678901234567890N
    >    let b = -98765432109876543210N
    >    inspect!(a * b, content="-1219326311370217952237463801111263526900")
    >    inspect!(a * 0N, content="0")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,211:::impl <a href="moonbitlang/core/builtin#Neg">Neg</a> for <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,211:::fn op_neg(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
    ```
    > 
    >  Negates a big integer, returning a new big integer with the opposite sign. If
    > the input is zero, returns zero.
    > 
    >  Parameters:
    > 
    >  * `self` : The big integer to negate.
    > 
    >  Returns a new big integer with the opposite sign of the input, or zero if the
    > input is zero.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "BigInt::op_neg" {
    >    inspect!(-42N, content="-42")
    >    inspect!(-(-42N), content="42")
    >    inspect!(-0N, content="0")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,700:::impl <a href="moonbitlang/core/builtin#Shl">Shl</a> for <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,700:::fn op_shl(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, n : Int) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
    ```
    > 
    >  Performs a left shift operation on a `BigInt` value. Preserves the sign of
    > the original number while shifting only its absolute value.
    > 
    >  Parameters:
    > 
    >  * `self` : The `BigInt` value to be shifted.
    >  * `n` : The number of positions to shift left. Must be non-negative.
    > 
    >  Returns a new `BigInt` value that is the result of shifting the absolute
    > value of the input left by `n` positions, maintaining the original sign.
    > 
    >  Throws a panic if the shift count is negative.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "BigInt::op_shl" {
    >    let x = 5N
    >    inspect!(x << 2, content="20")
    >    let y = -5N
    >    inspect!(y << 2, content="-20")
    >  }
    >  
    >  test "panic BigInt::op_shl/negative_shift" {
    >    let x = 5N
    >    ignore(x << -1) // Panics with "negative shift count"
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,1004:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,1004:::fn output(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
    >  Formats and writes a `BigInt` value to a logger by converting it to a string
    > representation.
    > 
    >  Implements the `Show` trait for `BigInt` type, allowing `BigInt` values to be
    > converted to strings and used in string interpolation.
    > 
    >  Parameters:
    > 
    >  * `self` : The `BigInt` value to be formatted.
    >  * `logger` : A logger that implements the `Logger` trait, which will receive
    >    the formatted string output.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "BigInt::output" {
    >    let n = 12345678901234567890N
    >    inspect!(n, content="12345678901234567890")
    >    let neg = -42N
    >    inspect!(neg, content="-42")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,764:::impl <a href="moonbitlang/core/builtin#Shr">Shr</a> for <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,764:::fn op_shr(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, n : Int) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
    ```
    > 
    >  Performs arithmetic right shift operation on a big integer value. The shift
    > operation preserves the sign of the number while shifting the absolute value
    > right by `n` bits. For negative numbers, the result is rounded towards
    > negative infinity.
    > 
    >  Parameters:
    > 
    >  * `self` : The big integer value to be shifted.
    >  * `n` : The number of bits to shift right. Must be non-negative.
    > 
    >  Returns a new `BigInt` value that represents the result of shifting `self`
    > right by `n` bits.
    > 
    >  Throws a panic if `n` is negative.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "BigInt::op_shr" {
    >    let n = BigInt::from_string("1024")
    >    inspect!(n >> 3, content="128")
    >    let neg = BigInt::from_string("-1024")
    >    inspect!(neg >> 3, content="-128")
    >  }
    >  
    >  test "panic BigInt::op_shr/negative_shift" {
    >    let n = BigInt::from_string("1024")
    >    ignore(n >> -1) // Panics with "negative shift count"
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,288:::impl <a href="moonbitlang/core/builtin#Sub">Sub</a> for <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,288:::fn op_sub(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, other : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
    ```
    > 
    >  Subtracts one arbitrary-precision integer from another. Handles positive and
    > negative numbers appropriately.
    > 
    >  Parameters:
    > 
    >  * `self` : The minuend (the number to subtract from).
    >  * `other` : The subtrahend (the number to be subtracted).
    > 
    >  Returns a new `BigInt` representing the difference between `self` and
    > `other`.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "BigInt::op_sub" {
    >    let a = 12345678901234567890N
    >    let b = 9876543210987654321N
    >    inspect!(a - b, content="2469135690246913569")
    >    inspect!(-a - b, content="-22222222112222222211")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,218:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,218:::fn to_json(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### asr
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_deprecated.mbt,18:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::asr(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, n : Int) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
- #### from\_hex
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,1112:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::from_hex(input : String) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  >  Converts a hexadecimal string to a `BigInt`. The string can be prefixed with
  > a minus sign (`-`) to indicate a negative number. The string must contain
  > only hexadecimal digits (`0-9`, `a-f`, or `A-F`).
  > 
  >  Parameters:
  > 
  >  * `input` : A string containing the hexadecimal representation of an integer.
  >    Must be non-empty and contain only valid hexadecimal digits. May be prefixed
  >    with a minus sign to indicate a negative number.
  > 
  >  Returns a `BigInt` value representing the hexadecimal number.
  > 
  >  Throws a runtime error if:
  > 
  >  * The input string is empty.
  >  * The input string contains characters other than hexadecimal digits (0-9,
  >    a-f, A-F) or a leading minus sign.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "BigInt::from_hex" {
  >    inspect!(BigInt::from_hex("ff"), content="255")
  >    inspect!(BigInt::from_hex("-ff"), content="-255")
  >    inspect!(BigInt::from_hex("DEADBEEF"), content="3735928559")
  >  }
  >  
  >  test "panic BigInt::from_hex/invalid_input" {
  >    ignore(BigInt::from_hex("")) // Empty string
  >    ignore(BigInt::from_hex("0x123")) // Invalid prefix
  >    ignore(BigInt::from_hex("12g")) // Invalid character
  >  }
  >  ```
- #### from\_int
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,100:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::from_int(n : Int) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  >  Converts a 32-bit signed integer to a BigInt.
  > 
  >  Parameters:
  > 
  >  * `value` : The 32-bit signed integer (`Int`) to be converted.
  > 
  >  Returns a `BigInt` equivalent to the input integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "BigInt::from_int" {
  >    let big = BigInt::from_int(42)
  >    inspect!(big, content="42")
  >    let neg = BigInt::from_int(-42)
  >    inspect!(neg, content="-42")
  >  }
  >  ```
- #### from\_int64
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,145:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::from_int64(n : Int64) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  >  Converts a signed 64-bit integer to a `BigInt`.
  > 
  >  Parameters:
  > 
  >  * `number` : A 64-bit signed integer (`Int64`) to be converted.
  > 
  >  Returns a `BigInt` value that represents the same numerical value as the
  > input.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "BigInt::from_int64" {
  >    let big = BigInt::from_int64(9223372036854775807L) // max value of Int64
  >    inspect!(big, content="9223372036854775807")
  >    let neg = BigInt::from_int64(-9223372036854775808L) // min value of Int64
  >    inspect!(neg, content="-9223372036854775808")
  >  }
  >  ```
- #### from\_octets
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,1344:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::from_octets(input : Bytes, signum~ : Int = ..) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  >  Converts a big-endian byte sequence to a `BigInt` value with an optional
  > sign. Interprets the input bytes as a big-endian representation of an
  > unsigned integer, and applies the specified sign to create the final `BigInt`
  > value.
  > 
  >  Parameters:
  > 
  >  * `bytes` : A sequence of bytes representing the magnitude of the number in
  >    big-endian order. The sequence must not be empty unless `sign` is 0.
  >  * `sign` : An integer specifying the sign of the resulting number (default:
  >    1\). A value of 1 creates a positive number, -1 creates a negative number, and
  >    0 returns zero regardless of the input bytes.
  > 
  >  Returns a `BigInt` value representing the number encoded in the byte sequence
  > with the specified sign.
  > 
  >  Throws a panic if the input byte sequence is empty and the sign is not 0.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "BigInt::from_octets" {
  >    let bytes = b"\x01\x02\x03" // Represents 0x010203
  >    let positive = BigInt::from_octets(bytes)
  >    let negative = BigInt::from_octets(bytes, signum=-1)
  >    inspect!(positive, content="66051")
  >    inspect!(negative, content="-66051")
  >  }
  >  
  >  test "panic BigInt::from_octets/empty" {
  >    ignore(BigInt::from_octets(b"")) // Panics with "empty octet string"
  >  }
  >  ```
- #### from\_string
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,1040:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::from_string(input : String) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  >  Converts a decimal string representation to a BigInt value. The string can
  > optionally start with a minus sign (-) to indicate a negative number,
  > followed by one or more decimal digits.
  > 
  >  Parameters:
  > 
  >  * `input` : The string to be converted. Must be a valid decimal number string
  >    consisting of optional leading minus sign followed by decimal digits (0-9).
  > 
  >  Returns a `BigInt` value representing the decimal number in the input string.
  > 
  >  Throws a panic if:
  > 
  >  * The input string is empty
  >  * The input string contains non-decimal digits
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "BigInt::from_string" {
  >    let pos = BigInt::from_string("12345")
  >    let neg = BigInt::from_string("-12345")
  >    inspect!(pos, content="12345")
  >    inspect!(neg, content="-12345")
  >  }
  >  
  >  test "panic BigInt::from_string/invalid" {
  >    ignore(BigInt::from_string("")) // Empty string
  >    ignore(BigInt::from_string("12a34")) // Invalid character
  >  }
  >  ```
- #### from\_uint
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,121:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::from_uint(n : UInt) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  >  Converts an unsigned 32-bit integer to a `BigInt`.
  > 
  >  Parameters:
  > 
  >  * `value` : The unsigned 32-bit integer to be converted.
  > 
  >  Returns a `BigInt` representing the same numerical value as the input.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "BigInt::from_uint" {
  >    let n = 42U
  >    inspect!(BigInt::from_uint(n), content="42")
  >  }
  >  ```
- #### from\_uint64
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,174:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::from_uint64(n : UInt64) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  >  Converts an unsigned 64-bit integer to a `BigInt`.
  > 
  >  Parameters:
  > 
  >  * `value` : The unsigned 64-bit integer (`UInt64`) to be converted.
  > 
  >  Returns a new `BigInt` with the same value as the input. The resulting
  > `BigInt` will always have a positive sign since the input is an unsigned
  > integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "BigInt::from_uint64" {
  >    let n = BigInt::from_uint64(12345678901234567890UL)
  >    inspect!(n, content="12345678901234567890")
  >    let zero = BigInt::from_uint64(0UL)
  >    inspect!(zero, content="0")
  >  }
  >  ```
- #### is\_zero
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,822:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::is_zero(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>) -> Bool
  ```
  > 
  >  Checks whether a `BigInt` value is equal to zero.
  > 
  >  Parameters:
  > 
  >  * `self` : The `BigInt` value to be checked.
  > 
  >  Returns `true` if the `BigInt` is zero, `false` otherwise.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "BigInt::is_zero" {
  >    inspect!(0N.is_zero(), content="true")
  >    inspect!(42N.is_zero(), content="false")
  >    inspect!((-1N).is_zero(), content="false")
  >  }
  >  ```
- #### lsl
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_deprecated.mbt,40:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::lsl(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, n : Int) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  >  Left shift a bigint
  > The sign of the result is the same as the sign of the input.
  > Only the absolute value is shifted.
  > 
- #### pow
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,1275:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::pow(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, exp : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, modulus? : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  >  Computes the result of raising a `BigInt` to the power of another `BigInt`,
  > with an optional modulus.
  > 
  >  When a modulus is provided, computes the modular exponentiation using the
  > square-and-multiply algorithm. This is particularly useful in cryptographic
  > applications where direct exponentiation would result in numbers too large to
  > handle efficiently.
  > 
  >  Parameters:
  > 
  >  * `self` : The base number to be raised to a power.
  >  * `exp` : The exponent (must be non-negative).
  >  * `modulus` : Optional modulus for modular exponentiation (must be positive
  >    if provided).
  > 
  >  Returns the result of the exponentiation, or the result modulo `modulus` if a
  > modulus is provided.
  > 
  >  Throws:
  > 
  >  * Aborts if the exponent is negative.
  >  * Aborts if the provided modulus is zero or negative.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "BigInt::pow" {
  >    let base = BigInt::from_string("3")
  >    let exp = BigInt::from_string("4")
  >    inspect!(base.pow(exp), content="81")
  >    inspect!(base.pow(exp, modulus=BigInt::from_string("10")), content="1")
  >  }
  >  
  >  test "panic BigInt::pow/negative_exponent" {
  >    let base = BigInt::from_string("3")
  >    let exp = BigInt::from_string("-1")
  >    ignore(base.pow(exp))
  >  }
  >  ```
- #### shl
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_deprecated.mbt,29:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::shl(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, n : Int) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  >  Left shift a bigint
  > The sign of the result is the same as the sign of the input.
  > Only the absolute value is shifted.
  > 
- #### shr
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_deprecated.mbt,51:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::shr(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, n : Int) -> <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
  ```
  > 
  >  Right shift a bigint
  > The sign of the result is the same as the sign of the input.
  > Only the absolute value is shifted.
  > 
- #### to\_hex
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,1182:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::to_hex(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, uppercase~ : Bool = ..) -> String
  ```
  > 
  >  Converts a big integer to its hexadecimal string representation. The output
  > string has no prefix (like "0x") and uses uppercase letters A-F by default
  > for digits above 9.
  > 
  >  Parameters:
  > 
  >  * `self` : The `BigInt` value to be converted.
  >  * `uppercase` : Whether to use uppercase (A-F) or lowercase (a-f) letters for
  >    hexadecimal digits above 9. Defaults to `true`.
  > 
  >  Returns a string representing the number in hexadecimal format. For negative
  > numbers, the string is prefixed with a minus sign.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "BigInt::to_hex" {
  >    let pos = BigInt::from_string("255")
  >    let neg = BigInt::from_string("-255")
  >    inspect!(pos.to_hex(), content="FF")
  >    inspect!(neg.to_hex(), content="-FF")
  >    inspect!(pos.to_hex(uppercase=false), content="ff")
  >    inspect!(0N.to_hex(), content="0")
  >  }
  >  ```
- #### to\_int
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,1795:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::to_int(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>) -> Int
  ```
  > 
  >  Converts a `BigInt` to a 32-bit signed integer (`Int`).
  > 
  >  Parameters:
  > 
  >  * `self` : The `BigInt` value to be converted.
  > 
  >  Returns a 32-bit signed integer representing the lower 32 bits of the input
  > `BigInt`.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "BigInt::to_int" {
  >    let big = 2147483648N // 2^31
  >    inspect!(big.to_int(), content="-2147483648") // Overflow to Int.min_value
  >  }
  >  ```
- #### to\_int64
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,1843:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::to_int64(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>) -> Int64
  ```
  > 
  >  Converts a `BigInt` to a signed 64-bit integer (`Int64`).
  > 
  >  Parameters:
  > 
  >  * `value` : The `BigInt` value to be converted.
  > 
  >  Returns a 64-bit signed integer (`Int64`) representing the lower 64 bits of
  > the input `BigInt`.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "BigInt::to_int64" {
  >    let big = 9223372036854775807N // max value of Int64
  >    inspect!(big.to_int64(), content="9223372036854775807")
  >    let bigger = big + 1
  >    inspect!(bigger.to_int64(), content="-9223372036854775808") // Overflow to Int64.min_value
  >  }
  >  ```
- #### to\_octets
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,1416:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::to_octets(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>, length? : Int) -> Bytes
  ```
  > 
  >  Converts a non-negative arbitrary-precision integer to a big-endian byte
  > sequence. The output can be padded with leading zeros to meet a specified
  > length requirement, but only if the actual length is less than the requested
  > length.
  > 
  >  Parameters:
  > 
  >  * `self` : The arbitrary-precision integer to convert. Must be non-negative.
  >  * `length` : Optional minimum length of the output byte sequence. If
  >    provided, must be positive. Defaults to 1 if not specified.
  > 
  >  Returns a byte sequence representing the number in big-endian order, possibly
  > padded with leading zeros to reach the specified length.
  > 
  >  Throws a panic if:
  > 
  >  * The input number is negative
  >  * The specified length is negative or zero
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "BigInt::to_octets" {
  >    let n = BigInt::from_hex("abcdef")
  >    inspect!(n.to_octets(length=4), content="b\"\\x00\\xab\\xcd\\xef\"")
  >    let m = BigInt::from_string("0")
  >    inspect!(m.to_octets(), content="b\"\\x00\"")
  >  }
  >  
  >  test "panic BigInt::to_octets/negative" {
  >    let n = -BigInt::from_hex("abcdef")
  >    ignore(n.to_octets()) // Panics with "negative BigInt"
  >    let m = BigInt::from_hex("abcdef")
  >    ignore(m.to_octets(length=-1)) // Panics with "negative length"
  >  }
  >  ```
- #### to\_string
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,934:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::to_string(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>) -> String
  ```
  > 
  >  Converts a `BigInt` value to its decimal string representation.
  > 
  >  Parameters:
  > 
  >  * `self` : The `BigInt` value to convert to a string.
  > 
  >  Returns a string containing the decimal representation of the number, with a
  > leading minus sign for negative numbers.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "BigInt::to_string" {
  >    let n = 12345678901234567890N
  >    inspect!(n.to_string(), content="12345678901234567890")
  >    let neg = -42N
  >    inspect!(neg.to_string(), content="-42")
  >    let zero = 0N
  >    inspect!(zero.to_string(), content="0")
  >  }
  >  ```
- #### to\_uint
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,1818:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::to_uint(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>) -> UInt
  ```
  > 
  >  Converts a `BigInt` to an unsigned 32-bit integer (`UInt`).
  > 
  >  Parameters:
  > 
  >  * `self` : The `BigInt` value to be converted.
  > 
  >  Returns a `UInt` value representing the lower 32 bits of the input `BigInt`.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "BigInt::to_uint" {
  >    let n = 42N
  >    inspect!(n.to_uint(), content="42")
  >    let neg = -1N
  >    inspect!(neg.to_uint(), content="4294967295") // 2^32 - 1
  >  }
  >  ```
- #### to\_uint64
  ```moonbit
  :::source,moonbitlang/core/builtin/bigint_nonjs.mbt,1867:::fn <a href="moonbitlang/core/bigint#BigInt">BigInt</a>::to_uint64(self : <a href="moonbitlang/core/bigint#BigInt">BigInt</a>) -> UInt64
  ```
  > 
  >  Converts a `BigInt` to an unsigned 64-bit integer (`UInt64`).
  > 
  >  Parameters:
  > 
  >  * `self` : The `BigInt` value to be converted.
  > 
  >  Returns a `UInt64` value representing the lower 64 bits of the input
  > `BigInt`.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "BigInt::to_uint64" {
  >    let n = 12345678901234567890N
  >    inspect!(n.to_uint64(), content="12345678901234567890")
  >    let neg = -1N
  >    inspect!(neg.to_uint64(), content="18446744073709551615") // 2^64 - 1
  >  }
  >  ```

## Failure

```moonbit
:::source,moonbitlang/core/builtin/failure.mbt,36:::pub(all) type! Failure String

```

 Represents a generic test failure type used primarily in test assertions and
validations.

 Since this is a type definition using `type!` syntax, it creates an error
type `Failure` that wraps a `String` value containing the failure message.

 Parameters:

 * `message` : A string describing the nature of the failure.

 Example:

 ```moonbit
 test "Failure" {
   let err : Failure = Failure("Test assertion failed")
   match err {
     Failure(msg) => inspect!(msg, content="Test assertion failed")
   }
 }
 ```

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/show.mbt,160:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/builtin#Failure">Failure</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/show.mbt,160:::fn output(self : <a href="moonbitlang/core/builtin#Failure">Failure</a>, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 

## Hasher

```moonbit
:::source,moonbitlang/core/builtin/hasher.mbt,49:::type Hasher
```

 Represents a hasher that implements the xxHash32 algorithm. The hasher
maintains a mutable accumulator that is updated with each value added to the
hash computation.

 This struct provides methods for combining different types of values into a
single hash value, making it suitable for implementing hash functions for
custom types.

 Example:

 ```moonbit
 test "Hasher/basic" {
   let hasher = Hasher::new()
   hasher.combine_int(42)
   hasher.combine_string("hello")
   inspect!(hasher.finalize(), content="860601284")
 }
 ```

#### mooncakes-io-method-mark-Methods
- #### combine
  ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,99:::fn <a href="moonbitlang/core/builtin#Hasher">Hasher</a>::combine[T : <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>, value : T) -> Unit
  ```
  > 
  >  Combines a hashable value with the current state of the hasher. This is
  > typically used to incrementally build a hash value from multiple components.
  > 
  >  Parameters:
  > 
  >  * `self` : The hasher instance to update.
  >  * `value` : The value to be combined with the current hash state. Must
  >    implement the `Hash` trait.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Hasher::combine" {
  >    let hasher = Hasher::new()
  >    hasher.combine(42)
  >    hasher.combine("hello")
  >    inspect!(hasher.finalize(), content="860601284")
  >  }
  >  ```
- #### combine\_bool
  ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,143:::fn <a href="moonbitlang/core/builtin#Hasher">Hasher</a>::combine_bool(self : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>, value : Bool) -> Unit
  ```
  > 
  >  Combines a boolean value into the current hash state. The boolean value is
  > converted to an integer (1 for true, 0 for false) before being combined with
  > the hash.
  > 
  >  Parameters:
  > 
  >  * `self` : The hasher instance to update.
  >  * `value` : The boolean value to be combined into the hash state.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Hasher::combine_bool" {
  >    let hasher = Hasher::new()
  >    hasher.combine_bool(true)
  >    inspect!(hasher.finalize(), content="-205818221")
  >  }
  >  ```
- #### combine\_byte
  ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,308:::fn <a href="moonbitlang/core/builtin#Hasher">Hasher</a>::combine_byte(self : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>, value : Byte) -> Unit
  ```
  > 
  >  Combines a byte value into the hash state.
  > 
  >  Parameters:
  > 
  >  * `hasher` : The hasher object to update with the byte value.
  >  * `byte` : The byte value to be combined into the hash.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Hasher::combine_byte" {
  >    let hasher = Hasher::new()
  >    hasher.combine_byte(b'\xFF')
  >    inspect!(hasher.finalize(), content="1955036104")
  >  }
  >  ```
- #### combine\_bytes
  ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,331:::fn <a href="moonbitlang/core/builtin#Hasher">Hasher</a>::combine_bytes(self : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>, value : Bytes) -> Unit
  ```
  > 
  >  Combines a byte sequence into the hasher's internal state using xxHash32
  > algorithm. Processes the input bytes in chunks of 4 bytes for efficiency,
  > with remaining bytes processed individually.
  > 
  >  Parameters:
  > 
  >  * `hasher` : The hasher object to update with the byte sequence.
  >  * `bytes` : The byte sequence to be combined into the hash.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Hasher::combine_bytes" {
  >    let hasher = Hasher::new()
  >    hasher.combine_bytes(b"\xFF\x00\xFF\x00")
  >    inspect!(hasher.finalize(), content="-686861102")
  >  }
  >  ```
- #### combine\_char
  ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,389:::fn <a href="moonbitlang/core/builtin#Hasher">Hasher</a>::combine_char(self : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>, value : Char) -> Unit
  ```
  > 
  >  Combines a character value into the hasher's internal state. The character is
  > first converted to its Unicode code point (as an integer) before being
  > combined.
  > 
  >  Parameters:
  > 
  >  * `self` : The hasher instance to update.
  >  * `value` : The character value to be combined into the hash state.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Hasher::combine_char" {
  >    let hasher = Hasher::new()
  >    hasher.combine_char('A')
  >    inspect!(hasher.finalize(), content="-1625495534")
  >  }
  >  ```
- #### combine\_double
  ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,263:::fn <a href="moonbitlang/core/builtin#Hasher">Hasher</a>::combine_double(self : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>, value : Double) -> Unit
  ```
  > 
  >  Combines a double-precision floating-point number into the hasher's internal
  > state by reinterpreting its bits as a 64-bit integer. Maintains consistent
  > hashing behavior regardless of the floating-point value's representation.
  > 
  >  Parameters:
  > 
  >  * `hasher` : The hasher to combine the value into.
  >  * `value` : The double-precision floating-point number to be combined into
  >    the hash.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Hasher::combine_double" {
  >    let hasher = Hasher::new()
  >    hasher.combine_double(3.14)
  >    inspect!(hasher.finalize(), content="-428265677")
  >  }
  >  ```
- #### combine\_float
  ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,287:::fn <a href="moonbitlang/core/builtin#Hasher">Hasher</a>::combine_float(self : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>, value : Float) -> Unit
  ```
  > 
  >  Combines a 32-bit floating-point value into the hasher by reinterpreting its
  > bit pattern as a 32-bit integer. The operation maintains the same hash result
  > regardless of the floating-point value's representation.
  > 
  >  Parameters:
  > 
  >  * `hasher` : The hasher object that maintains the internal state of the
  >    hashing operation.
  >  * `value` : The 32-bit floating-point value to be combined into the hash.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Hasher::combine_float" {
  >    let hasher = Hasher::new()
  >    hasher.combine_float(3.14)
  >    inspect!(hasher.finalize(), content="635116317") // Hash of the bits of 3.14
  >  }
  >  ```
- #### combine\_int
  ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,166:::fn <a href="moonbitlang/core/builtin#Hasher">Hasher</a>::combine_int(self : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>, value : Int) -> Unit
  ```
  > 
  >  Combines a 32-bit integer value into the hasher's internal state. The value
  > is processed
  > as a 4-byte sequence, and the internal accumulator is updated accordingly.
  > 
  >  Parameters:
  > 
  >  * `self` : The hasher instance to update.
  >  * `value` : A 32-bit integer value to be incorporated into the hash.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Hasher::combine_int" {
  >    let hasher = Hasher::new()
  >    hasher.combine_int(42)
  >    inspect!(hasher.finalize(), content="1161967057")
  >  }
  >  ```
- #### combine\_int64
  ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,190:::fn <a href="moonbitlang/core/builtin#Hasher">Hasher</a>::combine_int64(self : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>, value : Int64) -> Unit
  ```
  > 
  >  Combines a 64-bit integer value into the hash state by splitting it into two
  > 32-bit parts and processing them separately. This method is used internally
  > by the hash implementation to incorporate 64-bit integers into the hash
  > computation.
  > 
  >  Parameters:
  > 
  >  * `hasher` : The hasher object whose internal state will be updated.
  >  * `value` : The 64-bit integer value to be incorporated into the hash state.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Hasher::combine_int64" {
  >    let hasher = Hasher::new()
  >    hasher.combine_int64(42L)
  >    inspect!(hasher.finalize(), content="-1962516083")
  >  }
  >  ```
- #### combine\_string
  ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,364:::fn <a href="moonbitlang/core/builtin#Hasher">Hasher</a>::combine_string(self : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>, value : String) -> Unit
  ```
  > 
  >  Combines a string value into the current hash state by processing each
  > character in the string sequentially.
  > 
  >  Parameters:
  > 
  >  * `self` : The hasher object whose state will be updated.
  >  * `value` : The string value to be combined into the hash state.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Hasher::combine_string" {
  >    let hasher = Hasher::new()
  >    hasher.combine_string("hello")
  >    inspect!(hasher.finalize(), content="-655549713")
  >  }
  >  ```
- #### combine\_uint
  ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,215:::fn <a href="moonbitlang/core/builtin#Hasher">Hasher</a>::combine_uint(self : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>, value : UInt) -> Unit
  ```
  > 
  >  Combines an unsigned 32-bit integer into the hasher's internal state by
  > reinterpreting it as a signed integer and incorporating it into the hash
  > computation.
  > 
  >  Parameters:
  > 
  >  * `hasher` : The hasher object to update.
  >  * `value` : The unsigned 32-bit integer value to be combined into the hash.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Hasher::combine_uint" {
  >    let hasher = Hasher::new()
  >    hasher.combine_uint(42U)
  >    inspect!(hasher.finalize(), content="1161967057")
  >  }
  >  ```
- #### combine\_uint64
  ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,239:::fn <a href="moonbitlang/core/builtin#Hasher">Hasher</a>::combine_uint64(self : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>, value : UInt64) -> Unit
  ```
  > 
  >  Combines a 64-bit unsigned integer into the hasher's internal state. Useful
  > for hashing `UInt64` values as part of a larger composite structure.
  > 
  >  Parameters:
  > 
  >  * `self` : The hasher instance to update.
  >  * `value` : The 64-bit unsigned integer value to be incorporated into the
  >    hash.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Hasher::combine_uint64" {
  >    let hasher = Hasher::new()
  >    hasher.combine_uint64(42UL)
  >    inspect!(hasher.finalize(), content="-1962516083")
  >  }
  >  ```
- #### combine\_unit
  ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,120:::fn <a href="moonbitlang/core/builtin#Hasher">Hasher</a>::combine_unit(self : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
  ```
  > 
  >  Combines the unit value (i.e., `()`) into the hasher's internal state by
  > hashing it as an integer value of 0.
  > 
  >  Parameters:
  > 
  >  * `hasher` : The hasher object to combine the unit value into.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Hasher::combine_unit" {
  >    let hasher = Hasher::new()
  >    hasher.combine_unit()
  >    inspect!(hasher.finalize(), content="148298089")
  >  }
  >  ```
- #### finalize
  ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,412:::fn <a href="moonbitlang/core/builtin#Hasher">Hasher</a>::finalize(self : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Int
  ```
  > 
  >  Finalizes the hashing process and returns the computed hash value. Applies an
  > avalanche function to improve the distribution of the hash value.
  > 
  >  Parameters:
  > 
  >  * `hasher` : The hasher object containing the accumulated hash state.
  > 
  >  Returns a 32-bit integer representing the final hash value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Hasher::finalize" {
  >    let hasher = Hasher::new()
  >    hasher.combine_byte(b'\xFF')
  >    inspect!(hasher.finalize(), content="1955036104")
  >  }
  >  ```
- #### new
  ```moonbit
  :::source,moonbitlang/core/builtin/hasher.mbt,75:::fn <a href="moonbitlang/core/builtin#Hasher">Hasher</a>::new(seed~ : Int = ..) -> <a href="moonbitlang/core/builtin#Hasher">Hasher</a>
  ```
  > 
  >  Creates a new hasher with an optional seed value.
  > 
  >  Parameters:
  > 
  >  * `seed` : An integer value used to initialize the hasher's internal state.
  >    Defaults to 0.
  > 
  >  Returns a new `Hasher` instance initialized with the given seed value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Hasher::new" {
  >    let h1 = Hasher::new() // Create a hasher with default seed
  >    let h2 = Hasher::new(seed=42) // Create a hasher with custom seed
  >    let x = 123
  >    h1.combine(x)
  >    h2.combine(x)
  >    inspect!(h1.finalize() != h2.finalize(), content="true") // Different seeds produce different hashes
  >  }
  >  ```

## InspectError

```moonbit
:::source,moonbitlang/core/builtin/console.mbt,69:::pub(all) type! InspectError String

```

 Represents an error type used by the `inspect!` function to indicate failures
in value inspection. Contains a string message describing the nature of the
inspection failure.

 Returns a type constructor that creates an error type from a string message.

 Example:

 ```moonbit
 test "inspect/failure" {
   let x : Int = 42
   inspect!(x, content="42") // Raises InspectError with detailed failure message
 }
 ```

## Iter

```moonbit
:::source,moonbitlang/core/builtin/iter.mbt,17:::type Iter[T]
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,772:::impl[T] <a href="moonbitlang/core/builtin#Add">Add</a> for <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/iter.mbt,772:::fn op_add[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], other : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,37:::impl[T : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/iter.mbt,37:::fn output[T : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### all
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,68:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::all[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], f : (T) -> Bool) -> Bool
  ```
  > 
- #### any
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,63:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::any[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], f : (T) -> Bool) -> Bool
  ```
  > 
- #### append
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,735:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::append[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], a : T) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
  >  Appends a single element to the end of the iterator.
  > 
  >  #### Type Parameters
  > 
  >  - `T`: The type of the elements in the iterator.
  > 
  >  #### Arguments
  > 
  >  * `self` - The input iterator.
  >  * `a` - The element to be appended to the iterator.
  > 
  >  #### Returns
  > 
  >  Returns a new iterator with the element `a` appended to the original iterator.
- #### collect
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,788:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::collect[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]) -> <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  >  Collects the elements of the iterator into an array.
- #### concat
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,761:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::concat[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], other : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
  >  Combines two iterators into one by appending the elements of the second iterator to the first.
  > 
  >  #### Type Parameters
  > 
  >  - `T`: The type of the elements in the iterators.
  > 
  >  #### Arguments
  > 
  >  * `self` - The first input iterator.
  >  * `other` - The second input iterator to be appended to the first.
  > 
  >  #### Returns
  > 
  >  Returns a new iterator that contains the elements of `self` followed by the elements of `other`.
- #### contains
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,931:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::contains[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A], value : A) -> Bool
  ```
  > 
  >  Checks if the iterator contains an element equal to the given value.
  > 
  >  Parameters:
  > 
  >  * `self` : The iterator to search in.
  >  * `value` : The value to search for.
  > 
  >  Returns `true` if the iterator contains an element equal to the given value,
  > `false` otherwise.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Iter::contains" {
  >    let iter = [1, 2, 3, 4, 5].iter()
  >    inspect!(iter.contains(3), content="true")
  >    inspect!(iter.contains(6), content="false")
  >  }
  >  
  >  test "Iter::contains/empty" {
  >    let iter = Iter::empty()
  >    inspect!(iter.contains(1), content="false")
  >  }
  >  ```
- #### count
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,133:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::count[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]) -> Int
  ```
  > 
  >  Counts the number of elements in the iterator.
  > 
  >  #### Type Parameters
  > 
  >  - `T`: The type of the elements in the iterator.
  > 
  >  #### Arguments
  > 
  >  - `self`: The iterator to consume.
  > 
  >  #### Returns
  > 
  >  Returns the number of elements in the iterator.
- #### drop
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,617:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::drop[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], n : Int) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
  >  Skips the first `n` elements from the iterator.
  > 
  >  #### Type Parameters
  > 
  >  - `T`: The type of the elements in the iterator.
  > 
  >  #### Arguments
  > 
  >  * `self` - The input iterator.
  >  * `n` - The number of elements to skip.
  > 
  >  #### Returns
  > 
  >  A new iterator that starts after skipping the first `n` elements.
- #### drop\_while
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,646:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::drop_while[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], f : (T) -> Bool) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
  >  Skips elements from the iterator as long as the predicate function returns `true`.
  > 
  >  #### Type Parameters
  > 
  >  - `T`: The type of the elements in the iterator.
  > 
  >  #### Arguments
  > 
  >  * `self` - The input iterator.
  >  * `f` - The predicate function that determines whether an element should be skipped.
  > 
  >  #### Returns
  > 
  >  A new iterator that starts after skipping the elements as long as the predicate function returns `true`.
- #### each
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,56:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::each[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], f : (T) -> Unit) -> Unit
  ```
  > 
  >  Iterates over each element in the iterator, applying the function `f` to each element.
  > 
  >  #### Type Parameters
  > 
  >  - `T`: The type of the elements in the iterator.
  > 
  >  #### Arguments
  > 
  >  - `self`: The iterator to consume.
  >  - `f`: A function that takes an element of type `T` and returns `Unit`. This function is applied to each element of the iterator.
  >    TODO: change the intrinsic to match the function name
- #### eachi
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,85:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::eachi[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], f : (Int, T) -> Unit) -> Unit
  ```
  > 
  >  Iterates over each element in the iterator, applying the function `f` to each element with index.
  > 
  >  #### Type Parameters
  > 
  >  - `T`: The type of the elements in the iterator.
  > 
  >  #### Arguments
  > 
  >  - `self`: The iterator to consume.
  >  - `f`: A function that takes an index of type `Int` and an element of type `T` and returns `Unit`. This function is applied to each element of the iterator.
  >    TODO: Add intrinsic
- #### empty
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,155:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::empty[T]() -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
  >  Creates an empty iterator.
  > 
  >  #### Type Parameters
  > 
  >  - `T`: The type of the elements in the iterator.
  > 
  >  #### Returns
  > 
  >  Returns an empty iterator of type `Iter[T]`.
- #### filter
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,391:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::filter[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], f : (T) -> Bool) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
  >  Filters the elements of the iterator based on a predicate function.
  > 
  >  #### Type Parameters
  > 
  >  - `T`: The type of the elements in the iterator.
  > 
  >  #### Arguments
  > 
  >  * `self` - The input iterator.
  >  * `f` - The predicate function that determines whether an element should be included in the filtered iterator.
  > 
  >  #### Returns
  > 
  >  A new iterator that only contains the elements for which the predicate function returns `IterContinue`.
- #### filter\_map
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,421:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::filter_map[A, B](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A], f : (A) -> B?) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[B]
  ```
  > 
  >  Transforms the elements of the iterator using a mapping function that returns an `Option`.
  > The elements for which the function returns `None` are filtered out.
- #### find\_first
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,675:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::find_first[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], f : (T) -> Bool) -> T?
  ```
  > 
  >  Finds the first element in the iterator that satisfies the predicate function.
  > 
  >  #### Type Parameters
  > 
  >  - `T`: The type of the elements in the iterator.
  > 
  >  #### Arguments
  > 
  >  * `self` - The input iterator.
  >  * `f` - The predicate function that determines whether an element is the first element to be found.
  > 
  >  #### Returns
  > 
  >  An `Option` that contains the first element that satisfies the predicate function, or `None` if no such element is found.
- #### flat\_map
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,458:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::flat_map[T, R](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], f : (T) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[R]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[R]
  ```
  > 
  >  Transforms each element of the iterator into an iterator and flattens the resulting iterators into a single iterator.
  > 
  >  #### Type Parameters
  > 
  >  - `T`: The type of the elements in the iterator.
  >  - `R`: The type of the transformed elements.
  > 
  >  #### Arguments
  > 
  >  * `self` - The input iterator.
  >  * `f` - The function that transforms each element of the iterator into an iterator.
  > 
  >  #### Returns
  > 
  >  A new iterator that contains the flattened elements.
- #### flatten
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,471:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::flatten[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[<a href="moonbitlang/core/builtin#Iter">Iter</a>[T]]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  >  
  >  iter.map(f).flatten() == iter..flat\_map(f)
  >  ```moonbit
  >  test {
  >    fn f(n : Int) { Int::until(0,n) }
  >    let xs = f(10)
  >    assert_eq!(xs.map(f).flatten().to_array(),xs.flat_map(f).to_array())
  >  }
  >  ```
- #### fold
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,111:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::fold[T, B](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], init~ : B, f : (B, T) -> B) -> B
  ```
  > 
  >  Folds the elements of the iterator using the given function, starting with the given initial value.
  > 
  >  #### Type Parameters
  > 
  >  - `T`: The type of the elements in the iterator.
  >  - `B`: The type of the accumulator value.
  > 
  >  #### Arguments
  > 
  >  - `self`: The iterator to consume.
  >  - `f`: A function that takes an accumulator of type `B` and an element of type `T`, and returns a new accumulator value.
  >  - `init`: The initial value for the fold operation.
  > 
  >  #### Returns
  > 
  >  Returns the final accumulator value after folding all elements of the iterator.
- #### head
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,848:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::head[A](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]) -> A?
  ```
  > 
  >  Returns the first element of the iterator, or `None` if the iterator is empty.
  > 
  >  #### Type Parameters
  > 
  >  - `A` : The type of the elements in the iterator.
  > 
  >  #### Parameters
  > 
  >  - `self` : The iterator to retrieve the first element from.
  > 
  >  #### Returns
  > 
  >  - An `Option` containing the first element of the iterator if it exists, otherwise `None`.
  > 
  >  #### Examples
  > 
  >  ```
  >  let iter = Iter::singleton(42)
  >  assert_eq!(iter.head(), Some(42))
  >  ```
- #### intersperse
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,871:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::intersperse[A](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A], sep : A) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
  ```
  > 
  >  Inserts a separator element `sep` between each element of the iterator.
  > 
  >  #### Parameters
  > 
  >  - `self` : The iterator to intersperse the separator into.
  >  - `sep` : The separator element to insert between each element of the iterator.
  > 
  >  #### Examples
  > 
  >  ```
  >  let arr = []
  >  [1, 2, 3].iter().intersperse(0).each(fn(i) {arr.push(i)})
  >  assert_eq!(arr, [1, 0, 2, 0, 3])
  >  ```
- #### iter
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,813:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::iter[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
  >  Iter itself is an iterator.
  > so that it works with array spread operator. e.g, `[..iter]`
- #### join
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,796:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::join(self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[String], sep : String) -> String
  ```
  > 
  >  Collects the elements of the iterator into a string.
- #### just\_run
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,26:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::just_run[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], f : (T) -> <a href="moonbitlang/core/builtin#IterResult">IterResult</a>) -> Unit
  ```
  > 
- #### last
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,819:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::last[A](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]) -> A?
  ```
  > 
  >  Returns the last element of the iterator, or `None` if the iterator is empty.
- #### map
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,414:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::map[T, R](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], f : (T) -> R) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[R]
  ```
  > 
  >  Transforms the elements of the iterator using a mapping function.
  > 
  >  #### Type Parameters
  > 
  >  - `T`: The type of the elements in the iterator.
  >  - `R`: The type of the transformed elements.
  > 
  >  #### Arguments
  > 
  >  * `self` - The input iterator.
  >  * `f` - The mapping function that transforms each element of the iterator.
  > 
  >  #### Returns
  > 
  >  A new iterator that contains the transformed elements.
- #### map\_option
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,437:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::map_option[A, B](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A], f : (A) -> B?) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[B]
  ```
  > 
  >  Transforms the elements of the iterator using a mapping function that returns an `Option`.
  > The elements for which the function returns `None` are filtered out.
  > 
- #### map\_while
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,583:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::map_while[A, B](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A], f : (A) -> B?) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[B]
  ```
  > 
  >  Transforms the elements of the iterator using a mapping function upto the function returns `None`.
- #### maximum
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,949:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::maximum[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]) -> T?
  ```
  > 
- #### minimum
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,961:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::minimum[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]) -> T?
  ```
  > 
- #### new
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,141:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::new[T](f : ((T) -> <a href="moonbitlang/core/builtin#IterResult">IterResult</a>) -> <a href="moonbitlang/core/builtin#IterResult">IterResult</a>) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
  >  Do not use this method, it is for internal use only.
- #### nth
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,944:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::nth[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], n : Int) -> T?
  ```
  > 
  >  Returns the nth element of the iterator, or `None` if the iterator is
  > shorter than `n` elements.
- #### op\_as\_view
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,888:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::op_as_view[A](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[A], start~ : Int = .., end? : Int) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[A]
  ```
  > 
- #### peek
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,686:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::peek[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]) -> T?
  ```
  > 
- #### prepend
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,710:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::prepend[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], a : T) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
  >  Prepends a single element to the beginning of the iterator.
  > 
  >  #### Type Parameters
  > 
  >  - `T`: The type of the elements in the iterator.
  > 
  >  #### Arguments
  > 
  >  * `self` - The input iterator.
  >  * `a` - The element to be prepended to the iterator.
  > 
  >  #### Returns
  > 
  >  Returns a new iterator with the element `a` prepended to the original iterator.
- #### repeat
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,192:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::repeat[T](a : T) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
  >  Creates an iterator that repeats the given element indefinitely.
  > 
  >  #### Type Parameters
  > 
  >  - `T`: The type of the elements in the iterator.
  > 
  >  #### Arguments
  > 
  >  - `a`: The element to be repeated.
  > 
  >  #### Returns
  > 
  >  Returns an iterator of type `Iter[T]` that repeats the element `a` indefinitely.
- #### run
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,21:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::run[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], f : (T) -> <a href="moonbitlang/core/builtin#IterResult">IterResult</a>) -> <a href="moonbitlang/core/builtin#IterResult">IterResult</a>
  ```
  > 
- #### singleton
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,173:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::singleton[T](a : T) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
  >  Creates an iterator that contains a single element.
  > 
  >  #### Type Parameters
  > 
  >  - `T`: The type of the element in the iterator.
  > 
  >  #### Arguments
  > 
  >  - `a`: The single element to be contained in the iterator.
  > 
  >  #### Returns
  > 
  >  Returns an iterator of type `Iter[T]` that contains the single element `a`.
- #### take
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,515:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::take[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], n : Int) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
  >  Takes the first `n` elements from the iterator.
  > 
  >  #### Type Parameters
  > 
  >  - `T`: The type of the elements in the iterator.
  > 
  >  #### Arguments
  > 
  >  * `self` - The input iterator.
  >  * `n` - The number of elements to take.
  > 
  >  #### Returns
  > 
  >  A new iterator that contains the first `n` elements.
- #### take\_while
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,556:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::take_while[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], f : (T) -> Bool) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
  >  Takes elements from the iterator as long as the predicate function returns `true`.
  > 
  >  #### Type Parameters
  > 
  >  - `T`: The type of the elements in the iterator.
  > 
  >  #### Arguments
  > 
  >  * `self` - The input iterator.
  >  * `f` - The predicate function that determines whether an element should be taken.
  > 
  >  #### Returns
  > 
  >  A new iterator that contains the elements as long as the predicate function returns `true`.
- #### tap
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,490:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::tap[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], f : (T) -> Unit) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
  >  Applies a function to each element of the iterator without modifying the iterator.
  > 
  >  #### Type Parameters
  > 
  >  - `T`: The type of the elements in the iterator.
  > 
  >  #### Arguments
  > 
  >  * `self` - The input iterator.
  >  * `f` - The function to apply to each element of the iterator.
  > 
  >  #### Returns
  > 
  >  The same iterator.
- #### to\_array
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,778:::fn <a href="moonbitlang/core/builtin#Iter">Iter</a>::to_array[T](self : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]) -> <a href="moonbitlang/core/array#Array">Array</a>[T]
  ```
  > 
  >  Collects the elements of the iterator into an array.

## Iter2

```moonbit
:::source,moonbitlang/core/builtin/iter2.mbt,23:::type Iter2[A, B]
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/iter2.mbt,35:::impl[A : <a href="moonbitlang/core/builtin#Show">Show</a>, B : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[A, B]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/iter2.mbt,35:::fn output[A : <a href="moonbitlang/core/builtin#Show">Show</a>, B : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[A, B], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### concat
  ```moonbit
  :::source,moonbitlang/core/builtin/iter2.mbt,114:::fn <a href="moonbitlang/core/builtin#Iter2">Iter2</a>::concat[A, B](self : <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[A, B], other : <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[A, B]) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[A, B]
  ```
  > 
  >  Combines two iterators into one by appending the elements of the second iterator to the first.
  > 
  >  #### Arguments
  > 
  >  * `self` - The first input iterator.
  >  * `other` - The second input iterator to be appended to the first.
  > 
  >  #### Returns
  > 
  >  Returns a new iterator that contains the elements of `self` followed by the elements of `other`.
  > 
  >  #### Examples
  > 
  >  ```moonbit
  >  test "Iter2::concat" {
  >    inspect!(
  >      "abc".iter2().concat("def".iter2()).to_array(),
  >      content="[(0, 'a'), (1, 'b'), (2, 'c'), (0, 'd'), (1, 'e'), (2, 'f')]",
  >    )
  >  }
  >  ```
- #### each
  ```moonbit
  :::source,moonbitlang/core/builtin/iter2.mbt,62:::fn <a href="moonbitlang/core/builtin#Iter2">Iter2</a>::each[A, B](self : <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[A, B], f : (A, B) -> Unit) -> Unit
  ```
  > 
- #### iter
  ```moonbit
  :::source,moonbitlang/core/builtin/iter2.mbt,71:::fn <a href="moonbitlang/core/builtin#Iter2">Iter2</a>::iter[A, B](self : <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[A, B]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[(A, B)]
  ```
  > 
- #### iter2
  ```moonbit
  :::source,moonbitlang/core/builtin/iter2.mbt,76:::fn <a href="moonbitlang/core/builtin#Iter2">Iter2</a>::iter2[A, B](self : <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[A, B]) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[A, B]
  ```
  > 
- #### new
  ```moonbit
  :::source,moonbitlang/core/builtin/iter2.mbt,55:::fn <a href="moonbitlang/core/builtin#Iter2">Iter2</a>::new[A, B](f : ((A, B) -> <a href="moonbitlang/core/builtin#IterResult">IterResult</a>) -> <a href="moonbitlang/core/builtin#IterResult">IterResult</a>) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[A, B]
  ```
  > 
- #### run
  ```moonbit
  :::source,moonbitlang/core/builtin/iter2.mbt,27:::fn <a href="moonbitlang/core/builtin#Iter2">Iter2</a>::run[A, B](self : <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[A, B], f : (A, B) -> <a href="moonbitlang/core/builtin#IterResult">IterResult</a>) -> <a href="moonbitlang/core/builtin#IterResult">IterResult</a>
  ```
  > 
- #### to\_array
  ```moonbit
  :::source,moonbitlang/core/builtin/iter2.mbt,84:::fn <a href="moonbitlang/core/builtin#Iter2">Iter2</a>::to_array[A, B](self : <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[A, B]) -> <a href="moonbitlang/core/array#Array">Array</a>[(A, B)]
  ```
  > 

## IterResult

```moonbit
:::source,moonbitlang/core/builtin/iter.mbt,31:::pub(all) enum IterResult {
  IterEnd
  IterContinue
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,34:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/builtin#IterResult">IterResult</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/iter.mbt,34:::fn op_equal(<a href="moonbitlang/core/builtin#IterResult">IterResult</a>, <a href="moonbitlang/core/builtin#IterResult">IterResult</a>) -> Bool
    ```
    > automatically derived

## Json

```moonbit
:::source,moonbitlang/core/builtin/json.mbt,16:::pub(all) enum Json {
  Null
  True
  False
  Number(Double)
  String(String)
  Array(<a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/core/json#Json">Json</a>])
  Object(<a href="moonbitlang/core/builtin#Map">Map</a>[String, <a href="moonbitlang/core/json#Json">Json</a>])
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,298:::impl <a href="moonbitlang/core/builtin#Default">Default</a> for <a href="moonbitlang/core/json#Json">Json</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,298:::fn default() -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,24:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/json#Json">Json</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,24:::fn op_equal(<a href="moonbitlang/core/json#Json">Json</a>, <a href="moonbitlang/core/json#Json">Json</a>) -> Bool
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### array
  ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,128:::fn <a href="moonbitlang/core/json#Json">Json</a>::array(array : <a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/core/json#Json">Json</a>]) -> <a href="moonbitlang/core/json#Json">Json</a>
  ```
  > 
  >  Creates a JSON array value from a MoonBit array.
  > 
  >  Parameters:
  > 
  >  * `values` : An array of JSON values to be converted to a JSON array value.
  > 
  >  Returns a JSON value representing the given array.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "array" {
  >    let values : Array[Json] = [1.0, "hello"]
  >    inspect!(
  >      Json::array(values),
  >      content="Array([Number(1), String(\"hello\")])",
  >    )
  >  }
  >  ```
- #### boolean
  ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,100:::fn <a href="moonbitlang/core/json#Json">Json</a>::boolean(boolean : Bool) -> <a href="moonbitlang/core/json#Json">Json</a>
  ```
  > 
  >  Creates a JSON boolean value from a MoonBit boolean.
  > 
  >  Parameters:
  > 
  >  * `boolean` : A MoonBit boolean to be converted to a JSON boolean value.
  > 
  >  Returns a JSON value representing the given boolean.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "boolean" {
  >    inspect!(Json::boolean(true), content="True")
  >    inspect!(Json::boolean(false), content="False")
  >  }
  >  ```
- #### null
  ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,38:::fn <a href="moonbitlang/core/json#Json">Json</a>::null() -> <a href="moonbitlang/core/json#Json">Json</a>
  ```
  > 
  >  Creates a JSON null value.
  > 
  >  Returns a JSON value representing `null`.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "null" {
  >    inspect!(Json::null(), content="Null")
  >  }
  >  ```
- #### number
  ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,59:::fn <a href="moonbitlang/core/json#Json">Json</a>::number(number : Double) -> <a href="moonbitlang/core/json#Json">Json</a>
  ```
  > 
  >  Creates a JSON number value from a double-precision floating-point number.
  > 
  >  Parameters:
  > 
  >  * `value` : A double-precision floating-point number to be converted to a
  >    JSON number.
  > 
  >  Returns a JSON value representing the given number.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "number" {
  >    inspect!(Json::number(3.14), content="Number(3.14)")
  >  }
  >  ```
- #### object
  ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,153:::fn <a href="moonbitlang/core/json#Json">Json</a>::object(object : <a href="moonbitlang/core/builtin#Map">Map</a>[String, <a href="moonbitlang/core/json#Json">Json</a>]) -> <a href="moonbitlang/core/json#Json">Json</a>
  ```
  > 
  >  Creates a JSON object value from a MoonBit map.
  > 
  >  Parameters:
  > 
  >  * `map` : A map from strings to JSON values to be converted to a JSON object
  >    value.
  > 
  >  Returns a JSON value representing the given map.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "object" {
  >    let map : Map[String, Json] = { "name": "John", "age": 42.0 }
  >    inspect!(
  >      Json::object(map),
  >      content="Object({\"name\": String(\"John\"), \"age\": Number(42)})",
  >    )
  >  }
  >  ```
- #### string
  ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,79:::fn <a href="moonbitlang/core/json#Json">Json</a>::string(string : String) -> <a href="moonbitlang/core/json#Json">Json</a>
  ```
  > 
  >  Creates a JSON string value from a MoonBit string.
  > 
  >  Parameters:
  > 
  >  * `string` : A MoonBit string to be converted to a JSON string value.
  > 
  >  Returns a JSON value representing the given string.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "string" {
  >    inspect!(Json::string("hello"), content="String(\"hello\")")
  >  }
  >  ```

## Map

```moonbit
:::source,moonbitlang/core/builtin/linked_hash_map.mbt,48:::type Map[K, V]
```

 Mutable linked hash map that maintains the order of insertion, not thread safe.

 #### Example

 ```
 let map = { 3: "three", 8 :  "eight", 1 :  "one"}
 assert_eq!(map.get(2), None)
 assert_eq!(map.get(3), Some("three"))
 map.set(3, "updated")
 assert_eq!(map.get(3), Some("updated"))
 ```

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,577:::impl[K, V] <a href="moonbitlang/core/builtin#Default">Default</a> for <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/linked_hash_map.mbt,577:::fn default[K, V]() -> <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,538:::impl[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/linked_hash_map.mbt,538:::fn op_equal[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V], that : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,397:::impl[K : <a href="moonbitlang/core/builtin#Show">Show</a>, V : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/linked_hash_map.mbt,397:::fn output[K : <a href="moonbitlang/core/builtin#Show">Show</a>, V : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,254:::impl[K : <a href="moonbitlang/core/builtin#Show">Show</a>, V : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,254:::fn to_json[K : <a href="moonbitlang/core/builtin#Show">Show</a>, V : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### capacity
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,419:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::capacity[K, V](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]) -> Int
  ```
  > 
  >  Get the capacity of the map.
- #### clear
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,455:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::clear[K, V](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]) -> Unit
  ```
  > 
  >  Clears the map, removing all key-value pairs. Keeps the allocated space.
- #### contains
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,255:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::contains[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V], key : K) -> Bool
  ```
  > 
  >  Check if the hash map contains a key.
- #### each
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,431:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::each[K, V](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V], f : (K, V) -> Unit) -> Unit
  ```
  > 
  >  Iterate over all key-value pairs of the map in the order of insertion.
- #### eachi
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,443:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::eachi[K, V](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V], f : (Int, K, V) -> Unit) -> Unit
  ```
  > 
  >  Iterate over all key-value pairs of the map in the order of insertion, with index.
- #### from\_array
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,106:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::from_array[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](arr : <a href="moonbitlang/core/array#Array">Array</a>[(K, V)]) -> <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]
  ```
  > 
  >  Create a hash map from array.
- #### from\_iter
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,568:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::from_iter[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[(K, V)]) -> <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]
  ```
  > 
- #### get
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,168:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::get[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V], key : K) -> V?
  ```
  > 
  >  Get the value associated with a key.
- #### get\_or\_default
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,214:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::get_or_default[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V], key : K, default : V) -> V
  ```
  > 
  >  Returns the value associated with the key in the map, or computes and returns
  > a default value if the key does not exist.
  > 
  >  Parameters:
  > 
  >  * `map` : The map to search in.
  >  * `key` : The key to look up in the map.
  >  * `default` : A function that returns a default value when the key is not
  >    found.
  > 
  >  Returns either the value associated with the key if it exists, or the result
  > of calling the default function.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "get_or_default" {
  >    let map = { "a": 1, "b": 2 }
  >    inspect!(map.get_or_default("a", 0), content="1")
  >    inspect!(map.get_or_default("c", 42), content="42")
  >  }
  >  ```
- #### get\_or\_init
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,238:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::get_or_init[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V], key : K, default : () -> V) -> V
  ```
  > 
  >  Returns the value for the given key, or sets and returns a default value if the key does not exist.
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,425:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::is_empty[K, V](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]) -> Bool
  ```
  > 
  >  Check if the hash map is empty.
- #### iter
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,464:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::iter[K, V](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[(K, V)]
  ```
  > 
  >  Returns the iterator of the hash map, provide elements in the order of insertion.
- #### iter2
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,479:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::iter2[K, V](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[K, V]
  ```
  > 
- #### keys
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,494:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::keys[K, V](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[K]
  ```
  > 
- #### new
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,90:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::new[K, V](capacity~ : Int = ..) -> <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]
  ```
  > 
  >  Create a hash map.
  > The capacity of the map will be the smallest power of 2 that is
  > greater than or equal to the provided \[capacity\].
- #### of
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,556:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::of[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[(K, V)]) -> <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]
  ```
  > 
- #### op\_get
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,187:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::op_get[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V], key : K) -> V?
  ```
  > 
- #### op\_set
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,158:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::op_set[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V], key : K, value : V) -> Unit
  ```
  > 
- #### remove
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,264:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::remove[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V], key : K) -> Unit
  ```
  > 
  >  Remove a key-value pair from hash map.
- #### set
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,115:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::set[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, V](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V], key : K, value : V) -> Unit
  ```
  > 
  >  Set a key-value pair into the hash map.
  > @alert unsafe "Panic if the hash map is full."
- #### size
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,413:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::size[K, V](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]) -> Int
  ```
  > 
  >  Get the number of key-value pairs in the map.
- #### to\_array
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,523:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::to_array[K, V](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]) -> <a href="moonbitlang/core/array#Array">Array</a>[(K, V)]
  ```
  > 
  >  Converts the hash map to an array.
- #### values
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_map.mbt,508:::fn <a href="moonbitlang/core/builtin#Map">Map</a>::values[K, V](self : <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[V]
  ```
  > 

## Set

```moonbit
:::source,moonbitlang/core/builtin/linked_hash_set.mbt,38:::type Set[K]
```

 Mutable linked hash set that maintains the order of insertion, not thread safe.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,440:::impl[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/builtin#Set">Set</a>[K]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/linked_hash_set.mbt,440:::fn op_equal[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K], other : <a href="moonbitlang/core/builtin#Set">Set</a>[K]) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,342:::impl[K : <a href="moonbitlang/core/builtin#Show">Show</a>] <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/builtin#Set">Set</a>[K]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/linked_hash_set.mbt,342:::fn output[K : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K], logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/json.mbt,263:::impl[X : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>] <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="moonbitlang/core/builtin#Set">Set</a>[X]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/json.mbt,263:::fn to_json[X : <a href="moonbitlang/core/builtin#ToJson">ToJson</a>](self : <a href="moonbitlang/core/builtin#Set">Set</a>[X]) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### add
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,131:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::add[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K], key : K) -> Unit
  ```
  > 
  >  Insert a key into the hash set.
- #### add\_and\_check
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,88:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::add_and_check[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K], key : K) -> Bool
  ```
  > 
  >  Insert a key into the hash set.if the key exists return false
- #### capacity
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,364:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::capacity[K](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K]) -> Int
  ```
  > 
  >  Get the capacity of the set.
- #### clear
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,400:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::clear[K](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K]) -> Unit
  ```
  > 
  >  Clears the set, removing all keys. Keeps the allocated space.
- #### contains
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,174:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::contains[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K], key : K) -> Bool
  ```
  > 
  >  Check if the hash set contains a key.
- #### difference
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,475:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::difference[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K], other : <a href="moonbitlang/core/builtin#Set">Set</a>[K]) -> <a href="moonbitlang/core/builtin#Set">Set</a>[K]
  ```
  > 
- #### each
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,376:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::each[K](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K], f : (K) -> Unit) -> Unit
  ```
  > 
  >  Iterate over all keys of the set in the order of insertion.
- #### eachi
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,388:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::eachi[K](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K], f : (Int, K) -> Unit) -> Unit
  ```
  > 
  >  Iterate over all keys of the set in the order of insertion, with index.
- #### from\_array
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,71:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::from_array[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](arr : <a href="moonbitlang/core/array#Array">Array</a>[K]) -> <a href="moonbitlang/core/builtin#Set">Set</a>[K]
  ```
  > 
  >  Create a hash set from array.
- #### from\_iter
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,468:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::from_iter[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[K]) -> <a href="moonbitlang/core/builtin#Set">Set</a>[K]
  ```
  > 
- #### insert
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,82:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::insert[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K], key : K) -> Unit
  ```
  > 
  >  Insert a key into the hash set.
  > 
- #### intersection
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,501:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::intersection[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K], other : <a href="moonbitlang/core/builtin#Set">Set</a>[K]) -> <a href="moonbitlang/core/builtin#Set">Set</a>[K]
  ```
  > 
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,370:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::is_empty[K](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K]) -> Bool
  ```
  > 
  >  Check if the hash set is empty.
- #### iter
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,409:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::iter[K](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[K]
  ```
  > 
  >  Returns the iterator of the hash set, provide elements in the order of insertion.
- #### new
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,55:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::new[K](capacity~ : Int = ..) -> <a href="moonbitlang/core/builtin#Set">Set</a>[K]
  ```
  > 
  >  Create a hash set.
  > The capacity of the set will be the smallest power of 2 that is
  > greater than or equal to the provided \[capacity\].
- #### of
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,456:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::of[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[K]) -> <a href="moonbitlang/core/builtin#Set">Set</a>[K]
  ```
  > 
- #### remove
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,194:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::remove[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K], key : K) -> Unit
  ```
  > 
  >  Remove a key from hash set.
- #### remove\_and\_check
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,218:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::remove_and_check[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K], key : K) -> Bool
  ```
  > 
  >  Remove a key from hash set.if the key exists, delete it and return true
- #### size
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,358:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::size[K](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K]) -> Int
  ```
  > 
  >  Get the number of keys in the set.
- #### symmetric\_difference
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,482:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::symmetric_difference[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K], other : <a href="moonbitlang/core/builtin#Set">Set</a>[K]) -> <a href="moonbitlang/core/builtin#Set">Set</a>[K]
  ```
  > 
- #### to\_array
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,425:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::to_array[K](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K]) -> <a href="moonbitlang/core/array#Array">Array</a>[K]
  ```
  > 
  >  Converts the hash set to an array.
- #### union
  ```moonbit
  :::source,moonbitlang/core/builtin/linked_hash_set.mbt,493:::fn <a href="moonbitlang/core/builtin#Set">Set</a>::union[K : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/core/builtin#Set">Set</a>[K], other : <a href="moonbitlang/core/builtin#Set">Set</a>[K]) -> <a href="moonbitlang/core/builtin#Set">Set</a>[K]
  ```
  > 

## SnapshotError

```moonbit
:::source,moonbitlang/core/builtin/console.mbt,232:::pub(all) type! SnapshotError String

```

 Represents an error that occurs during snapshot testing. Contains a string
message describing the error.

 Used internally by the test driver to handle snapshot-related errors. Not
intended for direct use by end users.

 Example:

 ```moonbit
 test "SnapshotError" {
   let err : SnapshotError = SnapshotError("failed to load snapshot")
   match err {
     SnapshotError(msg) => assert_eq!(msg, "failed to load snapshot")
   }
 }
 ```

## SourceLoc

```moonbit
:::source,moonbitlang/core/builtin/autoloc.mbt,23:::pub(all) extern type SourceLoc
```

 Represents a source code location in a MoonBit program, containing
information about the file path, line number, and column number. Used
internally by the compiler for error reporting and debugging purposes.

 This type is public to all packages but its internal representation is
opaque. Users cannot construct values of this type directly; they are
automatically created by the compiler when needed.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/autoloc.mbt,42:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/autoloc.mbt,42:::fn output(self : <a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a>, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### to\_string
  ```moonbit
  :::source,moonbitlang/core/builtin/autoloc.mbt,39:::fn <a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a>::to_string(self : <a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a>) -> String
  ```
  > 
  >  Converts a source location to its string representation.
  > 
  >  Parameters:
  > 
  >  * `source_location` : A source code location containing information about the
  >    file path, line number, and column number.
  > 
  >  Returns a string representation of the source location, typically in the
  > format "file:line:column".
  > 
  >  Note: This function is primarily used internally by the compiler for error
  > reporting and debugging purposes. Source locations are automatically created
  > by the compiler when needed.

## StringBuilder

```moonbit
:::source,moonbitlang/core/builtin/stringbuilder_buffer.mbt,16:::type StringBuilder
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/builtin/stringbuilder_buffer.mbt,68:::impl <a href="moonbitlang/core/builtin#Logger">Logger</a> for <a href="moonbitlang/core/builtin#StringBuilder">StringBuilder</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/stringbuilder_buffer.mbt,75:::fn write_char(self : <a href="moonbitlang/core/builtin#StringBuilder">StringBuilder</a>, ch : Char) -> Unit
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/stringbuilder_buffer.mbt,68:::fn write_string(self : <a href="moonbitlang/core/builtin#StringBuilder">StringBuilder</a>, str : String) -> Unit
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/stringbuilder_buffer.mbt,82:::fn write_substring(self : <a href="moonbitlang/core/builtin#StringBuilder">StringBuilder</a>, str : String, start : Int, len : Int) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/builtin/stringbuilder_buffer.mbt,101:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/builtin#StringBuilder">StringBuilder</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/builtin/stringbuilder_buffer.mbt,101:::fn output(self : <a href="moonbitlang/core/builtin#StringBuilder">StringBuilder</a>, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
    >  TODO: improve perf

#### mooncakes-io-method-mark-Methods
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/builtin/stringbuilder_buffer.mbt,40:::fn <a href="moonbitlang/core/builtin#StringBuilder">StringBuilder</a>::is_empty(self : <a href="moonbitlang/core/builtin#StringBuilder">StringBuilder</a>) -> Bool
  ```
  > 
  >  Return whether the given buffer is empty.
- #### new
  ```moonbit
  :::source,moonbitlang/core/builtin/stringbuilder_buffer.mbt,32:::fn <a href="moonbitlang/core/builtin#StringBuilder">StringBuilder</a>::new(size_hint~ : Int = ..) -> <a href="moonbitlang/core/builtin#StringBuilder">StringBuilder</a>
  ```
  > 
  >  Creates a new string builder with an optional initial capacity hint.
  > 
  >  Parameters:
  > 
  >  * `size_hint` : An optional initial capacity hint for the internal buffer. If
  >    less than 1, a minimum capacity of 1 is used. Defaults to 0. It is the size of bytes,
  >    not the size of characters. `size_hint` may be ignored on some platforms, JS for example.
  > 
  >  Returns a new `StringBuilder` instance with the specified initial capacity.
  > 
- #### reset
  ```moonbit
  :::source,moonbitlang/core/builtin/stringbuilder_buffer.mbt,108:::fn <a href="moonbitlang/core/builtin#StringBuilder">StringBuilder</a>::reset(self : <a href="moonbitlang/core/builtin#StringBuilder">StringBuilder</a>) -> Unit
  ```
  > 
- #### to\_string
  ```moonbit
  :::source,moonbitlang/core/builtin/stringbuilder_buffer.mbt,95:::fn <a href="moonbitlang/core/builtin#StringBuilder">StringBuilder</a>::to_string(self : <a href="moonbitlang/core/builtin#StringBuilder">StringBuilder</a>) -> String
  ```
  > 
- #### write\_iter
  ```moonbit
  :::source,moonbitlang/core/builtin/stringbuilder.mbt,41:::fn <a href="moonbitlang/core/builtin#StringBuilder">StringBuilder</a>::write_iter(self : <a href="moonbitlang/core/builtin#StringBuilder">StringBuilder</a>, iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[Char]) -> Unit
  ```
  > 
  >  Writes characters from an iterator to the StringBuilder.
  > 
  >  Parameters:
  > 
  >  * `self` : The StringBuilder to write to.
  >  * `iter` : An iterator yielding characters to write.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "write_iter" {
  >    let sb = StringBuilder::new()
  >    let chars = "Hello🤣".iter()
  >    sb.write_iter(chars)
  >    assert_eq!(sb.to_string(), "Hello🤣")
  >  }
  >  ```
- #### write\_object
  ```moonbit
  :::source,moonbitlang/core/builtin/stringbuilder.mbt,16:::fn <a href="moonbitlang/core/builtin#StringBuilder">StringBuilder</a>::write_object[T : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/builtin#StringBuilder">StringBuilder</a>, obj : T) -> Unit
  ```
  > 

## UninitializedArray

```moonbit
:::source,moonbitlang/core/builtin/uninitialized_array.mbt,16:::type UninitializedArray[T]
```


#### mooncakes-io-method-mark-Methods
- #### length
  ```moonbit
  :::source,moonbitlang/core/builtin/uninitialized_array.mbt,95:::fn <a href="moonbitlang/core/builtin#UninitializedArray">UninitializedArray</a>::length[A](self : <a href="moonbitlang/core/builtin#UninitializedArray">UninitializedArray</a>[A]) -> Int
  ```
  > 
  >  Returns the length of an uninitialized array.
  > 
  >  Parameters:
  > 
  >  - `array` : The uninitialized array whose length is to be determined.
  > 
  >  Returns the length of the uninitialized array as an integer.
- #### make
  ```moonbit
  :::source,moonbitlang/core/builtin/uninitialized_array.mbt,26:::fn <a href="moonbitlang/core/builtin#UninitializedArray">UninitializedArray</a>::make[T](size : Int) -> <a href="moonbitlang/core/builtin#UninitializedArray">UninitializedArray</a>[T]
  ```
  > 
  >  Creates an uninitialized array of the specified size.
  > 
  >  Parameters:
  > 
  >  - `size` : The number of elements the array should hold.
  > 
  >  Returns an uninitialized array of type `T` with the specified size.
- #### op\_as\_view
  ```moonbit
  :::source,moonbitlang/core/builtin/uninitialized_array.mbt,71:::fn <a href="moonbitlang/core/builtin#UninitializedArray">UninitializedArray</a>::op_as_view[T](self : <a href="moonbitlang/core/builtin#UninitializedArray">UninitializedArray</a>[T], start~ : Int = .., end? : Int) -> <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[T]
  ```
  > 
  >  Creates a view into a portion of the uninitialized array.
  > 
  >  Parameters:
  > 
  >  * `array` : The uninitialized array to create a view from.
  >  * `start` : The starting index of the view (inclusive). Defaults to 0.
  >  * `end` : The ending index of the view (exclusive). If not provided, defaults
  >    to the length of the array.
  > 
  >  Returns an `ArrayView` that provides a window into the specified portion of
  > the array.
  > 
  >  Throws an error if the indices are out of bounds or if `start` is greater
  > than `end`.
- #### op\_get
  ```moonbit
  :::source,moonbitlang/core/builtin/uninitialized_array.mbt,37:::fn <a href="moonbitlang/core/builtin#UninitializedArray">UninitializedArray</a>::op_get[T](self : <a href="moonbitlang/core/builtin#UninitializedArray">UninitializedArray</a>[T], index : Int) -> T
  ```
  > 
  >  Retrieves the element at the specified index from an uninitialized array.
  > 
  >  Parameters:
  > 
  >  - `array` : The uninitialized array from which to retrieve the element.
  >  - `index` : The index of the element to retrieve.
  > 
  >  Returns the element at the specified index.
- #### op\_set
  ```moonbit
  :::source,moonbitlang/core/builtin/uninitialized_array.mbt,50:::fn <a href="moonbitlang/core/builtin#UninitializedArray">UninitializedArray</a>::op_set[T](self : <a href="moonbitlang/core/builtin#UninitializedArray">UninitializedArray</a>[T], index : Int, value : T) -> Unit
  ```
  > 
  >  Sets the value at the specified index in an uninitialized array.
  > 
  >  Parameters:
  > 
  >  - `array` : The uninitialized array where the value will be set.
  >  - `index` : The position in the array where the value will be set.
  >  - `value` : The value to be set at the specified index.

## abort

```moonbit
:::source,moonbitlang/core/builtin/intrinsics.mbt,84:::fn abort[T](msg : String) -> T
```

 Aborts the program with an error message. Always causes a panic, regardless
of the message provided.

 Parameters:

 * `message` : A string containing the error message to be displayed when
   aborting.

 Returns a value of type `T`. However, this function never actually returns a
value as it always causes a panic.

 Example:

 ```moonbit
 test "panic abort/with_message" {
   let x : Int = abort("Something went wrong") // specify return type as Int
   ignore(x)
 }
 ```

## assert\_eq

```moonbit
:::source,moonbitlang/core/builtin/assert.mbt,49:::fn assert_eq[T : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Show">Show</a>](a : T, b : T, loc~ : <a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a> = _) -> Unit!<a href="moonbitlang/core/error#Error">Error</a>
```

 Asserts that two values are equal. If they are not equal, raises a failure
with a message containing the source location and the values being compared.

 Parameters:

 * `a` : First value to compare.
 * `b` : Second value to compare.
 * `loc` : Source location information to include in failure messages. This is
   usually automatically provided by the compiler.

 Throws a `Failure` error if the values are not equal, with a message showing
the location of the failing assertion and the actual values that were
compared.

 Example:

 ```moonbit
 test "assert_eq" {
   assert_eq!(1, 1)
   assert_eq!("hello", "hello")
 }
 
 test "panic assert_eq/not_equal" {
   ignore(assert_eq!(1, 2)) // Will fail with message showing values and location
 }
 ```

## assert\_false

```moonbit
:::source,moonbitlang/core/builtin/assert.mbt,148:::fn assert_false(x : Bool, loc~ : <a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a> = _) -> Unit!<a href="moonbitlang/core/error#Error">Error</a>
```

 Tests whether a boolean condition is false, throwing an error if the
condition is true.

 Parameters:

 * `condition` : The boolean condition to test.
 * `location` : The source location where the assertion is made. Used in error
   messages.

 Throws a `Failure` error if the condition is true. The error message includes
the source location and the value that was expected to be false.

 Example:

 ```moonbit
 test "assert_false" {
   assert_false!(false)
   assert_false!(1 > 2)
 }
 
 test "panic assert_false/with_true" {
   assert_false!(true) // This will fail with an error message
 }
 ```

## assert\_not\_eq

```moonbit
:::source,moonbitlang/core/builtin/assert.mbt,81:::fn assert_not_eq[T : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Show">Show</a>](a : T, b : T, loc~ : <a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a> = _) -> Unit!<a href="moonbitlang/core/error#Error">Error</a>
```

 Asserts that two values of the same type are not equal. If the values are
equal, raises a failure with a detailed error message including the source
location and string representation of both values.

 Parameters:

 * `first` : The first value to compare.
 * `second` : The second value to compare.
 * `location` : Source location information for error reporting. Defaults to
   the current location.

 Throws a `Failure` error if the values are equal. The error message includes
the source location and string representations of both values.

 Example:

 ```moonbit
 test "assert_not_eq" {
   assert_not_eq!(1, 2) // Passes
 }
 
 test "panic assert_not_eq/equal_values" {
   ignore(assert_not_eq!(42, 42)) // Fails with detailed error message
 }
 ```

## assert\_true

```moonbit
:::source,moonbitlang/core/builtin/assert.mbt,117:::fn assert_true(x : Bool, loc~ : <a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a> = _) -> Unit!<a href="moonbitlang/core/error#Error">Error</a>
```

 Asserts that the given boolean value is true. Throws an error with source
location information if the assertion fails.

 Parameters:

 * `condition` : The boolean value to be checked.
 * `location` : The source location where the assertion is made. Defaults to
   the current location.

 Throws a `Failure` error with a descriptive message including the source
location if the condition is false.

 Example:

 ```moonbit
 test "assert_true" {
   assert_true!(true)
 }
 
 test "panic assert_true/false_condition" {
   ignore(assert_true!(false)) // Throws Failure
 }
 ```

## dump

```moonbit
:::source,moonbitlang/core/builtin/console.mbt,45:::fn dump[T](t : T, name? : String, loc~ : <a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a> = _) -> T
```

 Prints and returns the value of a given expression for quick and dirty debugging.

## fail

```moonbit
:::source,moonbitlang/core/builtin/failure.mbt,60:::fn fail[T](msg : String, loc~ : <a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a> = _) -> T!<a href="moonbitlang/core/builtin#Failure">Failure</a>
```

 Raises a `Failure` error with a given message and source location.

 Parameters:

 * `message` : A string containing the error message to be included in the
   failure.
 * `location` : The source code location where the failure occurred.
   Automatically provided by the compiler when not specified.

 Returns a value of type `T` wrapped in a `Failure` error type.

 Throws an error of type `Failure` with a message that includes both the
source location and the provided error message.

 Example:

 ```moonbit
 test "panic fail" {
   fail!("Something went wrong")
 }
 ```

## ignore

```moonbit
:::source,moonbitlang/core/builtin/intrinsics.mbt,35:::fn ignore[T](t : T) -> Unit
```

 Evaluates an expression and discards its result. This is useful when you want
to execute an expression for its side effects but don't care about its return
value, or when you want to explicitly indicate that a value is intentionally
unused.

 Parameters:

 * `value` : The value to be ignored. Can be of any type.

 Example:

 ```moonbit
 test "ignore" {
   let x = 42
   ignore(x) // Explicitly ignore the value
   let mut sum = 0
   ignore([1, 2, 3].iter().each(fn(x) { sum = sum + x })) // Ignore the Unit return value of each()
 }
 ```

## inspect

```moonbit
:::source,moonbitlang/core/builtin/console.mbt,195:::fn inspect(obj : <a href="moonbitlang/core/builtin#Show">Show</a>, content~ : String = .., loc~ : <a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a> = _, args_loc~ : <a href="moonbitlang/core/builtin#ArgsLoc">ArgsLoc</a> = _) -> Unit!<a href="moonbitlang/core/builtin#InspectError">InspectError</a>
```

 Tests if the string representation of an object matches the expected content.
Used primarily in test cases to verify the correctness of `Show`
implementations and program outputs.

 Parameters:

 * `object` : The object to be inspected. Must implement the `Show` trait.
 * `content` : The expected string representation of the object. Defaults to
   an empty string.
 * `location` : Source code location information for error reporting.
   Automatically provided by the compiler.
 * `arguments_location` : Location information for function arguments in
   source code. Automatically provided by the compiler.

 Throws an `InspectError` if the actual string representation of the object
does not match the expected content. The error message includes detailed
information about the mismatch, including source location and both expected
and actual values.

 Example:

 ```moonbit skip
 test "inspect/basic" {
   inspect!(42, content="42")
   inspect!("hello", content="hello")
   inspect!([1, 2, 3], content="[1, 2, 3]")
 }
 ```

## not

```moonbit
:::source,moonbitlang/core/builtin/intrinsics.mbt,112:::fn not(x : Bool) -> Bool
```

 Performs logical negation on a boolean value.

 Parameters:

 * `value` : The boolean value to negate.

 Returns the logical NOT of the input value: `true` if the input is `false`,
and `false` if the input is `true`.

 Example:

 ```moonbit
 test "not" {
   inspect!(not(true), content="false")
   inspect!(not(false), content="true")
 }
 ```

## op\_ge

```moonbit
:::source,moonbitlang/core/builtin/op.mbt,35:::fn op_ge[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self_ : T, other : T) -> Bool
```


## op\_gt

```moonbit
:::source,moonbitlang/core/builtin/op.mbt,23:::fn op_gt[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self_ : T, other : T) -> Bool
```


## op\_le

```moonbit
:::source,moonbitlang/core/builtin/op.mbt,29:::fn op_le[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self_ : T, other : T) -> Bool
```


## op\_lt

```moonbit
:::source,moonbitlang/core/builtin/op.mbt,17:::fn op_lt[T : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self_ : T, other : T) -> Bool
```


## op\_notequal

```moonbit
:::source,moonbitlang/core/builtin/op.mbt,41:::fn op_notequal[T : <a href="moonbitlang/core/builtin#Eq">Eq</a>](x : T, y : T) -> Bool
```


## panic

```moonbit
:::source,moonbitlang/core/builtin/intrinsics.mbt,90:::fn panic[T]() -> T
```


## physical\_equal

```moonbit
:::source,moonbitlang/core/builtin/intrinsics.mbt,62:::fn physical_equal[T](a : T, b : T) -> Bool
```

 Tests if two values are physically equal (i.e., point to the same memory
location). Unlike structural equality testing (`==`), this function checks if
two references point to exactly the same object in memory.

 Parameters:

 * `first` : The first value to compare.
 * `second` : The second value to compare.
 * `T` : The type parameter representing the type of values being compared.

 Returns `true` if both values refer to the same object in memory, `false`
otherwise.

 Example:

 ```moonbit
 test "physical_equal" {
   let arr1 = [1, 2, 3]
   let arr2 = arr1
   let arr3 = [1, 2, 3]
   inspect!(physical_equal(arr1, arr2), content="true") // Same object
   inspect!(physical_equal(arr1, arr3), content="false") // Different objects with same content
 }
 ```

## println

```moonbit
:::source,moonbitlang/core/builtin/console.mbt,38:::fn println[T : <a href="moonbitlang/core/builtin#Show">Show</a>](input : T) -> Unit
```

 Prints any value that implements the `Show` trait to the standard output,
followed by a newline.

 Parameters:

 * `value` : The value to be printed. Must implement the `Show` trait.

 Example:

 ```moonbit skip
 test "println" {
   println(42)
   println("Hello, World!")
   println([1, 2, 3])
 }
 ```

## repr

```moonbit
:::source,moonbitlang/core/builtin/traits.mbt,124:::fn repr[T : <a href="moonbitlang/core/builtin#Show">Show</a>](t : T) -> String
```


## Logger


#### mooncakes-io-method-mark-Methods
- #### write\_iter
  ```moonbit
  :::source,moonbitlang/core/builtin/traits.mbt,93:::fn <a href="moonbitlang/core/builtin#Logger">Logger</a>::write_iter[T : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/builtin#Logger">Logger</a>, iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[T], prefix~ : String = .., suffix~ : String = .., sep~ : String = .., trailing~ : Bool = ..) -> Unit
  ```
  > 
- #### write\_object
  ```moonbit
  :::source,moonbitlang/core/builtin/traits.mbt,88:::fn <a href="moonbitlang/core/builtin#Logger">Logger</a>::write_object[Obj : <a href="moonbitlang/core/builtin#Show">Show</a>](self : <a href="moonbitlang/core/builtin#Logger">Logger</a>, obj : Obj) -> Unit
  ```
  > 

## Bytes


#### mooncakes-io-method-mark-Methods
- #### copy
  ```moonbit
  :::source,moonbitlang/core/builtin/bytes.mbt,200:::fn <a href="moonbitlang/core/bytes#Bytes">Bytes</a>::copy(self : Bytes) -> Bytes
  ```
  > 
  >  Creates a new byte sequence by copying all bytes from the input sequence.
  > 
  >  Parameters:
  > 
  >  * `bytes` : The byte sequence to be copied.
  > 
  >  Returns a new `Bytes` containing the same sequence of bytes as the input.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Bytes::copy" {
  >    let original = b"\x01\x02\x03"
  >    let copy = original.copy()
  >    inspect!(copy, content="b\"\\x01\\x02\\x03\"")
  >  }
  >  ```
- #### length
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1388:::fn <a href="moonbitlang/core/bytes#Bytes">Bytes</a>::length(self : Bytes) -> Int
  ```
  > 
  >  Returns the number of bytes in a byte sequence.
  > 
  >  Parameters:
  > 
  >  * `bytes` : The byte sequence whose length is to be determined.
  > 
  >  Returns an integer representing the length (number of bytes) of the sequence.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Bytes::length" {
  >    let bytes = b"\x01\x02\x03"
  >    inspect!(bytes.length(), content="3")
  >    let empty = b""
  >    inspect!(empty.length(), content="0")
  >  }
  >  ```
- #### make
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1421:::fn <a href="moonbitlang/core/bytes#Bytes">Bytes</a>::make(len : Int, init : Byte) -> Bytes
  ```
  > 
  >  Creates a new byte sequence of the specified length, where each byte is
  > initialized to the given value.
  > 
  >  Parameters:
  > 
  >  * `length` : The length of the byte sequence to create. Must be non-negative.
  >  * `initial_value` : The byte value used to initialize each position in the
  >    sequence.
  > 
  >  Returns a new byte sequence of the specified length with all positions
  > initialized to the given value.
  > 
  >  Throws a panic if `length` is negative.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Bytes::make" {
  >    let bytes = Bytes::make(3, b'\xFF')
  >    inspect!(bytes, content=
  >    #|b"\xff\xff\xff"
  >  )
  >    let empty = Bytes::make(0, b'\x00')
  >    inspect!(empty, content="b\"\"")
  >  }
  >  
  >  test "panic Bytes::make/negative_length" {
  >    ignore(Bytes::make(-1, b'\x00')) // Panics: negative length
  >  }
  >  ```
- #### makei
  ```moonbit
  :::source,moonbitlang/core/builtin/bytes.mbt,41:::fn <a href="moonbitlang/core/bytes#Bytes">Bytes</a>::makei(length : Int, value : (Int) -> Byte) -> Bytes
  ```
  >  
  >  Creates a new byte sequence of the specified length, where each byte is
  > initialized using a function that maps indices to bytes.
  > 
  >  Parameters:
  > 
  >  * `length` : The length of the byte sequence to create. If `length` is less than or
  >    equal to 0, returns an empty byte sequence.
  >  * `value` : A function that takes an index (from 0 to `length - 1`) and
  >    returns a byte for that position.
  > 
  >  Returns a new byte sequence containing the bytes produced by applying the
  > value function to each index.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Bytes::makei" {
  >    let bytes = Bytes::makei(3, fn(i) { (i + 65).to_byte() })
  >    assert_eq!(bytes, b"ABC")
  >  }
  >  ```
- #### new
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1447:::fn <a href="moonbitlang/core/bytes#Bytes">Bytes</a>::new(len : Int) -> Bytes
  ```
  > 
  >  Creates a new byte sequence filled with zero bytes.
  > 
  >  Parameters:
  > 
  >  * `length` : The length of the byte sequence to create. Must be a
  >    non-negative integer.
  > 
  >  Returns a new byte sequence of the specified length, with all bytes
  > initialized to zero.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Bytes::new" {
  >    let bytes = Bytes::new(3)
  >    inspect!(bytes, content="b\"\\x00\\x00\\x00\"")
  >  }
  >  
  >  test "Bytes::new/empty" {
  >    let bytes = Bytes::new(0)
  >    inspect!(bytes, content="b\"\"")
  >  }
  >  ```
- #### of\_string
  ```moonbit
  :::source,moonbitlang/core/builtin/bytes.mbt,71:::fn <a href="moonbitlang/core/bytes#Bytes">Bytes</a>::of_string(str : String) -> Bytes
  ```
  > 
  >  Creates a byte sequence from a UTF-16 encoded string. Each character in the
  > string is encoded as a pair of bytes in little-endian order.
  > 
  >  Parameters:
  > 
  >  * `string` : The input string to be converted to a byte sequence.
  > 
  >  Returns a new byte sequence containing the UTF-16LE encoded representation of
  > the input string.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Bytes::of_string" {
  >    let bytes = Bytes::of_string("ABC")
  >    inspect!(bytes, content="b\"\\x41\\x00\\x42\\x00\\x43\\x00\"")
  >  }
  >  ```
- #### op\_get
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1334:::fn <a href="moonbitlang/core/bytes#Bytes">Bytes</a>::op_get(self : Bytes, idx : Int) -> Byte
  ```
  > 
  >  Retrieves a byte at the specified index from a byte sequence.
  > 
  >  Parameters:
  > 
  >  * `bytes` : The byte sequence to access.
  >  * `index` : The position in the byte sequence from which to retrieve the
  >    byte.
  > 
  >  Returns a byte value from the specified position in the sequence.
  > 
  >  Throws a panic if the index is negative or greater than or equal to the
  > length of the byte sequence.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Bytes::op_get" {
  >    let bytes = b"\x01\x02\x03"
  >    inspect!(bytes[1], content="b'\\x02'")
  >  }
  >  
  >  test "panic Bytes::op_get/out_of_bounds" {
  >    let bytes = b"\x01\x02\x03"
  >    ignore(bytes[3]) // Index out of bounds
  >  }
  >  ```
- #### to\_unchecked\_string
  ```moonbit
  :::source,moonbitlang/core/builtin/bytes.mbt,92:::fn <a href="moonbitlang/core/bytes#Bytes">Bytes</a>::to_unchecked_string(self : Bytes, offset~ : Int = .., length~ : Int = ..) -> String
  ```
  > 
  >  Return an unchecked string, containing the subsequence of `self` that starts at
  > `offset` and has length `length`. Both `offset` and `length`
  > are indexed by byte.
  >  
  >  Note this function does not validate the encoding of the byte sequence,
  > it simply copy the bytes into a new String.
- #### unsafe\_get
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1367:::fn <a href="moonbitlang/core/bytes#Bytes">Bytes</a>::unsafe_get(self : Bytes, idx : Int) -> Byte
  ```
  > 
  >  Retrieves a byte at the specified index from a byte sequence without
  > performing bounds checking. This is a low-level operation that should be used
  > with caution.
  > 
  >  Parameters:
  > 
  >  * `bytes` : The byte sequence to retrieve the byte from.
  >  * `index` : The position in the byte sequence from which to retrieve the
  >    byte.
  > 
  >  Returns a single byte from the specified position in the byte sequence.
  > 
  >  Throws a panic if the index is negative or greater than or equal to the
  > length of the byte sequence.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Bytes::unsafe_get" {
  >    let bytes = b"\x01\x02\x03"
  >    inspect!(bytes.unsafe_get(1), content="b'\\x02'")
  >  }
  >  
  >  test "panic Bytes::unsafe_get/out_of_bounds" {
  >    let bytes = b"\x01\x02\x03"
  >    ignore(bytes.unsafe_get(3)) // Index out of bounds
  >  }
  >  ```
  > 
  >  @alert unsafe "Panic if index is out of bounds"

## FixedArray


#### mooncakes-io-method-mark-Methods
- #### blit\_from\_bytes
  ```moonbit
  :::source,moonbitlang/core/builtin/bytes.mbt,162:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::blit_from_bytes(self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Byte], bytes_offset : Int, src : Bytes, src_offset : Int, length : Int) -> Unit
  ```
  > 
  >  Copy `length` chars from byte sequence `src`, starting at `src_offset`,
  > into byte sequence `self`, starting at `bytes_offset`.
- #### blit\_from\_string
  ```moonbit
  :::source,moonbitlang/core/builtin/bytes.mbt,137:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::blit_from_string(self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Byte], bytes_offset : Int, str : String, str_offset : Int, length : Int) -> Unit
  ```
  > 
  >  Copies characters from a string to a byte sequence in UTF-16LE encoding. Each
  > character is converted into two bytes, with the lower byte stored first.
  > 
  >  Parameters:
  > 
  >  * `self` : The destination byte array to copy the characters into.
  >  * `bytes_offset` : The starting position in the destination array where bytes
  >    will be written.
  >  * `str` : The source string containing the characters to copy.
  >  * `str_offset` : The starting position in the source string from which
  >    characters will be read.
  >  * `length` : The number of characters to copy.
  > 
  >  Throws a runtime error if:
  > 
  >  * `length` is negative
  >  * `bytes_offset` is negative
  >  * `str_offset` is negative
  >  * The range `[bytes_offset, bytes_offset + length * 2)` exceeds the length of
  >    the destination array
  >  * The range `[str_offset, str_offset + length)` exceeds the length of the
  >    source string
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "FixedArray::blit_from_string" {
  >    let bytes = FixedArray::make(6, b'\x00')
  >    bytes.blit_from_string(0, "ABC", 0, 3)
  >    inspect!(bytes[0], content="b'\\x41'") // 'A'
  >    inspect!(bytes[1], content="b'\\x00'")
  >    inspect!(bytes[2], content="b'\\x42'") // 'B'
  >  }
  >  ```
- #### blit\_to
  ```moonbit
  :::source,moonbitlang/core/builtin/fixedarray_block.mbt,106:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::blit_to[A](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A], dst : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A], len~ : Int, src_offset~ : Int = .., dst_offset~ : Int = ..) -> Unit
  ```
  > 
  >  Copies a sequence of elements from the source fixed array to a destination
  > fixed array. The arrays may overlap, in which case the copy is performed in a
  > way that preserves the data.
  > 
  >  Parameters:
  > 
  >  * `self` : The source fixed array from which elements will be copied.
  >  * `dst` : The destination fixed array where elements will be copied to.
  >  * `len` : The number of elements to copy.
  >  * `src_offset` : The starting position in the source array. Defaults to 0.
  >  * `dst_offset` : The starting position in the destination array. Defaults to
  >  0. 
  > 
  >  Throws a panic if:
  > 
  >  * `src_offset + len` exceeds the length of the source array
  >  * `dst_offset + len` exceeds the length of the destination array
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "FixedArray::blit_to" {
  >    let src = FixedArray::make(5, 1)
  >    let dst = FixedArray::make(5, 0)
  >    src.blit_to(dst, len=3, src_offset=1, dst_offset=2)
  >    inspect!(dst, content="[0, 0, 1, 1, 1]")
  >  }
  >  
  >  test "panic FixedArray::blit_to/out_of_bounds" {
  >    let src = FixedArray::make(3, 1)
  >    let dst = FixedArray::make(3, 0)
  >    ignore(src.blit_to(dst, len=4)) // Panics: length out of bounds
  >  }
  >  ```
- #### fill
  ```moonbit
  :::source,moonbitlang/core/builtin/fixedarray.mbt,113:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::fill[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], value : T) -> Unit
  ```
  > 
  >  Fill the array with a given value.
  > 
  >  #### Example
  >  ```
  >  let fa : FixedArray[Int] = [0, 0, 0, 0, 0]
  >  fa.fill(3)
  >  assert_eq!(fa[0], 3)
  >  ```
- #### get
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1586:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::get[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], idx : Int) -> T
  ```
  > 
  >  Retrieves an element at the specified index from a fixed-size array. This
  > function is similar to `op_get` but provides explicit bounds checking.
  > 
  >  Parameters:
  > 
  >  * `array` : The fixed-size array to access.
  >  * `index` : The position in the array from which to retrieve the element.
  > 
  >  Returns the element at the specified index.
  > 
  >  Throws a runtime error if the index is out of bounds (less than 0 or greater
  > than or equal to the length of the array).
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "FixedArray::get" {
  >    let arr = [1, 2, 3]
  >    inspect!(arr.get(1), content="Some(2)")
  >  }
  >  
  >  test "FixedArray::get/out_of_bounds" {
  >    let arr = [1, 2, 3]
  >    inspect!(arr.get(3), content="None")
  >  }
  >  ```
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/builtin/fixedarray.mbt,138:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::is_empty[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]) -> Bool
  ```
  > 
  >  Tests whether the FixedArray contains no elements.
  > 
  >  Parameters:
  > 
  >  * `FixedArray` : The FixedArray to check.
  > 
  >  Returns `true` if the FixedArray has no elements, `false` otherwise.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "FixedArray::is_empty" {
  >    let empty : FixedArray[Int] = []
  >    inspect!(empty.is_empty(), content="true")
  >    let non_empty = [1, 2, 3]
  >    inspect!(non_empty.is_empty(), content="false")
  >  }
  >  ```
- #### iter
  ```moonbit
  :::source,moonbitlang/core/builtin/fixedarray.mbt,38:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::iter[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[T]
  ```
  > 
  > 
  >  Creates an iterator over the elements of a fixed-size array, providing
  > sequential access to each element.
  > 
  >  Parameters:
  > 
  >  * `array` : The fixed-size array to iterate over.
  > 
  >  Returns an iterator that yields each element of the array in order from first
  > to last.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "FixedArray::iter" {
  >    let arr = FixedArray::make(3, 42)
  >    let mut sum = 0
  >    arr.iter().each(fn(x) { sum = sum + x })
  >    inspect!(sum, content="126")
  >  }
  >  ```
- #### iter2
  ```moonbit
  :::source,moonbitlang/core/builtin/fixedarray.mbt,71:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::iter2[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[Int, T]
  ```
  > 
  >  Returns an iterator that yields both indices and values from the fixed array.
  > The iterator provides pairs of `(index, value)` where indices start from 0
  > and increment sequentially.
  > 
  >  Parameters:
  > 
  >  * `array` : The fixed array to iterate over.
  > 
  >  Returns an iterator of type `Iter2[Int, T]` that yields tuples of indices and
  > values from the array.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "FixedArray::iter2" {
  >    let arr = FixedArray::make(3, 10)
  >    let mut sum = 0
  >    arr.iter2().each(fn(i, x) { sum = sum + i + x })
  >    inspect!(sum, content="33") // (0 + 10) + (1 + 10) + (2 + 10) = 33
  >  }
  >  ```
- #### length
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1666:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::length[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]) -> Int
  ```
  > 
  >  Returns the number of elements in a fixed-size array.
  > 
  >  Parameters:
  > 
  >  * `array` : The fixed-size array whose length is to be determined.
  > 
  >  Returns an integer representing the number of elements in the array.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "FixedArray::length" {
  >    let arr = FixedArray::make(3, 42)
  >    inspect!(arr.length(), content="3")
  >  }
  >  ```
- #### make
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1695:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::make[T](len : Int, init : T) -> <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T]
  ```
  > 
  >  Creates a new fixed-size array with the specified length, initializing all
  > elements with the given value.
  > 
  >  Parameters:
  > 
  >  * `length` : The length of the array to create. Must be non-negative.
  >  * `initial_value` : The value used to initialize all elements in the array.
  > 
  >  Returns a new fixed-size array of type `FixedArray[T]` with `length`
  > elements, where each element is initialized to `initial_value`.
  > 
  >  Throws a panic if `length` is negative.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "FixedArray::make" {
  >    let arr = FixedArray::make(3, 42)
  >    inspect!(arr[0], content="42")
  >    inspect!(arr.length(), content="3")
  >  }
  >  
  >  test "panic FixedArray::make/negative_length" {
  >    ignore(FixedArray::make(-1, 0))
  >  }
  >  ```
- #### op\_get
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1525:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::op_get[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], idx : Int) -> T
  ```
  > 
  >  Retrieves an element at the specified index from a fixed-size array. This
  > function implements the array indexing operator `[]`.
  > 
  >  Parameters:
  > 
  >  * `array` : The fixed-size array to access.
  >  * `index` : The position in the array from which to retrieve the element.
  > 
  >  Returns the element at the specified index.
  > 
  >  Throws a runtime error if the index is out of bounds (negative or greater
  > than or equal to the length of the array).
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "FixedArray::op_get" {
  >    let arr = FixedArray::make(3, 42)
  >    inspect!(arr[1], content="42")
  >  }
  >  
  >  test "panic FixedArray::op_get/out_of_bounds" {
  >    let arr = FixedArray::make(3, 0)
  >    ignore(arr[3]) // Index out of bounds
  >  }
  >  ```
- #### op\_set
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1618:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::op_set[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], idx : Int, val : T) -> Unit
  ```
  > 
  >  Sets a value at the specified index in a fixed-size array. The original value
  > at that index is overwritten.
  > 
  >  Parameters:
  > 
  >  * `array` : The fixed-size array to modify.
  >  * `index` : The position in the array where the value will be set.
  >  * `value` : The new value to assign at the specified index.
  > 
  >  Throws a runtime error if the index is out of bounds (less than 0 or greater
  > than or equal to the length of the array).
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "FixedArray::op_set" {
  >    let arr = [1, 2, 3]
  >    arr[1] = 42
  >    inspect!(arr, content="[1, 42, 3]")
  >  }
  >  
  >  test "panic FixedArray::op_set/out_of_bounds" {
  >    let arr = [1, 2, 3]
  >    arr[3] = 42 // Index out of bounds
  >  }
  >  ```
  > 
  >  @alert unsafe "Panic if index is out of bounds."
- #### set
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1647:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::set[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], idx : Int, val : T) -> Unit
  ```
  > 
  >  Sets the value at the specified index in a fixed-size array.
  > 
  >  Parameters:
  > 
  >  * `array` : The fixed-size array to be modified.
  >  * `index` : The index at which to set the value. Must be non-negative and
  >    less than the array's length.
  >  * `value` : The value to be set at the specified index.
  > 
  >  Throws a runtime error if the index is out of bounds (less than 0 or greater
  > than or equal to the array's length).
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "FixedArray::set" {
  >    let arr = FixedArray::make(3, 0)
  >    arr.set(1, 42)
  >    inspect!(arr[1], content="42")
  >  }
  >  
  >  test "panic FixedArray::set/out_of_bounds" {
  >    let arr = FixedArray::make(3, 0)
  >    ignore(arr.set(3, 42)) // Panic: index out of bounds
  >  }
  >  ```
- #### set\_utf16be\_char
  ```moonbit
  :::source,moonbitlang/core/builtin/bytes.mbt,306:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::set_utf16be_char(self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Byte], offset : Int, value : Char) -> Int
  ```
  > 
  >  Fill UTF16BE encoded char `value` into byte sequence `self`, starting at `offset`.
  > It return the length of bytes has been written.
  > @alert unsafe "Panic if the \[value\] is out of range"
- #### set\_utf16le\_char
  ```moonbit
  :::source,moonbitlang/core/builtin/bytes.mbt,278:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::set_utf16le_char(self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Byte], offset : Int, value : Char) -> Int
  ```
  > 
  >  Fill UTF16LE encoded char `value` into byte sequence `self`, starting at `offset`.
  > It return the length of bytes has been written.
  > @alert unsafe "Panic if the \[value\] is out of range"
- #### set\_utf8\_char
  ```moonbit
  :::source,moonbitlang/core/builtin/bytes.mbt,241:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::set_utf8_char(self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Byte], offset : Int, value : Char) -> Int
  ```
  > 
  >  Encodes a Unicode character into UTF-8 bytes and writes them into a fixed
  > array of bytes at the specified offset.
  > 
  >  Parameters:
  > 
  >  * `array` : The fixed array of bytes to write into.
  >  * `offset` : The starting position in the array where the encoded bytes will
  >    be written.
  >  * `char` : The Unicode character to be encoded.
  > 
  >  Returns the number of bytes written (1 to 4 bytes depending on the
  > character's code point).
  > 
  >  Throws a panic if:
  > 
  >  * The character's code point is greater than 0x10FFFF.
  >  * The array's size is insufficient to store the encoded bytes at the given
  >    offset.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "FixedArray::set_utf8_char" {
  >    let buf = FixedArray::make(4, b'\x00')
  >    let written = buf.set_utf8_char(0, '€') // Euro symbol (U+20AC)
  >    inspect!(written, content="3") // UTF-8 encoding takes 3 bytes
  >    inspect!(buf[0], content="b'\\xE2'")
  >    inspect!(buf[1], content="b'\\x82'")
  >    inspect!(buf[2], content="b'\\xAC'")
  >  }
  >  
  >  test "panic FixedArray::set_utf8_char/invalid_char" {
  >    let buf = FixedArray::make(4, b'\x00')
  >    ignore(buf.set_utf8_char(0, Char::from_int(0x110000))) // Invalid Unicode code point
  >  }
  >  ```
- #### unsafe\_blit
  ```moonbit
  :::source,moonbitlang/core/builtin/fixedarray_block.mbt,37:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::unsafe_blit[A](dst : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A], dst_offset : Int, src : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[A], src_offset : Int, len : Int) -> Unit
  ```
  > 
  >  Copies a slice of elements from one fixed array to another.
  > 
  >  This function copies `len` elements from `src` starting at `src_offset` to `dst` starting at `dst_offset`.
  > The arrays may overlap, in which case the copy is performed in a way that preserves the data.
  > 
  >  #### Example
  >  ```
  >  let src = FixedArray::from_array([1, 2, 3, 4, 5])
  >  let dst = FixedArray::from_array([0, 0, 0, 0, 0])
  >  FixedArray::unsafe_blit(dst, 0, src, 0, 3)
  >  assert_eq!(dst, FixedArray::from_array([1, 2, 3, 0, 0]))
  >  ```
  > 
  >  The behavior is undefined and platform-specific if:
  >  - `len < 0`
  >  - `src_offset < 0`
  >  - `dst_offset < 0`
  >  - `dst_offset + len > dst.length()`
  >  - `src_offset + len > src.length()`
  > 
- #### unsafe\_get
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1557:::fn <a href="moonbitlang/core/array#FixedArray">FixedArray</a>::unsafe_get[T](self : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[T], idx : Int) -> T
  ```
  > 
  >  Retrieves an element from a fixed-size array at the specified index without
  > performing bounds checking. This is an unsafe operation that may cause
  > undefined behavior if used incorrectly.
  > 
  >  Parameters:
  > 
  >  * `array` : The fixed-size array to retrieve the element from.
  >  * `index` : The position in the array from which to retrieve the element.
  > 
  >  Returns the element at the specified index in the array.
  > 
  >  Throws a panic if the index is out of bounds (negative or greater than or
  > equal to the array's length).
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "FixedArray::unsafe_get" {
  >    let arr = FixedArray::make(3, 42)
  >    inspect!(arr.unsafe_get(1), content="42")
  >  }
  >  
  >  test "panic FixedArray::unsafe_get/out_of_bounds" {
  >    let arr = FixedArray::make(3, 42)
  >    ignore(arr.unsafe_get(3)) // Index out of bounds
  >  }
  >  ```
  > 
  >  @alert unsafe "Panic if index is out of bounds"

## Option


#### mooncakes-io-method-mark-Methods
- #### to\_string
  ```moonbit
  :::source,moonbitlang/core/builtin/option.mbt,25:::fn <a href="moonbitlang/core/option#Option">Option</a>::to_string[X : <a href="moonbitlang/core/builtin#Show">Show</a>](self : X?) -> String
  ```
  > 
- #### unwrap
  ```moonbit
  :::source,moonbitlang/core/builtin/option.mbt,35:::fn <a href="moonbitlang/core/option#Option">Option</a>::unwrap[X](self : X?) -> X
  ```
  > 
  >  Extract the value in `Some`.
  > @alert unsafe "Panic if input is `None`."

## String


#### mooncakes-io-method-mark-Methods
- #### char\_length
  ```moonbit
  :::source,moonbitlang/core/builtin/string.mbt,160:::fn <a href="moonbitlang/core/string#String">String</a>::char_length(self : String, start_offset~ : Int = .., end_offset~ : Int = ..) -> Int
  ```
  > 
  >  Returns the number of Unicode code points (characters) in the string.
  > 
  >  This method counts actual Unicode characters, properly handling surrogate pairs
  > that represent single characters like emojis. For the raw UTF-16 code unit count,
  > use `length()` instead.
  > 
  >  #### Examples
  > 
  >  ```
  >  let s = "Hello🤣";
  >  inspect!(s.char_length(), content = "6"); // 6 actual characters
  >  inspect!(s.length(), content = "7");  // 5 ASCII chars + 2 surrogate pairs
  >  ```
- #### charcode\_at
  ```moonbit
  :::source,moonbitlang/core/builtin/string.mbt,79:::fn <a href="moonbitlang/core/string#String">String</a>::charcode_at(self : String, index : Int) -> Int
  ```
  > 
  >  Returns the UTF-16 code unit at the given index.
  > 
  >  #### Examples
  > 
  >  ```
  >  let s = "Hello🤣";
  >  inspect!(s.charcode_at(0), content="72");
  >  inspect!(s.charcode_at(5), content="55358"); // First surrogate of 🤣
  >  inspect!(s.charcode_at(6), content="56611"); // Second surrogate of 🤣
  >  ```
  > 
  >  #### Panics
  > 
  >  @alert unsafe "Panics if the index is out of bounds."
- #### charcode\_length
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1723:::fn <a href="moonbitlang/core/string#String">String</a>::charcode_length(self : String) -> Int
  ```
  > 
- #### codepoint\_at
  ```moonbit
  :::source,moonbitlang/core/builtin/string.mbt,101:::fn <a href="moonbitlang/core/string#String">String</a>::codepoint_at(self : String, index : Int) -> Char
  ```
  > 
  >  Returns the Unicode code point at the given index.
  > 
  >  This method counts Unicode code points (characters) rather than UTF-16 code units.
  > It properly handles surrogate pairs to return the correct Unicode character.
  > 
  >  #### Examples
  > 
  >  ```
  >  let s = "Hello🤣";
  >  inspect!(s.codepoint_at(0), content="H");
  >  inspect!(s.codepoint_at(5), content="🤣"); // Returns full emoji character
  >  ```
  > 
  >  #### Panics
  > 
  >  Panics if:
  >  - The index is out of bounds
  >  - The string contains an invalid surrogate pair
- #### codepoint\_length
  ```moonbit
  :::source,moonbitlang/core/builtin/string.mbt,189:::fn <a href="moonbitlang/core/string#String">String</a>::codepoint_length(self : String, start_offset~ : Int = .., end_offset~ : Int = ..) -> Int
  ```
  > 
- #### escape
  ```moonbit
  :::source,moonbitlang/core/builtin/show.mbt,168:::fn <a href="moonbitlang/core/string#String">String</a>::escape(self : String) -> String
  ```
  > 
  >  Returns a valid MoonBit string literal representation of a string,
  > add quotes and escape special characters.
- #### get
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1786:::fn <a href="moonbitlang/core/string#String">String</a>::get(self : String, idx : Int) -> Char
  ```
  > 
  >  Retrieves the character at the specified index in a string.
  > 
  >  Parameters:
  > 
  >  * `string` : The string to access.
  >  * `index` : The position in the string from which to retrieve the character.
  > 
  >  Returns a Unicode character at the specified position in the string.
  > 
  >  Throws a runtime error if the index is negative or greater than or equal to
  > the length of the string.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "String::get" {
  >    let s = "Hello, 世界"
  >    inspect!(s.get(0), content="H")
  >    inspect!(s.get(7), content="世")
  >  }
  >  
  >  test "panic String::get/out_of_bounds" {
  >    let s = "Hello"
  >    ignore(s.get(-1)) // Negative index
  >    ignore(s.get(5)) // Index equals length
  >  }
  >  ```
- #### length
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1719:::fn <a href="moonbitlang/core/string#String">String</a>::length(self : String) -> Int
  ```
  > 
  >  Returns the number of UTF-16 code units in the string. Note that this is not
  > necessarily equal to the number of Unicode characters (code points) in the
  > string, as some characters may be represented by multiple UTF-16 code units.
  > 
  >  Parameters:
  > 
  >  * `string` : The string whose length is to be determined.
  > 
  >  Returns the number of UTF-16 code units in the string.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "String::length" {
  >    inspect!("hello".length(), content="5")
  >    inspect!("🤣".length(), content="2") // Emoji uses two UTF-16 code units
  >    inspect!("".length(), content="0") // Empty string
  >  }
  >  ```
- #### make
  ```moonbit
  :::source,moonbitlang/core/builtin/string.mbt,24:::fn <a href="moonbitlang/core/string#String">String</a>::make(length : Int, value : Char) -> String
  ```
  > 
  >  Create new string of `length`, where each character is `value`
  > 
  >  ```
  >  assert_eq!(String::make(5,'S'), "SSSSS")
  >  ```
- #### op\_get
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1755:::fn <a href="moonbitlang/core/string#String">String</a>::op_get(self : String, idx : Int) -> Char
  ```
  > 
  >  Retrieves the character at the specified index in a string. Each character in
  > the string is represented as a UTF-16 code unit.
  > 
  >  Parameters:
  > 
  >  * `string` : The string from which to retrieve the character.
  >  * `index` : The position in the string from which to retrieve the character.
  > 
  >  Returns the character at the specified index.
  > 
  >  Throws a runtime error if `index` is negative or greater than or equal to the
  > length of the string.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "String::op_get" {
  >    let s = "Hello, 世界!"
  >    inspect!(s[0], content="H")
  >    inspect!(s[7], content="世")
  >  }
  >  
  >  test "panic String::op_get/out_of_bounds" {
  >    let s = "Hello"
  >    ignore(s[5]) // Index out of bounds
  >  }
  >  ```
  > 
  >  @alert unsafe "Panic if index is out of bounds"
- #### substring
  ```moonbit
  :::source,moonbitlang/core/builtin/string.mbt,242:::fn <a href="moonbitlang/core/string#String">String</a>::substring(self : String, start~ : Int = .., end? : Int) -> String
  ```
  > 
  >  Returns a new string containing characters from the original string starting
  > at `start` index up to (but not including) `end` index.
  > 
  >  Parameters:
  > 
  >  * `string` : The source string from which to extract the substring.
  >  * `start` : The starting index of the substring (inclusive). Defaults to 0.
  >  * `end` : The ending index of the substring (exclusive). Defaults to the
  >    length of the string.
  > 
  >  Returns a new string containing the specified substring.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "substring/basic" {
  >    let s = "Hello world"
  >    inspect!(s.substring(start=0, end=5), content="Hello")
  >    inspect!(s.substring(start=6, end=11), content="world")
  >    inspect!(s.substring(), content="Hello world")
  >  }
  >  
  >  test "substring/empty" {
  >    let s = "test"
  >    inspect!(s.substring(start=2, end=2), content="")
  >    inspect!("".substring(), content="")
  >  }
  >  
  >  test "panic substring/invalid_range" {
  >    let s = "test"
  >    ignore(s.substring(start=-1))
  >    ignore(s.substring(end=5))
  >    ignore(s.substring(start=3, end=2))
  >  }
  >  ```
- #### to\_string
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1879:::fn <a href="moonbitlang/core/string#String">String</a>::to_string(self : String) -> String
  ```
  > 
  >  Returns the string itself without any modifications. This method is primarily
  > used to implement the `Show` trait, which requires a `to_string` function.
  > 
  >  Parameters:
  > 
  >  * `string` : The string value to be returned.
  > 
  >  Returns the same string that was passed in.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "String::to_string" {
  >    let s = "hello"
  >    inspect!(s.to_string(), content="hello")
  >  }
  >  ```
- #### unsafe\_char\_at
  ```moonbit
  :::source,moonbitlang/core/builtin/string.mbt,136:::fn <a href="moonbitlang/core/string#String">String</a>::unsafe_char_at(self : String, index : Int) -> Char
  ```
  > 
  >  Returns the Unicode code point at the given index without bounds checking.
- #### unsafe\_charcode\_at
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1812:::fn <a href="moonbitlang/core/string#String">String</a>::unsafe_charcode_at(self : String, idx : Int) -> Int
  ```
  > 
  >  Returns the UTF-16 code unit at a given position in the string without
  > performing bounds checking. This is a low-level function that provides direct
  > access to the internal representation of the string.
  > 
  >  Parameters:
  > 
  >  * `string` : The string from which to retrieve the code unit.
  >  * `index` : The position of the code unit to retrieve.
  > 
  >  Returns the UTF-16 code unit at the specified position as an integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "String::unsafe_charcode_at" {
  >    let s = "Hello🤣"
  >    inspect!(s.unsafe_charcode_at(0), content="72") // 'H'
  >    inspect!(s.unsafe_charcode_at(5), content="55358") // First surrogate of 🤣
  >    inspect!(s.unsafe_charcode_at(6), content="56611") // Second surrogate of 🤣
  >  }
  >  ```
  > 
  >  @alert unsafe "Panic if index is out of bounds."

## Double


#### mooncakes-io-method-mark-Methods
- #### convert\_uint
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1184:::fn <a href="moonbitlang/core/double#Double">Double</a>::convert_uint(val : UInt) -> Double
  ```
  > 
  >  Converts an unsigned 32-bit integer to a double-precision floating-point
  > number. Since the range of unsigned 32-bit integers is smaller than what can
  > be precisely represented by a double-precision floating-point number, this
  > conversion is guaranteed to be exact.
  > 
  >  Parameters:
  > 
  >  * `value` : The unsigned 32-bit integer to be converted.
  > 
  >  Returns a double-precision floating-point number that exactly represents the
  > input value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Double::convert_uint" {
  >    let n = 42U
  >    inspect!(Double::convert_uint(n), content="42")
  >    let max = 4294967295U // maximum value of UInt
  >    inspect!(Double::convert_uint(max), content="4294967295")
  >  }
  >  ```
- #### convert\_uint64
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,993:::fn <a href="moonbitlang/core/double#Double">Double</a>::convert_uint64(val : UInt64) -> Double
  ```
  > 
  >  Converts an unsigned 64-bit integer to a double-precision floating-point
  > number. The conversion is exact for integers up to 53 bits (the size of the
  > mantissa in a double-precision number), but may lose precision for larger
  > values.
  > 
  >  Parameters:
  > 
  >  * `value` : The unsigned 64-bit integer to be converted.
  > 
  >  Returns a double-precision floating-point number representing the same
  > numerical value as the input.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Double::convert_uint64" {
  >    let n = 12345678901234567890UL
  >    inspect!(Double::convert_uint64(n), content="12345678901234567000")
  >  }
  >  ```
- #### op\_neq
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1110:::fn <a href="moonbitlang/core/double#Double">Double</a>::op_neq(self : Double, other : Double) -> Bool
  ```
  > 
  >  Tests for inequality between two double-precision floating-point numbers.
  > Takes into account special cases like NaN, where two NaN values are
  > considered not equal to each other.
  > 
  >  Parameters:
  > 
  >  * `self` : The first double-precision floating-point number to compare.
  >  * `other` : The second double-precision floating-point number to compare.
  > 
  >  Returns `true` if the two numbers are not equal according to IEEE 754 rules,
  > `false` otherwise.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Double::op_neq" {
  >    inspect!(1.0 != 2.0, content="true")
  >    inspect!(1.0 != 1.0, content="false")
  >    inspect!(0.0 / 0.0 != 0.0 / 0.0, content="true") // NaN != NaN
  >  }
  >  ```
- #### reinterpret\_as\_i64
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,895:::fn <a href="moonbitlang/core/double#Double">Double</a>::reinterpret_as_i64(self : Double) -> Int64
  ```
  > 
  >  Reinterprets the bits of a double-precision floating-point number as a 64-bit
  > signed integer without any conversion. This is a low-level operation that
  > simply reinterprets the bit pattern of the input value.
  > 
  >  Parameters:
  > 
  >  * `value` : The double-precision floating-point number whose bits are to be
  >    reinterpreted.
  > 
  >  Returns a 64-bit signed integer that has the same bit pattern as the input
  > double-precision floating-point number.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Double::reinterpret_as_i64" {
  >    let d = 1.0
  >    // 1.0 in IEEE 754 double format has the bit pattern 0x3FF0000000000000
  >    inspect!(d.reinterpret_as_int64(), content="4607182418800017408")
  >  }
  >  ```
  > 
- #### reinterpret\_as\_int64
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,920:::fn <a href="moonbitlang/core/double#Double">Double</a>::reinterpret_as_int64(self : Double) -> Int64
  ```
  > 
  >  Reinterprets the bits of a double-precision floating-point number as a 64-bit
  > signed integer without performing any conversion. Preserves the exact bit
  > pattern of the input value.
  > 
  >  Parameters:
  > 
  >  * `number` : The double-precision floating-point number whose bits will be
  >    reinterpreted.
  > 
  >  Returns a 64-bit signed integer containing the same bit pattern as the input
  > floating-point number.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Double::reinterpret_as_int64" {
  >    let d = 1.0
  >    inspect!(d.reinterpret_as_int64(), content="4607182418800017408") // IEEE 754 representation of 1.0
  >    let neg = -0.0
  >    inspect!(neg.reinterpret_as_int64(), content="-9223372036854775808") // Sign bit set
  >  }
  >  ```
- #### reinterpret\_as\_u64
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,947:::fn <a href="moonbitlang/core/double#Double">Double</a>::reinterpret_as_u64(self : Double) -> UInt64
  ```
  > 
  >  Reinterprets the bits of a double-precision floating-point number as an
  > unsigned 64-bit integer. The bit pattern is preserved during the conversion,
  > with no mathematical conversion performed.
  > 
  >  Parameters:
  > 
  >  * `self` : The double-precision floating-point number to be reinterpreted.
  > 
  >  Returns an unsigned 64-bit integer containing the same bit pattern as the
  > input floating-point number.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Double::reinterpret_as_u64" {
  >    let zero = 0.0
  >    let positive = 1.0
  >    inspect!(zero.reinterpret_as_uint64(), content="0")
  >    inspect!(positive.reinterpret_as_uint64(), content="4607182418800017408")
  >  }
  >  ```
  > 
- #### reinterpret\_as\_uint64
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,970:::fn <a href="moonbitlang/core/double#Double">Double</a>::reinterpret_as_uint64(self : Double) -> UInt64
  ```
  > 
  >  Reinterprets the bits of a double-precision floating-point number as an
  > unsigned 64-bit integer, preserving the exact bit pattern without performing
  > any numerical conversion.
  > 
  >  Parameters:
  > 
  >  * `self` : The double-precision floating-point number whose bits will be
  >    reinterpreted.
  > 
  >  Returns an unsigned 64-bit integer that has the same bit pattern as the input
  > floating-point number.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Double::reinterpret_as_uint64" {
  >    let d = 1.0
  >    inspect!(d.reinterpret_as_uint64(), content="4607182418800017408") // Binary: 0x3FF0000000000000
  >  }
  >  ```
- #### sqrt
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1058:::fn <a href="moonbitlang/core/double#Double">Double</a>::sqrt(self : Double) -> Double
  ```
  > 
  >  Calculates the square root of a double-precision floating-point number. For
  > non-negative numbers, returns the positive square root. For negative numbers
  > or NaN, returns NaN.
  > 
  >  Parameters:
  > 
  >  * `self` : The double-precision floating-point number whose square root is to
  >    be calculated.
  > 
  >  Returns the square root of the input number, or NaN if the input is negative
  > or NaN.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Double::sqrt" {
  >    inspect!(4.0.sqrt(), content="2")
  >    inspect!(0.0.sqrt(), content="0")
  >    inspect!((-1.0).sqrt(), content="NaN")
  >  }
  >  ```
- #### to\_float
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,3006:::fn <a href="moonbitlang/core/double#Double">Double</a>::to_float(self : Double) -> Float
  ```
  > 
  >  Converts a double-precision floating-point number to a single-precision
  > floating-point number. The conversion may result in a loss of precision due
  > to the reduced number of bits available in the single-precision format.
  > 
  >  Parameters:
  > 
  >  * `value` : The double-precision floating-point number to be converted.
  > 
  >  Returns a single-precision floating-point number that represents the closest
  > possible value to the input double-precision number.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Double::to_float" {
  >    let d = 3.14159265359
  >    inspect!(d.to_float().to_double(), content="3.1415927410125732") // Note the loss of precision
  >  }
  >  ```
- #### to\_int
  ```moonbit
  :::source,moonbitlang/core/builtin/double_to_int_wasm.mbt,43:::fn <a href="moonbitlang/core/double#Double">Double</a>::to_int(self : Double) -> Int
  ```
  > 
  >  Converts a double-precision floating-point number to a 32-bit integer.
  > Handles special cases including NaN and numbers outside the valid Int range.
  > 
  >  Parameters:
  > 
  >  * `self` : The double-precision floating-point number to be converted.
  > 
  >  Returns an 32-bit integer value according to the following rules:
  > 
  >  * Returns 0 if the input is NaN
  >  * Returns `@int.max_value` (2147483647) if the input is greater than or
  >    equal to `@int.max_value`
  >  * Returns `@int.min_value` (-2147483648) if the input is less than or equal
  >    to `@int.min_value`
  >  * Otherwise returns the integer part of the input by truncating towards zero
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Double::to_int/normal" {
  >    inspect!(42.0.to_int(), content="42")
  >    inspect!((-42.5).to_int(), content="-42")
  >    inspect!((0.0 / 0.0).to_int(), content="0") // NaN
  >    inspect!((1.0 / 0.0).to_int(), content="2147483647") // Infinity
  >    inspect!((-1.0 / 0.0).to_int(), content="-2147483648") // -Infinity
  >  }
  >  ```
- #### to\_int64
  ```moonbit
  :::source,moonbitlang/core/builtin/double_to_int64_wasm.mbt,43:::fn <a href="moonbitlang/core/double#Double">Double</a>::to_int64(self : Double) -> Int64
  ```
  > 
  >  Converts a double-precision floating-point number to a 64-bit integer.
  > Handles special cases including NaN and numbers outside the valid Int range.
  > 
  >  Parameters:
  > 
  >  * `self` : The double-precision floating-point number to be converted.
  > 
  >  Returns an 64-bit integer value according to the following rules:
  > 
  >  * Returns 0 if the input is NaN
  >  * Returns `@int64.max_value` (9223372036854775807L) if the input is greater than or
  >    equal to `@int64.max_value`
  >  * Returns `@int64.min_value` (-9223372036854775808L) if the input is less than or equal
  >    to `@int64.min_value`
  >  * Otherwise returns the integer part of the input by truncating towards zero
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Double::to_int64" {
  >    inspect!(42.0.to_int64(), content="42")
  >    inspect!((-42.5).to_int64(), content="-42")
  >    inspect!((0.0 / 0.0).to_int64(), content="0") // NaN
  >    inspect!((1.0 / 0.0).to_int64(), content="9223372036854775807") // Infinity
  >    inspect!((-1.0 / 0.0).to_int64(), content="-9223372036854775808") // -Infinity
  >  }
  >  ```
- #### to\_uint64
  ```moonbit
  :::source,moonbitlang/core/builtin/double_to_int64_wasm.mbt,71:::fn <a href="moonbitlang/core/double#Double">Double</a>::to_uint64(self : Double) -> UInt64
  ```
  > 
  >  Converts a double-precision floating-point number to an unsigned 64-bit
  > integer, handling special cases and value ranges.
  > 
  >  Parameters:
  > 
  >  * `value` : The double-precision floating-point number to be converted.
  > 
  >  Returns an unsigned 64-bit integer value according to the following rules:
  > 
  >  * Returns 0 if the input is NaN
  >  * Returns `UInt64::max_value` (18446744073709551615UL) if the input is
  >    greater than or equal to `UInt64::max_value`
  >  * Returns 0UL if the input is less than or equal to 0
  >  * Otherwise returns the integer part of the input by truncating towards zero
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Double::to_uint64" {
  >    inspect!(42.0.to_uint64(), content="42")
  >    inspect!((-42.5).to_uint64(), content="0")
  >    inspect!((0.0 / 0.0).to_uint64(), content="0") // NaN
  >    inspect!((1.0 / 0.0).to_uint64(), content="18446744073709551615") // Infinity
  >  }
  >  ```
- #### until
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,344:::fn <a href="moonbitlang/core/double#Double">Double</a>::until(self : Double, end : Double, step~ : Double = .., inclusive~ : Bool = ..) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[Double]
  ```
  > 
  >  Creates an iterator that iterates over a range of Double with default step 1.0 .
  > To grow the range downward, set the `step` parameter to a negative value.
  > 
  >  #### Arguments
  > 
  >  * `start` - The starting value of the range (inclusive).
  >  * `end` - The ending value of the range (exclusive by default).
  >  * `step` - The step size of the range (default 1.0).
  >  * `inclusive` - Whether the ending value is inclusive (default false).
  > 
  >  #### Returns
  > 
  >  Returns an iterator that iterates over the range of Double from `start` to `end - 1`.
- #### upto
  ```moonbit
  :::source,moonbitlang/core/builtin/iter_upto.mbt,200:::fn <a href="moonbitlang/core/double#Double">Double</a>::upto(self : Double, end : Double, inclusive~ : Bool = ..) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[Double]
  ```
  > 
  >  Creates an iterator that iterates over a range of Double with default step 1.0 .
  > 
  >  #### Arguments
  > 
  >  * `start` - The starting value of the range (inclusive).
  >  * `end` - The ending value of the range (exclusive).
  >  * `inclusive` - Whether the ending value is inclusive (default false).
  > 
  >  #### Returns
  > 
  >  Returns an iterator that iterates over the range of Double from `start` to `end - 1`.

## Float


#### mooncakes-io-method-mark-Methods
- #### op\_neq
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2789:::fn <a href="moonbitlang/core/float#Float">Float</a>::op_neq(self : Float, other : Float) -> Bool
  ```
  > 
  >  Tests if two single-precision floating-point numbers are not equal. This
  > operation follows IEEE 754 rules for floating-point comparison, including
  > special handling of NaN values.
  > 
  >  Parameters:
  > 
  >  * `self` : The first floating-point number to compare.
  >  * `other` : The second floating-point number to compare.
  > 
  >  Returns `true` if the two floating-point numbers are not equal, `false` if
  > they are equal. Note that if either operand is NaN, the result is `true`.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Float::op_neq" {
  >    let x = 1.0.to_float()
  >    let y = 2.0.to_float()
  >    let nan = (0.0 / 0.0).to_float()
  >    inspect!(x != y, content="true")
  >    inspect!(x != x, content="false")
  >    inspect!(nan != nan, content="true") // NaN is not equal to itself
  >  }
  >  ```
- #### reinterpret\_as\_int
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2862:::fn <a href="moonbitlang/core/float#Float">Float</a>::reinterpret_as_int(self : Float) -> Int
  ```
  > 
  >  Reinterprets the bits of a 32-bit floating-point number as a 32-bit signed
  > integer without performing any numeric conversion. The bit pattern is
  > preserved exactly, only the type interpretation changes.
  > 
  >  Parameters:
  > 
  >  * `self` : The 32-bit floating-point number whose bits are to be
  >    reinterpreted.
  > 
  >  Returns a 32-bit signed integer that has the same bit pattern as the input
  > floating-point number.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Float::reinterpret_as_int" {
  >    let f = 1.0.to_float()
  >    // IEEE 754 representation of 1.0 is 0x3F800000
  >    inspect!(f.reinterpret_as_int(), content="1065353216")
  >  }
  >  ```
- #### reinterpret\_as\_uint
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2885:::fn <a href="moonbitlang/core/float#Float">Float</a>::reinterpret_as_uint(self : Float) -> UInt
  ```
  > 
  >  Reinterprets the bits of a 32-bit floating-point number as an unsigned 32-bit
  > integer without performing any numeric conversion. Preserves the exact bit
  > pattern of the input value, only changing how these bits are interpreted.
  > 
  >  Parameters:
  > 
  >  * `float` : The 32-bit floating-point number whose bits are to be
  >    reinterpreted.
  > 
  >  Returns an unsigned 32-bit integer (`UInt`) that has the same bit pattern as
  > the input floating-point number.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Float::reinterpret_as_uint" {
  >    let x : Float = 1.0
  >    inspect!(x.reinterpret_as_uint(), content="1065353216") // Decimal representation of 0x3F800000
  >  }
  >  ```
- #### sqrt
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2736:::fn <a href="moonbitlang/core/float#Float">Float</a>::sqrt(self : Float) -> Float
  ```
  > 
  >  Calculates the square root of a floating-point number. For non-negative
  > numbers, returns the principal square root. For negative numbers or NaN,
  > returns NaN.
  > 
  >  Parameters:
  > 
  >  * `self` : The floating-point number whose square root is to be calculated.
  > 
  >  Returns a 32-bit floating-point number representing the square root of the
  > input value:
  > 
  >  * For a positive number, returns its principal square root
  >  * For zero (positive or negative), returns zero with the same sign
  >  * For NaN or negative numbers, returns NaN
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Float::sqrt" {
  >    let x = 16.0.to_float()
  >    let root = x.sqrt()
  >    inspect!(root.to_double(), content="4")
  >    let neg = (-4.0).to_float()
  >    let neg_root = neg.sqrt()
  >    inspect!(neg_root.to_double(), content="NaN")
  >  }
  >  ```
- #### to\_double
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2838:::fn <a href="moonbitlang/core/float#Float">Float</a>::to_double(self : Float) -> Double
  ```
  > 
  >  Converts a 32-bit floating-point number to a double-precision (64-bit)
  > floating-point number.
  > 
  >  Parameters:
  > 
  >  * `self` : The 32-bit floating-point number to be converted.
  > 
  >  Returns a double-precision floating-point number that preserves the exact
  > value of the input. Since double-precision has more bits than
  > single-precision, this conversion is always exact and never loses precision.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Float::to_double" {
  >    let f = 3.14.to_float()
  >    inspect!(f.to_double(), content="3.140000104904175")
  >  }
  >  ```
- #### until
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,301:::fn <a href="moonbitlang/core/float#Float">Float</a>::until(self : Float, end : Float, step~ : Float = .., inclusive~ : Bool = ..) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[Float]
  ```
  > 
  >  Creates an iterator that iterates over a range of Float with default step 1.0 .
  > To grow the range downward, set the `step` parameter to a negative value.
  > 
  >  #### Arguments
  > 
  >  * `start` - The starting value of the range (inclusive).
  >  * `end` - The ending value of the range (exclusive by default).
  >  * `step` - The step size of the range (default 1.0).
  >  * `inclusive` - Whether the ending value is inclusive (default false).
  > 
  >  #### Returns
  > 
  >  Returns an iterator that iterates over the range of Float from `start` to `end - 1`.
- #### upto
  ```moonbit
  :::source,moonbitlang/core/builtin/iter_upto.mbt,165:::fn <a href="moonbitlang/core/float#Float">Float</a>::upto(self : Float, end : Float, inclusive~ : Bool = ..) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[Float]
  ```
  > 
  >  Creates an iterator that iterates over a range of Float with default step 1.0 .
  > 
  >  #### Arguments
  > 
  >  * `start` - The starting value of the range (inclusive).
  >  * `end` - The ending value of the range (exclusive).
  >  * `inclusive` - Whether the ending value is inclusive (default false).
  > 
  >  #### Returns
  > 
  >  Returns an iterator that iterates over the range of Float from `start` to `end - 1`.

## UInt64


#### mooncakes-io-method-mark-Methods
- #### clz
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1617:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::clz(self : UInt64) -> Int
  ```
  > 
  >  Counts the number of leading zero bits in a 64-bit unsigned integer, starting
  > from the most significant bit.
  > 
  >  Parameters:
  > 
  >  * `value` : The 64-bit unsigned integer to count leading zeros in.
  > 
  >  Returns the number of consecutive zeros starting from the most significant
  > bit. For a zero value, returns 64.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt64::clz" {
  >    inspect!(0UL.clz(), content="64")
  >    inspect!(1UL.clz(), content="63")
  >    inspect!(0x8000_0000_0000_0000UL.clz(), content="0")
  >  }
  >  ```
- #### ctz
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1641:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::ctz(self : UInt64) -> Int
  ```
  > 
  >  Counts the number of trailing zero bits in a 64-bit unsigned integer. The
  > trailing zeros are the contiguous zeros at the least significant end of the
  > binary representation.
  > 
  >  Parameters:
  > 
  >  * `value` : The 64-bit unsigned integer to count trailing zeros in.
  > 
  >  Returns the number of trailing zero bits in the input value. If the input is
  > 0, returns 64.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt64::ctz" {
  >    let x = 0x8000000000000000UL // Binary: 1000...0000 (63 trailing zeros)
  >    inspect!(x.ctz(), content="63")
  >    let y = 0UL
  >    inspect!(y.ctz(), content="64")
  >  }
  >  ```
- #### extend\_uint
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,818:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::extend_uint(val : UInt) -> UInt64
  ```
  > 
  >  Converts an unsigned 32-bit integer to an unsigned 64-bit integer by
  > zero-extending it. The resulting value preserves the original number's
  > magnitude while using 64 bits to represent it.
  > 
  >  Parameters:
  > 
  >  * `value` : The unsigned 32-bit integer (`UInt`) to be converted.
  > 
  >  Returns an unsigned 64-bit integer (`UInt64`) representing the same numerical
  > value as the input.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt64::extend_uint" {
  >    let n = 42U
  >    inspect!(UInt64::extend_uint(n), content="42")
  >    let max = 4294967295U // Maximum value of UInt
  >    inspect!(UInt64::extend_uint(max), content="4294967295")
  >  }
  >  ```
- #### lnot
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1440:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::lnot(self : UInt64) -> UInt64
  ```
  > 
  >  Performs a bitwise NOT operation on a 64-bit unsigned integer. Flips all bits
  > in the number, changing each 0 to 1 and each 1 to 0.
  > 
  >  Parameters:
  > 
  >  * `self` : The 64-bit unsigned integer value on which to perform the bitwise
  >    NOT operation.
  > 
  >  Returns a new `UInt64` value with all bits flipped from the input value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt64::lnot" {
  >    let x = 0xFFFF_FFFF_0000_0000UL
  >    inspect!(x.lnot(), content="4294967295") // 0x0000_0000_FFFF_FFFF
  >  }
  >  ```
- #### lsl
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1467:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::lsl(self : UInt64, shift : Int) -> UInt64
  ```
  > 
  >  Performs a left shift operation on a 64-bit unsigned integer by a specified
  > number of bits.
  > 
  >  Parameters:
  > 
  >  * `value` : The 64-bit unsigned integer to be shifted.
  >  * `shift` : The number of positions to shift left. Only the lowest 6 bits are
  >    used, effectively making the shift value wrap around at 64.
  > 
  >  Returns a new `UInt64` value representing the result of shifting the bits
  > left by the specified number of positions. Bits shifted beyond the 64-bit
  > boundary are discarded, and zeros are shifted in from the right.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt64::lsl" {
  >    let x = 1UL
  >    inspect!(x << 4, content="16") // 1 << 4 = 16
  >  }
  >  ```
  > 
- #### lsr
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1544:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::lsr(self : UInt64, shift : Int) -> UInt64
  ```
  > 
  >  Performs a logical right shift operation on a 64-bit unsigned integer. Moves
  > all bits to the right by a specified number of positions, filling the
  > leftmost bits with zeros.
  > 
  >  Parameters:
  > 
  >  * `self` : The 64-bit unsigned integer to be shifted.
  >  * `shift` : The number of positions to shift right. If this value is negative
  >    or greater than 63, the behavior is undefined.
  > 
  >  Returns a new `UInt64` value containing the result of the right shift
  > operation.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt64::lsr" {
  >    let x = 0xF000000000000000UL
  >    inspect!(x >> 4, content="1080863910568919040") // 0x0F00000000000000
  >  }
  >  ```
  > 
- #### popcnt
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1662:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::popcnt(self : UInt64) -> Int
  ```
  > 
  >  Counts the number of bits set to 1 in the binary representation of an
  > unsigned 64-bit integer.
  > 
  >  Parameters:
  > 
  >  * `self` : The unsigned 64-bit integer whose bits are to be counted.
  > 
  >  Returns an integer representing the number of 1 bits (population count) in
  > the binary representation of the input.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt64::popcnt" {
  >    let n = 0x7000_0001_1F00_100FUL // Binary: 0111 0000 ... 0001 1111 0000 0000 0001 0000 0000 1111
  >    inspect!(n.popcnt(), content="14") // Has 14 bits set to 1
  >  }
  >  ```
- #### reinterpret\_as\_double
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,678:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::reinterpret_as_double(self : UInt64) -> Double
  ```
  > 
  >  Reinterprets the bits of an unsigned 64-bit integer as a double-precision
  > floating-point number according to IEEE 754 standard. The bit pattern of the
  > input is preserved, only the type interpretation changes.
  > 
  >  Parameters:
  > 
  >  * `value` : The unsigned 64-bit integer whose bits are to be reinterpreted as
  >    a double-precision floating-point number.
  > 
  >  Returns a double-precision floating-point number that has the same bit
  > pattern as the input unsigned 64-bit integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt64::reinterpret_as_double" {
  >    // 0x4045000000000000 represents 42.0 in IEEE 754 double format
  >    let n = 4636737291354636288UL
  >    inspect!(n.reinterpret_as_double(), content="100")
  >  }
  >  ```
- #### reinterpret\_as\_int64
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1092:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::reinterpret_as_int64(self : UInt64) -> Int64
  ```
  > 
  >  Reinterprets the bits of an unsigned 64-bit integer as a signed 64-bit
  > integer. The bits remain the same, but their interpretation changes. This
  > operation is useful for low-level bit manipulation and type conversions where
  > you want to preserve the exact bit pattern.
  > 
  >  Parameters:
  > 
  >  * `value` : The unsigned 64-bit integer (`UInt64`) to be reinterpreted.
  > 
  >  Returns a signed 64-bit integer (`Int64`) that has the same bit pattern as
  > the input value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt64::reinterpret_as_int64" {
  >    let max = 18446744073709551615UL // Maximum value of UInt64
  >    inspect!(max.reinterpret_as_int64(), content="-1") // All bits set to 1 represents -1 in two's complement
  >  }
  >  ```
- #### shl
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1493:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::shl(self : UInt64, shift : Int) -> UInt64
  ```
  > 
  >  Performs a left shift operation on an unsigned 64-bit integer value, shifting
  > bits to the left by the specified number of positions.
  > 
  >  Parameters:
  > 
  >  * `number` : The unsigned 64-bit integer to be shifted.
  >  * `shift` : The number of positions to shift the bits left. Must be
  >    non-negative.
  > 
  >  Returns an unsigned 64-bit integer representing the result of the left shift
  > operation.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt64::shl" {
  >    let x = 1UL
  >    inspect!(x << 2, content="4") // 1 << 2 = 4
  >  }
  >  ```
  > 
- #### shr
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1517:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::shr(self : UInt64, shift : Int) -> UInt64
  ```
  > 
  >  Performs a logical right shift on an unsigned 64-bit integer by a specified
  > number of bit positions. All bits shifted in from the left are zeros.
  > 
  >  Parameters:
  > 
  >  * `self` : The unsigned 64-bit integer to be shifted.
  >  * `shift` : The number of positions to shift right.
  > 
  >  Returns the result of shifting the bits in `self` right by `shift` positions.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt64::shr" {
  >    let x = 0xFF00000000000000UL
  >    inspect!(x >> 8, content="71776119061217280")
  >  }
  >  ```
  > 
- #### to\_byte
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1492:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::to_byte(self : UInt64) -> Byte
  ```
  > 
  >  Converts an unsigned 64-bit integer to a byte by truncating it to fit within
  > the byte range (0 to 255).
  > 
  >  Parameters:
  > 
  >  * `self` : The unsigned 64-bit integer to be converted.
  > 
  >  Returns a byte containing the least significant 8 bits of the input integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt64::to_byte" {
  >    let n = 258UL // In binary: 100000010
  >    inspect!(n.to_byte(), content="b'\\x02'") // Only keeps 00000010
  >  }
  >  ```
- #### to\_double
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1166:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::to_double(self : UInt64) -> Double
  ```
  > 
  >  Converts an unsigned 64-bit integer to a double-precision floating-point
  > number.
  > 
  >  Parameters:
  > 
  >  * `self` : The unsigned 64-bit integer (`UInt64`) to be converted.
  > 
  >  Returns a double-precision floating-point number (`Double`) that represents
  > the same numerical value as the input. Note that due to the limited precision
  > of double-precision floating-point numbers, values larger than 2^53 may lose
  > precision during the conversion.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt64::to_double" {
  >    let n = 12345678901234567890UL
  >    inspect!(n.to_double(), content="12345678901234567000") // Note the slight precision loss
  >    let small = 42UL
  >    inspect!(small.to_double(), content="42")
  >  }
  >  ```
- #### to\_float
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1687:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::to_float(self : UInt64) -> Float
  ```
  > 
  >  Converts an unsigned 64-bit integer to a 32-bit floating-point number. Due to
  > floating-point precision limitations, the conversion may lose precision if
  > the integer value is too large to be represented exactly as a float.
  > 
  >  Parameters:
  > 
  >  * `self` : The unsigned 64-bit integer to be converted.
  > 
  >  Returns a 32-bit floating-point number that represents the input value. If
  > the input value is too large to be represented exactly, the result will be
  > rounded to the nearest representable float value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt64::to_float" {
  >    let n = 42UL
  >    inspect!(n.to_float().to_double(), content="42")
  >    let big = 18446744073709551615UL // UInt64::max_value
  >    inspect!(big.to_float().to_double(), content="18446744073709552000")
  >  }
  >  ```
- #### to\_int
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1141:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::to_int(self : UInt64) -> Int
  ```
  > 
  >  Converts an unsigned 64-bit integer to a 32-bit signed integer. The
  > conversion truncates the value to fit within the 32-bit range, possibly
  > losing information if the input value is too large.
  > 
  >  Parameters:
  > 
  >  * `self` : The unsigned 64-bit integer to be converted.
  > 
  >  Returns a 32-bit signed integer representing the lower 32 bits of the input
  > value. If the input value is larger than the maximum value of a 32-bit signed
  > integer (2147483647), the result will be the truncated value interpreted as a
  > signed integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt64::to_int" {
  >    let a = 42UL
  >    inspect!(a.to_int(), content="42")
  >    let b = 18446744073709551615UL // max value of UInt64
  >    inspect!(b.to_int(), content="-1") // truncated to 32 bits
  >  }
  >  ```
- #### to\_int64
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1069:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::to_int64(self : UInt64) -> Int64
  ```
  > 
  >  Reinterprets a 64-bit unsigned integer as a 64-bit signed integer. The bits
  > of the number remain unchanged; only the interpretation of these bits
  > changes. This function is deprecated; use `reinterpret_as_int64` instead.
  > 
  >  Parameters:
  > 
  >  * `value` : The 64-bit unsigned integer to be reinterpreted.
  > 
  >  Returns a 64-bit signed integer representing the same bit pattern as the
  > input.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt64::reinterpret_as_int64" {
  >    let max = 18446744073709551615UL
  >    inspect!(max.reinterpret_as_int64(), content="-1")
  >  }
  >  ```
  > 
- #### to\_string
  ```moonbit
  :::source,moonbitlang/core/builtin/to_string.mbt,62:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::to_string(self : UInt64, radix~ : Int = ..) -> String
  ```
  > 
- #### to\_uint
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1115:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::to_uint(self : UInt64) -> UInt
  ```
  > 
  >  Converts a 64-bit unsigned integer to a 32-bit unsigned integer by truncating
  > the higher 32 bits.
  > 
  >  Parameters:
  > 
  >  * `self` : The 64-bit unsigned integer to be converted.
  > 
  >  Returns a 32-bit unsigned integer containing the lower 32 bits of the input
  > value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt64::to_uint" {
  >    let big = 0xFFFFFFFFFFFFFFFFUL // max value of UInt64
  >    inspect!(big.to_uint(), content="4294967295") // 0xFFFFFFFF, max value of UInt
  >    let small = 42UL
  >    inspect!(small.to_uint(), content="42")
  >  }
  >  ```
- #### trunc\_double
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,768:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::trunc_double(val : Double) -> UInt64
  ```
  > 
  >  Converts a double-precision floating-point number to an unsigned 64-bit
  > integer by truncating its decimal part. This is a raw conversion function
  > that does not handle special cases like NaN or infinity.
  > 
  >  Parameters:
  > 
  >  * `value` : The double-precision floating-point number to be truncated and
  >    converted.
  > 
  >  Returns an unsigned 64-bit integer. The decimal part of the input is
  > discarded (truncated towards zero).
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt64::trunc_double" {
  >    inspect!(UInt64::trunc_double(42.75), content="42")
  >  }
  >  ```
- #### upto
  ```moonbit
  :::source,moonbitlang/core/builtin/iter_upto.mbt,95:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::upto(self : UInt64, end : UInt64, inclusive~ : Bool = ..) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[UInt64]
  ```
  > 
  >  Creates an iterator that iterates over a range of UInt64 with default step 1UL.
  > 
  >  #### Arguments
  > 
  >  * `start` - The starting value of the range (inclusive).
  >  * `end` - The ending value of the range (exclusive).
  >  * `inclusive` - Whether the ending value is inclusive (default false).
  > 
  >  #### Returns
  > 
  >  Returns an iterator that iterates over the range of UInt64 from `start` to `end - 1`.

## UInt16


#### mooncakes-io-method-mark-Methods
- #### to\_byte
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,3142:::fn <a href="moonbitlang/core/uint16#UInt16">UInt16</a>::to_byte(self : UInt16) -> Byte
  ```
  > 
  >  Converts a 16-bit unsigned integer to an 8-bit byte by truncating the higher
  > bits.
  > 
  >  Parameters:
  > 
  >  * `value` : The 16-bit unsigned integer to be converted.
  > 
  >  Returns a byte containing the least significant 8 bits of the input value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt16::to_byte" {
  >    let x = Int::to_uint16(258) // Binary: 0000_0001_0000_0010
  >    inspect!(x.to_byte(), content="b'\\x02'") // Only keeps 0000_0010
  >  }
  >  ```
- #### to\_int
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,3122:::fn <a href="moonbitlang/core/uint16#UInt16">UInt16</a>::to_int(self : UInt16) -> Int
  ```
  > 
  >  Converts an unsigned 16-bit integer to a 32-bit signed integer. The value is
  > zero-extended to fill the higher bits.
  > 
  >  Parameters:
  > 
  >  * `value` : The unsigned 16-bit integer to be converted.
  > 
  >  Returns a 32-bit signed integer. Since the input value is always non-negative
  > and less than 65536, the conversion never results in overflow.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt16::to_int" {
  >    let x = Int::to_uint16(42)
  >    inspect!(x.to_int(), content="42")
  >    let max = Int::to_uint16(65535) // maximum value of UInt16
  >    inspect!(max.to_int(), content="65535")
  >  }
  >  ```
- #### to\_int64
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,868:::fn <a href="moonbitlang/core/uint16#UInt16">UInt16</a>::to_int64(self : UInt16) -> Int64
  ```
  > 
  >  Converts an unsigned 16-bit integer to a signed 64-bit integer. The resulting
  > value will always be non-negative since the input is unsigned.
  > 
  >  Parameters:
  > 
  >  * `value` : The unsigned 16-bit integer to be converted.
  > 
  >  Returns a 64-bit signed integer representing the same numerical value as the
  > input.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt16::to_int64" {
  >    let x = Int::to_uint16(42)
  >    inspect!(x.to_int64(), content="42")
  >    let max = Int::to_uint16(65535) // maximum value of UInt16
  >    inspect!(max.to_int64(), content="65535")
  >  }
  >  ```
- #### to\_string
  ```moonbit
  :::source,moonbitlang/core/builtin/to_string.mbt,84:::fn <a href="moonbitlang/core/uint16#UInt16">UInt16</a>::to_string(self : UInt16, radix~ : Int = ..) -> String
  ```
  > 

## UInt


#### mooncakes-io-method-mark-Methods
- #### clz
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2455:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::clz(self : UInt) -> Int
  ```
  > 
  >  Counts the number of leading zero bits in an unsigned 32-bit integer,
  > starting from the most significant bit.
  > 
  >  Parameters:
  > 
  >  * `value` : The unsigned 32-bit integer whose leading zeros are to be
  >    counted.
  > 
  >  Returns the number of consecutive zeros starting from the most significant
  > bit. For a zero value, returns 32.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt::clz" {
  >    inspect!(0U.clz(), content="32")
  >    inspect!(1U.clz(), content="31")
  >    inspect!(0x80000000U.clz(), content="0")
  >  }
  >  ```
- #### ctz
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2479:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::ctz(self : UInt) -> Int
  ```
  > 
  >  Counts the number of trailing zero bits in an unsigned 32-bit integer,
  > starting from the least significant bit. For a zero input, returns 32.
  > 
  >  Parameters:
  > 
  >  * `self` : The unsigned 32-bit integer whose trailing zeros are to be
  >    counted.
  > 
  >  Returns the number of consecutive zeros at the least significant end of the
  > binary representation. Returns 32 if the input is zero.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt::ctz" {
  >    let x = 24U // Binary: ...011000
  >    inspect!(x.ctz(), content="3") // 3 trailing zeros
  >    let y = 0U
  >    inspect!(y.ctz(), content="32") // All bits are zero
  >  }
  >  ```
- #### land
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2199:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::land(self : UInt, other : UInt) -> UInt
  ```
  > 
  >  Performs a bitwise AND operation between two unsigned 32-bit integers. For
  > each bit position, the result is 1 if the bits at that position in both
  > operands are 1, and 0 otherwise.
  > 
  >  Parameters:
  > 
  >  * `self` : The first unsigned 32-bit integer operand.
  >  * `other` : The second unsigned 32-bit integer operand.
  > 
  >  Returns an unsigned 32-bit integer representing the result of the bitwise AND
  > operation.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt::land" {
  >    let a = 0xF0F0U // 1111_0000_1111_0000
  >    let b = 0xFF00U // 1111_1111_0000_0000
  >    inspect!(a & b, content="61440") // 1111_0000_0000_0000 = 61440
  >  }
  >  ```
- #### lnot
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2267:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::lnot(self : UInt) -> UInt
  ```
  > 
  >  Performs a bitwise NOT operation on an unsigned 32-bit integer. Flips all
  > bits in the number (changes each 0 to 1 and each 1 to 0).
  > 
  >  Parameters:
  > 
  >  * `self` : The unsigned 32-bit integer value on which to perform the bitwise
  >    NOT operation.
  > 
  >  Returns a new unsigned 32-bit integer where each bit is inverted from the
  > input value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt::lnot" {
  >    let x = 0xFF00U // Binary: 1111_1111_0000_0000
  >    inspect!(x.lnot(), content="4294902015") // Binary: ...0000_0000_1111_1111
  >  }
  >  ```
- #### lor
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2222:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::lor(self : UInt, other : UInt) -> UInt
  ```
  > 
  >  Performs a bitwise OR operation between two unsigned 32-bit integers. For
  > each bit position, the result is 1 if at least one of the corresponding bits
  > in either operand is 1.
  > 
  >  Parameters:
  > 
  >  * `self` : The first unsigned 32-bit integer operand.
  >  * `other` : The second unsigned 32-bit integer operand.
  > 
  >  Returns the result of the bitwise OR operation as an unsigned 32-bit integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt::lor" {
  >    let a = 0xF0F0U // Binary: 1111_0000_1111_0000
  >    let b = 0x0F0FU // Binary: 0000_1111_0000_1111
  >    inspect!(a | b, content="65535") // Binary: 1111_1111_1111_1111
  >  }
  >  ```
- #### lsl
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2298:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::lsl(self : UInt, shift : Int) -> UInt
  ```
  > 
  >  Performs a left shift operation on an unsigned 32-bit integer. Shifts each
  > bit in the number to the left by the specified number of positions, filling
  > the rightmost positions with zeros.
  > 
  >  Parameters:
  > 
  >  * `self` : The unsigned 32-bit integer to be shifted.
  >  * `shift` : The number of positions to shift the bits. Must be non-negative
  >    and less than 32. Values outside this range are wrapped to fit within it
  >    (i.e., `shift & 31`).
  > 
  >  Returns a new `UInt` value representing the result of shifting the bits left
  > by the specified number of positions. Each position shifted multiplies the
  > number by 2.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt::lsl" {
  >    let x = 1U
  >    inspect!(x << 3, content="8") // Using the recommended operator
  >    let y = 8U
  >    inspect!(y << 1, content="16") // Using the recommended operator
  >  }
  >  ```
  > 
- #### lsr
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2350:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::lsr(self : UInt, shift : Int) -> UInt
  ```
  > 
  >  Performs a logical right shift on an unsigned 32-bit integer. Each bit in the
  > input value is shifted right by the specified number of positions, with zeros
  > shifted in from the left. DEPRECATED: Use the `>>` operator instead.
  > 
  >  Parameters:
  > 
  >  * `self` : The unsigned 32-bit integer to be shifted.
  >  * `shift` : The number of positions to shift right. Must be non-negative.
  > 
  >  Returns a new `UInt` value representing the result of the logical right shift
  > operation.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt::lsr" {
  >    let x = 0xF0000000U
  >    inspect!(x >> 4, content="251658240") // Using the recommended operator
  >  }
  >  ```
  > 
- #### lxor
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2245:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::lxor(self : UInt, other : UInt) -> UInt
  ```
  > 
  >  Performs a bitwise XOR (exclusive OR) operation between two unsigned 32-bit
  > integers. Each bit in the result is set to 1 if the corresponding bits in the
  > operands are different, and 0 if they are the same.
  > 
  >  Parameters:
  > 
  >  * `self` : The first unsigned 32-bit integer operand.
  >  * `other` : The second unsigned 32-bit integer operand.
  > 
  >  Returns the result of the bitwise XOR operation.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt::lxor" {
  >    let a = 0xFF00U // Binary: 1111_1111_0000_0000
  >    let b = 0x0F0FU // Binary: 0000_1111_0000_1111
  >    inspect!(a ^ b, content="61455") // Binary: 1111_0000_0000_1111
  >  }
  >  ```
- #### op\_neq
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2148:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::op_neq(self : UInt, other : UInt) -> Bool
  ```
  > 
  >  Checks if two unsigned 32-bit integers are not equal.
  > 
  >  Parameters:
  > 
  >  * `self` : The first unsigned integer to compare.
  >  * `other` : The second unsigned integer to compare.
  > 
  >  Returns `true` if the two integers are not equal, `false` otherwise.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt::op_neq" {
  >    let a = 42U
  >    let b = 24U
  >    inspect!(a != b, content="true")
  >    inspect!(a != a, content="false")
  >  }
  >  ```
- #### popcnt
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2500:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::popcnt(self : UInt) -> Int
  ```
  > 
  >  Counts the number of 1 bits (population count) in the binary representation
  > of an unsigned 32-bit integer.
  > 
  >  Parameters:
  > 
  >  * `self` : The unsigned 32-bit integer whose bits are to be counted.
  > 
  >  Returns an integer representing the count of set bits (1s) in the binary
  > representation.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt::popcnt" {
  >    let x = 0xF0F0U // Binary: 1111 0000 1111 0000
  >    inspect!(x.popcnt(), content="8") // Has 8 bits set to 1
  >  }
  >  ```
- #### reinterpret\_as\_float
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2956:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::reinterpret_as_float(self : UInt) -> Float
  ```
  > 
  >  Reinterprets the bits of an unsigned 32-bit integer as a single-precision
  > floating-point number (IEEE 754). The bit pattern is preserved exactly, only
  > the type interpretation changes.
  > 
  >  Parameters:
  > 
  >  * `self` : The unsigned 32-bit integer whose bits are to be reinterpreted as
  >    a single-precision floating-point number.
  > 
  >  Returns a single-precision floating-point number (`Float`) whose bit pattern
  > is identical to the input integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt::reinterpret_as_float" {
  >    let n = 0x3F800000U // Bit pattern for 1.0f
  >    inspect!(n.reinterpret_as_float().to_double(), content="1")
  >  }
  >  ```
- #### reinterpret\_as\_int
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1937:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::reinterpret_as_int(self : UInt) -> Int
  ```
  > 
  >  reinterpret the unsigned int as signed int
  > For number within the range of 0..=2^31-1,
  > the value is the same. For number within the range of 2^31..=2^32-1,
  > the value is negative
- #### shl
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2324:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::shl(self : UInt, shift : Int) -> UInt
  ```
  > 
  >  Performs a left shift operation on an unsigned 32-bit integer. Shifts each
  > bit in the integer to the left by the specified number of positions, filling
  > the rightmost positions with zeros.
  > 
  >  Parameters:
  > 
  >  * `self` : The unsigned 32-bit integer to be shifted.
  >  * `shift` : The number of positions to shift left. Must be between 0 and 31
  >    inclusive. Values outside this range will be masked with `& 31`.
  > 
  >  Returns a new `UInt` value containing the result of the left shift operation.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt::shl" {
  >    let x = 1U
  >    inspect!(x << 3, content="8") // Binary: 1 -> 1000
  >  }
  >  ```
  > 
- #### shr
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2375:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::shr(self : UInt, shift : Int) -> UInt
  ```
  > 
  >  Performs a logical right shift operation on an unsigned 32-bit integer by a
  > specified number of positions. All bits shifted in from the left are zeros.
  > 
  >  Parameters:
  > 
  >  * `number` : The unsigned 32-bit integer to be shifted.
  >  * `shift` : The number of positions to shift right. Must be non-negative.
  > 
  >  Returns a new `UInt` value that represents the result of shifting all bits in
  > `number` to the right by `shift` positions.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt::shr" {
  >    let x = 0xFF000000U
  >    inspect!(x >> 8, content="16711680") // 0x00FF0000
  >  }
  >  ```
  > 
- #### to\_byte
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2549:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::to_byte(self : UInt) -> Byte
  ```
  > 
  >  Converts an unsigned 32-bit integer to a byte by taking its least significant
  > 8 bits. Any bits beyond the first 8 bits are truncated.
  > 
  >  Parameters:
  > 
  >  * `self` : The unsigned 32-bit integer to be converted. Only the least
  >    significant 8 bits will be used.
  > 
  >  Returns a byte containing the least significant 8 bits of the input integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt::to_byte" {
  >    let n = 258U // In binary: 100000010
  >    inspect!(n.to_byte(), content="b'\\x02'") // Only keeps 00000010
  >    let big = 4294967295U // Maximum value of UInt
  >    inspect!(big.to_byte(), content="b'\\xFF'") // Only keeps 11111111
  >  }
  >  ```
- #### to\_double
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2576:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::to_double(self : UInt) -> Double
  ```
  > 
  >  Converts an unsigned 32-bit integer to a double-precision floating-point
  > number. Since the range of unsigned 32-bit integers is smaller than what can
  > be precisely represented by a double-precision floating-point number, this
  > conversion is guaranteed to be exact.
  > 
  >  Parameters:
  > 
  >  * `value` : The unsigned 32-bit integer to be converted.
  > 
  >  Returns a double-precision floating-point number that exactly represents the
  > input value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Double::convert_uint" {
  >    let n = 42U
  >    inspect!(n.to_double(), content="42")
  >    let max = 4294967295U // maximum value of UInt
  >    inspect!(max.to_double(), content="4294967295")
  >  }
  >  ```
- #### to\_float
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,3030:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::to_float(self : UInt) -> Float
  ```
  > 
  >  Converts an unsigned 32-bit integer to a single-precision floating-point
  > number. Due to the limited precision of the 32-bit floating-point format,
  > values above 16777216 (2^24) may lose precision during conversion.
  > 
  >  Parameters:
  > 
  >  * `self` : The unsigned 32-bit integer to be converted.
  > 
  >  Returns a 32-bit floating-point number that represents the same numerical
  > value as the input unsigned integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt::to_float" {
  >    let n = 42U
  >    inspect!(n.to_float().to_double(), content="42")
  >    let big = 16777216U // 2^24
  >    inspect!(big.to_float().to_double(), content="16777216") // Last precisely representable integer
  >  }
  >  ```
- #### to\_int
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1965:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::to_int(self : UInt) -> Int
  ```
  > 
  >  Reinterprets an unsigned 32-bit integer as a signed 32-bit integer. For
  > values within the range of 0 to 2^31-1, the value remains the same. For
  > values within the range of 2^31 to 2^32-1, the value becomes negative due to
  > two's complement representation.
  > 
  >  Parameters:
  > 
  >  * `self` : The unsigned 32-bit integer to be reinterpreted.
  > 
  >  Returns a signed 32-bit integer that has the same bit pattern as the input
  > unsigned integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt::to_int" {
  >    let a = 42U
  >    inspect!(a.reinterpret_as_int(), content="42")
  >    let b = 4294967295U // maximum value of UInt (2^32 - 1)
  >    inspect!(b.reinterpret_as_int(), content="-1") // becomes -1 when reinterpreted as Int
  >  }
  >  ```
  > 
- #### to\_string
  ```moonbit
  :::source,moonbitlang/core/builtin/to_string.mbt,43:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::to_string(self : UInt, radix~ : Int = ..) -> String
  ```
  > 
- #### to\_uint64
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2524:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::to_uint64(self : UInt) -> UInt64
  ```
  > 
  >  Converts an unsigned 32-bit integer to an unsigned 64-bit integer by
  > zero-extending it. The resulting value preserves the original number's
  > magnitude while using 64 bits to represent it.
  > 
  >  Parameters:
  > 
  >  * `self` : The unsigned 32-bit integer (`UInt`) to be converted.
  > 
  >  Returns an unsigned 64-bit integer (`UInt64`) representing the same numerical
  > value as the input.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt::to_uint64" {
  >    let n = 42U
  >    inspect!(n.to_uint64(), content="42")
  >    let max = 4294967295U // Maximum value of UInt
  >    inspect!(max.to_uint64(), content="4294967295")
  >  }
  >  ```
- #### trunc\_double
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,841:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::trunc_double(val : Double) -> UInt
  ```
  > 
  >  Converts a double-precision floating-point number to an unsigned 32-bit
  > integer by truncating the decimal part. When the input is NaN or negative,
  > returns 0. When the input exceeds the maximum value of UInt (4294967295),
  > returns 4294967295.
  > 
  >  Parameters:
  > 
  >  * `value` : The double-precision floating-point number to be converted.
  > 
  >  Returns an unsigned 32-bit integer representing the truncated value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "UInt::trunc_double" {
  >    inspect!(UInt::trunc_double(42.75), content="42")
  >  }
  >  ```
- #### upto
  ```moonbit
  :::source,moonbitlang/core/builtin/iter_upto.mbt,60:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::upto(self : UInt, end : UInt, inclusive~ : Bool = ..) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[UInt]
  ```
  > 
  >  Creates an iterator that iterates over a range of UInt with default step 1U.
  > 
  >  #### Arguments
  > 
  >  * `start` - The starting value of the range (inclusive).
  >  * `end` - The ending value of the range (exclusive).
  >  * `inclusive` - Whether the ending value is inclusive (default false).
  > 
  >  #### Returns
  > 
  >  Returns an iterator that iterates over the range of UInt from `start` to `end - 1`.

## Int64


#### mooncakes-io-method-mark-Methods
- #### asr
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,369:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::asr(self : Int64, other : Int) -> Int64
  ```
  > 
  >  DEPRECATED: Use the infix operator `>>` instead.
  > 
  >  Performs an arithmetic right shift operation on a 64-bit integer. In an
  > arithmetic right shift, the leftmost bit (sign bit) is copied to fill in from
  > the left. This preserves the sign of the number.
  > 
  >  Parameters:
  > 
  >  * `self` : The 64-bit integer to be shifted.
  >  * `positions` : The number of positions to shift right. Must be non-negative.
  > 
  >  Returns a new 64-bit integer that is the result of shifting `self` right by
  > `positions` bits, with sign extension.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int64::asr" {
  >    let x = -240L // 0b1111_1111_0001_0000 in two's complement
  >    inspect!(x >> 4, content="-15") // 0b1111_1111_1111_0001, using recommended syntax
  >  }
  >  ```
  > 
- #### clz
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,491:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::clz(self : Int64) -> Int
  ```
  > 
  >  Counts the number of leading zero bits in a 64-bit signed integer, starting
  > from the most significant bit.
  > 
  >  Parameters:
  > 
  >  * `number` : The 64-bit signed integer whose leading zeros are to be counted.
  > 
  >  Returns the number of leading zero bits (0 to 64).
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int64::clz" {
  >    let a = 0x0000_0001_0000_0000L
  >    inspect!(a.clz(), content="31") // 31 leading zeros before the first 1 bit
  >    let b = 0L
  >    inspect!(b.clz(), content="64") // All bits are zero
  >  }
  >  ```
- #### ctz
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,469:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::ctz(self : Int64) -> Int
  ```
  > 
  >  Returns the number of trailing zero bits in a 64-bit integer. For zero input,
  > returns 64.
  > 
  >  Parameters:
  > 
  >  * `value` : The 64-bit integer to count trailing zeros in.
  > 
  >  Returns the number of trailing zero bits (0 to 64).
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int64::ctz" {
  >    inspect!(0x8000000000000000L.ctz(), content="63") // Binary: 1000...0000
  >    inspect!(0x0000000000000001L.ctz(), content="0") // Binary: ...0001
  >    inspect!(0L.ctz(), content="64") // All zeros
  >  }
  >  ```
- #### lnot
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,193:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::lnot(self : Int64) -> Int64
  ```
  > 
  >  Performs a bitwise NOT operation on a 64-bit integer. Each bit in the input
  > value is flipped (0 becomes 1 and 1 becomes 0).
  > 
  >  Parameters:
  > 
  >  * `self` : The 64-bit integer on which to perform the bitwise NOT operation.
  > 
  >  Returns a new 64-bit integer where each bit is the inverse of the
  > corresponding bit in the input value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int64::lnot" {
  >    let a = -1L // All bits are 1
  >    let b = 0L // All bits are 0
  >    inspect!(a.lnot(), content="0")
  >    inspect!(b.lnot(), content="-1")
  >  }
  >  ```
- #### lsl
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,289:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::lsl(self : Int64, other : Int) -> Int64
  ```
  > 
  >  Performs a left shift operation on a 64-bit signed integer. Shifts each bit
  > in the integer to the left by the specified number of positions, filling the
  > vacated bit positions with zeros.
  > 
  >  Parameters:
  > 
  >  * `self` : The 64-bit signed integer to be shifted.
  >  * `shift` : The number of positions to shift. Must be non-negative and less
  >    than 64.
  > 
  >  Returns a new 64-bit integer with bits shifted left by the specified number
  > of positions.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int64::lsl" {
  >    let x = 1L
  >    inspect!(x << 2, content="4") // Binary: 1 -> 100
  >  }
  >  ```
  > 
- #### lsr
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,341:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::lsr(self : Int64, other : Int) -> Int64
  ```
  > 
  >  **DEPRECATED:** Use `UInt64` type and infix operator `>>` instead.
  > 
  >  Performs a logical right shift on a 64-bit integer value. In a logical right
  > shift, zeros are shifted in from the left, regardless of the sign bit.
  > 
  >  Parameters:
  > 
  >  * `value` : The 64-bit integer value to be shifted.
  >  * `shift` : The number of positions to shift right. Must be non-negative.
  > 
  >  Returns a new 64-bit integer value that is the result of shifting the bits of
  > `value` right by `shift` positions.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int64::lsr" {
  >    let x = (-4L).reinterpret_as_uint64() // Convert to UInt64 first
  >    inspect!(x >> 1, content="9223372036854775806") // Using the recommended operator
  >  }
  >  ```
  > 
- #### popcnt
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,519:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::popcnt(self : Int64) -> Int
  ```
  > 
  >  Returns the number of 1 bits ('population count') in the 64-bit integer's
  > binary representation.
  > 
  >  Parameters:
  > 
  >  * `value` : The 64-bit integer whose bits are to be counted.
  > 
  >  Returns an integer representing the number of set bits (1s) in the binary
  > representation of the input.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int64::popcnt" {
  >    let x = 0x7000_0001_1F00_100FL // 0111000000000000000000000001000111110000000100001111
  >    inspect!(x.popcnt(), content="14")
  >  }
  >  ```
  > 
  >  ```moonbit
  >  test "Int64::popcnt/edge_cases" {
  >    inspect!((-1L).popcnt(), content="64") // All bits set
  >    inspect!(0L.popcnt(), content="0") // No bits set
  >  }
  >  ```
- #### reinterpret\_as\_double
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,654:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::reinterpret_as_double(self : Int64) -> Double
  ```
  > 
  >  Reinterprets the bits of a 64-bit signed integer as a double-precision
  > floating-point number (IEEE 754). The bit pattern is preserved exactly, only
  > the type interpretation changes.
  > 
  >  Parameters:
  > 
  >  * `value` : The 64-bit signed integer whose bits are to be reinterpreted as a
  >    double-precision floating-point number.
  > 
  >  Returns a double-precision floating-point number whose bit pattern is
  > identical to the input integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int64::reinterpret_as_double" {
  >    let n = 4607182418800017408L // Bit pattern for 1.0
  >    inspect!(n.reinterpret_as_double(), content="1")
  >  }
  >  ```
- #### reinterpret\_as\_uint64
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1044:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::reinterpret_as_uint64(self : Int64) -> UInt64
  ```
  > 
  >  Reinterprets a 64-bit signed integer as an unsigned 64-bit integer without
  > changing its bit pattern. The reinterpretation follows the standard two's
  > complement representation rules.
  > 
  >  Parameters:
  > 
  >  * `self` : The 64-bit signed integer to be reinterpreted.
  > 
  >  Returns a 64-bit unsigned integer that has the same bit pattern as the input.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int64::reinterpret_as_uint64" {
  >    let neg = -1L
  >    inspect!(neg.reinterpret_as_uint64(), content="18446744073709551615") // All bits set to 1
  >    let pos = 42L
  >    inspect!(pos.reinterpret_as_uint64(), content="42") // Positive numbers remain unchanged
  >  }
  >  ```
- #### shl
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,314:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::shl(self : Int64, other : Int) -> Int64
  ```
  > 
  >  Performs a left shift operation on a 64-bit integer value. Shifts the bits of
  > the integer to the left by a specified number of positions, filling the
  > rightmost positions with zeros.
  > 
  >  Parameters:
  > 
  >  * `self` : The 64-bit integer value to be shifted.
  >  * `shift` : The number of positions to shift the bits to the left.
  > 
  >  Returns a new 64-bit integer value after performing the left shift operation.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int64::shl" {
  >    let x = 1L
  >    inspect!(x << 3, content="8") // Equivalent to x << 3
  >  }
  >  ```
  > 
- #### shr
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,395:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::shr(self : Int64, other : Int) -> Int64
  ```
  > 
  >  Performs an arithmetic right shift operation on a 64-bit integer value,
  > shifting the bits to the right by the specified number of positions. The sign
  > bit is copied to fill the leftmost positions.
  > 
  >  Parameters:
  > 
  >  * `self` : The 64-bit integer value to be shifted.
  >  * `shift` : The number of bit positions to shift right. Must be non-negative.
  > 
  >  Returns a new `Int64` value representing the result of the arithmetic right
  > shift operation.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int64::shr" {
  >    let n = -1024L
  >    inspect!(n >> 3, content="-128") // Preserves sign bit
  >  }
  >  ```
  > 
- #### to\_byte
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,701:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::to_byte(self : Int64) -> Byte
  ```
  > 
  >  Converts a 64-bit signed integer to a byte by taking its least significant 8
  > bits. Any bits beyond the first 8 bits are truncated.
  > 
  >  Parameters:
  > 
  >  * `self` : The 64-bit signed integer to be converted. Only the least
  >    significant 8 bits will be used.
  > 
  >  Returns a byte containing the least significant 8 bits of the input integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int64::to_byte" {
  >    let n = 258L // In binary: 100000010
  >    inspect!(n.to_byte(), content="b'\\x02'") // Only keeps 00000010
  >    let neg = -1L // In binary: all 1's
  >    inspect!(neg.to_byte(), content="b'\\xFF'") // Only keeps 11111111
  >  }
  >  ```
- #### to\_double
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,631:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::to_double(self : Int64) -> Double
  ```
  > 
  >  Converts a 64-bit signed integer to a double-precision floating-point number.
  > 
  >  Parameters:
  > 
  >  * `self` : The 64-bit signed integer to be converted.
  > 
  >  Returns a double-precision floating-point number that represents the same
  > value as the input integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int64::to_double" {
  >    let big = 9223372036854775807L // max value of Int64
  >    inspect!(big.to_double(), content="9223372036854776000")
  >    let neg = -42L
  >    inspect!(neg.to_double(), content="-42")
  >  }
  >  ```
- #### to\_float
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,794:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::to_float(self : Int64) -> Float
  ```
  > 
  >  Converts a 64-bit integer to a 32-bit floating-point number. The conversion
  > may result in loss of precision due to the limited precision of the 32-bit
  > floating-point format.
  > 
  >  Parameters:
  > 
  >  * `self` : The 64-bit integer value to be converted.
  > 
  >  Returns a 32-bit floating-point number that represents the input integer
  > value. Note that for values outside the range of representable 32-bit
  > floating-point numbers, the result will be rounded to the nearest
  > representable value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int64::to_float" {
  >    let n = 42L
  >    let f = n.to_float()
  >    // Convert to double for comparison since Float doesn't implement Show
  >    inspect!(f.to_double(), content="42")
  >  }
  >  ```
- #### to\_int
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,609:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::to_int(self : Int64) -> Int
  ```
  > 
  >  Converts a 64-bit signed integer to a 32-bit signed integer by truncating
  > higher bits.
  > 
  >  Parameters:
  > 
  >  * `value` : The 64-bit signed integer (`Int64`) to be converted.
  > 
  >  Returns a 32-bit signed integer (`Int`). Note that values outside the range
  > of 32-bit integers will be truncated, potentially leading to loss of
  > information.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int64::to_int" {
  >    let small = 42L
  >    let big = 2147483648L // 2^31
  >    inspect!(small.to_int(), content="42")
  >    inspect!(big.to_int(), content="-2147483648") // Truncated to Int.min_value
  >  }
  >  ```
- #### to\_int16
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,724:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::to_int16(self : Int64) -> Int16
  ```
  > 
  >  Converts a 64-bit signed integer to a 16-bit signed integer by truncating the
  > value to fit within the 16-bit range (-32768 to 32767).
  > 
  >  Parameters:
  > 
  >  * `value` : The 64-bit signed integer to be converted.
  > 
  >  Returns a 16-bit signed integer representing the lower 16 bits of the input
  > value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int64::to_int16" {
  >    let big = 100000L
  >    inspect!(big.to_int16(), content="-31072") // 100000 doesn't fit in Int16, gets truncated
  >    let small = 42L
  >    inspect!(small.to_int16(), content="42") // 42 fits in Int16, remains unchanged
  >  }
  >  ```
- #### to\_string
  ```moonbit
  :::source,moonbitlang/core/builtin/to_string.mbt,19:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::to_string(self : Int64, radix~ : Int = ..) -> String
  ```
  > 
- #### to\_uint16
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,746:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::to_uint16(self : Int64) -> UInt16
  ```
  > 
  >  Converts a 64-bit signed integer to a 16-bit unsigned integer by truncating
  > the value to fit within the range of UInt16 (0 to 65535).
  > 
  >  Parameters:
  > 
  >  * `value` : The 64-bit signed integer to be converted to UInt16.
  > 
  >  Returns a 16-bit unsigned integer representing the lower 16 bits of the input
  > value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int64::to_uint16" {
  >    inspect!(42L.to_uint16(), content="42")
  >    inspect!((-1L).to_uint16(), content="65535") // Wraps around to maximum UInt16 value
  >    inspect!(70000L.to_uint16(), content="4464") // Value is truncated
  >  }
  >  ```
- #### to\_uint64
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,1021:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::to_uint64(self : Int64) -> UInt64
  ```
  > 
  >  Reinterprets a 64-bit signed integer as an unsigned 64-bit integer without
  > changing its bits. When the value is non-negative, i.e., within the range
  > \[0, 2^63-1\], the value remains the same. When the value is negative, it
  > becomes a large number in the range \[2^63, 2^64-1\].
  > 
  >  Parameters:
  > 
  >  * `value` : The 64-bit signed integer (`Int64`) to be reinterpreted.
  > 
  >  Returns an unsigned 64-bit integer (`UInt64`) containing the same bit pattern
  > as the input.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int64::to_uint64" {
  >    let pos = 42L
  >    let neg = -1L
  >    inspect!(pos.reinterpret_as_uint64(), content="42")
  >    inspect!(neg.reinterpret_as_uint64(), content="18446744073709551615") // 2^64 - 1
  >  }
  >  ```
  > 
- #### until
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,258:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::until(self : Int64, end : Int64, step~ : Int64 = .., inclusive~ : Bool = ..) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[Int64]
  ```
  > 
  >  Creates an iterator that iterates over a range of Int64 with default step 1L.
  > To grow the range downward, set the `step` parameter to a negative value.
  > 
  >  #### Arguments
  > 
  >  * `start` - The starting value of the range (inclusive).
  >  * `end` - The ending value of the range (exclusive by default).
  >  * `step` - The step size of the range (default 1L).
  >  * `inclusive` - Whether the ending value is inclusive (default false).
  > 
  >  #### Returns
  > 
  >  Returns an iterator that iterates over the range of Int64 from `start` to `end - 1`.
- #### upto
  ```moonbit
  :::source,moonbitlang/core/builtin/iter_upto.mbt,130:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::upto(self : Int64, end : Int64, inclusive~ : Bool = ..) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[Int64]
  ```
  > 
  >  Creates an iterator that iterates over a range of Int64 with default step 1L.
  > 
  >  #### Arguments
  > 
  >  * `start` - The starting value of the range (inclusive).
  >  * `end` - The ending value of the range (exclusive).
  >  * `inclusive` - Whether the ending value is inclusive (default false).
  > 
  >  #### Returns
  > 
  >  Returns an iterator that iterates over the range of Int64 from `start` to `end - 1`.

## Int16


#### mooncakes-io-method-mark-Methods
- #### to\_byte
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,3073:::fn <a href="moonbitlang/core/int16#Int16">Int16</a>::to_byte(self : Int16) -> Byte
  ```
  > 
  >  Converts a 16-bit signed integer to a byte by truncating its value to fit
  > within the byte range (0 to 255). Only the least significant 8 bits of the
  > integer are retained.
  > 
  >  Parameters:
  > 
  >  * `value` : The 16-bit signed integer to be converted to a byte.
  > 
  >  Returns a byte containing the least significant 8 bits of the input value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int16::to_byte" {
  >    let x = Int::to_int16(258) // In binary: 0000_0001_0000_0010
  >    inspect!(x.to_byte(), content="b'\\x02'") // Only keeps 0000_0010
  >  }
  >  ```
- #### to\_int
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,3052:::fn <a href="moonbitlang/core/int16#Int16">Int16</a>::to_int(self : Int16) -> Int
  ```
  > 
  >  Converts a 16-bit signed integer to a 32-bit signed integer by sign
  > extension.
  > 
  >  Parameters:
  > 
  >  * `value` : The 16-bit signed integer to be converted.
  > 
  >  Returns a 32-bit signed integer that has the same value as the input.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int16::to_int" {
  >    let n = Int::to_int16(42)
  >    inspect!(n.to_int(), content="42")
  >    let neg = Int::to_int16(-42)
  >    inspect!(neg.to_int(), content="-42")
  >  }
  >  ```
- #### to\_int64
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,845:::fn <a href="moonbitlang/core/int16#Int16">Int16</a>::to_int64(self : Int16) -> Int64
  ```
  > 
- #### to\_string
  ```moonbit
  :::source,moonbitlang/core/builtin/to_string.mbt,74:::fn <a href="moonbitlang/core/int16#Int16">Int16</a>::to_string(self : Int16, radix~ : Int = ..) -> String
  ```
  > 

## Int


#### mooncakes-io-method-mark-Methods
- #### asr
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,624:::fn <a href="moonbitlang/core/int#Int">Int</a>::asr(self : Int, other : Int) -> Int
  ```
  > 
  >  Performs an arithmetic right shift operation on a 32-bit integer value,
  > preserving the sign bit by replicating it into the positions vacated by the
  > shift. This is a deprecated function; use the infix operator `>>` instead.
  > 
  >  Parameters:
  > 
  >  * `self` : The integer value to be shifted.
  >  * `shift` : The number of positions to shift right. Must be non-negative.
  > 
  >  Returns a new integer value that is the result of arithmetically shifting
  > `self` right by `shift` positions.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::asr" {
  >    let x = -16
  >    inspect!(x >> 2, content="-4") // Right shift preserves sign bit
  >  }
  >  ```
  > 
- #### clz
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,679:::fn <a href="moonbitlang/core/int#Int">Int</a>::clz(self : Int) -> Int
  ```
  > 
- #### ctz
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,676:::fn <a href="moonbitlang/core/int#Int">Int</a>::ctz(self : Int) -> Int
  ```
  > 
  >  Counts the number of consecutive zero bits at the least significant end of
  > the integer's binary representation.
  > 
  >  Parameters:
  > 
  >  * `self` : The integer value whose trailing zeros are to be counted.
  > 
  >  Returns the number of trailing zero bits (0 to 32). For example, returns 0 if
  > the value is odd (least significant bit is 1), returns 32 if the value is 0
  > (all bits are zeros).
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::ctz" {
  >    let x = 0
  >    inspect!(x.ctz(), content="32") // All bits are zero
  >    let y = 1
  >    inspect!(y.ctz(), content="0") // No trailing zeros
  >    let z = 16
  >    inspect!(z.ctz(), content="4") // Binary: ...10000
  >  }
  >  ```
- #### is\_neg
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,775:::fn <a href="moonbitlang/core/int#Int">Int</a>::is_neg(self : Int) -> Bool
  ```
  > 
  >  Tests whether an integer is negative.
  > 
  >  Parameters:
  > 
  >  * `self` : The integer to test.
  > 
  >  Returns `true` if the integer is negative, `false` otherwise.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::is_neg" {
  >    let neg = -42
  >    let zero = 0
  >    let pos = 42
  >    inspect!(neg.is_neg(), content="true")
  >    inspect!(zero.is_neg(), content="false")
  >    inspect!(pos.is_neg(), content="false")
  >  }
  >  ```
- #### is\_non\_neg
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,781:::fn <a href="moonbitlang/core/int#Int">Int</a>::is_non_neg(self : Int) -> Bool
  ```
  > 
- #### is\_non\_pos
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,778:::fn <a href="moonbitlang/core/int#Int">Int</a>::is_non_pos(self : Int) -> Bool
  ```
  > 
- #### is\_pos
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,752:::fn <a href="moonbitlang/core/int#Int">Int</a>::is_pos(self : Int) -> Bool
  ```
  > 
- #### land
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,411:::fn <a href="moonbitlang/core/int#Int">Int</a>::land(self : Int, other : Int) -> Int
  ```
  > 
  >  Performs a bitwise AND operation between two 32-bit integers. Each bit in the
  > result is set to 1 only if the corresponding bits in both operands are 1.
  > 
  >  Parameters:
  > 
  >  * `self` : The first 32-bit integer operand.
  >  * `other` : The second 32-bit integer operand.
  > 
  >  Returns the result of the bitwise AND operation. The resulting value has a
  > bit set to 1 at each position where both input integers have a bit set to 1.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::land" {
  >    let x = 0xF0 // 11110000
  >    let y = 0xAA // 10101010
  >    inspect!(x & y, content="160") // 10100000 = 160
  >  }
  >  ```
- #### lnot
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,388:::fn <a href="moonbitlang/core/int#Int">Int</a>::lnot(self : Int) -> Int
  ```
  > 
  >  Performs a bitwise NOT operation on a 32-bit integer. Flips each bit in the
  > integer's binary representation (0 becomes 1 and 1 becomes 0).
  > 
  >  Parameters:
  > 
  >  * `value` : The 32-bit integer on which to perform the bitwise NOT operation.
  > 
  >  Returns a new integer with all bits flipped from the input value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::lnot" {
  >    let a = -1 // All bits are 1
  >    let b = 0 // All bits are 0
  >    inspect!(a.lnot(), content="0")
  >    inspect!(b.lnot(), content="-1")
  >  }
  >  ```
- #### lor
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,435:::fn <a href="moonbitlang/core/int#Int">Int</a>::lor(self : Int, other : Int) -> Int
  ```
  > 
  >  Performs a bitwise OR operation between two 32-bit integers. For each bit
  > position, the result is 1 if at least one of the corresponding bits in either
  > operand is 1.
  > 
  >  Parameters:
  > 
  >  * `self` : The first integer operand.
  >  * `other` : The second integer operand.
  > 
  >  Returns a new integer where each bit is set to 1 if at least one of the
  > corresponding bits in either operand is 1, and 0 otherwise.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::lor" {
  >    let x = 0xF0F0 // 1111_0000_1111_0000
  >    let y = 0x0F0F // 0000_1111_0000_1111
  >    inspect!(x | y, content="65535") // 1111_1111_1111_1111 = 65535
  >  }
  >  ```
- #### lsl
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,540:::fn <a href="moonbitlang/core/int#Int">Int</a>::lsl(self : Int, other : Int) -> Int
  ```
  > 
  >  Performs a left shift operation on a 32-bit integer. Shifts each bit in the
  > integer to the left by the specified number of positions, filling the vacated
  > bit positions with zeros.
  > 
  >  Parameters:
  > 
  >  * `self` : The integer value to be shifted.
  >  * `shift` : The number of positions to shift the bits to the left.
  > 
  >  Returns an integer containing the result of shifting `self` left by `shift`
  > positions.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::lsl" {
  >    let x = 1
  >    inspect!(x << 3, content="8") // Binary: 1 -> 1000
  >    let y = 42
  >    inspect!(y << 2, content="168") // Binary: 101010 -> 10101000
  >  }
  >  ```
  > 
- #### lsr
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,596:::fn <a href="moonbitlang/core/int#Int">Int</a>::lsr(self : Int, other : Int) -> Int
  ```
  > 
  >  Performs a logical right shift operation on a signed 32-bit integer. In a
  > logical right shift, zeros are shifted in from the left, regardless of the
  > sign bit. This function is DEPRECATED and users should use `UInt` type with
  > the infix operator `>>` instead.
  > 
  >  Parameters:
  > 
  >  * `self` : The signed 32-bit integer value to be shifted.
  >  * `shift` : The number of positions to shift right. Must be non-negative.
  > 
  >  Returns a signed 32-bit integer containing the same bits as if the input were
  > treated as an unsigned integer and shifted right logically.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::lsr" {
  >    let x = -4 // Binary: 11111...11100
  >    let unsigned = x.reinterpret_as_uint() // Convert to UInt first
  >    inspect!(unsigned >> 1, content="2147483646") // Using the recommended operator
  >  }
  >  ```
  > 
- #### lxor
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,458:::fn <a href="moonbitlang/core/int#Int">Int</a>::lxor(self : Int, other : Int) -> Int
  ```
  > 
  >  Performs a bitwise XOR operation between two integers.
  > 
  >  Parameters:
  > 
  >  * `self` : The first integer operand.
  >  * `other` : The second integer operand.
  > 
  >  Returns a new integer where each bit is set to 1 if the corresponding bits in
  > the operands are different, and 0 if they are the same.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::lxor" {
  >    let x = 0xF0F0 // 1111_0000_1111_0000
  >    let y = 0x0F0F // 0000_1111_0000_1111
  >    inspect!(x ^ y, content="65535") // 1111_1111_1111_1111
  >    inspect!(x ^ x, content="0") // XOR with self gives 0
  >  }
  >  ```
- #### popcnt
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,702:::fn <a href="moonbitlang/core/int#Int">Int</a>::popcnt(self : Int) -> Int
  ```
  > 
  >  Counts the number of set bits (1s) in the binary representation of a 32-bit
  > integer.
  > 
  >  Parameters:
  > 
  >  * `self` : The 32-bit integer whose bits are to be counted.
  > 
  >  Returns the number of bits set to 1 in the binary representation of the input
  > integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::popcnt" {
  >    let x = 0b1011 // Binary: 1011 (3 bits set)
  >    inspect!(x.popcnt(), content="3")
  >    let y = -1 // All bits set in two's complement
  >    inspect!(y.popcnt(), content="32")
  >  }
  >  ```
- #### reinterpret\_as\_float
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2933:::fn <a href="moonbitlang/core/int#Int">Int</a>::reinterpret_as_float(self : Int) -> Float
  ```
  > 
  >  Reinterprets the bits of a 32-bit integer as a single-precision
  > floating-point number according to IEEE 754 standard. The bit pattern of the
  > input is preserved, only the type interpretation changes.
  > 
  >  Parameters:
  > 
  >  * `self` : The 32-bit integer whose bits are to be reinterpreted as a
  >    single-precision floating-point number.
  > 
  >  Returns a 32-bit floating-point number (`Float`) that has the same bit
  > pattern as the input integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::reinterpret_as_float" {
  >    // 0x3F800000 represents 1.0 in IEEE 754 single-precision format
  >    let n = 1065353216 // 0x3F800000
  >    inspect!(n.reinterpret_as_float().to_double(), content="1")
  >  }
  >  ```
- #### reinterpret\_as\_uint
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,848:::fn <a href="moonbitlang/core/int#Int">Int</a>::reinterpret_as_uint(self : Int) -> UInt
  ```
  > 
  >  reinterpret the signed int as unsigned int, when the value is
  > non-negative, i.e, 0..=2^31-1, the value is the same. When the
  > value is negative, it turns into a large number,
  > for example, -1 turns into 2^32-1
- #### shl
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,568:::fn <a href="moonbitlang/core/int#Int">Int</a>::shl(self : Int, other : Int) -> Int
  ```
  > 
  >  Performs a left shift operation on a 32-bit integer. Shifts the bits of the
  > first operand to the left by the specified number of positions. The rightmost
  > positions are filled with zeros.
  > 
  >  Parameters:
  > 
  >  * `value` : The integer value to be shifted.
  >  * `shift` : The number of positions to shift left. Must be non-negative and
  >    less than 32.
  > 
  >  Returns a new integer value after performing the left shift operation. The
  > value is equal to multiplying the input by 2 raised to the power of the shift
  > count.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::shl" {
  >    let x = 1
  >    inspect!(x << 3, content="8") // Equivalent to x << 3
  >  }
  >  ```
  > 
- #### shr
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,650:::fn <a href="moonbitlang/core/int#Int">Int</a>::shr(self : Int, other : Int) -> Int
  ```
  > 
  >  Performs an arithmetic right shift operation on a 32-bit integer by the
  > specified number of positions. The operation preserves the sign bit,
  > replicating it into the positions vacated by the shift.
  > 
  >  Parameters:
  > 
  >  * `self` : The integer value to be shifted.
  >  * `shift` : The number of positions to shift right.
  > 
  >  Returns a new integer representing the result of shifting `self` right by
  > `shift` positions.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::shr" {
  >    let n = -1024
  >    inspect!(n >> 3, content="-128") // Preserves sign bit during right shift
  >  }
  >  ```
  > 
- #### to\_byte
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1472:::fn <a href="moonbitlang/core/int#Int">Int</a>::to_byte(self : Int) -> Byte
  ```
  > 
  >  Converts a 32-bit signed integer to a byte by taking its least significant 8
  > bits. Any bits beyond the first 8 bits are truncated.
  > 
  >  Parameters:
  > 
  >  * `value` : The 32-bit signed integer to be converted. Only the least
  >    significant 8 bits will be used.
  > 
  >  Returns a byte containing the least significant 8 bits of the input integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::to_byte" {
  >    let n = 258 // In binary: 100000010
  >    inspect!(n.to_byte(), content="b'\\x02'") // Only keeps 00000010
  >    let neg = -1 // In binary: all 1's
  >    inspect!(neg.to_byte(), content="b'\\xFF'") // Only keeps 11111111
  >  }
  >  ```
- #### to\_double
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,820:::fn <a href="moonbitlang/core/int#Int">Int</a>::to_double(self : Int) -> Double
  ```
  > 
  >  Converts a 32-bit integer to a double-precision floating-point number. The
  > conversion preserves the exact value since all integers in the range of `Int`
  > can be represented exactly as `Double` values.
  > 
  >  Parameters:
  > 
  >  * `self` : The 32-bit integer to be converted.
  > 
  >  Returns a double-precision floating-point number that represents the same
  > numerical value as the input integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::to_double" {
  >    let n = 42
  >    inspect!(n.to_double(), content="42")
  >    let neg = -42
  >    inspect!(neg.to_double(), content="-42")
  >  }
  >  ```
- #### to\_float
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2909:::fn <a href="moonbitlang/core/int#Int">Int</a>::to_float(self : Int) -> Float
  ```
  > 
  >  Converts an integer to a 32-bit floating-point number. The conversion is
  > exact for small integers, but may lose precision for large integers due to
  > the limited precision of the floating-point format.
  > 
  >  Parameters:
  > 
  >  * `number` : The integer value to be converted to a floating-point number.
  > 
  >  Returns a 32-bit floating-point number representing the same value as the
  > input integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::to_float" {
  >    let n = 42
  >    let f = n.to_float()
  >    // Convert back to double for comparison since Float doesn't implement Show
  >    inspect!(f.to_double(), content="42")
  >  }
  >  ```
- #### to\_int16
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,3076:::fn <a href="moonbitlang/core/int#Int">Int</a>::to_int16(self : Int) -> Int16
  ```
  > 
- #### to\_int64
  ```moonbit
  :::source,moonbitlang/core/builtin/int64_nonjs.mbt,842:::fn <a href="moonbitlang/core/int#Int">Int</a>::to_int64(self : Int) -> Int64
  ```
  > 
  >  Converts a 32-bit signed integer to a 64-bit signed integer. All 32-bit
  > integers can be represented exactly in 64-bit integer format, so the
  > conversion is lossless.
  > 
  >  Parameters:
  > 
  >  * `self` : The 32-bit signed integer to be converted.
  > 
  >  Returns a 64-bit signed integer that represents the same numerical value as
  > the input.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::to_int64" {
  >    let n = 42
  >    inspect!(n.to_int64(), content="42")
  >    let neg = -42
  >    inspect!(neg.to_int64(), content="-42")
  >  }
  >  ```
- #### to\_string
  ```moonbit
  :::source,moonbitlang/core/builtin/to_string.mbt,31:::fn <a href="moonbitlang/core/int#Int">Int</a>::to_string(self : Int, radix~ : Int = ..) -> String
  ```
  > 
- #### to\_uint
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,876:::fn <a href="moonbitlang/core/int#Int">Int</a>::to_uint(self : Int) -> UInt
  ```
  > 
  >  Reinterprets a signed 32-bit integer as an unsigned 32-bit integer. For
  > numbers within the range \[0, 2^31-1\], the value remains the same. For
  > negative numbers, they are reinterpreted as large positive numbers in the
  > range \[2^31, 2^32-1\].
  > 
  >  Parameters:
  > 
  >  * `value` : The signed 32-bit integer to be reinterpreted.
  > 
  >  Returns an unsigned 32-bit integer that has the same bit pattern as the
  > input.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::to_uint" {
  >    let pos = 42
  >    let neg = -1
  >    inspect!(pos.reinterpret_as_uint(), content="42")
  >    inspect!(neg.reinterpret_as_uint(), content="4294967295") // 2^32 - 1
  >  }
  >  ```
  > 
- #### to\_uint16
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,3168:::fn <a href="moonbitlang/core/int#Int">Int</a>::to_uint16(self : Int) -> UInt16
  ```
  > 
  >  Converts a 32-bit signed integer to a 16-bit unsigned integer by truncating
  > its value to fit within the range of 0 to 65535.
  > 
  >  Parameters:
  > 
  >  * `integer` : The 32-bit signed integer to be converted. Values outside the
  >    range of UInt16 will be truncated to fit.
  > 
  >  Returns a 16-bit unsigned integer containing the lower 16 bits of the input
  > value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::to_uint16" {
  >    let n = 42
  >    inspect!(n.to_uint16(), content="42")
  >    let neg = -1
  >    inspect!(neg.to_uint16(), content="65535") // -1 becomes max value of UInt16
  >    let large = 65536
  >    inspect!(large.to_uint16(), content="0") // Values wrap around
  >  }
  >  ```
- #### to\_uint64
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,901:::fn <a href="moonbitlang/core/int#Int">Int</a>::to_uint64(self : Int) -> UInt64
  ```
  > 
  >  Converts a 32-bit signed integer to an unsigned 64-bit integer by first
  > converting it to a signed 64-bit integer and then reinterpreting the bits as
  > an unsigned value.
  > 
  >  Parameters:
  > 
  >  * `value` : The 32-bit signed integer to be converted.
  > 
  >  Returns an unsigned 64-bit integer representing the same bit pattern as the
  > input value when extended to 64 bits.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int::to_uint64" {
  >    let pos = 42
  >    inspect!(pos.to_uint64(), content="42")
  >    let neg = -1
  >    inspect!(neg.to_uint64(), content="18446744073709551615") // 2^64 - 1
  >  }
  >  ```
- #### until
  ```moonbit
  :::source,moonbitlang/core/builtin/iter.mbt,215:::fn <a href="moonbitlang/core/int#Int">Int</a>::until(self : Int, end : Int, step~ : Int = .., inclusive~ : Bool = ..) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[Int]
  ```
  > 
  >  Creates an iterator that iterates over a range of Int with default step 1.
  > To grow the range downward, set the `step` parameter to a negative value.
  > 
  >  #### Arguments
  > 
  >  * `start` - The starting value of the range (inclusive).
  >  * `end` - The ending value of the range (exclusive by default).
  >  * `step` - The step size of the range (default 1).
  >  * `inclusive` - Whether the ending value is inclusive (default false).
  > 
  >  #### Returns
  > 
  >  Returns an iterator that iterates over the range of Int from `start` to `end - 1`.
- #### upto
  ```moonbit
  :::source,moonbitlang/core/builtin/iter_upto.mbt,29:::fn <a href="moonbitlang/core/int#Int">Int</a>::upto(self : Int, end : Int, inclusive~ : Bool = ..) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[Int]
  ```
  > 
  >  Creates an iterator that iterates over a range of Int with default step 1.
  > 
  >  #### Arguments
  > 
  >  * `start` - The starting value of the range (inclusive).
  >  * `end` - The ending value of the range (exclusive).
  >  * `inclusive` - Whether the ending value is inclusive (default false).
  > 
  >  #### Returns
  > 
  >  Returns an iterator that iterates over the range of Int from `start` to `end - 1`.

## Char


#### mooncakes-io-method-mark-Methods
- #### from\_int
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1236:::fn <a href="moonbitlang/core/char#Char">Char</a>::from_int(val : Int) -> Char
  ```
  > 
  > 
- #### op\_sub
  ```moonbit
  :::source,moonbitlang/core/builtin/char.mbt,37:::fn <a href="moonbitlang/core/char#Char">Char</a>::op_sub(self : Char, that : Char) -> Int
  ```
  > 
  >  Calculates the difference between the Unicode code points of two characters.
  > 
  >  Parameters:
  > 
  >  * `self` : The first character whose code point serves as the minuend.
  >  * `other` : The second character whose code point serves as the subtrahend.
  > 
  >  Returns an integer representing the difference between the Unicode code
  > points of the two characters.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Char::op_sub" {
  >    let a = 'b'
  >    let b = 'a'
  >    inspect!(a - b, content="1") // Unicode point of 'b' (98) minus 'a' (97)
  >  }
  >  ```
- #### to\_int
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1206:::fn <a href="moonbitlang/core/char#Char">Char</a>::to_int(self : Char) -> Int
  ```
  > 
  >  Converts a character to its Unicode code point value as an integer.
  > 
  >  Parameters:
  > 
  >  * `self` : The character to be converted.
  > 
  >  Returns an integer representing the Unicode code point value of the
  > character.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Char::to_int" {
  >    inspect!('A'.to_int(), content="65") // ASCII value of 'A'
  >    inspect!('あ'.to_int(), content="12354") // Unicode code point of 'あ'
  >  }
  >  ```
- #### to\_uint
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1230:::fn <a href="moonbitlang/core/char#Char">Char</a>::to_uint(self : Char) -> UInt
  ```
  > 
  >  Converts a Unicode character to its unsigned 32-bit integer code point
  > representation. The character's code point value is first converted to a
  > signed integer and then reinterpreted as an unsigned integer.
  > 
  >  Parameters:
  > 
  >  * `character` : The Unicode character to be converted.
  > 
  >  Returns an unsigned 32-bit integer representing the character's Unicode code
  > point.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Char::to_uint" {
  >    let c = 'A'
  >    inspect!(c.to_uint(), content="65") // ASCII value of 'A'
  >    let emoji = '🤣'
  >    inspect!(emoji.to_uint(), content="129315") // Unicode code point U+1F923
  >  }
  >  ```

## Byte


#### mooncakes-io-method-mark-Methods
- #### lnot
  ```moonbit
  :::source,moonbitlang/core/builtin/byte.mbt,233:::fn <a href="moonbitlang/core/byte#Byte">Byte</a>::lnot(self : Byte) -> Byte
  ```
  > 
  >  Performs a bitwise NOT operation on the given `Byte` value.
  > 
  >  Parameters:
  > 
  >  - `value` : The `Byte` value to apply the bitwise NOT operation on.
  > 
  >  Returns the result of the bitwise NOT operation as a `Byte`.
- #### lsl
  ```moonbit
  :::source,moonbitlang/core/builtin/byte.mbt,332:::fn <a href="moonbitlang/core/byte#Byte">Byte</a>::lsl(self : Byte, count : Int) -> Byte
  ```
  > 
  >  positions.
  > 
  >  Parameters:
  > 
  >  - `byte_value` : The `Byte` value whose bits are to be shifted.
  >  - `shift_count` : The number of bit positions to shift the `byte_value` to
  >    the left.
  > 
  >  Returns the resulting `Byte` value after the bitwise left shift operation.
  > 
- #### lsr
  ```moonbit
  :::source,moonbitlang/core/builtin/byte.mbt,348:::fn <a href="moonbitlang/core/byte#Byte">Byte</a>::lsr(self : Byte, count : Int) -> Byte
  ```
  > 
  >  bits.
  > 
  >  Parameters:
  > 
  >  - `value` : The `Byte` value to be shifted.
  >  - `count` : The number of bits to shift the `value` to the right.
  > 
  >  Returns the result of the logical shift right operation as a `Byte`.
  > 
- #### to\_double
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2982:::fn <a href="moonbitlang/core/byte#Byte">Byte</a>::to_double(self : Byte) -> Double
  ```
  >  TODO: use intrinsics implement this
- #### to\_float
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,2979:::fn <a href="moonbitlang/core/byte#Byte">Byte</a>::to_float(self : Byte) -> Float
  ```
  > 
  >  Converts a byte value to a 32-bit floating-point number (IEEE 754
  > single-precision format). The byte value is treated as an unsigned 8-bit
  > integer during the conversion.
  > 
  >  Parameters:
  > 
  >  * `byte` : The byte value to be converted to a float.
  > 
  >  Returns a 32-bit floating-point number representing the byte value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Byte::to_float" {
  >    let b = b'\xFF' // 255 in decimal
  >    let f = b.to_float()
  >    // Convert to double for comparison since Float doesn't implement Show
  >    inspect!(f.to_double(), content="255")
  >  }
  >  ```
- #### to\_int
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1907:::fn <a href="moonbitlang/core/byte#Byte">Byte</a>::to_int(self : Byte) -> Int
  ```
  > 
  >  Converts a byte value to a 32-bit signed integer. The resulting integer will
  > have the same binary representation as the byte value, preserving the
  > numerical value in the range \[0, 255\].
  > 
  >  Parameters:
  > 
  >  * `byte` : The byte value to be converted to an integer.
  > 
  >  Returns a 32-bit signed integer representing the same numerical value as the
  > input byte.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Byte::to_int" {
  >    let b = b'\xFF' // byte with value 255
  >    inspect!(b.to_int(), content="255")
  >    let zero = b'\x00'
  >    inspect!(zero.to_int(), content="0")
  >  }
  >  ```
- #### to\_int16
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,3099:::fn <a href="moonbitlang/core/byte#Byte">Byte</a>::to_int16(self : Byte) -> Int16
  ```
  > 
  >  Converts a byte value to a 16-bit signed integer. The byte value is
  > sign-extended to 16 bits during the conversion.
  > 
  >  Parameters:
  > 
  >  * `byte` : The byte value to be converted to an `Int16`.
  > 
  >  Returns a 16-bit signed integer representing the same value as the input
  > byte.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Byte::to_int16" {
  >    let b = b'\xFF' // -1 as a signed byte
  >    inspect!(b.to_int16(), content="255") // Sign is preserved
  >    let p = b'\x7F' // 127 as a signed byte
  >    inspect!(p.to_int16(), content="127")
  >  }
  >  ```
- #### to\_int64
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,1928:::fn <a href="moonbitlang/core/byte#Byte">Byte</a>::to_int64(self : Byte) -> Int64
  ```
  > 
  >  Converts a byte value to a 64-bit signed integer by first converting it to a
  > 32-bit integer and then extending it to a 64-bit integer.
  > 
  >  Parameters:
  > 
  >  * `byte` : The byte value to be converted.
  > 
  >  Returns a 64-bit signed integer representing the same numerical value as the
  > input byte.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Byte::to_int64" {
  >    let b = b'\xFF'
  >    inspect!(b.to_int64(), content="255")
  >  }
  >  ```
- #### to\_string
  ```moonbit
  :::source,moonbitlang/core/builtin/byte.mbt,161:::fn <a href="moonbitlang/core/byte#Byte">Byte</a>::to_string(self : Byte) -> String
  ```
  > 
  >  Converts a `Byte` to its string representation in hexadecimal format.
  > 
  >  Parameters:
  > 
  >  - `byte` : The `Byte` value to be converted.
  > 
  >  Returns a `String` representing the `Byte` in the format `b'\xHH'`, where
  > `HH` is the hexadecimal representation of the byte.
- #### to\_uint
  ```moonbit
  :::source,moonbitlang/core/builtin/byte.mbt,285:::fn <a href="moonbitlang/core/byte#Byte">Byte</a>::to_uint(self : Byte) -> UInt
  ```
  > 
  >  Converts a `Byte` to a `UInt`.
  > 
  >  Parameters:
  > 
  >  - `byte` : The `Byte` value to be converted.
  > 
  >  Returns the `UInt` representation of the `Byte`.
- #### to\_uint16
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,3190:::fn <a href="moonbitlang/core/byte#Byte">Byte</a>::to_uint16(self : Byte) -> UInt16
  ```
  > 
  >  Converts a byte value to a 16-bit unsigned integer by zero-extending it.
  > 
  >  Parameters:
  > 
  >  * `byte` : The byte value to be converted.
  > 
  >  Returns a 16-bit unsigned integer (`UInt16`) representing the same value as
  > the input byte.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Byte::to_uint16" {
  >    let b = b'\xFF' // byte with value 255
  >    inspect!(b.to_uint16(), content="255")
  >    let zero = b'\x00'
  >    inspect!(zero.to_uint16(), content="0")
  >  }
  >  ```

## Bool


#### mooncakes-io-method-mark-Methods
- #### op\_compare
  ```moonbit
  :::source,moonbitlang/core/builtin/intrinsics.mbt,169:::fn <a href="moonbitlang/core/bool#Bool">Bool</a>::op_compare(self : Bool, other : Bool) -> Int
  ```
  > 
  >  Compares two boolean values and returns their relative order. This is a
  > deprecated method and users should use `compare` instead.
  > 
  >  Parameters:
  > 
  >  * `self` : The first boolean value to compare.
  >  * `other` : The second boolean value to compare against.
  > 
  >  Returns an integer indicating the relative order:
  > 
  >  * A negative value if `self` is less than `other` (i.e., `self` is `false`
  >    and `other` is `true`)
  >  * Zero if `self` equals `other`
  >  * A positive value if `self` is greater than `other` (i.e., `self` is `true`
  >    and `other` is `false`)
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Bool::op_compare/deprecated" {
  >    let t = true
  >    let f = false
  >    // This usage is deprecated, use compare() instead
  >    inspect!(t.compare(f), content="1")
  >    inspect!(f.compare(t), content="-1")
  >    inspect!(t.compare(t), content="0")
  >  }
  >  ```
  > 
