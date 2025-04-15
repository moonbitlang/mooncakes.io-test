# Documentation
|Type|description|
|---|---|
|[LexEngine](#LexEngine)||
|[T](#T)||

|Value|description|
|---|---|
|[run](#run)||

## LexEngine

```moonbit
:::source,moonbitlang/ulex/tests/bytes_test/lexengine/lexengine.mbt,5:::pub(all) struct LexEngine {
  graph : <a href="moonbitlang/core/array#Array">Array</a>[(Int) -> (Int, <a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/core/array#Array">Array</a>[Int]])]
  end_nodes : <a href="moonbitlang/core/array#Array">Array</a>[(Int, <a href="moonbitlang/core/array#Array">Array</a>[((Int, Int), (Int, Int))])?]
  start_tags : <a href="moonbitlang/core/array#Array">Array</a>[Int]
  code_blocks_n : Int
}
```


#### mooncakes-io-method-mark-Methods
- #### run
  ```moonbit
  :::source,moonbitlang/ulex/tests/bytes_test/lexengine/lexengine.mbt,14:::fn <a href="moonbitlang/ulex/tests/bytes_test/lexengine#LexEngine">LexEngine</a>::run(self : <a href="moonbitlang/ulex/tests/bytes_test/lexengine#LexEngine">LexEngine</a>, lexbuf : <a href="moonbitlang/ulex/tests/bytes_test/lexbuf#BytesLexbuf">@moonbitlang/ulex/tests/bytes_test/lexbuf.BytesLexbuf</a>) -> (Int, <a href="moonbitlang/core/array#Array">Array</a>[(Int, Int)])
  ```
  > 

## T

```moonbit
:::source,moonbitlang/ulex/tests/bytes_test/lexengine/lexengine.mbt,2:::type T = <a href="moonbitlang/ulex/tests/bytes_test/lexengine#LexEngine">LexEngine</a>
```


## run

```moonbit
:::source,moonbitlang/ulex/tests/bytes_test/lexengine/lexengine.mbt,14:::fn run(self : <a href="moonbitlang/ulex/tests/bytes_test/lexengine#LexEngine">LexEngine</a>, lexbuf : <a href="moonbitlang/ulex/tests/bytes_test/lexbuf#BytesLexbuf">@moonbitlang/ulex/tests/bytes_test/lexbuf.BytesLexbuf</a>) -> (Int, <a href="moonbitlang/core/array#Array">Array</a>[(Int, Int)])
```

