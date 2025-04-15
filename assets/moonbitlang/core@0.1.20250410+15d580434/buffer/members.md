# Documentation
|Type|description|
|---|---|
|[T](#T)||
|[Buffer](#Buffer)| Extensible buffer.|

|Value|description|
|---|---|
|[contents](#contents)||
|[is\_empty](#is_empty)||
|[length](#length)||
|[new](#new)||
|[reset](#reset)||
|[to\_bytes](#to_bytes)||
|[write\_byte](#write_byte)||
|[write\_bytes](#write_bytes)||
|[write\_bytesview](#write_bytesview)||
|[write\_double\_be](#write_double_be)||
|[write\_double\_le](#write_double_le)||
|[write\_float\_be](#write_float_be)||
|[write\_float\_le](#write_float_le)||
|[write\_int64\_be](#write_int64_be)||
|[write\_int64\_le](#write_int64_le)||
|[write\_int\_be](#write_int_be)||
|[write\_int\_le](#write_int_le)||
|[write\_iter](#write_iter)||
|[write\_object](#write_object)||
|[write\_uint64\_be](#write_uint64_be)||
|[write\_uint64\_le](#write_uint64_le)||
|[write\_uint\_be](#write_uint_be)||
|[write\_uint\_le](#write_uint_le)||

## T

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,37:::type T
```

 Extensible buffer.

 It provides accumulative concatenation of bytes in linear time.
The capacity of buffer will automatically expand as necessary.

 Note: StringBuilder is recommended for string concatenation in favor of
Buffer, since it is optimized for all targets.
 #### Usage

 ```
 let buf = @buffer.new(size_hint=100)
 buf.write_string("Tes")
 buf.write_char('t')
 inspect!(buf.contents(), content=
   #|b"\x54\x00\x65\x00\x73\x00\x74\x00"
 )
 ```

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,193:::impl <a href="moonbitlang/core/builtin#Logger">Logger</a> for <a href="moonbitlang/core/buffer#T">T</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/buffer/buffer.mbt,654:::fn write_char(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Char) -> Unit
    ```
    > 
    >  Writes a UTF-16LE encoded character into the buffer. Automatically grows the
    > buffer if necessary.
    > 
    >  Parameters:
    > 
    >  * `buffer` : The buffer to write to.
    >  * `char` : The character to be written.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "write_char" {
    >    let buf = @buffer.new()
    >    buf.write_char('A')
    >    inspect!(buf.contents(), content=
    >    #|b"\x41\x00"
    >  )
    >  }
    >  ```
  * ```moonbit
    :::source,moonbitlang/core/buffer/buffer.mbt,193:::fn write_string(self : <a href="moonbitlang/core/buffer#T">T</a>, value : String) -> Unit
    ```
    > 
    >  Writes a UTF-16LE encoded string into the buffer. The buffer will
    > automatically grow if needed to accommodate the string.
    > 
    >  Parameters:
    > 
    >  * `buffer` : The buffer to write to.
    >  * `string` : The string to be written.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "write_string" {
    >    let buf = @buffer.new()
    >    buf.write_string("Test")
    >    // Each UTF-16 char takes 2 bytes in little-endian format
    >    // 'T' -> [0x54, 0x00]
    >    // 'e' -> [0x65, 0x00]
    >    // 's' -> [0x73, 0x00]
    >    // 't' -> [0x74, 0x00]
    >    inspect!(
    >      buf.contents(),
    >      content=
    >        #|b"\x54\x00\x65\x00\x73\x00\x74\x00"
    >      ,
    >    )
    >  }
    >  ```
  * ```moonbit
    :::source,moonbitlang/core/buffer/buffer.mbt,622:::fn write_substring(self : <a href="moonbitlang/core/buffer#T">T</a>, value : String, start : Int, len : Int) -> Unit
    ```
    > 
    >  Writes a portion of a string into the buffer in UTF-16LE encoding.
    > 
    >  Parameters:
    > 
    >  * `self` : The buffer to write to.
    >  * `str` : The source string from which the substring will be taken.
    >  * `offset` : The starting position in the source string (inclusive). Must be
    >    non-negative.
    >  * `count` : The number of characters to write. Must be non-negative and
    >    `offset + count` must not exceed the length of the source string.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "write_substring" {
    >    let buf = @buffer.new()
    >    buf.write_substring("Hello, World!", 0, 5)
    >    inspect!(
    >      buf.contents(),
    >      content=
    >        #|b"\x48\x00\x65\x00\x6c\x00\x6c\x00\x6f\x00"
    >      ,
    >    )
    >  }
    >  ```
- ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,759:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/buffer#T">T</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/buffer/buffer.mbt,759:::fn output(self : <a href="moonbitlang/core/buffer#T">T</a>, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### contents
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,134:::fn <a href="moonbitlang/core/buffer#T">T</a>::contents(self : <a href="moonbitlang/core/buffer#T">T</a>) -> Bytes
  ```
  > 
  >  Returns a copy of the buffer's content as a sequence of bytes.
  > 
  >  Parameters:
  > 
  >  * `buffer` : The buffer to read from.
  > 
  >  Returns a `Bytes` object containing all bytes written to the buffer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "contents" {
  >    let buf = @buffer.new()
  >    buf.write_string("Test")
  >    inspect!(
  >      buf.contents(),
  >      content=
  >        #|b"\x54\x00\x65\x00\x73\x00\x74\x00"
  >      ,
  >    )
  >  }
  >  ```
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,107:::fn <a href="moonbitlang/core/buffer#T">T</a>::is_empty(self : <a href="moonbitlang/core/buffer#T">T</a>) -> Bool
  ```
  > 
  >  Returns whether the buffer is empty.
  > 
  >  Parameters:
  > 
  >  * `buffer` : The buffer to check.
  > 
  >  Returns `true` if the buffer is empty (i.e., contains no bytes), `false`
  > otherwise.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "buffer::is_empty" {
  >    let buf = @buffer.new()
  >    inspect!(buf.is_empty(), content="true")
  >    buf.write_string("test")
  >    inspect!(buf.is_empty(), content="false")
  >  }
  >  ```
- #### length
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,83:::fn <a href="moonbitlang/core/buffer#T">T</a>::length(self : <a href="moonbitlang/core/buffer#T">T</a>) -> Int
  ```
  > 
  >  Returns the number of bytes currently stored in the buffer.
  > 
  >  Parameters:
  > 
  >  * `buffer`: The buffer to get the length from.
  > 
  >  Returns the length of the buffer in bytes.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "length" {
  >    let buf = @buffer.new()
  >    buf.write_string("Test")
  >    inspect!(buf.length(), content="8") // each char takes 2 bytes in UTF-16
  >  }
  >  ```
- #### reset
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,729:::fn <a href="moonbitlang/core/buffer#T">T</a>::reset(self : <a href="moonbitlang/core/buffer#T">T</a>) -> Unit
  ```
  > 
  >  Resets the buffer to its initial state by restoring its initial capacity and
  > clearing its contents.
  > 
  >  Parameters:
  > 
  >  * `self` : The buffer to be reset.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "reset" {
  >    let buf = @buffer.new(size_hint=4)
  >    buf.write_string("Test")
  >    buf.reset()
  >    inspect!(buf.length(), content="0")
  >    inspect!(buf.is_empty(), content="true")
  >  }
  >  ```
- #### to\_bytes
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,754:::fn <a href="moonbitlang/core/buffer#T">T</a>::to_bytes(self : <a href="moonbitlang/core/buffer#T">T</a>) -> Bytes
  ```
  > 
  >  Returns a copy of the buffer's contents as a `Bytes` object. The returned
  > bytes will have the same length as the buffer.
  > 
  >  Parameters:
  > 
  >  * `buffer` : The buffer whose contents will be converted to bytes.
  > 
  >  Returns a `Bytes` object containing a copy of the buffer's contents.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "to_bytes" {
  >    let buf = @buffer.new()
  >    buf.write_string("Test")
  >    let bytes = buf.to_bytes()
  >    inspect!(bytes.length(), content="8")
  >  }
  >  ```
- #### write\_byte
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,678:::fn <a href="moonbitlang/core/buffer#T">T</a>::write_byte(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Byte) -> Unit
  ```
  > 
  >  Writes a single byte to the end of the buffer. The buffer will automatically
  > grow if necessary to accommodate the new byte.
  > 
  >  Parameters:
  > 
  >  * `buffer` : The buffer to write to.
  >  * `byte` : The byte value to be written.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "write_byte" {
  >    let buf = @buffer.new()
  >    buf.write_byte(b'\x41')
  >    inspect!(buf.contents(), content="b\"\\x41\"")
  >  }
  >  ```
- #### write\_bytes
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,554:::fn <a href="moonbitlang/core/buffer#T">T</a>::write_bytes(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Bytes) -> Unit
  ```
  > 
  >  Writes a sequence of bytes into the buffer.
  > 
  >  Parameters:
  > 
  >  * `buffer` : An extensible buffer to write into.
  >  * `bytes` : The sequence of bytes to be written.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "write_bytes" {
  >    let buf = @buffer.new()
  >    buf.write_bytes(b"Test")
  >    inspect!(
  >      buf.contents(),
  >      content=
  >        #|b"\x54\x65\x73\x74"
  >      ,
  >    )
  >  }
  >  ```
- #### write\_bytesview
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,584:::fn <a href="moonbitlang/core/buffer#T">T</a>::write_bytesview(self : <a href="moonbitlang/core/buffer#T">T</a>, value : <a href="moonbitlang/core/bytes#View">@moonbitlang/core/bytes.View</a>) -> Unit
  ```
  > 
  >  Writes a sequence of bytes from a @bytes.View into the buffer.
  > 
  >  Parameters:
  > 
  >  * `buffer` : The buffer to write to.
  >  * `value` : The View containing the bytes to write.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "write_bytesview" {
  >    let buf = @buffer.new()
  >    let view = b"Test"[1:3]
  >    buf.write_bytesview(view)
  >    inspect!(
  >      buf.contents(),
  >      content=
  >        #|b"\x65\x73"
  >      ,
  >    )
  >  }
  >  ```
- #### write\_double\_be
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,432:::fn <a href="moonbitlang/core/buffer#T">T</a>::write_double_be(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Double) -> Unit
  ```
  > 
  >  Writes an IEEE 754 double-precision floating-point number into the buffer in
  > big-endian format (most significant byte first).
  > 
  >  Parameters:
  > 
  >  * `buffer` : The buffer to write to.
  >  * `value` : The double-precision floating-point number to be written.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "write_double_be" {
  >    let buf = @buffer.new()
  >    buf.write_double_be(1.0)
  >    inspect!(buf.contents(), content="b\"\\x3f\\xf0\\x00\\x00\\x00\\x00\\x00\\x00\"")
  >  }
  >  ```
- #### write\_double\_le
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,457:::fn <a href="moonbitlang/core/buffer#T">T</a>::write_double_le(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Double) -> Unit
  ```
  > 
  >  Writes a double-precision floating-point number into the buffer in
  > little-endian format.
  > 
  >  Parameters:
  > 
  >  * `buffer` : The buffer to write to.
  >  * `value` : The double-precision floating-point number to write.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "write_double_le" {
  >    let buf = @buffer.new()
  >    buf.write_double_le(3.14)
  >    inspect!(
  >      buf.contents(),
  >      content="b\"\\x1f\\x85\\xeb\\x51\\xb8\\x1e\\x09\\x40\"",
  >    )
  >  }
  >  ```
- #### write\_float\_be
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,481:::fn <a href="moonbitlang/core/buffer#T">T</a>::write_float_be(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Float) -> Unit
  ```
  > 
  >  Writes a 32-bit floating-point number to the buffer in big-endian byte order.
  > The float value is first reinterpreted as a 32-bit unsigned integer before
  > writing.
  > 
  >  Parameters:
  > 
  >  * `buffer` : The buffer to write to.
  >  * `value` : The floating-point number to be written.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "write_float_be" {
  >    let buf = @buffer.new()
  >    buf.write_float_be(3.14)
  >    // In big-endian format, 3.14 is represented as [0x40, 0x48, 0xF5, 0xC3]
  >    inspect!(buf.contents(), content="b\"\\x40\\x48\\xf5\\xc3\"")
  >  }
  >  ```
- #### write\_float\_le
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,504:::fn <a href="moonbitlang/core/buffer#T">T</a>::write_float_le(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Float) -> Unit
  ```
  > 
  >  Writes a Float value into the buffer in little-endian format. The float value
  > is converted to its binary representation and written as four bytes.
  > 
  >  Parameters:
  > 
  >  * `buffer` : The buffer to write to.
  >  * `value` : The Float value to be written.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "write_float_le" {
  >    let buf = @buffer.new()
  >    buf.write_float_le(3.14)
  >    // The bytes are written in little-endian format
  >    inspect!(buf.contents(), content="b\"\\xc3\\xf5\\x48\\x40\"")
  >  }
  >  ```
- #### write\_int64\_be
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,291:::fn <a href="moonbitlang/core/buffer#T">T</a>::write_int64_be(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Int64) -> Unit
  ```
  > 
  >  Writes a 64-bit integer into the buffer in big-endian format, where the most
  > significant byte is written first.
  > 
  >  Parameters:
  > 
  >  * `buffer` : The buffer to write into.
  >  * `value` : The 64-bit integer to be written.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "write_int64_be" {
  >    let buf = @buffer.new()
  >    buf.write_int64_be(0x0102030405060708L)
  >    inspect!(
  >      buf.contents(),
  >      content=
  >        #|b"\x01\x02\x03\x04\x05\x06\x07\x08"
  >      ,
  >    )
  >  }
  >  ```
- #### write\_int64\_le
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,314:::fn <a href="moonbitlang/core/buffer#T">T</a>::write_int64_le(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Int64) -> Unit
  ```
  > 
  >  Writes a 64-bit signed integer to the buffer in little-endian byte order.
  > 
  >  Parameters:
  > 
  >  * `buffer` : The buffer to write to.
  >  * `value` : The 64-bit signed integer to write.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "write_int64_le" {
  >    let buf = @buffer.new()
  >    buf.write_int64_le(-1L)
  >    inspect!(buf.contents(), content=
  >    #|b"\xff\xff\xff\xff\xff\xff\xff\xff"
  >  )
  >  }
  >  ```
- #### write\_int\_be
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,387:::fn <a href="moonbitlang/core/buffer#T">T</a>::write_int_be(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Int) -> Unit
  ```
  > 
  >  Writes a 32-bit integer to the buffer in big-endian format. Big-endian means
  > the most significant byte is written first.
  > 
  >  Parameters:
  > 
  >  * `buffer` : The buffer to write to.
  >  * `value` : The 32-bit integer to be written.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "write_int_be" {
  >    let buf = @buffer.new()
  >    buf.write_int_be(0x12345678)
  >    inspect!(buf.contents(), content="b\"\\x12\\x34\\x56\\x78\"")
  >  }
  >  ```
- #### write\_int\_le
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,410:::fn <a href="moonbitlang/core/buffer#T">T</a>::write_int_le(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Int) -> Unit
  ```
  > 
  >  Writes a 32-bit integer into the buffer in little-endian format. The integer
  > is first reinterpreted as an unsigned integer, then written as 4 bytes where
  > the least significant byte is written first.
  > 
  >  Parameters:
  > 
  >  * `buffer` : The buffer to write into.
  >  * `value` : The integer value to be written.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "write_int_le" {
  >    let buf = @buffer.new()
  >    buf.write_int_le(-1)
  >    inspect!(buf.contents(), content="b\"\\xff\\xff\\xff\\xff\"")
  >  }
  >  ```
- #### write\_iter
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,704:::fn <a href="moonbitlang/core/buffer#T">T</a>::write_iter(self : <a href="moonbitlang/core/buffer#T">T</a>, iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[Byte]) -> Unit
  ```
  > 
  >  Writes bytes from an iterator to the buffer.
  > 
  >  Parameters:
  > 
  >  * `self` : The buffer to write to.
  >  * `iter` : An iterator yielding bytes to write.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "write_iter" {
  >    let buf = @buffer.new()
  >    let bytes = b"Hello"
  >    buf.write_iter(bytes.iter())
  >    inspect!(buf.contents(), content=
  >    #|b"\x48\x65\x6c\x6c\x6f"
  >  )
  >  }
  >  ```
- #### write\_object
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,528:::fn <a href="moonbitlang/core/buffer#T">T</a>::write_object(self : <a href="moonbitlang/core/buffer#T">T</a>, value : <a href="moonbitlang/core/builtin#Show">Show</a>) -> Unit
  ```
  > 
  >  Writes a string representation of any value that implements the `Show` trait
  > into the buffer.
  > 
  >  Parameters:
  > 
  >  * `buffer` : The buffer to write to.
  >  * `value` : Any value that implements the `Show` trait. The value will be
  >    converted to a string using its `to_string` method before being written to
  >    the buffer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "write_object" {
  >    let buf = @buffer.new()
  >    buf.write_object(42)
  >    inspect!(buf.contents().to_unchecked_string(), content="42")
  >  }
  >  ```
- #### write\_uint64\_be
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,223:::fn <a href="moonbitlang/core/buffer#T">T</a>::write_uint64_be(self : <a href="moonbitlang/core/buffer#T">T</a>, value : UInt64) -> Unit
  ```
  > 
  >  Writes an unsigned 64-bit integer into the buffer in big-endian format (most
  > significant byte first).
  > 
  >  Parameters:
  > 
  >  * `buffer` : The buffer to write to.
  >  * `value` : The unsigned 64-bit integer to be written.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "write_uint64_be" {
  >    let buf = @buffer.new()
  >    buf.write_uint64_be(0xAABBCCDD11223344)
  >    // Bytes are written in big-endian order
  >    inspect!(
  >      buf.contents(),
  >      content=
  >        #|b"\xaa\xbb\xcc\xdd\x11\x22\x33\x44"
  >      ,
  >    )
  >  }
  >  ```
- #### write\_uint64\_le
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,257:::fn <a href="moonbitlang/core/buffer#T">T</a>::write_uint64_le(self : <a href="moonbitlang/core/buffer#T">T</a>, value : UInt64) -> Unit
  ```
  > 
  >  Writes an unsigned 64-bit integer to the buffer in little-endian byte order.
  > Each byte is written sequentially from least significant to most significant.
  > 
  >  Parameters:
  > 
  >  * `buffer` : The buffer to write to.
  >  * `value` : The UInt64 value to be written.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "write_uint64_le" {
  >    let buf = @buffer.new()
  >    buf.write_uint64_le(0x0123456789ABCDEF)
  >    inspect!(
  >      buf.contents(),
  >      content=
  >        #|b"\xef\xcd\xab\x89\x67\x45\x23\x01"
  >      ,
  >    )
  >  }
  >  ```
- #### write\_uint\_be
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,336:::fn <a href="moonbitlang/core/buffer#T">T</a>::write_uint_be(self : <a href="moonbitlang/core/buffer#T">T</a>, value : UInt) -> Unit
  ```
  > 
  >  Writes a 32-bit unsigned integer into the buffer in big-endian format (most
  > significant byte first).
  > 
  >  Parameters:
  > 
  >  * `buffer` : The buffer to write to.
  >  * `value` : The unsigned integer value to write.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "write_uint_be" {
  >    let buf = @buffer.new()
  >    buf.write_uint_be(0x12345678)
  >    inspect!(buf.contents(), content="b\"\\x12\\x34\\x56\\x78\"")
  >  }
  >  ```
- #### write\_uint\_le
  ```moonbit
  :::source,moonbitlang/core/buffer/buffer.mbt,362:::fn <a href="moonbitlang/core/buffer#T">T</a>::write_uint_le(self : <a href="moonbitlang/core/buffer#T">T</a>, value : UInt) -> Unit
  ```
  > 
  >  Writes a 32-bit unsigned integer into the buffer in little-endian format. The
  > integer is split into 4 bytes and written in order from least significant to
  > most significant byte.
  > 
  >  Parameters:
  > 
  >  * `buffer` : The buffer to write to.
  >  * `value` : A 32-bit unsigned integer to be written.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "write_uint_le" {
  >    let buf = @buffer.new()
  >    buf.write_uint_le(0x12345678)
  >    inspect!(buf.contents(), content="b\"\\x78\\x56\\x34\\x12\"")
  >  }
  >  ```

## Buffer

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,17:::type Buffer = <a href="moonbitlang/core/buffer#T">T</a>
```
 Extensible buffer.
@alert deprecated "Use type `T` instead"

## contents

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,134:::fn contents(self : <a href="moonbitlang/core/buffer#T">T</a>) -> Bytes
```

 Returns a copy of the buffer's content as a sequence of bytes.

 Parameters:

 * `buffer` : The buffer to read from.

 Returns a `Bytes` object containing all bytes written to the buffer.

 Example:

 ```moonbit
 test "contents" {
   let buf = @buffer.new()
   buf.write_string("Test")
   inspect!(
     buf.contents(),
     content=
       #|b"\x54\x00\x65\x00\x73\x00\x74\x00"
     ,
   )
 }
 ```

## is\_empty

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,107:::fn is_empty(self : <a href="moonbitlang/core/buffer#T">T</a>) -> Bool
```

 Returns whether the buffer is empty.

 Parameters:

 * `buffer` : The buffer to check.

 Returns `true` if the buffer is empty (i.e., contains no bytes), `false`
otherwise.

 Example:

 ```moonbit
 test "buffer::is_empty" {
   let buf = @buffer.new()
   inspect!(buf.is_empty(), content="true")
   buf.write_string("test")
   inspect!(buf.is_empty(), content="false")
 }
 ```

## length

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,83:::fn length(self : <a href="moonbitlang/core/buffer#T">T</a>) -> Int
```

 Returns the number of bytes currently stored in the buffer.

 Parameters:

 * `buffer`: The buffer to get the length from.

 Returns the length of the buffer in bytes.

 Example:

 ```moonbit
 test "length" {
   let buf = @buffer.new()
   buf.write_string("Test")
   inspect!(buf.length(), content="8") // each char takes 2 bytes in UTF-16
 }
 ```

## new

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,159:::fn new(size_hint~ : Int = ..) -> <a href="moonbitlang/core/buffer#T">T</a>
```

 Creates a new extensible buffer with specified initial capacity. If the
initial capacity is less than 1, the buffer will be initialized with capacity
1\.

 Parameters:

 * `size_hint` : Initial capacity of the buffer in bytes. Defaults to 0.

 Returns a new buffer of type `T`.

 Example:

 ```moonbit
 test "new" {
   let buf = @buffer.new(size_hint=10)
   inspect!(buf.length(), content="0")
   buf.write_string("test")
   inspect!(buf.length(), content="8")
 }
 ```

## reset

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,729:::fn reset(self : <a href="moonbitlang/core/buffer#T">T</a>) -> Unit
```

 Resets the buffer to its initial state by restoring its initial capacity and
clearing its contents.

 Parameters:

 * `self` : The buffer to be reset.

 Example:

 ```moonbit
 test "reset" {
   let buf = @buffer.new(size_hint=4)
   buf.write_string("Test")
   buf.reset()
   inspect!(buf.length(), content="0")
   inspect!(buf.is_empty(), content="true")
 }
 ```

## to\_bytes

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,754:::fn to_bytes(self : <a href="moonbitlang/core/buffer#T">T</a>) -> Bytes
```

 Returns a copy of the buffer's contents as a `Bytes` object. The returned
bytes will have the same length as the buffer.

 Parameters:

 * `buffer` : The buffer whose contents will be converted to bytes.

 Returns a `Bytes` object containing a copy of the buffer's contents.

 Example:

 ```moonbit
 test "to_bytes" {
   let buf = @buffer.new()
   buf.write_string("Test")
   let bytes = buf.to_bytes()
   inspect!(bytes.length(), content="8")
 }
 ```

## write\_byte

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,678:::fn write_byte(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Byte) -> Unit
```

 Writes a single byte to the end of the buffer. The buffer will automatically
grow if necessary to accommodate the new byte.

 Parameters:

 * `buffer` : The buffer to write to.
 * `byte` : The byte value to be written.

 Example:

 ```moonbit
 test "write_byte" {
   let buf = @buffer.new()
   buf.write_byte(b'\x41')
   inspect!(buf.contents(), content="b\"\\x41\"")
 }
 ```

## write\_bytes

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,554:::fn write_bytes(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Bytes) -> Unit
```

 Writes a sequence of bytes into the buffer.

 Parameters:

 * `buffer` : An extensible buffer to write into.
 * `bytes` : The sequence of bytes to be written.

 Example:

 ```moonbit
 test "write_bytes" {
   let buf = @buffer.new()
   buf.write_bytes(b"Test")
   inspect!(
     buf.contents(),
     content=
       #|b"\x54\x65\x73\x74"
     ,
   )
 }
 ```

## write\_bytesview

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,584:::fn write_bytesview(self : <a href="moonbitlang/core/buffer#T">T</a>, value : <a href="moonbitlang/core/bytes#View">@moonbitlang/core/bytes.View</a>) -> Unit
```

 Writes a sequence of bytes from a @bytes.View into the buffer.

 Parameters:

 * `buffer` : The buffer to write to.
 * `value` : The View containing the bytes to write.

 Example:

 ```moonbit
 test "write_bytesview" {
   let buf = @buffer.new()
   let view = b"Test"[1:3]
   buf.write_bytesview(view)
   inspect!(
     buf.contents(),
     content=
       #|b"\x65\x73"
     ,
   )
 }
 ```

## write\_double\_be

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,432:::fn write_double_be(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Double) -> Unit
```

 Writes an IEEE 754 double-precision floating-point number into the buffer in
big-endian format (most significant byte first).

 Parameters:

 * `buffer` : The buffer to write to.
 * `value` : The double-precision floating-point number to be written.

 Example:

 ```moonbit
 test "write_double_be" {
   let buf = @buffer.new()
   buf.write_double_be(1.0)
   inspect!(buf.contents(), content="b\"\\x3f\\xf0\\x00\\x00\\x00\\x00\\x00\\x00\"")
 }
 ```

## write\_double\_le

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,457:::fn write_double_le(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Double) -> Unit
```

 Writes a double-precision floating-point number into the buffer in
little-endian format.

 Parameters:

 * `buffer` : The buffer to write to.
 * `value` : The double-precision floating-point number to write.

 Example:

 ```moonbit
 test "write_double_le" {
   let buf = @buffer.new()
   buf.write_double_le(3.14)
   inspect!(
     buf.contents(),
     content="b\"\\x1f\\x85\\xeb\\x51\\xb8\\x1e\\x09\\x40\"",
   )
 }
 ```

## write\_float\_be

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,481:::fn write_float_be(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Float) -> Unit
```

 Writes a 32-bit floating-point number to the buffer in big-endian byte order.
The float value is first reinterpreted as a 32-bit unsigned integer before
writing.

 Parameters:

 * `buffer` : The buffer to write to.
 * `value` : The floating-point number to be written.

 Example:

 ```moonbit
 test "write_float_be" {
   let buf = @buffer.new()
   buf.write_float_be(3.14)
   // In big-endian format, 3.14 is represented as [0x40, 0x48, 0xF5, 0xC3]
   inspect!(buf.contents(), content="b\"\\x40\\x48\\xf5\\xc3\"")
 }
 ```

## write\_float\_le

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,504:::fn write_float_le(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Float) -> Unit
```

 Writes a Float value into the buffer in little-endian format. The float value
is converted to its binary representation and written as four bytes.

 Parameters:

 * `buffer` : The buffer to write to.
 * `value` : The Float value to be written.

 Example:

 ```moonbit
 test "write_float_le" {
   let buf = @buffer.new()
   buf.write_float_le(3.14)
   // The bytes are written in little-endian format
   inspect!(buf.contents(), content="b\"\\xc3\\xf5\\x48\\x40\"")
 }
 ```

## write\_int64\_be

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,291:::fn write_int64_be(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Int64) -> Unit
```

 Writes a 64-bit integer into the buffer in big-endian format, where the most
significant byte is written first.

 Parameters:

 * `buffer` : The buffer to write into.
 * `value` : The 64-bit integer to be written.

 Example:

 ```moonbit
 test "write_int64_be" {
   let buf = @buffer.new()
   buf.write_int64_be(0x0102030405060708L)
   inspect!(
     buf.contents(),
     content=
       #|b"\x01\x02\x03\x04\x05\x06\x07\x08"
     ,
   )
 }
 ```

## write\_int64\_le

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,314:::fn write_int64_le(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Int64) -> Unit
```

 Writes a 64-bit signed integer to the buffer in little-endian byte order.

 Parameters:

 * `buffer` : The buffer to write to.
 * `value` : The 64-bit signed integer to write.

 Example:

 ```moonbit
 test "write_int64_le" {
   let buf = @buffer.new()
   buf.write_int64_le(-1L)
   inspect!(buf.contents(), content=
   #|b"\xff\xff\xff\xff\xff\xff\xff\xff"
 )
 }
 ```

## write\_int\_be

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,387:::fn write_int_be(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Int) -> Unit
```

 Writes a 32-bit integer to the buffer in big-endian format. Big-endian means
the most significant byte is written first.

 Parameters:

 * `buffer` : The buffer to write to.
 * `value` : The 32-bit integer to be written.

 Example:

 ```moonbit
 test "write_int_be" {
   let buf = @buffer.new()
   buf.write_int_be(0x12345678)
   inspect!(buf.contents(), content="b\"\\x12\\x34\\x56\\x78\"")
 }
 ```

## write\_int\_le

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,410:::fn write_int_le(self : <a href="moonbitlang/core/buffer#T">T</a>, value : Int) -> Unit
```

 Writes a 32-bit integer into the buffer in little-endian format. The integer
is first reinterpreted as an unsigned integer, then written as 4 bytes where
the least significant byte is written first.

 Parameters:

 * `buffer` : The buffer to write into.
 * `value` : The integer value to be written.

 Example:

 ```moonbit
 test "write_int_le" {
   let buf = @buffer.new()
   buf.write_int_le(-1)
   inspect!(buf.contents(), content="b\"\\xff\\xff\\xff\\xff\"")
 }
 ```

## write\_iter

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,704:::fn write_iter(self : <a href="moonbitlang/core/buffer#T">T</a>, iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[Byte]) -> Unit
```

 Writes bytes from an iterator to the buffer.

 Parameters:

 * `self` : The buffer to write to.
 * `iter` : An iterator yielding bytes to write.

 Example:

 ```moonbit
 test "write_iter" {
   let buf = @buffer.new()
   let bytes = b"Hello"
   buf.write_iter(bytes.iter())
   inspect!(buf.contents(), content=
   #|b"\x48\x65\x6c\x6c\x6f"
 )
 }
 ```

## write\_object

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,528:::fn write_object(self : <a href="moonbitlang/core/buffer#T">T</a>, value : <a href="moonbitlang/core/builtin#Show">Show</a>) -> Unit
```

 Writes a string representation of any value that implements the `Show` trait
into the buffer.

 Parameters:

 * `buffer` : The buffer to write to.
 * `value` : Any value that implements the `Show` trait. The value will be
   converted to a string using its `to_string` method before being written to
   the buffer.

 Example:

 ```moonbit
 test "write_object" {
   let buf = @buffer.new()
   buf.write_object(42)
   inspect!(buf.contents().to_unchecked_string(), content="42")
 }
 ```

## write\_uint64\_be

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,223:::fn write_uint64_be(self : <a href="moonbitlang/core/buffer#T">T</a>, value : UInt64) -> Unit
```

 Writes an unsigned 64-bit integer into the buffer in big-endian format (most
significant byte first).

 Parameters:

 * `buffer` : The buffer to write to.
 * `value` : The unsigned 64-bit integer to be written.

 Example:

 ```moonbit
 test "write_uint64_be" {
   let buf = @buffer.new()
   buf.write_uint64_be(0xAABBCCDD11223344)
   // Bytes are written in big-endian order
   inspect!(
     buf.contents(),
     content=
       #|b"\xaa\xbb\xcc\xdd\x11\x22\x33\x44"
     ,
   )
 }
 ```

## write\_uint64\_le

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,257:::fn write_uint64_le(self : <a href="moonbitlang/core/buffer#T">T</a>, value : UInt64) -> Unit
```

 Writes an unsigned 64-bit integer to the buffer in little-endian byte order.
Each byte is written sequentially from least significant to most significant.

 Parameters:

 * `buffer` : The buffer to write to.
 * `value` : The UInt64 value to be written.

 Example:

 ```moonbit
 test "write_uint64_le" {
   let buf = @buffer.new()
   buf.write_uint64_le(0x0123456789ABCDEF)
   inspect!(
     buf.contents(),
     content=
       #|b"\xef\xcd\xab\x89\x67\x45\x23\x01"
     ,
   )
 }
 ```

## write\_uint\_be

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,336:::fn write_uint_be(self : <a href="moonbitlang/core/buffer#T">T</a>, value : UInt) -> Unit
```

 Writes a 32-bit unsigned integer into the buffer in big-endian format (most
significant byte first).

 Parameters:

 * `buffer` : The buffer to write to.
 * `value` : The unsigned integer value to write.

 Example:

 ```moonbit
 test "write_uint_be" {
   let buf = @buffer.new()
   buf.write_uint_be(0x12345678)
   inspect!(buf.contents(), content="b\"\\x12\\x34\\x56\\x78\"")
 }
 ```

## write\_uint\_le

```moonbit
:::source,moonbitlang/core/buffer/buffer.mbt,362:::fn write_uint_le(self : <a href="moonbitlang/core/buffer#T">T</a>, value : UInt) -> Unit
```

 Writes a 32-bit unsigned integer into the buffer in little-endian format. The
integer is split into 4 bytes and written in order from least significant to
most significant byte.

 Parameters:

 * `buffer` : The buffer to write to.
 * `value` : A 32-bit unsigned integer to be written.

 Example:

 ```moonbit
 test "write_uint_le" {
   let buf = @buffer.new()
   buf.write_uint_le(0x12345678)
   inspect!(buf.contents(), content="b\"\\x78\\x56\\x34\\x12\"")
 }
 ```
