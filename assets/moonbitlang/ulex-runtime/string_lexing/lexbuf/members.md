# Documentation
|Trait|description|
|---|---|
|[@moonbitlang/ulex-runtime/string\_lexing/lexbuf.Lexbuf](#@moonbitlang/ulex-runtime/string_lexing/lexbuf.Lexbuf)||

## @moonbitlang/ulex-runtime/string\_lexing/lexbuf.Lexbuf

```moonbit
:::source,moonbitlang/ulex-runtime/string_lexing/lexbuf/lexbuf.mbt,1:::pub(open) trait @moonbitlang/ulex-runtime/string_lexing/lexbuf.Lexbuf {
  next(Self) -> Char?
  curr_pos(Self) -> Int
  reset(Self, Int) -> Unit
  unsafe_get(Self, Int) -> Char
  sub_lexeme(Self, Int, Int) -> <a href="moonbitlang/core/string#StringView">@moonbitlang/core/string.StringView</a>
}
```

