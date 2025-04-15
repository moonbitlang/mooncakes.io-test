# Documentation
|Type|description|
|---|---|
|[BytesLexbuf](#BytesLexbuf)||
|[Lexbuf](#Lexbuf)||
|[LexbufClass](#LexbufClass)||
|[StringLexbuf](#StringLexbuf)||
|[Class](#Class)||
|[T](#T)||

|Value|description|
|---|---|
|[from\_bytes](#from_bytes)||
|[from\_string](#from_string)||

## BytesLexbuf

```moonbit
:::source,moonbitlang/ulex-runtime/lexbuf/bytes_lexbuf.mbt,2:::type BytesLexbuf
```


## Lexbuf

```moonbit
:::source,moonbitlang/ulex-runtime/lexbuf/lexbuf.mbt,17:::pub(all) type Lexbuf[T, C, S, P] (<a href="moonbitlang/ulex-runtime/lexbuf#LexbufClass">LexbufClass</a>[T, C, S, P], T)
```


#### mooncakes-io-method-mark-Methods
- #### curr\_pos
  ```moonbit
  :::source,moonbitlang/ulex-runtime/lexbuf/lexbuf.mbt,62:::fn <a href="moonbitlang/ulex-runtime/lexbuf#Lexbuf">Lexbuf</a>::curr_pos[T, C, S, P](self : <a href="moonbitlang/ulex-runtime/lexbuf#Lexbuf">Lexbuf</a>[T, C, S, P]) -> P
  ```
  > 
- #### next
  ```moonbit
  :::source,moonbitlang/ulex-runtime/lexbuf/lexbuf.mbt,56:::fn <a href="moonbitlang/ulex-runtime/lexbuf#Lexbuf">Lexbuf</a>::next[T, C, S, P](self : <a href="moonbitlang/ulex-runtime/lexbuf#Lexbuf">Lexbuf</a>[T, C, S, P]) -> Char?
  ```
  > 
- #### reset
  ```moonbit
  :::source,moonbitlang/ulex-runtime/lexbuf/lexbuf.mbt,68:::fn <a href="moonbitlang/ulex-runtime/lexbuf#Lexbuf">Lexbuf</a>::reset[T, C, S, P](self : <a href="moonbitlang/ulex-runtime/lexbuf#Lexbuf">Lexbuf</a>[T, C, S, P], pos : P) -> Unit
  ```
  > 
- #### sub\_lexeme
  ```moonbit
  :::source,moonbitlang/ulex-runtime/lexbuf/lexbuf.mbt,80:::fn <a href="moonbitlang/ulex-runtime/lexbuf#Lexbuf">Lexbuf</a>::sub_lexeme[T, C, S, P](self : <a href="moonbitlang/ulex-runtime/lexbuf#Lexbuf">Lexbuf</a>[T, C, S, P], start : P, end : P) -> S
  ```
  > 
- #### unsafe\_get
  ```moonbit
  :::source,moonbitlang/ulex-runtime/lexbuf/lexbuf.mbt,74:::fn <a href="moonbitlang/ulex-runtime/lexbuf#Lexbuf">Lexbuf</a>::unsafe_get[T, C, S, P](self : <a href="moonbitlang/ulex-runtime/lexbuf#Lexbuf">Lexbuf</a>[T, C, S, P], pos : P) -> C
  ```
  > 

## LexbufClass

```moonbit
:::source,moonbitlang/ulex-runtime/lexbuf/lexbuf.mbt,8:::pub(all) struct LexbufClass[T, C, S, P] {
  next : (T) -> Char?
  curr_pos : (T) -> P
  reset : (T, P) -> Unit
  unsafe_get : (T, P) -> C
  sub_lexeme : (T, P, P) -> S
}
```


## StringLexbuf

```moonbit
:::source,moonbitlang/ulex-runtime/lexbuf/string_lexbuf.mbt,2:::type StringLexbuf
```


## Class

```moonbit
:::source,moonbitlang/ulex-runtime/lexbuf/lexbuf.mbt,2:::type Class[T, C, S, P] = <a href="moonbitlang/ulex-runtime/lexbuf#LexbufClass">LexbufClass</a>[T, C, S, P]
```


## T

```moonbit
:::source,moonbitlang/ulex-runtime/lexbuf/lexbuf.mbt,5:::type T[T, C, S, P] = <a href="moonbitlang/ulex-runtime/lexbuf#Lexbuf">Lexbuf</a>[T, C, S, P]
```


## from\_bytes

```moonbit
:::source,moonbitlang/ulex-runtime/lexbuf/lexbuf.mbt,47:::fn from_bytes(bytes : Bytes, start~ : Int = .., end~ : Int = ..) -> <a href="moonbitlang/ulex-runtime/lexbuf#Lexbuf">Lexbuf</a>[<a href="moonbitlang/ulex-runtime/lexbuf#BytesLexbuf">BytesLexbuf</a>, Byte, <a href="moonbitlang/core/bytes#View">@moonbitlang/core/bytes.View</a>, Int]
```


## from\_string

```moonbit
:::source,moonbitlang/ulex-runtime/lexbuf/lexbuf.mbt,38:::fn from_string(str : String, start~ : Int = .., end~ : Int = ..) -> <a href="moonbitlang/ulex-runtime/lexbuf#Lexbuf">Lexbuf</a>[<a href="moonbitlang/ulex-runtime/lexbuf#StringLexbuf">StringLexbuf</a>, Char, String, Int]
```

