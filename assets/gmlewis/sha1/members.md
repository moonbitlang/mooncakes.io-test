# gmlewis/sha1
[![check](https://github.com/gmlewis/moonbit-sha1/actions/workflows/check.yml/badge.svg)](https://github.com/gmlewis/moonbit-sha1/actions/workflows/check.yml)

This is a simple sha1 hash algorithm based on Go's implementation:
https://cs.opensource.google/go/go/+/refs/tags/go1.23.0:src/crypto/sha1/sha1.go
which has the copyright notice:

```
// Copyright 2009 The Go Authors. All rights reserved.
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
|[Digest](#Digest)||

|Value|description|
|---|---|
|[check\_sum](#check_sum)||
|[reset](#reset)||

## Digest

```moonbit
:::source,gmlewis/sha1/sha1.mbt,36:::type Digest
```

 `Digest` represents the partial evaluation of a checksum.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/sha1/sha1.mbt,130:::impl <a href="gmlewis/io#ByteWriter">@gmlewis/io.ByteWriter</a> for <a href="gmlewis/sha1#Digest">Digest</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/sha1/sha1.mbt,130:::fn write_byte(self : <a href="gmlewis/sha1#Digest">Digest</a>, b : Byte) -> <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?
    ```
    > 
    >  `write_byte` writes a byte to the digest.
- ```moonbit
  :::source,gmlewis/sha1/sha1.mbt,119:::impl <a href="gmlewis/io#Writer">@gmlewis/io.Writer</a> for <a href="gmlewis/sha1#Digest">Digest</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/sha1/sha1.mbt,119:::fn write(self : <a href="gmlewis/sha1#Digest">Digest</a>, buf : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> (Int, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
    ```
    > 
    >  `write` writes a slice of bytes to the digest.

#### mooncakes-io-method-mark-Methods
- #### check\_sum
  ```moonbit
  :::source,gmlewis/sha1/sha1.mbt,56:::fn <a href="gmlewis/sha1#Digest">Digest</a>::check_sum(self : <a href="gmlewis/sha1#Digest">Digest</a>) -> String
  ```
  > 
  >  `check_sum` returns the final sha1sum as a hex string.
- #### new
  ```moonbit
  :::source,gmlewis/sha1/sha1.mbt,45:::fn <a href="gmlewis/sha1#Digest">Digest</a>::new() -> <a href="gmlewis/sha1#Digest">Digest</a>
  ```
  > 
  >  `Digest::new` returns a new, reset Digest, ready to sum.
- #### reset
  ```moonbit
  :::source,gmlewis/sha1/sha1.mbt,104:::fn <a href="gmlewis/sha1#Digest">Digest</a>::reset(self : <a href="gmlewis/sha1#Digest">Digest</a>) -> Unit
  ```
  > 
  >  `reset` resets a digest for re-use.

## check\_sum

```moonbit
:::source,gmlewis/sha1/sha1.mbt,56:::fn check_sum(self : <a href="gmlewis/sha1#Digest">Digest</a>) -> String
```

 `check_sum` returns the final sha1sum as a hex string.

## reset

```moonbit
:::source,gmlewis/sha1/sha1.mbt,104:::fn reset(self : <a href="gmlewis/sha1#Digest">Digest</a>) -> Unit
```

 `reset` resets a digest for re-use.
