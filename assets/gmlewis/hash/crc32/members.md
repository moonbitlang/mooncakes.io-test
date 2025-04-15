# Documentation
|Type|description|
|---|---|
|[Digest](#Digest)||

|Value|description|
|---|---|
|[new](#new)||

## Digest

```moonbit
:::source,gmlewis/hash/crc32/crc32.mbt,10:::type Digest
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/hash/crc32/crc32.mbt,26:::impl <a href="gmlewis/hash#Hash32">@gmlewis/hash.Hash32</a> for <a href="gmlewis/hash/crc32#Digest">Digest</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/hash/crc32/crc32.mbt,64:::fn block_size(_self : <a href="gmlewis/hash/crc32#Digest">Digest</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/hash/crc32/crc32.mbt,54:::fn reset(self : <a href="gmlewis/hash/crc32#Digest">Digest</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,gmlewis/hash/crc32/crc32.mbt,59:::fn size(_self : <a href="gmlewis/hash/crc32#Digest">Digest</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/hash/crc32/crc32.mbt,42:::fn sum(self : <a href="gmlewis/hash/crc32#Digest">Digest</a>, p : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
    ```
    > 
  * ```moonbit
    :::source,gmlewis/hash/crc32/crc32.mbt,26:::fn sum32(self : <a href="gmlewis/hash/crc32#Digest">Digest</a>) -> UInt
    ```
    > 
    >  `sum32` returns the final crc32 as a UInt.
  * ```moonbit
    :::source,gmlewis/hash/crc32/crc32.mbt,32:::fn write(self : <a href="gmlewis/hash/crc32#Digest">Digest</a>, p : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> (Int, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
    ```
    > 
    >  `write` writes `p` to the digest.

## new

```moonbit
:::source,gmlewis/hash/crc32/crc32.mbt,16:::fn new() -> <a href="gmlewis/hash/crc32#Digest">Digest</a>
```

 `new` returns a new, reset Digest, ready to sum.
