A WASI interface dedicated to performing inferencing for Large Language Models.
---
# Documentation
|Type|description|
|---|---|
|[EmbeddingsResult](#EmbeddingsResult)||
|[EmbeddingsUsage](#EmbeddingsUsage)||
|[Error\_](#Error_)||
|[InferencingParams](#InferencingParams)||
|[InferencingResult](#InferencingResult)||
|[InferencingUsage](#InferencingUsage)||

|Value|description|
|---|---|
|[generate\_embeddings](#generate_embeddings)||
|[infer](#infer)||

## EmbeddingsResult

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,44:::pub(all) struct EmbeddingsResult {
  embeddings : <a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/core/array#Array">Array</a>[Double]]
  usage : <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#EmbeddingsUsage">EmbeddingsUsage</a>
}
```

 Result of generating embeddings

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,47:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#EmbeddingsResult">EmbeddingsResult</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,47:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#EmbeddingsResult">EmbeddingsResult</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#EmbeddingsResult">EmbeddingsResult</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,47:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#EmbeddingsResult">EmbeddingsResult</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,47:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#EmbeddingsResult">EmbeddingsResult</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## EmbeddingsUsage

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,38:::pub(all) struct EmbeddingsUsage {
  prompt_token_count : UInt
}
```

 Usage related to an embeddings generation request

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,40:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#EmbeddingsUsage">EmbeddingsUsage</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,40:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#EmbeddingsUsage">EmbeddingsUsage</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#EmbeddingsUsage">EmbeddingsUsage</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,40:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#EmbeddingsUsage">EmbeddingsUsage</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,40:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#EmbeddingsUsage">EmbeddingsUsage</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## Error\_

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,16:::pub(all) enum Error_ {
  ModelNotSupported
  RuntimeError(String)
  InvalidInput(String)
}
```

 The set of errors which may be raised by functions in this interface

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,20:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#Error_">Error_</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,20:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#Error_">Error_</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#Error_">Error_</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,20:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#Error_">Error_</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,20:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#Error_">Error_</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## InferencingParams

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,5:::pub(all) struct InferencingParams {
  max_tokens : UInt
  repeat_penalty : Double
  repeat_penalty_last_n_token_count : UInt
  temperature : Double
  top_k : UInt
  top_p : Double
}
```

 Inference request parameters

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,12:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#InferencingParams">InferencingParams</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,12:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#InferencingParams">InferencingParams</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#InferencingParams">InferencingParams</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,12:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#InferencingParams">InferencingParams</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,12:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#InferencingParams">InferencingParams</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## InferencingResult

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,31:::pub(all) struct InferencingResult {
  text : String
  usage : <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#InferencingUsage">InferencingUsage</a>
}
```

 An inferencing result

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,34:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#InferencingResult">InferencingResult</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,34:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#InferencingResult">InferencingResult</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#InferencingResult">InferencingResult</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,34:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#InferencingResult">InferencingResult</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,34:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#InferencingResult">InferencingResult</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## InferencingUsage

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,24:::pub(all) struct InferencingUsage {
  prompt_token_count : UInt
  generated_token_count : UInt
}
```

 Usage information related to the inferencing result

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,27:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#InferencingUsage">InferencingUsage</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,27:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#InferencingUsage">InferencingUsage</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#InferencingUsage">InferencingUsage</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,27:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#InferencingUsage">InferencingUsage</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,27:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#InferencingUsage">InferencingUsage</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## generate\_embeddings

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,121:::fn generate_embeddings(model : String, text : <a href="moonbitlang/core/array#Array">Array</a>[String]) -> <a href="moonbitlang/core/result#Result">Result</a>[<a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#EmbeddingsResult">EmbeddingsResult</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#Error_">Error_</a>]
```

 Generate embeddings for the supplied list of text

## infer

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/llm/top.mbt,51:::fn infer(model : String, prompt : String, params : <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#InferencingParams">InferencingParams</a>?) -> <a href="moonbitlang/core/result#Result">Result</a>[<a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#InferencingResult">InferencingResult</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/llm#Error_">Error_</a>]
```

 Perform inferencing using the provided model and prompt with the given optional params
