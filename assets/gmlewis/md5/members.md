# gmlewis/md5
[![check](https://github.com/gmlewis/moonbit-md5/actions/workflows/check.yml/badge.svg)](https://github.com/gmlewis/moonbit-md5/actions/workflows/check.yml)

This is a simple md5 hash algorithm based on Go's implementation:
https://cs.opensource.google/go/go/+/refs/tags/go1.23.0:src/crypto/md5/md5.go
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
|Trait|description|
|---|---|
|[@gmlewis/md5.HashFunc](#@gmlewis/md5.HashFunc)||

|Type|description|
|---|---|
|[Digest](#Digest)||

|Value|description|
|---|---|
|[reset](#reset)||

## @gmlewis/md5.HashFunc

```moonbit
:::source,gmlewis/md5/hash-func.mbt,3:::pub(open) trait @gmlewis/md5.HashFunc {
  name(Self) -> String
  write(Self, Byte) -> Unit
  check_sum(Self) -> String
}
```

 `HashFunc` represents a hash algorithm like `@crc32`, `@md5`, or `@sha256`.

## Digest

```moonbit
:::source,gmlewis/md5/md5.mbt,30:::type Digest
```

 `Digest` represents the partial evaluation of a checksum.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/md5/md5.mbt,57:::impl <a href="gmlewis/md5#HashFunc">HashFunc</a> for <a href="gmlewis/md5#Digest">Digest</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/md5/md5.mbt,63:::fn check_sum(self : <a href="gmlewis/md5#Digest">Digest</a>) -> String
    ```
    > 
    >  `check_sum` returns the final md5sum as a hex string.
  * ```moonbit
    :::source,gmlewis/md5/md5.mbt,57:::fn name(self : <a href="gmlewis/md5#Digest">Digest</a>) -> String
    ```
    > 
  * ```moonbit
    :::source,gmlewis/md5/md5.mbt,110:::fn write(self : <a href="gmlewis/md5#Digest">Digest</a>, b : Byte) -> Unit
    ```
    > 
    >  `write` writes a byte to the digest.

#### mooncakes-io-method-mark-Methods
- #### new
  ```moonbit
  :::source,gmlewis/md5/md5.mbt,42:::fn <a href="gmlewis/md5#Digest">Digest</a>::new() -> <a href="gmlewis/md5#Digest">Digest</a>
  ```
  > 
  >  `Digest::new` returns a new, reset Digest, ready to sum.
- #### reset
  ```moonbit
  :::source,gmlewis/md5/md5.mbt,99:::fn <a href="gmlewis/md5#Digest">Digest</a>::reset(self : <a href="gmlewis/md5#Digest">Digest</a>) -> Unit
  ```
  > 
  >  `reset` resets a digest for re-use.

## reset

```moonbit
:::source,gmlewis/md5/md5.mbt,99:::fn reset(self : <a href="gmlewis/md5#Digest">Digest</a>) -> Unit
```

 `reset` resets a digest for re-use.
