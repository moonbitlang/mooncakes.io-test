# Documentation
|Type|description|
|---|---|
|[BytesLexbuf](#BytesLexbuf)||
|[T](#T)||

|Value|description|
|---|---|
|[from\_bytes](#from_bytes)||

## BytesLexbuf

```moonbit
:::source,moonbitlang/ulex/tests/bytes_test/lexbuf/lexbuf.mbt,2:::type BytesLexbuf
```


#### mooncakes-io-method-mark-Methods
- #### curr\_pos
  ```moonbit
  :::source,moonbitlang/ulex/tests/bytes_test/lexbuf/lexbuf.mbt,33:::fn <a href="moonbitlang/ulex/tests/bytes_test/lexbuf#BytesLexbuf">BytesLexbuf</a>::curr_pos(self : <a href="moonbitlang/ulex/tests/bytes_test/lexbuf#BytesLexbuf">BytesLexbuf</a>) -> Int
  ```
  > 
- #### next
  ```moonbit
  :::source,moonbitlang/ulex/tests/bytes_test/lexbuf/lexbuf.mbt,21:::fn <a href="moonbitlang/ulex/tests/bytes_test/lexbuf#BytesLexbuf">BytesLexbuf</a>::next(self : <a href="moonbitlang/ulex/tests/bytes_test/lexbuf#BytesLexbuf">BytesLexbuf</a>) -> Byte?
  ```
  > 
- #### reset
  ```moonbit
  :::source,moonbitlang/ulex/tests/bytes_test/lexbuf/lexbuf.mbt,38:::fn <a href="moonbitlang/ulex/tests/bytes_test/lexbuf#BytesLexbuf">BytesLexbuf</a>::reset(self : <a href="moonbitlang/ulex/tests/bytes_test/lexbuf#BytesLexbuf">BytesLexbuf</a>, pos : Int) -> Unit
  ```
  > 
- #### sub\_lexeme
  ```moonbit
  :::source,moonbitlang/ulex/tests/bytes_test/lexbuf/lexbuf.mbt,48:::fn <a href="moonbitlang/ulex/tests/bytes_test/lexbuf#BytesLexbuf">BytesLexbuf</a>::sub_lexeme(self : <a href="moonbitlang/ulex/tests/bytes_test/lexbuf#BytesLexbuf">BytesLexbuf</a>, start : Int, end : Int) -> <a href="moonbitlang/core/bytes#View">@moonbitlang/core/bytes.View</a>
  ```
  > 
- #### unsafe\_get
  ```moonbit
  :::source,moonbitlang/ulex/tests/bytes_test/lexbuf/lexbuf.mbt,43:::fn <a href="moonbitlang/ulex/tests/bytes_test/lexbuf#BytesLexbuf">BytesLexbuf</a>::unsafe_get(self : <a href="moonbitlang/ulex/tests/bytes_test/lexbuf#BytesLexbuf">BytesLexbuf</a>, pos : Int) -> Byte
  ```
  > 

## T

```moonbit
:::source,moonbitlang/ulex/tests/bytes_test/lexbuf/lexbuf.mbt,9:::type T = <a href="moonbitlang/ulex/tests/bytes_test/lexbuf#BytesLexbuf">BytesLexbuf</a>
```


## from\_bytes

```moonbit
:::source,moonbitlang/ulex/tests/bytes_test/lexbuf/lexbuf.mbt,12:::fn from_bytes(bytes : Bytes, start~ : Int = .., end~ : Int = ..) -> <a href="moonbitlang/ulex/tests/bytes_test/lexbuf#BytesLexbuf">BytesLexbuf</a>
```

