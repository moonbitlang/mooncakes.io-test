# Documentation
|Type|description|
|---|---|
|[View](#View)||
|[Bytes](#Bytes)||

|Value|description|
|---|---|
|[default](#default)||
|[from\_array](#from_array)||
|[from\_fixedarray](#from_fixedarray)||
|[from\_iter](#from_iter)||
|[iter](#iter)||
|[of](#of)||
|[to\_array](#to_array)||
|[to\_fixedarray](#to_fixedarray)||

## View

```moonbit
:::source,moonbitlang/core/bytes/view.mbt,28:::type View
```

 A `@bytes.View` represents a view into a section of a `Bytes` without copying the data.

 #### Example
 
 ```
 let bs = b"\x00\x01\x02\x03\x04\x05"
 let bv = bs[1:4]
 assert_eq!(bv.length(), 3)
 assert_eq!(bv[0], b'\x01')
 assert_eq!(bv[1], b'\x02')
 assert_eq!(bv[2], b'\x03')
 ```

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,628:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for <a href="moonbitlang/core/bytes#View">View</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/bytes/view.mbt,628:::fn compare(self : <a href="moonbitlang/core/bytes#View">View</a>, other : <a href="moonbitlang/core/bytes#View">View</a>) -> Int
    ```
    > 
    >  Compares two views lexicographically. First compares the lengths of
    > the views, then compares bytes pairwise until a difference is found or
    > all bytes have been compared.
    > 
    >  Parameters:
    > 
    >  * `self` : The first view to compare.
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
    >  let bytes = b"abcabc"
    >  inspect!(bytes[0:3].compare(bytes[3:6]), content="0")  // abc = abc
    >  inspect!(bytes[0:3].compare(bytes[2:5]), content="-1") // abc < cab
    >  inspect!(bytes[1:4].compare(bytes[3:6]), content="1")  // bca > abc
    >  inspect!(bytes[0:3].compare(bytes[0:4]), content="-1") // abc < abca
    >  inspect!(bytes[1:5].compare(bytes[2:5]), content="1")  // bcab > cab
    >  ```
- ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,593:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/bytes#View">View</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/bytes/view.mbt,593:::fn op_equal(self : <a href="moonbitlang/core/bytes#View">View</a>, other : <a href="moonbitlang/core/bytes#View">View</a>) -> Bool
    ```
    > 
    >  Compares two views for equality. Returns true only if both views
    > have the same length and contain identical bytes in the same order.
    > 
    >  Parameters:
    > 
    >  * `self` : The first view to compare.
    >  * `other` : The second view to compare.
    > 
    >  Returns `true` if the byte sequences are equal, `false` otherwise.
    > 
    >  Example:
    >  ```moonbit
    >  let bytes = b"abcabc"
    >  inspect!(bytes[0:3] == bytes[3:6], content="true")
    >  inspect!(bytes[0:3] == bytes[2:5], content="false")
    >  inspect!(bytes[0:4] == bytes[3:6], content="false")
    >  ```
- ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,554:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/bytes#View">View</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/bytes/view.mbt,554:::fn output(self : <a href="moonbitlang/core/bytes#View">View</a>, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### data
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,645:::fn <a href="moonbitlang/core/bytes#View">View</a>::data(self : <a href="moonbitlang/core/bytes#View">View</a>) -> Bytes
  ```
  > 
  >  Retrieves the underlying `Bytes` from a `View`.
- #### iter
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,188:::fn <a href="moonbitlang/core/bytes#View">View</a>::iter(self : <a href="moonbitlang/core/bytes#View">View</a>) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[Byte]
  ```
  > 
  >  Returns an iterator over the `View`.
  >  
  >  #### Example
  >  
  >  ```
  >  let bv = b"\x00\x01\x02\x03\x04\x05"[:]
  >  let mut sum = 0
  >  bv.iter().each(fn(x) { sum = sum + x.to_int() })
  >  assert_eq!(sum, 15)
  >  ```
- #### length
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,52:::fn <a href="moonbitlang/core/bytes#View">View</a>::length(self : <a href="moonbitlang/core/bytes#View">View</a>) -> Int
  ```
  > 
  >  Returns the number of bytes in the view.
  > 
  >  Parameters:
  > 
  >  * `bytes_view` : The view of a byte sequence.
  > 
  >  Returns an integer representing the length of the view.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "View::length" {
  >    let bytes = b"\x00\x01\x02\x03\x04"
  >    let view = bytes[2:4]
  >    inspect!(view.length(), content="2")
  >  }
  >  ```
- #### op\_as\_view
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,164:::fn <a href="moonbitlang/core/bytes#View">View</a>::op_as_view(self : <a href="moonbitlang/core/bytes#View">View</a>, start~ : Int = .., end? : Int) -> <a href="moonbitlang/core/bytes#View">View</a>
  ```
  > 
  >  Creates a new `View` from the given `View`.
  >  
  >  #### Example
  >  
  >  ```
  >  let bv = b"\x00\x01\x02\x03\x04\x05"[:]
  >  let bv2 = bv[1:4]
  >  assert_eq!(bv2.length(), 3)
  >  assert_eq!(bv2[1], b'\x02')
  >  ```
- #### op\_get
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,83:::fn <a href="moonbitlang/core/bytes#View">View</a>::op_get(self : <a href="moonbitlang/core/bytes#View">View</a>, index : Int) -> Byte
  ```
  > 
  >  Retrieves a byte from the view at the specified index.
  > 
  >  Parameters:
  > 
  >  * `self` : The bytes view to retrieve the byte from.
  >  * `index` : The position in the view from which to retrieve the byte.
  > 
  >  Returns the byte at the specified index.
  > 
  >  Throws a runtime error if the index is out of bounds (negative or greater
  > than or equal to the length of the view).
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "View::op_get" {
  >    let bytes = b"\x01\x02\x03\x04\x05"
  >    let view = bytes[1:4] // view contains [0x02, 0x03, 0x04]
  >    inspect!(view[1], content="b'\\x03'")
  >  }
  >  
  >  test "panic View::op_get/out_of_bounds" {
  >    let view = b"\x01\x02\x03"[:]
  >    ignore(view[3]) // Index out of bounds
  >  }
  >  ```
- #### start\_offset
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,651:::fn <a href="moonbitlang/core/bytes#View">View</a>::start_offset(self : <a href="moonbitlang/core/bytes#View">View</a>) -> Int
  ```
  > 
  >  Retrieves the start index of the view.
- #### to\_double\_be
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,524:::fn <a href="moonbitlang/core/bytes#View">View</a>::to_double_be(self : <a href="moonbitlang/core/bytes#View">View</a>) -> Double
  ```
  > 
  >  Converts the bytes in a byte view to a double-precision floating-point number
  > using big-endian byte order. The byte view must contain exactly 8 bytes,
  > which represent the IEEE 754 double-precision format.
  > 
  >  Parameters:
  > 
  >  * `byte_view` : The byte view containing exactly 8 bytes to be interpreted as
  >    a double-precision floating-point number in big-endian order.
  > 
  >  Returns a double-precision floating-point number reconstructed from the
  > bytes.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "View::to_double_be" {
  >    // Bytes representing 1.0 in IEEE 754 double-precision format (big-endian)
  >    let bytes = b"\x3F\xF0\x00\x00\x00\x00\x00\x00"
  >    let view = bytes[:]
  >    inspect!(view.to_double_be(), content="1")
  >  }
  >  ```
- #### to\_double\_le
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,549:::fn <a href="moonbitlang/core/bytes#View">View</a>::to_double_le(self : <a href="moonbitlang/core/bytes#View">View</a>) -> Double
  ```
  > 
  >  Converts the bytes in the view to a double-precision floating-point number
  > using little-endian byte order. Interprets the first 8 bytes as a IEEE 754
  > double-precision binary floating-point format (binary64) value.
  > 
  >  Parameters:
  > 
  >  * `bytes` : The byte view to be converted. Must contain at least 8 bytes.
  > 
  >  Returns a `Double` value representing the bytes interpreted in little-endian
  > order.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "View::to_double_le" {
  >    let bytes = b"\x00\x00\x00\x00\x00\x00\xF0\x3F" // represents 1.0 in little-endian
  >    let view = bytes[:]
  >    inspect!(view.to_double_le(), content="1")
  >  }
  >  ```
- #### to\_float\_be
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,473:::fn <a href="moonbitlang/core/bytes#View">View</a>::to_float_be(self : <a href="moonbitlang/core/bytes#View">View</a>) -> Float
  ```
  > 
  >  Converts a 4-byte sequence to a 32-bit floating-point number using big-endian
  > byte order.
  > 
  >  Parameters:
  > 
  >  * `bytes_view` : A view into a byte sequence that must be exactly 4 bytes
  >    long. The bytes are interpreted in big-endian order (most significant byte
  >    first).
  > 
  >  Returns a 32-bit floating-point number obtained by interpreting the 4 bytes
  > as an IEEE 754 single-precision value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "View::to_float_be" {
  >    let bytes = b"\x40\x48\xF5\xC3" // Represents 3.14 in IEEE 754 format
  >    let view = bytes[:]
  >    let float = view.to_float_be()
  >    // Convert to double for comparison since Float doesn't implement Show
  >    inspect!(float.to_double(), content="3.140000104904175")
  >  }
  >  ```
- #### to\_float\_le
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,497:::fn <a href="moonbitlang/core/bytes#View">View</a>::to_float_le(self : <a href="moonbitlang/core/bytes#View">View</a>) -> Float
  ```
  > 
  >  Converts 4 bytes from a bytes view to a 32-bit floating-point number,
  > interpreting the bytes in little-endian order (least significant byte first).
  > 
  >  Parameters:
  > 
  >  * `self` : A bytes view containing at least 4 bytes to be interpreted as a
  >    floating-point number.
  > 
  >  Returns a 32-bit floating-point value constructed from the bytes.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "View::to_float_le" {
  >    let bytes = b"\x00\x00\x80\x3F" // Represents 1.0 in little-endian IEEE-754
  >    let f = bytes[:].to_float_le()
  >    inspect!(f.to_double(), content="1")
  >  }
  >  ```
- #### to\_int64\_be
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,419:::fn <a href="moonbitlang/core/bytes#View">View</a>::to_int64_be(self : <a href="moonbitlang/core/bytes#View">View</a>) -> Int64
  ```
  > 
  >  Interprets an 8-byte view as a signed 64-bit integer in big-endian byte
  > order. The highest byte (index 0) is treated as the most significant byte.
  > 
  >  Parameters:
  > 
  >  * `bytes_view` : A view containing exactly 8 bytes to be interpreted as a
  >    big-endian signed 64-bit integer.
  > 
  >  Returns a 64-bit signed integer (`Int64`) value constructed by interpreting
  > the bytes in big-endian order.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "View::to_int64_be" {
  >    let bytes = b"\x80\x00\x00\x00\x00\x00\x00\x00"[:] // Most negative 64-bit integer
  >    inspect!(bytes.to_int64_be(), content="-9223372036854775808")
  >  }
  >  ```
- #### to\_int64\_le
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,445:::fn <a href="moonbitlang/core/bytes#View">View</a>::to_int64_le(self : <a href="moonbitlang/core/bytes#View">View</a>) -> Int64
  ```
  > 
  >  Converts a sequence of 8 bytes into a signed 64-bit integer using
  > little-endian byte order. In little-endian order, the least significant byte
  > is stored at the lowest address (first byte).
  > 
  >  Parameters:
  > 
  >  * `bytes_view` : A view into a sequence of exactly 8 bytes. The first byte
  >    represents the least significant byte of the resulting integer.
  > 
  >  Returns a 64-bit signed integer (`Int64`) constructed from the bytes in
  > little-endian order.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "View::to_int64_le" {
  >    let bytes = b"\x01\x02\x03\x04\x05\x06\x07\x08"
  >    let view = bytes[:]
  >    inspect!(view.to_int64_le(), content="578437695752307201")
  >  }
  >  ```
- #### to\_int\_be
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,367:::fn <a href="moonbitlang/core/bytes#View">View</a>::to_int_be(self : <a href="moonbitlang/core/bytes#View">View</a>) -> Int
  ```
  > 
  >  Converts a 4-byte view of bytes to a 32-bit signed integer by interpreting
  > the bytes in big-endian order (most significant byte first). Interprets the
  > resulting unsigned integer as a signed integer using two's complement
  > representation.
  > 
  >  Parameters:
  > 
  >  * `View` : A view into a byte sequence that must be exactly 4 bytes
  >    long. The bytes are interpreted in big-endian order, where the first byte is
  >    the most significant byte and the last byte is the least significant byte.
  > 
  >  Returns a 32-bit signed integer constructed from the bytes in big-endian
  > order.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "View::to_int_be" {
  >    let bytes = b"\x80\x00\x00\x00"[:] // Represents -2147483648 in two's complement
  >    inspect!(bytes.to_int_be(), content="-2147483648")
  >  }
  >  ```
- #### to\_int\_le
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,395:::fn <a href="moonbitlang/core/bytes#View">View</a>::to_int_le(self : <a href="moonbitlang/core/bytes#View">View</a>) -> Int
  ```
  > 
  >  Converts 4 bytes from a byte sequence into a 32-bit signed integer using
  > little-endian byte order. The bytes are interpreted as follows: the least
  > significant byte is at the lowest address (first position), and the most
  > significant byte is at the highest address (last position).
  > 
  >  Parameters:
  > 
  >  * `bytes_view` : A view into a byte sequence that must be exactly 4 bytes
  >    long. The bytes are interpreted as a little-endian representation of a 32-bit
  >    integer.
  > 
  >  Returns a 32-bit signed integer (`Int`) constructed from the 4 bytes in
  > little-endian order.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "View::to_int_le" {
  >    let bytes = b"\x78\x56\x34\x12"
  >    let view = bytes[:]
  >    inspect!(view.to_int_le(), content="305419896") // 0x12345678 in decimal
  >  }
  >  ```
- #### to\_uint64\_be
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,291:::fn <a href="moonbitlang/core/bytes#View">View</a>::to_uint64_be(self : <a href="moonbitlang/core/bytes#View">View</a>) -> UInt64
  ```
  > 
  >  Converts a sequence of 8 bytes into a 64-bit unsigned integer using
  > big-endian byte order. The most significant byte is at index 0, and the least
  > significant byte is at index 7.
  > 
  >  Parameters:
  > 
  >  * `bytes` : A view into a byte sequence that must be at least 8 bytes long.
  >    The bytes are interpreted in big-endian order, where the first byte is the
  >    most significant byte.
  > 
  >  Returns a 64-bit unsigned integer constructed by concatenating the bytes in
  > big-endian order.
  > 
  >  Throws a runtime error if the byte sequence view is less than 8 bytes long or
  > if attempting to access an index beyond the view's bounds.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "View::to_uint64_be" {
  >    let bytes = b"\x01\x23\x45\x67\x89\xAB\xCD\xEF"[:]
  >    inspect!(bytes.to_uint64_be(), content="81985529216486895")
  >  }
  >  
  >  test "panic View::to_uint64_be/short_input" {
  >    let bytes = b"\x01\x02\x03"[:]
  >    ignore(bytes.to_uint64_be()) // Throws error: index out of bounds
  >  }
  >  ```
- #### to\_uint64\_le
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,333:::fn <a href="moonbitlang/core/bytes#View">View</a>::to_uint64_le(self : <a href="moonbitlang/core/bytes#View">View</a>) -> UInt64
  ```
  > 
  >  Converts an 8-byte sequence to an unsigned 64-bit integer using little-endian
  > byte order. Each byte in the view is treated as an 8-bit unsigned integer and
  > combined to form the final 64-bit value, with the least significant byte
  > first.
  > 
  >  Parameters:
  > 
  >  * `bytes_view` : A view into a byte sequence that must be exactly 8 bytes
  >    long. Each byte represents one byte of the resulting 64-bit integer, with the
  >    first byte being the least significant.
  > 
  >  Returns an unsigned 64-bit integer assembled from the bytes in little-endian
  > order.
  > 
  >  Throws a panic if the View is less than 8 bytes long or if trying to
  > access a byte beyond the view's bounds.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "View::to_uint64_le" {
  >    let bytes = b"\x01\x02\x03\x04\x05\x06\x07\x08"[:]
  >    inspect!(bytes.to_uint64_le(), content="578437695752307201")
  >  }
  >  
  >  test "panic View::to_uint64_le/short_view" {
  >    let bytes = b"\x01\x02\x03"[:]
  >    ignore(bytes.to_uint64_le()) // Panics: view is too short
  >  }
  >  ```
- #### to\_uint\_be
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,223:::fn <a href="moonbitlang/core/bytes#View">View</a>::to_uint_be(self : <a href="moonbitlang/core/bytes#View">View</a>) -> UInt
  ```
  > 
  >  Converts a 4-byte sequence to an unsigned 32-bit integer using big-endian
  > byte order. The first byte is treated as the most significant byte, and the
  > last byte as the least significant byte.
  > 
  >  Parameters:
  > 
  >  * `self` : A byte view containing exactly 4 bytes to be converted.
  > 
  >  Returns an unsigned 32-bit integer representing the byte sequence.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "View::to_uint_be" {
  >    let bytes = b"\x12\x34\x56\x78"[:]
  >    inspect!(bytes.to_uint_be(), content="305419896") // 0x12345678
  >  }
  >  
  >  test "panic View::to_uint_be/out_of_bounds" {
  >    let bytes = b"\x12\x34\x56"[:] // Less than 4 bytes
  >    ignore(bytes.to_uint_be()) // Panics with index out of bounds
  >  }
  >  ```
- #### to\_uint\_le
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,254:::fn <a href="moonbitlang/core/bytes#View">View</a>::to_uint_le(self : <a href="moonbitlang/core/bytes#View">View</a>) -> UInt
  ```
  > 
  >  Converts a sequence of 4 bytes into an unsigned 32-bit integer using
  > little-endian byte order. Each byte in the view contributes 8 bits to the
  > final integer, with the least significant byte at index 0.
  > 
  >  Parameters:
  > 
  >  * `view` : A `View` containing exactly 4 bytes to be interpreted as a
  >    little-endian unsigned integer.
  > 
  >  Returns an unsigned 32-bit integer (`UInt`) formed by interpreting the bytes
  > in little-endian order.
  > 
  >  Throws a panic if the view does not contain exactly 4 bytes.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "View::to_uint_le" {
  >    let bytes = b"\x01\x02\x03\x04"
  >    let view = bytes[:]
  >    inspect!(view.to_uint_le(), content="67305985") // 0x04030201
  >  }
  >  ```
- #### unsafe\_get
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,123:::fn <a href="moonbitlang/core/bytes#View">View</a>::unsafe_get(self : <a href="moonbitlang/core/bytes#View">View</a>, index : Int) -> Byte
  ```
  > 
  >  Retrieves a byte at the specified index from a bytes view without performing
  > bounds checking.
  > 
  >  Parameters:
  > 
  >  * `self` : The bytes view to retrieve the byte from.
  >  * `index` : The position in the view from which to retrieve the byte. The
  >    index is relative to the start of the view, not the underlying bytes.
  > 
  >  Returns a single byte from the specified position in the view.
  > 
  >  Throws a panic if the index is out of bounds (less than 0 or greater than or
  > equal to the length of the view).
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "View::unsafe_get" {
  >    let bytes = b"\x01\x02\x03\x04\x05"
  >    let view = bytes[2:4] // view contains [0x03, 0x04]
  >    inspect!(view.unsafe_get(0), content="b'\\x03'")
  >  }
  >  
  >  test "panic View::unsafe_get/out_of_bounds" {
  >    let view = b"\x01\x02\x03"[:]
  >    ignore(view.unsafe_get(3)) // Panic: index out of bounds
  >  }
  >  ```
  > 
  >  @alert unsafe "Panic if index is out of bounds"

## default

```moonbit
:::source,moonbitlang/core/bytes/bytes.mbt,260:::fn default() -> Bytes
```

 same as `Bytes::default`

## from\_array

```moonbit
:::source,moonbitlang/core/bytes/bytes.mbt,41:::fn from_array(arr : <a href="moonbitlang/core/array#Array">Array</a>[Byte]) -> Bytes
```

 same as `Bytes::from_array`

## from\_fixedarray

```moonbit
:::source,moonbitlang/core/bytes/bytes.mbt,80:::fn from_fixedarray(arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Byte], len? : Int) -> Bytes
```

 same as `Bytes::from_fixedarray`

## from\_iter

```moonbit
:::source,moonbitlang/core/bytes/bytes.mbt,147:::fn from_iter(iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[Byte]) -> Bytes
```

 same as `Bytes::from_iter`

## iter

```moonbit
:::source,moonbitlang/core/bytes/bytes.mbt,228:::fn iter(self : Bytes) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[Byte]
```

 Creates an iterator over the bytes in the sequence.

 Parameters:

 * `bytes` : A byte sequence to iterate over.

 Returns an iterator that yields each byte in the sequence in order.

 Example:

 ```moonbit
 test "Bytes::iter" {
   let bytes = Bytes::from_array([b'h', b'i'])
   let mut sum = 0
   bytes.iter().each(fn(b) { sum = sum + b.to_int() })
   inspect!(sum, content="209") // ASCII values: 'h'(104) + 'i'(105) = 209
 }
 ```

## of

```moonbit
:::source,moonbitlang/core/bytes/bytes.mbt,179:::fn of(arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Byte]) -> Bytes
```

 same as `Bytes::of`

## to\_array

```moonbit
:::source,moonbitlang/core/bytes/bytes.mbt,201:::fn to_array(self : Bytes) -> <a href="moonbitlang/core/array#Array">Array</a>[Byte]
```

 Converts a bytes sequence into an array of bytes.

 Parameters:

 * `bytes` : A sequence of bytes to be converted into an array.

 Returns an array containing the same bytes as the input sequence.

 Example:

 ```moonbit
 test "Bytes::to_array" {
   let bytes = b"hello"
   let arr = bytes.to_array()
   inspect!(arr, content="[b'\\x68', b'\\x65', b'\\x6C', b'\\x6C', b'\\x6F']")
 }
 ```

## to\_fixedarray

```moonbit
:::source,moonbitlang/core/bytes/bytes.mbt,109:::fn to_fixedarray(self : Bytes, len? : Int) -> <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Byte]
```

 Converts a bytes sequence into a fixed-size array of bytes. If an optional
length is provided, the resulting array will have exactly that length,
otherwise it will match the length of the input bytes.

 Parameters:

 * `self` : The bytes sequence to convert.
 * `len` : Optional. The desired length of the output array. If specified, the
   resulting array will have this length. If not specified, the length of the
   input bytes sequence will be used.

 Returns a fixed-size array containing the bytes from the input sequence.

 Example:

 ```moonbit
 test "Bytes::to_fixedarray" {
   let bytes = b"hello"
   let arr = bytes.to_fixedarray()
   inspect!(arr, content="[b'\\x68', b'\\x65', b'\\x6C', b'\\x6C', b'\\x6F']")
   let arr2 = bytes.to_fixedarray(len=3)
   inspect!(arr2, content="[b'\\x68', b'\\x65', b'\\x6C']")
 }
 ```

## Bytes


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/bytes/bytes.mbt,276:::impl <a href="moonbitlang/core/builtin#Add">Add</a> for Bytes
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/bytes/bytes.mbt,276:::fn op_add(self : Bytes, other : Bytes) -> Bytes
    ```
    > 
    >  Concatenates two bytes sequences.
    > 
    >  Parameters:
    > 
    >  * `self` : The first bytes sequence.
    >  * `other` : The second bytes sequence.
    >    TODO: marked as intrinsic, inline if it is constant
- ```moonbit
  :::source,moonbitlang/core/bytes/bytes.mbt,254:::impl <a href="moonbitlang/core/builtin#Default">Default</a> for Bytes
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/bytes/bytes.mbt,254:::fn default() -> Bytes
    ```
    > 
    >  Creates a new empty bytes sequence.
    > 
    >  Returns an empty bytes sequence.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "default" {
    >    let bytes = @bytes.default()
    >    inspect!(bytes, content="b\"\"")
    >    inspect!(bytes.length(), content="0")
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/bytes/xxhash.mbt,45:::impl <a href="moonbitlang/core/builtin#Hash">Hash</a> for Bytes
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/bytes/xxhash.mbt,45:::fn hash(self : Bytes) -> Int
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/core/bytes/xxhash.mbt,50:::fn hash_combine(self : Bytes, hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### from\_array
  ```moonbit
  :::source,moonbitlang/core/bytes/bytes.mbt,35:::fn <a href="moonbitlang/core/bytes#Bytes">Bytes</a>::from_array(arr : <a href="moonbitlang/core/array#Array">Array</a>[Byte]) -> Bytes
  ```
  > 
  >  Creates a new bytes sequence from a byte array.
  > 
  >  Parameters:
  > 
  >  * `array` : An array of bytes to be converted.
  > 
  >  Returns a new bytes sequence containing the same bytes as the input array.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Bytes::from_array" {
  >    let arr = [b'h', b'i']
  >    let bytes = @bytes.from_array(arr)
  >    inspect!(bytes, content=
  >      #|b"\x68\x69"
  >    )
  >  }
  >  ```
- #### from\_fixedarray
  ```moonbit
  :::source,moonbitlang/core/bytes/bytes.mbt,70:::fn <a href="moonbitlang/core/bytes#Bytes">Bytes</a>::from_fixedarray(arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Byte], len? : Int) -> Bytes
  ```
  > 
  >  Creates a new bytes sequence from a fixed-size array of bytes with an
  > optional length parameter.
  > 
  >  Parameters:
  > 
  >  * `array` : A fixed-size array of bytes to be converted into a bytes
  >    sequence.
  >  * `length` : (Optional) The length of the resulting bytes sequence. If not
  >    provided, uses the full length of the input array.
  > 
  >  Returns a new bytes sequence containing the bytes from the input array. If a
  > length is specified, only includes up to that many bytes.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Bytes::from_fixedarray" {
  >    let arr : FixedArray[Byte] = [b'h', b'e', b'l', b'l', b'o']
  >    let bytes = @bytes.from_fixedarray(arr, len=3)
  >    inspect!(bytes, content=
  >      #|b"\x68\x65\x6c"
  >    )
  >  }
  >  ```
- #### from\_iter
  ```moonbit
  :::source,moonbitlang/core/bytes/bytes.mbt,141:::fn <a href="moonbitlang/core/bytes#Bytes">Bytes</a>::from_iter(iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[Byte]) -> Bytes
  ```
  > 
  >  Creates a new bytes sequence from an iterator of bytes.
  > 
  >  Parameters:
  > 
  >  * `iterator` : An iterator that yields bytes.
  > 
  >  Returns a new bytes sequence containing all the bytes from the iterator.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "from_iter" {
  >    let iter = Iter::singleton(b'h')
  >    let bytes = @bytes.from_iter(iter)
  >    inspect!(bytes, content=
  >      #|b"\x68"
  >    )
  >  }
  >  ```
- #### iter
  ```moonbit
  :::source,moonbitlang/core/bytes/bytes.mbt,228:::fn <a href="moonbitlang/core/bytes#Bytes">Bytes</a>::iter(self : Bytes) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[Byte]
  ```
  > 
  >  Creates an iterator over the bytes in the sequence.
  > 
  >  Parameters:
  > 
  >  * `bytes` : A byte sequence to iterate over.
  > 
  >  Returns an iterator that yields each byte in the sequence in order.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Bytes::iter" {
  >    let bytes = Bytes::from_array([b'h', b'i'])
  >    let mut sum = 0
  >    bytes.iter().each(fn(b) { sum = sum + b.to_int() })
  >    inspect!(sum, content="209") // ASCII values: 'h'(104) + 'i'(105) = 209
  >  }
  >  ```
- #### of
  ```moonbit
  :::source,moonbitlang/core/bytes/bytes.mbt,173:::fn <a href="moonbitlang/core/bytes#Bytes">Bytes</a>::of(arr : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Byte]) -> Bytes
  ```
  > 
  >  Creates a new bytes sequence from a fixed-size byte array.
  > 
  >  Parameters:
  > 
  >  * `array` : A fixed-size array of bytes to be converted into a bytes
  >    sequence. Elements in the array should be of type `Byte`.
  > 
  >  Returns a new bytes sequence containing the same bytes as the input array.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "of" {
  >    let arr : FixedArray[Byte] = [b'h', b'e', b'l', b'l', b'o']
  >    let bytes = @bytes.of(arr)
  >    inspect!(bytes, content=
  >      #|b"\x68\x65\x6c\x6c\x6f"
  >    )
  >  }
  >  ```
  >  TODO: marked as intrinsic, inline if it is constant
- #### op\_as\_view
  ```moonbit
  :::source,moonbitlang/core/bytes/view.mbt,140:::fn <a href="moonbitlang/core/bytes#Bytes">Bytes</a>::op_as_view(self : Bytes, start~ : Int = .., end? : Int) -> <a href="moonbitlang/core/bytes#View">View</a>
  ```
  > 
  >  Creates a new `View` from the given `Bytes`.
  >  
  >  #### Example
  >  
  >  ```
  >  let bs = b"\x00\x01\x02\x03\x04\x05"
  >  let bv = bs[1:4]
  >  assert_eq!(bv.length(), 3)
  >  assert_eq!(bv[0], b'\x01')
  >  assert_eq!(bv[1], b'\x02')
  >  assert_eq!(bv[2], b'\x03')
  >  ```
- #### to\_array
  ```moonbit
  :::source,moonbitlang/core/bytes/bytes.mbt,201:::fn <a href="moonbitlang/core/bytes#Bytes">Bytes</a>::to_array(self : Bytes) -> <a href="moonbitlang/core/array#Array">Array</a>[Byte]
  ```
  > 
  >  Converts a bytes sequence into an array of bytes.
  > 
  >  Parameters:
  > 
  >  * `bytes` : A sequence of bytes to be converted into an array.
  > 
  >  Returns an array containing the same bytes as the input sequence.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Bytes::to_array" {
  >    let bytes = b"hello"
  >    let arr = bytes.to_array()
  >    inspect!(arr, content="[b'\\x68', b'\\x65', b'\\x6C', b'\\x6C', b'\\x6F']")
  >  }
  >  ```
- #### to\_fixedarray
  ```moonbit
  :::source,moonbitlang/core/bytes/bytes.mbt,109:::fn <a href="moonbitlang/core/bytes#Bytes">Bytes</a>::to_fixedarray(self : Bytes, len? : Int) -> <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Byte]
  ```
  > 
  >  Converts a bytes sequence into a fixed-size array of bytes. If an optional
  > length is provided, the resulting array will have exactly that length,
  > otherwise it will match the length of the input bytes.
  > 
  >  Parameters:
  > 
  >  * `self` : The bytes sequence to convert.
  >  * `len` : Optional. The desired length of the output array. If specified, the
  >    resulting array will have this length. If not specified, the length of the
  >    input bytes sequence will be used.
  > 
  >  Returns a fixed-size array containing the bytes from the input sequence.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Bytes::to_fixedarray" {
  >    let bytes = b"hello"
  >    let arr = bytes.to_fixedarray()
  >    inspect!(arr, content="[b'\\x68', b'\\x65', b'\\x6C', b'\\x6C', b'\\x6F']")
  >    let arr2 = bytes.to_fixedarray(len=3)
  >    inspect!(arr2, content="[b'\\x68', b'\\x65', b'\\x6C']")
  >  }
  >  ```
