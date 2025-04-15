WASI I/O is an I/O abstraction API which is currently focused on providing
stream types.

In the future, the component model is expected to add built-in stream types;
when it does, they are expected to subsume this API.
---
# Documentation
|Type|description|
|---|---|
|[InputStream](#InputStream)||
|[OutputStream](#OutputStream)||
|[StreamError](#StreamError)||

## InputStream

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,19:::pub(all) type InputStream Int
```

 An input bytestream.

 `input-stream`s are *non-blocking* to the extent practical on underlying
platforms. I/O operations always return promptly; if fewer bytes are
promptly available than requested, they return the number of bytes promptly
available, which could even be zero. To wait for data to be available,
use the `subscribe` function to obtain a `pollable` which can be polled
for using `wasi:io/poll`.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,19:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">InputStream</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,19:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">InputStream</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">InputStream</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,19:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">InputStream</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,19:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">InputStream</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### blocking\_read
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,110:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">InputStream</a>::blocking_read(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">InputStream</a>, len : UInt64) -> <a href="moonbitlang/core/result#Result">Result</a>[Bytes, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#StreamError">StreamError</a>]
  ```
  > 
  >  Read bytes from a stream, after blocking until at least one byte can
  > be read. Except for blocking, behavior is identical to `read`.
- #### blocking\_skip
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,179:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">InputStream</a>::blocking_skip(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">InputStream</a>, len : UInt64) -> <a href="moonbitlang/core/result#Result">Result</a>[UInt64, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#StreamError">StreamError</a>]
  ```
  > 
  >  Skip bytes from a stream, after blocking until at least one byte
  > can be skipped. Except for blocking behavior, identical to `skip`.
- #### drop
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,25:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">InputStream</a>::drop(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">InputStream</a>) -> Unit
  ```
  > 
- #### read
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,75:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">InputStream</a>::read(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">InputStream</a>, len : UInt64) -> <a href="moonbitlang/core/result#Result">Result</a>[Bytes, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#StreamError">StreamError</a>]
  ```
  > 
  >  Perform a non-blocking read from the stream.
  > 
  >  When the source of a `read` is binary data, the bytes from the source
  > are returned verbatim. When the source of a `read` is known to the
  > implementation to be text, bytes containing the UTF-8 encoding of the
  > text are returned.
  > 
  >  This function returns a list of bytes containing the read data,
  > when successful. The returned list will contain up to `len` bytes;
  > it may return fewer than requested, but not more. The list is
  > empty when no bytes are available for reading at this time. The
  > pollable given by `subscribe` will be ready when more bytes are
  > available.
  > 
  >  This function fails with a `stream-error` when the operation
  > encounters an error, giving `last-operation-failed`, or when the
  > stream is closed, giving `closed`.
  > 
  >  When the caller gives a `len` of 0, it represents a request to
  > read 0 bytes. If the stream is still open, this call should
  > succeed and return an empty list, or otherwise fail with `closed`.
  > 
  >  The `len` parameter is a `u64`, which could represent a list of u8 which
  > is not possible to allocate in wasm32, or not desirable to allocate as
  > as a return value by the callee. The callee may return a list of bytes
  > less than `len` in size while more bytes are available for reading.
- #### skip
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,147:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">InputStream</a>::skip(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">InputStream</a>, len : UInt64) -> <a href="moonbitlang/core/result#Result">Result</a>[UInt64, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#StreamError">StreamError</a>]
  ```
  > 
  >  Skip bytes from a stream. Returns number of bytes skipped.
  > 
  >  Behaves identical to `read`, except instead of returning a list
  > of bytes, returns the number of bytes consumed from the stream.
- #### subscribe
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,215:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">InputStream</a>::subscribe(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">InputStream</a>) -> <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll#Pollable">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll.Pollable</a>
  ```
  > 
  >  Create a `pollable` which will resolve once either the specified stream
  > has bytes available to read or the other end of the stream has been
  > closed.
  > The created `pollable` is a child resource of the `input-stream`.
  > Implementations may trap if the `input-stream` is dropped before
  > all derived `pollable`s created with this function are dropped.

## OutputStream

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,38:::pub(all) type OutputStream Int
```

 An output bytestream.

 `output-stream`s are *non-blocking* to the extent practical on
underlying platforms. Except where specified otherwise, I/O operations also
always return promptly, after the number of bytes that can be written
promptly, which could even be zero. To wait for the stream to be ready to
accept data, the `subscribe` function to obtain a `pollable` which can be
polled for using `wasi:io/poll`.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,38:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,38:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,38:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,38:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### blocking\_flush
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,391:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>::blocking_flush(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#StreamError">StreamError</a>]
  ```
  > 
  >  Request to flush buffered output, and block until flush completes
  > and stream is ready for writing again.
- #### blocking\_splice
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,572:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>::blocking_splice(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>, src : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">InputStream</a>, len : UInt64) -> <a href="moonbitlang/core/result#Result">Result</a>[UInt64, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#StreamError">StreamError</a>]
  ```
  > 
  >  Read from one stream and write to another, with blocking.
  > 
  >  This is similar to `splice`, except that it blocks until the
  > `output-stream` is ready for writing, and the `input-stream`
  > is ready for reading, before performing the `splice`.
- #### blocking\_write\_and\_flush
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,324:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>::blocking_write_and_flush(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>, contents : Bytes) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#StreamError">StreamError</a>]
  ```
  > 
  >  Perform a write of up to 4096 bytes, and then flush the stream. Block
  > until all of these operations are complete, or an error occurs.
  > 
  >  This is a convenience wrapper around the use of `check-write`,
  > `subscribe`, `write`, and `flush`, and is implemented with the
  > following pseudo-code:
  > 
  >  ```text
  >  let pollable = this.subscribe();
  >  while !contents.is_empty() {
  >  // Wait for the stream to become writable
  >  pollable.block();
  >  let Ok(n) = this.check-write(); // eliding error handling
  >  let len = min(n, contents.len());
  >  let (chunk, rest) = contents.split_at(len);
  >  this.write(chunk  );            // eliding error handling
  >  contents = rest;
  >  }
  >  this.flush();
  >  // Wait for completion of `flush`
  >  pollable.block();
  >  // Check for any errors that arose during `flush`
  >  let _ = this.check-write();         // eliding error handling
  >  ```
- #### blocking\_write\_zeroes\_and\_flush
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,492:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>::blocking_write_zeroes_and_flush(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>, len : UInt64) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#StreamError">StreamError</a>]
  ```
  > 
  >  Perform a write of up to 4096 zeroes, and then flush the stream.
  > Block until all of these operations are complete, or an error
  > occurs.
  > 
  >  This is a convenience wrapper around the use of `check-write`,
  > `subscribe`, `write-zeroes`, and `flush`, and is implemented with
  > the following pseudo-code:
  > 
  >  ```text
  >  let pollable = this.subscribe();
  >  while num_zeroes != 0 {
  >  // Wait for the stream to become writable
  >  pollable.block();
  >  let Ok(n) = this.check-write(); // eliding error handling
  >  let len = min(n, num_zeroes);
  >  this.write-zeroes(len);         // eliding error handling
  >  num_zeroes -= len;
  >  }
  >  this.flush();
  >  // Wait for completion of `flush`
  >  pollable.block();
  >  // Check for any errors that arose during `flush`
  >  let _ = this.check-write();         // eliding error handling
  >  ```
- #### check\_write
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,230:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>::check_write(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[UInt64, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#StreamError">StreamError</a>]
  ```
  > 
  >  Check readiness for writing. This function never blocks.
  > 
  >  Returns the number of bytes permitted for the next call to `write`,
  > or an error. Calling `write` with more bytes than this function has
  > permitted will trap.
  > 
  >  When this function returns 0 bytes, the `subscribe` pollable will
  > become ready when this function will report at least 1 byte, or an
  > error.
- #### drop
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,44:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>::drop(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>) -> Unit
  ```
  > 
- #### flush
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,366:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>::flush(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#StreamError">StreamError</a>]
  ```
  > 
  >  Request to flush buffered output. This function never blocks.
  > 
  >  This tells the output-stream that the caller intends any buffered
  > output to be flushed. the output which is expected to be flushed
  > is all that has been passed to `write` prior to this call.
  > 
  >  Upon calling this function, the `output-stream` will not accept any
  > writes (`check-write` will return `ok(0)`) until the flush has
  > completed. The `subscribe` pollable will become ready when the
  > flush has completed and the stream can accept more writes.
- #### splice
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,535:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>::splice(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>, src : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">InputStream</a>, len : UInt64) -> <a href="moonbitlang/core/result#Result">Result</a>[UInt64, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#StreamError">StreamError</a>]
  ```
  > 
  >  Read from one stream and write to another.
  > 
  >  The behavior of splice is equivelant to:
  >  1. calling `check-write` on the `output-stream`
  >  2. calling `read` on the `input-stream` with the smaller of the
  >     `check-write` permitted length and the `len` provided to `splice`
  >  3. calling `write` on the `output-stream` with that read data.
  > 
  >  Any error reported by the call to `check-write`, `read`, or
  > `write` ends the splice and reports that error.
  > 
  >  This function returns the number of bytes transferred; it may be less
  > than `len`.
- #### subscribe
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,426:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>::subscribe(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>) -> <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll#Pollable">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll.Pollable</a>
  ```
  > 
  >  Create a `pollable` which will resolve once the output-stream
  > is ready for more writing, or an error has occured. When this
  > pollable is ready, `check-write` will return `ok(n)` with n\>0, or an
  > error.
  > 
  >  If the stream is closed, this pollable is always ready immediately.
  > 
  >  The created `pollable` is a child resource of the `output-stream`.
  > Implementations may trap if the `output-stream` is dropped before
  > all derived `pollable`s created with this function are dropped.
- #### write
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,268:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>::write(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>, contents : Bytes) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#StreamError">StreamError</a>]
  ```
  > 
  >  Perform a write. This function never blocks.
  > 
  >  When the destination of a `write` is binary data, the bytes from
  > `contents` are written verbatim. When the destination of a `write` is
  > known to the implementation to be text, the bytes of `contents` are
  > transcoded from UTF-8 into the encoding of the destination and then
  > written.
  > 
  >  Precondition: check-write gave permit of Ok(n) and contents has a
  > length of less than or equal to n. Otherwise, this function will trap.
  > 
  >  returns Err(closed) without writing if the stream has closed since
  > the last call to check-write provided a permit.
- #### write\_zeroes
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,438:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>::write_zeroes(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">OutputStream</a>, len : UInt64) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#StreamError">StreamError</a>]
  ```
  > 
  >  Write zeroes to a stream.
  > 
  >  This should be used precisely like `write` with the exact same
  > preconditions (must use check-write first), but instead of
  > passing a list of bytes, you simply pass the number of zero-bytes
  > that should be written.

## StreamError

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,5:::pub(all) enum StreamError {
  LastOperationFailed(<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/error#Error_">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/error.Error_</a>)
  Closed
}
```

 An error for input-stream and output-stream operations.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,8:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#StreamError">StreamError</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,8:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#StreamError">StreamError</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#StreamError">StreamError</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,8:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#StreamError">StreamError</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams/top.mbt,8:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#StreamError">StreamError</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
