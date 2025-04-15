# gmlewis/base64
[![check](https://github.com/gmlewis/moonbit-base64/actions/workflows/check.yml/badge.svg)](https://github.com/gmlewis/moonbit-base64/actions/workflows/check.yml)

This is a simple base64 encoder based on Go's implementation:
https://cs.opensource.google/go/go/+/master:src/encoding/base64/base64.go
which has the copyright notice:

```
// Copyright 2009 The Go Authors. All rights reserved.
// Use of this source code is governed by a BSD-style
// license that can be found in the LICENSE file.
```

The UTF-16 / UTF-8 encoder/decoders are provided with permission by
@peter-jerry-ye from this repo: https://github.com/peter-jerry-ye/jstream

## Status

The code has been updated to support compiler:

```bash
$ moon version --all
moon 0.1.20250401 (f09c49c 2025-04-01) ~/.moon/bin/moon
moonc v0.1.20250401+b666cddf8 ~/.moon/bin/moonc
moonrun 0.1.20250401 (f09c49c 2025-04-01) ~/.moon/bin/moonrun
```

---
# Documentation
|Type|description|
|---|---|
|[CorruptInputError](#CorruptInputError)||

|Value|description|
|---|---|
|[array2str](#array2str)||
|[bytes2str](#bytes2str)||
|[std\_decode2bytes](#std_decode2bytes)||
|[std\_decode2str](#std_decode2str)||
|[std\_encode2bytes](#std_encode2bytes)||
|[std\_encode2str](#std_encode2str)||
|[str2array](#str2array)||
|[str2bytes](#str2bytes)||
|[url\_decode2bytes](#url_decode2bytes)||
|[url\_decode2str](#url_decode2str)||
|[url\_encode2bytes](#url_encode2bytes)||
|[url\_encode2str](#url_encode2str)||

## CorruptInputError

```moonbit
:::source,gmlewis/base64/base64-decode.mbt,8:::pub(all) type! CorruptInputError String

```

 This package is based on the Go implementation found here:
https://cs.opensource.google/go/go/+/master:src/encoding/base64/base64.go
which has the copyright notice:
Copyright 2009 The Go Authors. All rights reserved.
Use of this source code is governed by a BSD-style
license that can be found in the LICENSE file.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/base64/base64-decode.mbt,8:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/base64#CorruptInputError">CorruptInputError</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/base64/base64-decode.mbt,8:::fn output(<a href="gmlewis/base64#CorruptInputError">CorruptInputError</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## array2str

```moonbit
:::source,gmlewis/base64/bytes-2-str.mbt,37:::fn array2str(b : <a href="moonbitlang/core/array#ArrayView">ArrayView</a>[Byte]) -> String
```

 `array2str` decodes a UTF-8 `ArrayView[Byte]` to a UTF-16 `String`.
This is a more convenient version of `bytes2str` for when you have an `ArrayView[Byte]`.
If you have an `Array[Byte]`, you can use `array2str(arr[:])`.

 Examples:
 ```
 let arr = b"+/ Hello, 世界! 🌍".to_array()
 inspect!(array2str(arr[:]), content="+/ Hello, 世界! 🌍")
 ```

## bytes2str

```moonbit
:::source,gmlewis/base64/bytes-2-str.mbt,8:::fn bytes2str(b : Bytes) -> String
```

 `bytes2str` decodes a UTF-8 `Bytes` to a UTF-16 `String`.

 Examples:
 ```
 inspect!(bytes2str("+/ Hello, 世界! 🌍"), content="+/ Hello, 世界! 🌍")
 ```

## std\_decode2bytes

```moonbit
:::source,gmlewis/base64/base64-decode.mbt,22:::fn std_decode2bytes(src : String, no_padding~ : Bool = ..) -> Bytes!<a href="gmlewis/base64#CorruptInputError">CorruptInputError</a>
```

 `std_decode2bytes` base64-decodes the provided bytes using Standard encoding.
Setting `no_padding=true` is used for raw decoding.

 Note that standard encoding uses `+` and `/` characters whereas URL encoding uses `-` and `_`.

 Examples:
 ```
 let b = "+/ Hello, 世界! 🌍"
 inspect!(std_decode2bytes!("Ky8gSGVsbG8sIOS4lueVjCEg8J+MjQ==") |> bytes2str(), content=b)
 inspect!(std_decode2bytes!("Ky8gSGVsbG8sIOS4lueVjCEg8J+MjQ", no_padding=true) |> bytes2str(), content=b)
 ```

## std\_decode2str

```moonbit
:::source,gmlewis/base64/base64-decode.mbt,47:::fn std_decode2str(src : String, no_padding~ : Bool = ..) -> String!<a href="gmlewis/base64#CorruptInputError">CorruptInputError</a>
```

 `std_decode2str` base64-decodes the provided bytes using Standard encoding and returns a String.
Setting `no_padding=true` is used for raw decoding.

 Note that standard encoding uses `+` and `/` characters whereas URL encoding uses `-` and `_`.

 Examples:
 ```
 let b = "+/ Hello, 世界! 🌍"
 inspect!(std_decode2str!("Ky8gSGVsbG8sIOS4lueVjCEg8J+MjQ=="), content=b)
 inspect!(std_decode2str!("Ky8gSGVsbG8sIOS4lueVjCEg8J+MjQ", no_padding=true), content=b)
 ```

## std\_encode2bytes

```moonbit
:::source,gmlewis/base64/base64-encode.mbt,20:::fn std_encode2bytes(src : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Byte], no_padding~ : Bool = ..) -> Bytes
```

 `std_encode2bytes` base64-encodes the provided bytes using Standard encoding.
Setting `no_padding=true` is used for raw encoding.

 Note that standard encoding uses `+` and `/` characters whereas URL encoding uses `-` and `_`.

 Examples:
 ```
 let b : Bytes = "+/ Hello, 世界! 🌍"
 inspect!(std_encode2bytes(b.to_fixedarray()) |> bytes2str(), content="Ky8gSGVsbG8sIOS4lueVjCEg8J+MjQ==")
 inspect!(std_encode2bytes(b.to_fixedarray(), no_padding=true) |> bytes2str(), content="Ky8gSGVsbG8sIOS4lueVjCEg8J+MjQ")
 ```

## std\_encode2str

```moonbit
:::source,gmlewis/base64/base64-encode.mbt,44:::fn std_encode2str(src : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Byte], no_padding~ : Bool = ..) -> String
```

 `std_encode2str` base64-encodes the provided bytes using Standard encoding and returns a String.
Setting `no_padding=true` is used for raw encoding.

 Note that standard encoding uses `+` and `/` characters whereas URL encoding uses `-` and `_`.

 Examples:
 ```
 let b : Bytes = "+/ Hello, 世界! 🌍"
 inspect!(std_encode2str(b.to_fixedarray()), content="Ky8gSGVsbG8sIOS4lueVjCEg8J+MjQ==")
 inspect!(std_encode2str(b.to_fixedarray(), no_padding=true), content="Ky8gSGVsbG8sIOS4lueVjCEg8J+MjQ")
 ```

## str2array

```moonbit
:::source,gmlewis/base64/str-2-bytes.mbt,39:::fn str2array(s : String) -> <a href="moonbitlang/core/array#Array">Array</a>[Byte]
```

 `str2array` encodes a UTF-16 `String` as a UTF-8 `Array[Byte]`.
This is a more convenient version of `str2bytes` for when you want an `Array[Byte]`.

 Examples:
 ```
 inspect!(str2array("🌍"), content="[b'\\xF0', b'\\x9F', b'\\x8C', b'\\x8D']")
 ```

## str2bytes

```moonbit
:::source,gmlewis/base64/str-2-bytes.mbt,10:::fn str2bytes(s : String) -> Bytes
```

 `str2bytes` encodes a UTF-16 `String` as a UTF-8 `Bytes`.

 Examples:
 ```
 inspect!(str2bytes("+/ Hello, 世界! 🌍"), content=
   #|b"\x2b\x2f\x20\x48\x65\x6c\x6c\x6f\x2c\x20\xe4\xb8\x96\xe7\x95\x8c\x21\x20\xf0\x9f\x8c\x8d"
 )
 ```

## url\_decode2bytes

```moonbit
:::source,gmlewis/base64/base64-decode.mbt,66:::fn url_decode2bytes(src : String, no_padding~ : Bool = ..) -> Bytes!<a href="gmlewis/base64#CorruptInputError">CorruptInputError</a>
```

 `url_decode2bytes` base64-decodes the provided bytes using URL encoding.
Setting `no_padding=true` is used for raw decoding.

 Note that standard encoding uses `+` and `/` characters whereas URL encoding uses `-` and `_`.

 Examples:
 ```
 let b = "+/ Hello, 世界! 🌍"
 inspect!(url_decode2bytes!("Ky8gSGVsbG8sIOS4lueVjCEg8J-MjQ==") |> bytes2str(), content=b)
 inspect!(url_decode2bytes!("Ky8gSGVsbG8sIOS4lueVjCEg8J-MjQ", no_padding=true) |> bytes2str(), content=b)
 ```

## url\_decode2str

```moonbit
:::source,gmlewis/base64/base64-decode.mbt,91:::fn url_decode2str(src : String, no_padding~ : Bool = ..) -> String!<a href="gmlewis/base64#CorruptInputError">CorruptInputError</a>
```

 `url_decode2str` base64-decodes the provided bytes using URL encoding and returns a String.
Setting `no_padding=true` is used for raw decoding.

 Note that standard encoding uses `+` and `/` characters whereas URL encoding uses `-` and `_`.

 Examples:
 ```
 let b = "+/ Hello, 世界! 🌍"
 inspect!(url_decode2str!("Ky8gSGVsbG8sIOS4lueVjCEg8J-MjQ=="), content=b)
 inspect!(url_decode2str!("Ky8gSGVsbG8sIOS4lueVjCEg8J-MjQ", no_padding=true), content=b)
 ```

## url\_encode2bytes

```moonbit
:::source,gmlewis/base64/base64-encode.mbt,63:::fn url_encode2bytes(src : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Byte], no_padding~ : Bool = ..) -> Bytes
```

 `url_encode2bytes` base64-encodes the provided bytes using URL encoding.
Setting `no_padding=true` is used for raw encoding.

 Note that standard encoding uses `+` and `/` characters whereas URL encoding uses `-` and `_`.

 Examples:
 ```
 let b : Bytes = "+/ Hello, 世界! 🌍"
 inspect!(url_encode2bytes(b.to_fixedarray()) |> bytes2str(), content="Ky8gSGVsbG8sIOS4lueVjCEg8J-MjQ==")
 inspect!(url_encode2bytes(b.to_fixedarray(), no_padding=true) |> bytes2str(), content="Ky8gSGVsbG8sIOS4lueVjCEg8J-MjQ")
 ```

## url\_encode2str

```moonbit
:::source,gmlewis/base64/base64-encode.mbt,87:::fn url_encode2str(src : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Byte], no_padding~ : Bool = ..) -> String
```

 `url_encode2str` base64-encodes the provided bytes using URL encoding and returns a String.
Setting `no_padding=true` is used for raw encoding.

 Note that standard encoding uses `+` and `/` characters whereas URL encoding uses `-` and `_`.

 Examples:
 ```
 let b : Bytes = "+/ Hello, 世界! 🌍"
 inspect!(url_encode2str(b.to_fixedarray()), content="Ky8gSGVsbG8sIOS4lueVjCEg8J-MjQ==")
 inspect!(url_encode2str(b.to_fixedarray(), no_padding=true), content="Ky8gSGVsbG8sIOS4lueVjCEg8J-MjQ")
 ```
