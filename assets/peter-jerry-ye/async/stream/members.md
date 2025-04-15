# Stream

This package provides abstraction for Streams, including readable streams and writable streams.

The goal is to provide an abstraction for stream in Node.js, stream in wasi-io, and other IO-related library, such as libuv.

With the foundation, there will be higher level operations, such as buffered streams, text streams, etc.
---
# Documentation
|Trait|description|
|---|---|
|[@peter-jerry-ye/async/stream.Closable](#@peter-jerry-ye/async/stream.Closable)||
|[@peter-jerry-ye/async/stream.Flushable](#@peter-jerry-ye/async/stream.Flushable)||
|[@peter-jerry-ye/async/stream.InputStream](#@peter-jerry-ye/async/stream.InputStream)| |
|[@peter-jerry-ye/async/stream.OutputStream](#@peter-jerry-ye/async/stream.OutputStream)| |
|[@peter-jerry-ye/async/stream.Reader](#@peter-jerry-ye/async/stream.Reader)| |
|[@peter-jerry-ye/async/stream.Writer](#@peter-jerry-ye/async/stream.Writer)| |

|Type|description|
|---|---|
|[AsyncIterable](#AsyncIterable)||
|[BufferedReader](#BufferedReader)| A reader that buffers the input stream and provides line reading capabilities.|

|Value|description|
|---|---|
|[buffered\_reader](#buffered_reader)| Create a buffered reader from a reader|
|[input\_stream\_reader](#input_stream_reader)| Create a reader from an input stream through the given encoding.|
|[output\_stream\_writer](#output_stream_writer)| Create a writer from an output stream through the given encoding.|

## @peter-jerry-ye/async/stream.Closable

```moonbit
:::source,peter-jerry-ye/async/stream/types.mbt,16:::pub(open) trait @peter-jerry-ye/async/stream.Closable {
  closed(Self) -> Bool
  close(Self) -> Unit
}
```


## @peter-jerry-ye/async/stream.Flushable

```moonbit
:::source,peter-jerry-ye/async/stream/types.mbt,22:::pub(open) trait @peter-jerry-ye/async/stream.Flushable {
  flush(Self) -> <a href="peter-jerry-ye/async/promise#T">@peter-jerry-ye/async/promise.T</a>[Unit]
}
```


## @peter-jerry-ye/async/stream.InputStream

```moonbit
:::source,peter-jerry-ye/async/stream/types.mbt,30:::pub(open) trait @peter-jerry-ye/async/stream.InputStream : <a href="peter-jerry-ye/async/stream#Closable">Closable</a> {
  readable(Self) -> Bool
  read(Self, UInt64) -> <a href="peter-jerry-ye/async/promise#T">@peter-jerry-ye/async/promise.T</a>[Bytes]
}
```
 
 This trait represents an interface that provides the ability for low level async read operations.
 
 The `Self` here may represent a stream / file descriptor, or a stream / file descriptor + event loop.

## @peter-jerry-ye/async/stream.OutputStream

```moonbit
:::source,peter-jerry-ye/async/stream/types.mbt,39:::pub(open) trait @peter-jerry-ye/async/stream.OutputStream : <a href="peter-jerry-ye/async/stream#Closable">Closable</a> + <a href="peter-jerry-ye/async/stream#Flushable">Flushable</a> {
  writable(Self) -> Bool
  write(Self, Bytes) -> <a href="peter-jerry-ye/async/promise#T">@peter-jerry-ye/async/promise.T</a>[Unit]
}
```
 
 This trait represents an interface that provides the ability for low level async write operations.
 
 The `Self` here may represent a stream / file descriptor, or a stream / file descriptor + event loop.

## @peter-jerry-ye/async/stream.Reader

```moonbit
:::source,peter-jerry-ye/async/stream/types.mbt,48:::pub(open) trait @peter-jerry-ye/async/stream.Reader : <a href="peter-jerry-ye/async/stream#Closable">Closable</a> {
  readable(Self) -> Bool
  read(Self, UInt64) -> <a href="peter-jerry-ye/async/promise#T">@peter-jerry-ye/async/promise.T</a>[String]
}
```
 
 This trait represents an interface that provides the ability for async read operations based on Chars.
 
 The `Self` here may represent a stream / file descriptor, or a stream / file descriptor + event loop.

## @peter-jerry-ye/async/stream.Writer

```moonbit
:::source,peter-jerry-ye/async/stream/types.mbt,57:::pub(open) trait @peter-jerry-ye/async/stream.Writer : <a href="peter-jerry-ye/async/stream#Closable">Closable</a> + <a href="peter-jerry-ye/async/stream#Flushable">Flushable</a> {
  writable(Self) -> Bool
  write(Self, String) -> <a href="peter-jerry-ye/async/promise#T">@peter-jerry-ye/async/promise.T</a>[Unit]
}
```
 
 This trait represents an interface that provides the ability for async write operations based on Chars.
 
 The `Self` here may represent a stream / file descriptor, or a stream / file descriptor + event loop.

## AsyncIterable

```moonbit
:::source,peter-jerry-ye/async/stream/types.mbt,63:::pub(all) type AsyncIterable[T] () -> T!<a href="moonbitlang/core/error#Error">Error</a>
```


## BufferedReader

```moonbit
:::source,peter-jerry-ye/async/stream/buffered_reader.mbt,16:::pub struct BufferedReader {
  stream : <a href="peter-jerry-ye/async/stream#Reader">Reader</a>
  buffer : String
  offset : UInt
  len : UInt
}
```
 A reader that buffers the input stream and provides line reading capabilities.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,peter-jerry-ye/async/stream/buffered_reader.mbt,29:::impl <a href="peter-jerry-ye/async/stream#Closable">Closable</a> for <a href="peter-jerry-ye/async/stream#BufferedReader">BufferedReader</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/async/stream/buffered_reader.mbt,34:::fn close(self : <a href="peter-jerry-ye/async/stream#BufferedReader">BufferedReader</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,peter-jerry-ye/async/stream/buffered_reader.mbt,29:::fn closed(self : <a href="peter-jerry-ye/async/stream#BufferedReader">BufferedReader</a>) -> Bool
    ```
    > 
- ```moonbit
  :::source,peter-jerry-ye/async/stream/buffered_reader.mbt,42:::impl <a href="peter-jerry-ye/async/stream#Reader">Reader</a> for <a href="peter-jerry-ye/async/stream#BufferedReader">BufferedReader</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/async/stream/buffered_reader.mbt,47:::fn read(self : <a href="peter-jerry-ye/async/stream#BufferedReader">BufferedReader</a>, size : UInt64) -> <a href="peter-jerry-ye/async/promise#T">@peter-jerry-ye/async/promise.T</a>[String]
    ```
    > 
  * ```moonbit
    :::source,peter-jerry-ye/async/stream/buffered_reader.mbt,42:::fn readable(self : <a href="peter-jerry-ye/async/stream#BufferedReader">BufferedReader</a>) -> Bool
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### read\_line
  ```moonbit
  :::source,peter-jerry-ye/async/stream/buffered_reader.mbt,80:::fn <a href="peter-jerry-ye/async/stream#BufferedReader">BufferedReader</a>::read_line(self : <a href="peter-jerry-ye/async/stream#BufferedReader">BufferedReader</a>) -> <a href="peter-jerry-ye/async/promise#T">@peter-jerry-ye/async/promise.T</a>[String]
  ```
  > 

## buffered\_reader

```moonbit
:::source,peter-jerry-ye/async/stream/buffered_reader.mbt,24:::fn buffered_reader(stream : <a href="peter-jerry-ye/async/stream#Reader">Reader</a>) -> <a href="peter-jerry-ye/async/stream#BufferedReader">BufferedReader</a>
```
 Create a buffered reader from a reader

## input\_stream\_reader

```moonbit
:::source,peter-jerry-ye/async/stream/input_stream_reader.mbt,45:::fn input_stream_reader[T : <a href="peter-jerry-ye/async/stream#InputStream">InputStream</a> + <a href="peter-jerry-ye/async/stream#Closable">Closable</a>](stream : T, encoding~ : <a href="tonyfettes/encoding#Encoding">@tonyfettes/encoding.Encoding</a> = ..) -> <a href="peter-jerry-ye/async/stream#Reader">Reader</a>
```
 Create a reader from an input stream through the given encoding.

## output\_stream\_writer

```moonbit
:::source,peter-jerry-ye/async/stream/ouptut_stream_writer.mbt,47:::fn output_stream_writer[T : <a href="peter-jerry-ye/async/stream#OutputStream">OutputStream</a> + <a href="peter-jerry-ye/async/stream#Closable">Closable</a> + <a href="peter-jerry-ye/async/stream#Flushable">Flushable</a>](stream : T, encoding~ : <a href="tonyfettes/encoding#Encoding">@tonyfettes/encoding.Encoding</a> = ..) -> <a href="peter-jerry-ye/async/stream#Writer">Writer</a>
```
 Create a writer from an output stream through the given encoding.
