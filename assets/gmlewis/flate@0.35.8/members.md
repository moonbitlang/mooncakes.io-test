# gmlewis/flate
[![check](https://github.com/gmlewis/moonbit-flate/actions/workflows/check.yml/badge.svg)](https://github.com/gmlewis/moonbit-flate/actions/workflows/check.yml)

This is a simplified flate compression algorithm based on Go's implementation:
https://cs.opensource.google/go/go/+/refs/tags/go1.23.1:src/compress/flate/deflatefast.go
which has the copyright notice:

```
// Copyright 2016 The Go Authors. All rights reserved.
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
|Trait|description|
|---|---|
|[@gmlewis/flate.Reader](#@gmlewis/flate.Reader)||

|Type|description|
|---|---|
|[Decompressor](#Decompressor)||
|[DictWriter](#DictWriter)||
|[Writer](#Writer)||
|[Reader](#Reader)||

|Value|description|
|---|---|
|[ioeof](#ioeof)||
|[writer\_closed\_error](#writer_closed_error)||

## @gmlewis/flate.Reader

```moonbit
:::source,gmlewis/flate/inflate.mbt,224:::pub(open) trait @gmlewis/flate.Reader {
  read(Self, <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> (Int, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
  read_byte(Self) -> (Byte, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
}
```

 The actual read interface needed by \[Decompressor::new\].

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/flate/inflate.mbt,242:::impl <a href="gmlewis/flate#Reader">Reader</a> for <a href="gmlewis/io#Buffer">@gmlewis/io.Buffer</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/flate/inflate.mbt,242:::fn read(self : <a href="gmlewis/io#Buffer">@gmlewis/io.Buffer</a>, b : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> (Int, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
    ```
    > 
  * ```moonbit
    :::source,gmlewis/flate/inflate.mbt,247:::fn read_byte(self : <a href="gmlewis/io#Buffer">@gmlewis/io.Buffer</a>) -> (Byte, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
    ```
    > 

## Decompressor

```moonbit
:::source,gmlewis/flate/inflate.mbt,253:::type Decompressor
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/flate/inflate.mbt,407:::impl <a href="gmlewis/io#Closer">@gmlewis/io.Closer</a> for <a href="gmlewis/flate#Decompressor">Decompressor</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/flate/inflate.mbt,407:::fn close(self : <a href="gmlewis/flate#Decompressor">Decompressor</a>) -> <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?
    ```
    > 
- ```moonbit
  :::source,gmlewis/flate/inflate.mbt,379:::impl <a href="gmlewis/io#Reader">@gmlewis/io.Reader</a> for <a href="gmlewis/flate#Decompressor">Decompressor</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/flate/inflate.mbt,379:::fn read(self : <a href="gmlewis/flate#Decompressor">Decompressor</a>, b : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> (Int, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
    ```
    > 

## DictWriter

```moonbit
:::source,gmlewis/flate/writer.mbt,33:::type DictWriter
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/flate/writer.mbt,38:::impl <a href="gmlewis/io#Writer">@gmlewis/io.Writer</a> for <a href="gmlewis/flate#DictWriter">DictWriter</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/flate/writer.mbt,38:::fn write(self : <a href="gmlewis/flate#DictWriter">DictWriter</a>, b : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> (Int, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
    ```
    > 

## Writer

```moonbit
:::source,gmlewis/flate/writer.mbt,2:::type Writer
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/flate/writer.mbt,53:::impl <a href="gmlewis/io#Closer">@gmlewis/io.Closer</a> for <a href="gmlewis/flate#Writer">Writer</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/flate/writer.mbt,53:::fn close(self : <a href="gmlewis/flate#Writer">Writer</a>) -> <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?
    ```
    > 
    >  `close` closes the input to the flate Writer.
    > After closing the Writer, the compressed data can be read
    > from the `@io.Writer` provided to `new`.
- ```moonbit
  :::source,gmlewis/flate/writer.mbt,44:::impl <a href="gmlewis/io#Writer">@gmlewis/io.Writer</a> for <a href="gmlewis/flate#Writer">Writer</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/flate/writer.mbt,44:::fn write(self : <a href="gmlewis/flate#Writer">Writer</a>, data : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> (Int, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
    ```
    > 
    >  `write` writes the provided data to the flate Writer.

#### mooncakes-io-method-mark-Methods
- #### new
  ```moonbit
  :::source,gmlewis/flate/writer.mbt,10:::fn <a href="gmlewis/flate#Writer">Writer</a>::new(buf : <a href="gmlewis/io#Writer">@gmlewis/io.Writer</a>) -> <a href="gmlewis/flate#Writer">Writer</a>
  ```
  > 
  >  `Writer::new` returns a new \[@io.WriteCloser\] compressing data at the "BestSpeed" level.
  > It writes its (compressed) data to the provided `buf`.
- #### new\_dict
  ```moonbit
  :::source,gmlewis/flate/writer.mbt,24:::fn <a href="gmlewis/flate#Writer">Writer</a>::new_dict(w : <a href="gmlewis/io#Writer">@gmlewis/io.Writer</a>, dict : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> <a href="gmlewis/flate#Writer">Writer</a>
  ```
  > 

## ioeof

```moonbit
:::source,gmlewis/flate/inflate.mbt,19:::let ioeof : <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>
```


## writer\_closed\_error

```moonbit
:::source,gmlewis/flate/deflate.mbt,151:::let writer_closed_error : <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>
```


## Reader


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/flate/inflate.mbt,237:::impl <a href="gmlewis/io#ByteReader">@gmlewis/io.ByteReader</a> for <a href="gmlewis/flate#Reader">Reader</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/flate/inflate.mbt,237:::fn read_byte(self : <a href="gmlewis/flate#Reader">Reader</a>) -> (Byte, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
    ```
    > 
- ```moonbit
  :::source,gmlewis/flate/inflate.mbt,232:::impl <a href="gmlewis/io#Reader">@gmlewis/io.Reader</a> for <a href="gmlewis/flate#Reader">Reader</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/flate/inflate.mbt,232:::fn read(self : <a href="gmlewis/flate#Reader">Reader</a>, b : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> (Int, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### new
  ```moonbit
  :::source,gmlewis/flate/inflate.mbt,301:::fn <a href="gmlewis/flate#Reader">Reader</a>::new(r : <a href="gmlewis/flate#Reader">Reader</a>) -> <a href="gmlewis/flate#Decompressor">Decompressor</a>
  ```
  > 
  >  `Reader::new` returns a new \[@io.ReadCloser\] that can be used
  > to read the uncompressed version of r.
- #### new\_dict
  ```moonbit
  :::source,gmlewis/flate/inflate.mbt,311:::fn <a href="gmlewis/flate#Reader">Reader</a>::new_dict(r : <a href="gmlewis/flate#Reader">Reader</a>, dict : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> <a href="gmlewis/flate#Decompressor">Decompressor</a>
  ```
  > 
  >  `Reader::new_dict` is like \[NewReader\] but initializes the reader
  > with a preset dictionary. The returned \[Reader\] behaves as if
  > the uncompressed data stream started with the given dictionary,
  > which has already been read. NewReaderDict is typically used
  > to read data compressed by NewWriterDict.
