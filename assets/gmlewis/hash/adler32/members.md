# Documentation
|Type|description|
|---|---|
|[Digest](#Digest)||

|Value|description|
|---|---|
|[checksum](#checksum)||
|[marshal\_binary](#marshal_binary)||
|[new](#new)||
|[unmarshal\_binary](#unmarshal_binary)||

## Digest

```moonbit
:::source,gmlewis/hash/adler32/adler32.mbt,40:::type Digest
```

 Digest represents the partial evaluation of a checksum.
The low 16 bits are s1, the high 16 bits are s2.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/hash/adler32/adler32.mbt,45:::impl <a href="gmlewis/hash#Hash32">@gmlewis/hash.Hash32</a> for <a href="gmlewis/hash/adler32#Digest">Digest</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/hash/adler32/adler32.mbt,69:::fn block_size(_self : <a href="gmlewis/hash/adler32#Digest">Digest</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/hash/adler32/adler32.mbt,45:::fn reset(self : <a href="gmlewis/hash/adler32#Digest">Digest</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,gmlewis/hash/adler32/adler32.mbt,64:::fn size(_self : <a href="gmlewis/hash/adler32#Digest">Digest</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/hash/adler32/adler32.mbt,160:::fn sum(self : <a href="gmlewis/hash/adler32#Digest">Digest</a>, p : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
    ```
    > 
  * ```moonbit
    :::source,gmlewis/hash/adler32/adler32.mbt,155:::fn sum32(self : <a href="gmlewis/hash/adler32#Digest">Digest</a>) -> UInt
    ```
    > 
  * ```moonbit
    :::source,gmlewis/hash/adler32/adler32.mbt,121:::fn write(self : <a href="gmlewis/hash/adler32#Digest">Digest</a>, p : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> (Int, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
    ```
    > 
    >  Add p to the running checksum d.

#### mooncakes-io-method-mark-Methods
- #### marshal\_binary
  ```moonbit
  :::source,gmlewis/hash/adler32/adler32.mbt,80:::fn <a href="gmlewis/hash/adler32#Digest">Digest</a>::marshal_binary(self : <a href="gmlewis/hash/adler32#Digest">Digest</a>) -> (<a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte], <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
  ```
  > 
- #### unmarshal\_binary
  ```moonbit
  :::source,gmlewis/hash/adler32/adler32.mbt,108:::fn <a href="gmlewis/hash/adler32#Digest">Digest</a>::unmarshal_binary(self : <a href="gmlewis/hash/adler32#Digest">Digest</a>, b : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?
  ```
  > 

## checksum

```moonbit
:::source,gmlewis/hash/adler32/adler32.mbt,172:::fn checksum(data : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> UInt
```

 checksum returns the Adler-32 checksum of data.

## marshal\_binary

```moonbit
:::source,gmlewis/hash/adler32/adler32.mbt,80:::fn marshal_binary(self : <a href="gmlewis/hash/adler32#Digest">Digest</a>) -> (<a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte], <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
```


## new

```moonbit
:::source,gmlewis/hash/adler32/adler32.mbt,55:::fn new() -> <a href="gmlewis/hash/adler32#Digest">Digest</a>
```

 New returns a new hash.Hash32 computing the Adler-32 checksum. Its
Sum method will lay the value out in big-endian byte order. The
returned Hash32 also implements \[encoding.BinaryMarshaler\] and
\[encoding.BinaryUnmarshaler\] to marshal and unmarshal the internal
state of the hash.

## unmarshal\_binary

```moonbit
:::source,gmlewis/hash/adler32/adler32.mbt,108:::fn unmarshal_binary(self : <a href="gmlewis/hash/adler32#Digest">Digest</a>, b : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?
```

