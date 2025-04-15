# Documentation
|Type|description|
|---|---|
|[CardModel](#CardModel)||
|[Model](#Model)||
|[Msg](#Msg)||

|Value|description|
|---|---|
|[load](#load)||
|[update](#update)||
|[view](#view)||

## CardModel

```moonbit
:::source,Yoorkin/rabbit-tea/example/todoMVC/home/card.mbt,2:::type CardModel
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,Yoorkin/rabbit-tea/example/todoMVC/home/card.mbt,5:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="Yoorkin/rabbit-tea/example/todoMVC/home#CardModel">CardModel</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/example/todoMVC/home/card.mbt,5:::fn output(<a href="Yoorkin/rabbit-tea/example/todoMVC/home#CardModel">CardModel</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## Model

```moonbit
:::source,Yoorkin/rabbit-tea/example/todoMVC/home/home.mbt,9:::pub struct Model {
  cards : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/example/todoMVC/home#CardModel">CardModel</a>]
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,Yoorkin/rabbit-tea/example/todoMVC/home/home.mbt,11:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="Yoorkin/rabbit-tea/example/todoMVC/home#Model">Model</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/example/todoMVC/home/home.mbt,11:::fn output(<a href="Yoorkin/rabbit-tea/example/todoMVC/home#Model">Model</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## Msg

```moonbit
:::source,Yoorkin/rabbit-tea/example/todoMVC/home/home.mbt,2:::pub enum Msg {
  DeleteAll
  GotCardsData(<a href="moonbitlang/core/result#Result">Result</a>[<a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/example/todoMVC/home#CardModel">CardModel</a>], String])
  ReqResult(<a href="moonbitlang/core/result#Result">Result</a>[<a href="moonbitlang/core/json#Json">Json</a>, String])
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,Yoorkin/rabbit-tea/example/todoMVC/home/home.mbt,6:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="Yoorkin/rabbit-tea/example/todoMVC/home#Msg">Msg</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/example/todoMVC/home/home.mbt,6:::fn output(<a href="Yoorkin/rabbit-tea/example/todoMVC/home#Msg">Msg</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## load

```moonbit
:::source,Yoorkin/rabbit-tea/example/todoMVC/home/home.mbt,14:::fn load() -> (<a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[<a href="Yoorkin/rabbit-tea/example/todoMVC/home#Msg">Msg</a>], <a href="Yoorkin/rabbit-tea/example/todoMVC/home#Model">Model</a>)
```


## update

```moonbit
:::source,Yoorkin/rabbit-tea/example/todoMVC/home/home.mbt,35:::fn update(msg : <a href="Yoorkin/rabbit-tea/example/todoMVC/home#Msg">Msg</a>, model : <a href="Yoorkin/rabbit-tea/example/todoMVC/home#Model">Model</a>) -> (<a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[<a href="Yoorkin/rabbit-tea/example/todoMVC/home#Msg">Msg</a>], <a href="Yoorkin/rabbit-tea/example/todoMVC/home#Model">Model</a>)
```


## view

```moonbit
:::source,Yoorkin/rabbit-tea/example/todoMVC/home/home.mbt,22:::fn view(model : <a href="Yoorkin/rabbit-tea/example/todoMVC/home#Model">Model</a>) -> <a href="Yoorkin/rabbit-tea/html#T">@Yoorkin/rabbit-tea/html.T</a>[<a href="Yoorkin/rabbit-tea/example/todoMVC/home#Msg">Msg</a>]
```

