# Documentation
|Type|description|
|---|---|
|[ParseError](#ParseError)||
|[Token](#Token)||
|[TokenKind](#TokenKind)||
|[Position](#Position)||

|Value|description|
|---|---|
|[lex\_eoi](#lex_eoi)||
|[parse\_lex\_from\_string](#parse_lex_from_string)||
|[parse\_regex\_from\_string](#parse_regex_from_string)||
|[regex\_eoi](#regex_eoi)||

## ParseError

```moonbit
:::source,moonbitlang/ulex/lib/parser/parser.mbt,127:::pub enum ParseError {
  UnexpectedToken(<a href="moonbitlang/ulex/lib/parser#Token">Token</a>, (Unit, Unit), <a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/ulex/lib/parser#TokenKind">TokenKind</a>])
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/ulex/lib/parser/parser.mbt,129:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/ulex/lib/parser#ParseError">ParseError</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/parser/parser.mbt,129:::fn output(<a href="moonbitlang/ulex/lib/parser#ParseError">ParseError</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## Token

```moonbit
:::source,moonbitlang/ulex/lib/parser/parser.mbt,9:::pub(all) enum Token {
  EOI
  EOF
  PARSE_LBRACE
  LET
  AS
  UNDERSCORE
  RBRACE
  LPAREN
  RPAREN
  LBRACKET
  RBRACKET
  EQ
  SEMICOLON
  FAT_ARROW
  BAR
  STAR
  PLUS
  QUESTION
  MINUS
  CARET
  RULE_LC_IDENT_LPAREN_CODE_RPAREN_ARROW_CODE_LBRACE((String, String))
  LBRACE_CODE_RBRACE(String)
  LC_IDENT(String)
  CHAR(Char)
  STRING(String)
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/ulex/lib/parser/parser.mbt,35:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/ulex/lib/parser#Token">Token</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/parser/parser.mbt,35:::fn output(<a href="moonbitlang/ulex/lib/parser#Token">Token</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### kind
  ```moonbit
  :::source,moonbitlang/ulex/lib/parser/parser.mbt,37:::fn <a href="moonbitlang/ulex/lib/parser#Token">Token</a>::kind(self : <a href="moonbitlang/ulex/lib/parser#Token">Token</a>) -> <a href="moonbitlang/ulex/lib/parser#TokenKind">TokenKind</a>
  ```
  > 

## TokenKind

```moonbit
:::source,moonbitlang/ulex/lib/parser/parser.mbt,67:::pub(all) enum TokenKind {
  TK_EOI
  TK_EOF
  TK_PARSE_LBRACE
  TK_LET
  TK_AS
  TK_UNDERSCORE
  TK_RBRACE
  TK_LPAREN
  TK_RPAREN
  TK_LBRACKET
  TK_RBRACKET
  TK_EQ
  TK_SEMICOLON
  TK_FAT_ARROW
  TK_BAR
  TK_STAR
  TK_PLUS
  TK_QUESTION
  TK_MINUS
  TK_CARET
  TK_RULE_LC_IDENT_LPAREN_CODE_RPAREN_ARROW_CODE_LBRACE
  TK_LBRACE_CODE_RBRACE
  TK_LC_IDENT
  TK_CHAR
  TK_STRING
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/ulex/lib/parser/parser.mbt,95:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/ulex/lib/parser#TokenKind">TokenKind</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/parser/parser.mbt,95:::fn output(self : <a href="moonbitlang/ulex/lib/parser#TokenKind">TokenKind</a>, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 

## Position

```moonbit
:::source,moonbitlang/ulex/lib/parser/parser.mbt,7:::type Position = Unit
```


## lex\_eoi

```moonbit
:::source,moonbitlang/ulex/lib/parser/parser.mbt,1429:::fn lex_eoi(read_token : () -> (<a href="moonbitlang/ulex/lib/parser#Token">Token</a>, Unit, Unit), start_pos : Unit) -> <a href="moonbitlang/ulex/lib/type#Lex">@moonbitlang/ulex/lib/type.Lex</a>!<a href="moonbitlang/ulex/lib/parser#ParseError">ParseError</a>
```


## parse\_lex\_from\_string

```moonbit
:::source,moonbitlang/ulex/lib/parser/parse.mbt,2:::fn parse_lex_from_string(input : String) -> <a href="moonbitlang/ulex/lib/type#Lex">@moonbitlang/ulex/lib/type.Lex</a>!<a href="moonbitlang/ulex/lib/parser#ParseError">ParseError</a>
```


## parse\_regex\_from\_string

```moonbit
:::source,moonbitlang/ulex/lib/parser/parse.mbt,14:::fn parse_regex_from_string(input : String) -> <a href="moonbitlang/ulex/lib/type#Regex">@moonbitlang/ulex/lib/type.Regex</a>!<a href="moonbitlang/ulex/lib/parser#ParseError">ParseError</a>
```


## regex\_eoi

```moonbit
:::source,moonbitlang/ulex/lib/parser/parser.mbt,1440:::fn regex_eoi(read_token : () -> (<a href="moonbitlang/ulex/lib/parser#Token">Token</a>, Unit, Unit), start_pos : Unit) -> <a href="moonbitlang/ulex/lib/type#Regex">@moonbitlang/ulex/lib/type.Regex</a>!<a href="moonbitlang/ulex/lib/parser#ParseError">ParseError</a>
```

