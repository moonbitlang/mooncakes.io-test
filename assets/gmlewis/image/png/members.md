# Documentation
|Type|description|
|---|---|
|[Decoder](#Decoder)||
|[Encoder](#Encoder)||

|Value|description|
|---|---|
|[chunk\_order\_error](#chunk_order_error)||
|[decode](#decode)||
|[decode\_config](#decode_config)||
|[enc](#enc)||
|[encode](#encode)||
|[err\_negative\_read](#err_negative_read)||
|[write](#write)||

## Decoder

```moonbit
:::source,gmlewis/image/png/reader.mbt,163:::type Decoder
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/png/reader.mbt,459:::impl <a href="gmlewis/io#Reader">@gmlewis/io.Reader</a> for <a href="gmlewis/image/png#Decoder">Decoder</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/png/reader.mbt,459:::fn read(self : <a href="gmlewis/image/png#Decoder">Decoder</a>, p : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> (Int, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
    ```
    > 
    >  Read presents one or more IDAT chunks as one continuous stream (minus the
    > intermediate chunk headers and footers). If the PNG data looked like:
    > 
    >     ... len0 IDAT xxx crc0 len1 IDAT yy crc1 len2 IEND crc2
    > 
    >  then this reader presents xxxyy. For well-formed PNG data, the decoder state
    > immediately before the first Read call is that d.r is positioned between the
    > first IDAT and xxx, and the decoder state immediately after the last Read
    > call is that d.r is positioned between yy and crc1.

## Encoder

```moonbit
:::source,gmlewis/image/png/writer.mbt,10:::type Encoder
```

 Encoder encodes PNG images.

#### mooncakes-io-method-mark-Methods
- #### enc
  ```moonbit
  :::source,gmlewis/image/png/writer.mbt,553:::fn <a href="gmlewis/image/png#Encoder">Encoder</a>::enc(self : <a href="gmlewis/image/png#Encoder">Encoder</a>, w : <a href="gmlewis/io#Writer">@gmlewis/io.Writer</a>, m : <a href="gmlewis/image#Image">@gmlewis/image.Image</a>) -> <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?
  ```
  > 
  >  enc writes the Image m to w in PNG format.
- #### write
  ```moonbit
  :::source,gmlewis/image/png/writer.mbt,182:::fn <a href="gmlewis/image/png#Encoder">Encoder</a>::write(self : <a href="gmlewis/image/png#Encoder">Encoder</a>, b : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> (Int, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
  ```
  > 
  >  An Encoder is an io.Writer that satisfies writes by writing PNG IDAT chunks,
  > including an 8-byte header and 4-byte CRC checksum per write call. Such calls
  > should be relatively infrequent, since write\_idats uses a \[io.Buffer\].
  > 
  >  This method should only be called from write\_idats (via write\_image).
  > No other code should treat an Encoder as an io.Writer.

## chunk\_order\_error

```moonbit
:::source,gmlewis/image/png/reader.mbt,220:::let chunk_order_error : <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>
```


## decode

```moonbit
:::source,gmlewis/image/png/reader.mbt,1238:::fn decode(r : <a href="gmlewis/io#Reader">@gmlewis/io.Reader</a>) -> (<a href="gmlewis/image#Image">@gmlewis/image.Image</a>, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
```

 decode reads a PNG image from r and returns it as an \[image.Image\].
The type of Image returned depends on the PNG contents.

## decode\_config

```moonbit
:::source,gmlewis/image/png/reader.mbt,1262:::fn decode_config(r : <a href="gmlewis/io#Reader">@gmlewis/io.Reader</a>) -> (<a href="gmlewis/image#Config">@gmlewis/image.Config</a>, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
```

 decode\_config returns the color model and dimensions of a PNG image without
decoding the entire image.

## enc

```moonbit
:::source,gmlewis/image/png/writer.mbt,553:::fn enc(self : <a href="gmlewis/image/png#Encoder">Encoder</a>, w : <a href="gmlewis/io#Writer">@gmlewis/io.Writer</a>, m : <a href="gmlewis/image#Image">@gmlewis/image.Image</a>) -> <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?
```

 enc writes the Image m to w in PNG format.

## encode

```moonbit
:::source,gmlewis/image/png/writer.mbt,546:::fn encode(w : <a href="gmlewis/io#Writer">@gmlewis/io.Writer</a>, m : <a href="gmlewis/image#Image">@gmlewis/image.Image</a>) -> <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?
```


## err\_negative\_read

```moonbit
:::source,gmlewis/image/png/bufio.mbt,58:::let err_negative_read : <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>
```


## write

```moonbit
:::source,gmlewis/image/png/writer.mbt,182:::fn write(self : <a href="gmlewis/image/png#Encoder">Encoder</a>, b : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]) -> (Int, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
```

 An Encoder is an io.Writer that satisfies writes by writing PNG IDAT chunks,
including an 8-byte header and 4-byte CRC checksum per write call. Such calls
should be relatively infrequent, since write\_idats uses a \[io.Buffer\].

 This method should only be called from write\_idats (via write\_image).
No other code should treat an Encoder as an io.Writer.
