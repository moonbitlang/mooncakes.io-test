# gmlewis/gzip
[![check](https://github.com/gmlewis/moonbit-gzip/actions/workflows/check.yml/badge.svg)](https://github.com/gmlewis/moonbit-gzip/actions/workflows/check.yml)

This is a simplified gzip/gunzip algorithm based on Go's implementation:
https://cs.opensource.google/go/go/+/refs/tags/go1.23.0:src/compress/gzip/gzip.go
which has the copyright notice:

```
// Copyright 2010 The Go Authors. All rights reserved.
// Use of this source code is governed by a BSD-style
// license that can be found in the LICENSE file.
```

## Status

The code has been updated to support compiler:

```bash
$ moon version --all
moon 0.1.20250407 (24afaca 2025-04-07) ~/.moon/bin/moon
moonc v0.1.20250410+15d580434 ~/.moon/bin/moonc
moonrun 0.1.20250407 (24afaca 2025-04-07) ~/.moon/bin/moonrun
```

---
# Documentation
|Type|description|
|---|---|
|[CompressionLevel](#CompressionLevel)||
|[Header](#Header)||
|[Reader](#Reader)||
|[Writer](#Writer)||

|Value|description|
|---|---|
|[best\_speed](#best_speed)||
|[err\_checksum](#err_checksum)||
|[err\_header](#err_header)||
|[err\_unexpected\_eof](#err_unexpected_eof)||
|[flush](#flush)||
|[ioeof](#ioeof)||
|[multistream](#multistream)||
|[reset](#reset)||

## CompressionLevel

```moonbit
:::source,gmlewis/gzip/gzip.mbt,11:::pub(all) type CompressionLevel Int
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/gzip/gzip.mbt,11:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for <a href="gmlewis/gzip#CompressionLevel">CompressionLevel</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/gzip/gzip.mbt,11:::fn compare(<a href="gmlewis/gzip#CompressionLevel">CompressionLevel</a>, <a href="gmlewis/gzip#CompressionLevel">CompressionLevel</a>) -> Int
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/gzip/gzip.mbt,11:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/gzip#CompressionLevel">CompressionLevel</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/gzip/gzip.mbt,11:::fn op_equal(<a href="gmlewis/gzip#CompressionLevel">CompressionLevel</a>, <a href="gmlewis/gzip#CompressionLevel">CompressionLevel</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/gzip/gzip.mbt,11:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/gzip#CompressionLevel">CompressionLevel</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/gzip/gzip.mbt,11:::fn output(<a href="gmlewis/gzip#CompressionLevel">CompressionLevel</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## Header

```moonbit
:::source,gmlewis/gzip/gunzip.mbt,70:::pub(all) struct Header {
  comment : String
  extra : <a href="moonbitlang/core/array#Array">Array</a>[Byte]
  mod_time : <a href="moonbitlang/x/time#PlainDateTime">@moonbitlang/x/time.PlainDateTime</a>?
  name : String
  os : Byte
}
```

 The gzip file stores a header giving metadata about the compressed file.
That header is exposed as the fields of the \[Writer\] and \[Reader\] structs.

 Strings must be UTF-8 encoded and may only contain Unicode code points
U+0001 through U+00FF, due to limitations of the GZIP file format.

#### mooncakes-io-method-mark-Methods
- #### new
  ```moonbit
  :::source,gmlewis/gzip/gunzip.mbt,79:::fn <a href="gmlewis/gzip#Header">Header</a>::new() -> <a href="gmlewis/gzip#Header">Header</a>
  ```
  > 

## Reader

```moonbit
:::source,gmlewis/gzip/gunzip.mbt,98:::pub(all) struct Reader {
  header : <a href="gmlewis/gzip#Header">Header</a>
  // private fields
}
```

 A Reader is an \[IOReadCloser\] that can be read to retrieve
uncompressed data from a gzip-format compressed file.

 In general, a gzip file can be a concatenation of gzip files,
each with its own header. Reads from the Reader
return the concatenation of the uncompressed data of each.
Only the first header is recorded in the Reader fields.

 Gzip files store a length and checksum of the uncompressed data.
The Reader will return an \[err\_checksum\] when \[Reader.Read\]
reaches the end of the uncompressed data if it does not
have the expected length or checksum. Clients should treat data
returned by \[Reader.Read\] as tentative until they receive the \[ioeof\]
marking the end of the data.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/gzip/gunzip.mbt,432:::impl <a href="gmlewis/io#Closer">@gmlewis/io.Closer</a> for <a href="gmlewis/gzip#Reader">Reader</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/gzip/gunzip.mbt,432:::fn close(self : <a href="gmlewis/gzip#Reader">Reader</a>) -> <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?
    ```
    > 
    >  Close closes the \[Reader\]. It does not close the underlying \[io.Reader\].
    > In order for the GZIP checksum to be verified, the reader must be
    > fully consumed until the \[ioeof\].
- ```moonbit
  :::source,gmlewis/gzip/gunzip.mbt,371:::impl <a href="gmlewis/io#Reader">@gmlewis/io.Reader</a> for <a href="gmlewis/gzip#Reader">Reader</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/gzip/gunzip.mbt,371:::fn read(self : <a href="gmlewis/gzip#Reader">Reader</a>, p : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> (Int, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
    ```
    > 
    >  Read implements \[IOReadCloser\], reading uncompressed bytes from its underlying \[Reader\].

#### mooncakes-io-method-mark-Methods
- #### multistream
  ```moonbit
  :::source,gmlewis/gzip/gunzip.mbt,170:::fn <a href="gmlewis/gzip#Reader">Reader</a>::multistream(self : <a href="gmlewis/gzip#Reader">Reader</a>, ok : Bool) -> Unit
  ```
  > 
  >  Multistream controls whether the reader supports multistream files.
  > 
  >  If enabled (the default), the \[Reader\] expects the input to be a sequence
  > of individually gzipped data streams, each with its own header and
  > trailer, ending at EOF. The effect is that the concatenation of a sequence
  > of gzipped files is treated as equivalent to the gzip of the concatenation
  > of the sequence. This is standard behavior for gzip readers.
  > 
  >  Calling Multistream(false) disables this behavior; disabling the behavior
  > can be useful when reading file formats that distinguish individual gzip
  > data streams or mix gzip data streams with other data streams.
  > In this mode, when the \[Reader\] reaches the end of the data stream,
  > \[Reader.Read\] returns \[ioeof\]. The underlying reader must implement \[io.ByteReader\]
  > in order to be left positioned just after the gzip stream.
  > To start the next stream, call self.Reset(r) followed by self.Multistream(false).
  > If there is no next stream, self.Reset(r) will return \[ioeof\].
- #### new
  ```moonbit
  :::source,gmlewis/gzip/gunzip.mbt,122:::fn <a href="gmlewis/gzip#Reader">Reader</a>::new(r : <a href="gmlewis/flate#Reader">@gmlewis/flate.Reader</a>) -> (<a href="gmlewis/gzip#Reader">Reader</a>, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
  ```
  > 
  >  NewReader creates a new \[IOReader\] reading the given reader.
  > 
  >  It is the caller's responsibility to call Close on the \[Reader\] when done.
  > 
  >  The \[Reader.Header\] fields will be valid in the \[Reader\] returned.
- #### reset
  ```moonbit
  :::source,gmlewis/gzip/gunzip.mbt,141:::fn <a href="gmlewis/gzip#Reader">Reader</a>::reset(self : <a href="gmlewis/gzip#Reader">Reader</a>, r : <a href="gmlewis/flate#Reader">@gmlewis/flate.Reader</a>) -> <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?
  ```
  > 
  >  Reset discards the \[Reader\] z's state and makes it equivalent to the
  > result of its original state from \[NewReader\], but reading from r instead.
  > This permits reusing a \[Reader\] rather than allocating a new one.

## Writer

```moonbit
:::source,gmlewis/gzip/gzip.mbt,26:::pub(all) struct Writer {
  header : <a href="gmlewis/gzip#Header">Header</a>
  w : <a href="gmlewis/io#Writer">@gmlewis/io.Writer</a>
  level : <a href="gmlewis/gzip#CompressionLevel">CompressionLevel</a>
  wrote_header : Bool
  closed : Bool
  buf : <a href="moonbitlang/core/array#Array">Array</a>[Byte]
  compressor : <a href="gmlewis/io#WriteCloser">@gmlewis/io.WriteCloser</a>
  digest : UInt
  size : UInt
  err : <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?
}
```

 Writes to a Writer are compressed and written to w.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/gzip/gzip.mbt,259:::impl <a href="gmlewis/io#Closer">@gmlewis/io.Closer</a> for <a href="gmlewis/gzip#Writer">Writer</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/gzip/gzip.mbt,259:::fn close(self : <a href="gmlewis/gzip#Writer">Writer</a>) -> <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?
    ```
    > 
    >  close closes the \[Writer\] by flushing any unwritten data to the underlying
    > \[io.Writer\] and writing the GZIP footer.
    > It does not close the underlying \[io.Writer\].
- ```moonbit
  :::source,gmlewis/gzip/gzip.mbt,145:::impl <a href="gmlewis/io#Writer">@gmlewis/io.Writer</a> for <a href="gmlewis/gzip#Writer">Writer</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/gzip/gzip.mbt,145:::fn write(self : <a href="gmlewis/gzip#Writer">Writer</a>, p : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> (Int, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### flush
  ```moonbit
  :::source,gmlewis/gzip/gzip.mbt,240:::fn <a href="gmlewis/gzip#Writer">Writer</a>::flush(self : <a href="gmlewis/gzip#Writer">Writer</a>) -> <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?
  ```
  > 
  >  flush flushes any pending compressed data to the underlying writer.
  > 
  >  It is useful mainly in compressed network protocols, to ensure that
  > a remote reader has enough data to reconstruct a packet. Flush does
  > not return until the data has been written. If the underlying
  > writer returns an error, Flush returns that error.
  > 
  >  In the terminology of the zlib library, Flush is equivalent to Z\_SYNC\_FLUSH.
- #### new
  ```moonbit
  :::source,gmlewis/gzip/gzip.mbt,54:::fn <a href="gmlewis/gzip#Writer">Writer</a>::new(w : <a href="gmlewis/io#Writer">@gmlewis/io.Writer</a>) -> <a href="gmlewis/gzip#Writer">Writer</a>
  ```
  > 
  >  Writer::new returns a new \[IOWriter\] using the optional compression level
  > (or `default_compression`).
  > Writes to the returned writer are compressed and written to w.
  > 
  >  It is the caller's responsibility to call Close on the \[Writer\] when done.
  > Writes may be buffered and not flushed until Close.
  > 
  >  Callers that wish to set the fields in Writer.Header must do so before
  > the first call to Write, Flush, or Close.

## best\_speed

```moonbit
:::source,gmlewis/gzip/gzip.mbt,20:::let best_speed : <a href="gmlewis/gzip#CompressionLevel">CompressionLevel</a>
```


## err\_checksum

```moonbit
:::source,gmlewis/gzip/gunzip.mbt,43:::let err_checksum : <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>
```

 err\_checksum is returned when reading GZIP data that has an invalid checksum.

## err\_header

```moonbit
:::source,gmlewis/gzip/gunzip.mbt,47:::let err_header : <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>
```

 err\_header is returned when reading GZIP data that has an invalid header.

## err\_unexpected\_eof

```moonbit
:::source,gmlewis/gzip/gunzip.mbt,50:::let err_unexpected_eof : <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>
```


## flush

```moonbit
:::source,gmlewis/gzip/gzip.mbt,240:::fn flush(self : <a href="gmlewis/gzip#Writer">Writer</a>) -> <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?
```

 flush flushes any pending compressed data to the underlying writer.

 It is useful mainly in compressed network protocols, to ensure that
a remote reader has enough data to reconstruct a packet. Flush does
not return until the data has been written. If the underlying
writer returns an error, Flush returns that error.

 In the terminology of the zlib library, Flush is equivalent to Z\_SYNC\_FLUSH.

## ioeof

```moonbit
:::source,gmlewis/gzip/gunzip.mbt,53:::let ioeof : <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>
```


## multistream

```moonbit
:::source,gmlewis/gzip/gunzip.mbt,170:::fn multistream(self : <a href="gmlewis/gzip#Reader">Reader</a>, ok : Bool) -> Unit
```

 Multistream controls whether the reader supports multistream files.

 If enabled (the default), the \[Reader\] expects the input to be a sequence
of individually gzipped data streams, each with its own header and
trailer, ending at EOF. The effect is that the concatenation of a sequence
of gzipped files is treated as equivalent to the gzip of the concatenation
of the sequence. This is standard behavior for gzip readers.

 Calling Multistream(false) disables this behavior; disabling the behavior
can be useful when reading file formats that distinguish individual gzip
data streams or mix gzip data streams with other data streams.
In this mode, when the \[Reader\] reaches the end of the data stream,
\[Reader.Read\] returns \[ioeof\]. The underlying reader must implement \[io.ByteReader\]
in order to be left positioned just after the gzip stream.
To start the next stream, call self.Reset(r) followed by self.Multistream(false).
If there is no next stream, self.Reset(r) will return \[ioeof\].

## reset

```moonbit
:::source,gmlewis/gzip/gunzip.mbt,141:::fn reset(self : <a href="gmlewis/gzip#Reader">Reader</a>, r : <a href="gmlewis/flate#Reader">@gmlewis/flate.Reader</a>) -> <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?
```

 Reset discards the \[Reader\] z's state and makes it equivalent to the
result of its original state from \[NewReader\], but reading from r instead.
This permits reusing a \[Reader\] rather than allocating a new one.
