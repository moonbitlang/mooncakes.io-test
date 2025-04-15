# Documentation
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
|[panic](#panic)||
|[physical\_equal](#physical_equal)||
|[println](#println)||
|[repr](#repr)||

## ArgsLoc

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,16:::type ArgsLoc = <a href="moonbitlang/core/builtin#ArgsLoc">ArgsLoc</a>
```

 Represents a type for storing argument locations in source code. It is an
array of optional source locations, where each element corresponds to an
argument's location in the source code. Used internally by the compiler for
error reporting and debugging purposes.

## Array

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,16:::type Array[X] = <a href="moonbitlang/core/array#Array">Array</a>[X]
```

 An `Array` is a collection of values that supports random access and can
grow in size.

## ArrayView

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,16:::type ArrayView[X] = <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[X]
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

## BigInt

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,16:::type BigInt = <a href="moonbitlang/core/bigint#BigInt">BigInt</a>
```

 A big integer represented as an array of Int.

## Failure

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,16:::type Failure = <a href="moonbitlang/core/builtin#Failure">Failure</a>
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

## Hasher

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,16:::type Hasher = <a href="moonbitlang/core/builtin#Hasher">Hasher</a>
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

## InspectError

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,16:::type InspectError = <a href="moonbitlang/core/builtin#InspectError">InspectError</a>
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
:::source,moonbitlang/core/prelude/prelude.mbt,16:::type Iter[X] = <a href="moonbitlang/core/builtin#Iter">Iter</a>[X]
```


## Iter2

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,16:::type Iter2[X, Y] = <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[X, Y]
```


## IterResult

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,16:::type IterResult = <a href="moonbitlang/core/builtin#IterResult">IterResult</a>
```


## Json

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,16:::type Json = <a href="moonbitlang/core/json#Json">Json</a>
```


## Map

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,16:::type Map[K, V] = <a href="moonbitlang/core/builtin#Map">Map</a>[K, V]
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

## Set

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,16:::type Set[X] = <a href="moonbitlang/core/builtin#Set">Set</a>[X]
```

 Mutable linked hash set that maintains the order of insertion, not thread safe.

## SnapshotError

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,16:::type SnapshotError = <a href="moonbitlang/core/builtin#SnapshotError">SnapshotError</a>
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
:::source,moonbitlang/core/prelude/prelude.mbt,16:::type SourceLoc = <a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a>
```

 Represents a source code location in a MoonBit program, containing
information about the file path, line number, and column number. Used
internally by the compiler for error reporting and debugging purposes.

 This type is public to all packages but its internal representation is
opaque. Users cannot construct values of this type directly; they are
automatically created by the compiler when needed.

## StringBuilder

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,16:::type StringBuilder = <a href="moonbitlang/core/builtin#StringBuilder">StringBuilder</a>
```


## UninitializedArray

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,16:::type UninitializedArray[X] = <a href="moonbitlang/core/builtin#UninitializedArray">UninitializedArray</a>[X]
```


## Add

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,37:::type Add = <a href="moonbitlang/core/builtin#Add">Add</a>
```

 types implementing this trait can use the `+` operator

## BitAnd

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,37:::type BitAnd = <a href="moonbitlang/core/builtin#BitAnd">BitAnd</a>
```

 types implementing this trait can use the `&` operator

## BitOr

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,37:::type BitOr = <a href="moonbitlang/core/builtin#BitOr">BitOr</a>
```

 types implementing this trait can use the `|` operator

## BitXOr

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,37:::type BitXOr = <a href="moonbitlang/core/builtin#BitXOr">BitXOr</a>
```

 types implementing this trait can use the `^` operator

## Compare

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,37:::type Compare = <a href="moonbitlang/core/builtin#Compare">Compare</a>
```

 Trait for types whose elements are ordered

 The return value of \[compare\] is:
 - zero, if the two arguments are equal
 - negative, if the first argument is smaller
 - positive, if the first argument is greater

## Default

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,37:::type Default = <a href="moonbitlang/core/builtin#Default">Default</a>
```

 Trait for types with a default value

## Div

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,37:::type Div = <a href="moonbitlang/core/builtin#Div">Div</a>
```

 types implementing this trait can use the `/` operator

## Eq

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,37:::type Eq = <a href="moonbitlang/core/builtin#Eq">Eq</a>
```

 Trait for types whose elements can test for equality

## Hash

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,37:::type Hash = <a href="moonbitlang/core/builtin#Hash">Hash</a>
```

 Trait for types that can be hashed

## Logger

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,37:::type Logger = <a href="moonbitlang/core/builtin#Logger">Logger</a>
```

 Trait for a logger, where debug logs can be written into

## Mod

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,37:::type Mod = <a href="moonbitlang/core/builtin#Mod">Mod</a>
```

 types implementing this trait can use the `%` operator

## Mul

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,37:::type Mul = <a href="moonbitlang/core/builtin#Mul">Mul</a>
```

 types implementing this trait can use the `*` operator

## Neg

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,37:::type Neg = <a href="moonbitlang/core/builtin#Neg">Neg</a>
```

 types implementing this trait can use the unary `-` operator

## Shl

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,37:::type Shl = <a href="moonbitlang/core/builtin#Shl">Shl</a>
```

 types implementing this trait can use the `<<` operator

## Show

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,37:::type Show = <a href="moonbitlang/core/builtin#Show">Show</a>
```

 Trait for types that can be converted to `String`

## Shr

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,37:::type Shr = <a href="moonbitlang/core/builtin#Shr">Shr</a>
```

 types implementing this trait can use the `>>` operator

## Sub

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,37:::type Sub = <a href="moonbitlang/core/builtin#Sub">Sub</a>
```

 types implementing this trait can use the `-` operator

## ToJson

```moonbit
:::source,moonbitlang/core/prelude/prelude.mbt,37:::type ToJson = <a href="moonbitlang/core/builtin#ToJson">ToJson</a>
```

 Trait for types that can be converted to `Json`

## abort

```moonbit
:::source,moonbitlang/core/prelude/intrinsics.mbt,84:::fn abort[T](msg : String) -> T
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
:::source,moonbitlang/core/prelude/assert.mbt,49:::fn assert_eq[T : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Show">Show</a>](a : T, b : T, loc~ : <a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a> = _) -> Unit!<a href="moonbitlang/core/error#Error">Error</a>
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
:::source,moonbitlang/core/prelude/assert.mbt,148:::fn assert_false(x : Bool, loc~ : <a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a> = _) -> Unit!<a href="moonbitlang/core/error#Error">Error</a>
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
:::source,moonbitlang/core/prelude/assert.mbt,81:::fn assert_not_eq[T : <a href="moonbitlang/core/builtin#Eq">Eq</a> + <a href="moonbitlang/core/builtin#Show">Show</a>](a : T, b : T, loc~ : <a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a> = _) -> Unit!<a href="moonbitlang/core/error#Error">Error</a>
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
:::source,moonbitlang/core/prelude/assert.mbt,117:::fn assert_true(x : Bool, loc~ : <a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a> = _) -> Unit!<a href="moonbitlang/core/error#Error">Error</a>
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
:::source,moonbitlang/core/prelude/console.mbt,45:::fn dump[T](t : T, name? : String, loc~ : <a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a> = _) -> T
```

 Prints and returns the value of a given expression for quick and dirty debugging.

## fail

```moonbit
:::source,moonbitlang/core/prelude/failure.mbt,60:::fn fail[T](msg : String, loc~ : <a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a> = _) -> T!<a href="moonbitlang/core/builtin#Failure">Failure</a>
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
:::source,moonbitlang/core/prelude/intrinsics.mbt,35:::fn ignore[T](t : T) -> Unit
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
:::source,moonbitlang/core/prelude/console.mbt,195:::fn inspect(obj : <a href="moonbitlang/core/builtin#Show">Show</a>, content~ : String = .., loc~ : <a href="moonbitlang/core/builtin#SourceLoc">SourceLoc</a> = _, args_loc~ : <a href="moonbitlang/core/builtin#ArgsLoc">ArgsLoc</a> = _) -> Unit!<a href="moonbitlang/core/builtin#InspectError">InspectError</a>
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
:::source,moonbitlang/core/prelude/intrinsics.mbt,112:::fn not(x : Bool) -> Bool
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

## panic

```moonbit
:::source,moonbitlang/core/prelude/intrinsics.mbt,90:::fn panic[T]() -> T
```


## physical\_equal

```moonbit
:::source,moonbitlang/core/prelude/intrinsics.mbt,62:::fn physical_equal[T](a : T, b : T) -> Bool
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
:::source,moonbitlang/core/prelude/console.mbt,38:::fn println[T : <a href="moonbitlang/core/builtin#Show">Show</a>](input : T) -> Unit
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
:::source,moonbitlang/core/prelude/traits.mbt,124:::fn repr[T : <a href="moonbitlang/core/builtin#Show">Show</a>](t : T) -> String
```

