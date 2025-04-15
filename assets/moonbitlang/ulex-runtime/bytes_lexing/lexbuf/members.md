# Documentation
|Trait|description|
|---|---|
|[@moonbitlang/ulex-runtime/bytes\_lexing/lexbuf.Lexbuf](#@moonbitlang/ulex-runtime/bytes_lexing/lexbuf.Lexbuf)||

|Type|description|
|---|---|
|[BytesLexbuf](#BytesLexbuf)||

|Value|description|
|---|---|
|[from\_bytes](#from_bytes)||

## @moonbitlang/ulex-runtime/bytes\_lexing/lexbuf.Lexbuf

```moonbit
:::source,moonbitlang/ulex-runtime/bytes_lexing/lexbuf/lexbuf.mbt,1:::pub(open) trait @moonbitlang/ulex-runtime/bytes_lexing/lexbuf.Lexbuf {
  next(Self) -> Byte?
  curr_pos(Self) -> Int
  reset(Self, Int) -> Unit
  unsafe_get(Self, Int) -> Byte
  sub_lexeme(Self, Int, Int) -> <a href="moonbitlang/core/bytes#View">@moonbitlang/core/bytes.View</a>
}
```


## BytesLexbuf

```moonbit
:::source,moonbitlang/ulex-runtime/bytes_lexing/lexbuf/bytes_lexbuf.mbt,2:::type BytesLexbuf
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/ulex-runtime/bytes_lexing/lexbuf/bytes_lexbuf.mbt,18:::impl <a href="moonbitlang/ulex-runtime/bytes_lexing/lexbuf#Lexbuf">Lexbuf</a> for <a href="moonbitlang/ulex-runtime/bytes_lexing/lexbuf#BytesLexbuf">BytesLexbuf</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex-runtime/bytes_lexing/lexbuf/bytes_lexbuf.mbt,30:::fn curr_pos(self : <a href="moonbitlang/ulex-runtime/bytes_lexing/lexbuf#BytesLexbuf">BytesLexbuf</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/ulex-runtime/bytes_lexing/lexbuf/bytes_lexbuf.mbt,18:::fn next(self : <a href="moonbitlang/ulex-runtime/bytes_lexing/lexbuf#BytesLexbuf">BytesLexbuf</a>) -> Byte?
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/ulex-runtime/bytes_lexing/lexbuf/bytes_lexbuf.mbt,35:::fn reset(self : <a href="moonbitlang/ulex-runtime/bytes_lexing/lexbuf#BytesLexbuf">BytesLexbuf</a>, pos : Int) -> Unit
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/ulex-runtime/bytes_lexing/lexbuf/bytes_lexbuf.mbt,45:::fn sub_lexeme(self : <a href="moonbitlang/ulex-runtime/bytes_lexing/lexbuf#BytesLexbuf">BytesLexbuf</a>, start : Int, end : Int) -> <a href="moonbitlang/core/bytes#View">@moonbitlang/core/bytes.View</a>
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/ulex-runtime/bytes_lexing/lexbuf/bytes_lexbuf.mbt,40:::fn unsafe_get(self : <a href="moonbitlang/ulex-runtime/bytes_lexing/lexbuf#BytesLexbuf">BytesLexbuf</a>, pos : Int) -> Byte
    ```
    > 

## from\_bytes

```moonbit
:::source,moonbitlang/ulex-runtime/bytes_lexing/lexbuf/bytes_lexbuf.mbt,9:::fn from_bytes(bytes : Bytes, start~ : Int = .., end~ : Int = ..) -> <a href="moonbitlang/ulex-runtime/bytes_lexing/lexbuf#BytesLexbuf">BytesLexbuf</a>
```

