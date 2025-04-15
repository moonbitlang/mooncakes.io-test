# Documentation
|Type|description|
|---|---|
|[Card](#Card)||
|[Model](#Model)||
|[Msg](#Msg)||

|Value|description|
|---|---|
|[decode\_card](#decode_card)||
|[load](#load)||
|[update](#update)||
|[view](#view)||

## Card

```moonbit
:::source,Yoorkin/rabbit-tea/example/todoMVC/editor/editor.mbt,9:::type Card
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,Yoorkin/rabbit-tea/example/todoMVC/editor/editor.mbt,13:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="Yoorkin/rabbit-tea/example/todoMVC/editor#Card">Card</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/example/todoMVC/editor/editor.mbt,13:::fn output(<a href="Yoorkin/rabbit-tea/example/todoMVC/editor#Card">Card</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## Model

```moonbit
:::source,Yoorkin/rabbit-tea/example/todoMVC/editor/editor.mbt,2:::type Model
```


## Msg

```moonbit
:::source,Yoorkin/rabbit-tea/example/todoMVC/editor/editor.mbt,16:::type Msg
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,Yoorkin/rabbit-tea/example/todoMVC/editor/editor.mbt,22:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="Yoorkin/rabbit-tea/example/todoMVC/editor#Msg">Msg</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/example/todoMVC/editor/editor.mbt,22:::fn output(<a href="Yoorkin/rabbit-tea/example/todoMVC/editor#Msg">Msg</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## decode\_card

```moonbit
:::source,Yoorkin/rabbit-tea/example/todoMVC/editor/editor.mbt,40:::fn decode_card(data : <a href="moonbitlang/core/json#Json">Json</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[<a href="Yoorkin/rabbit-tea/example/todoMVC/editor#Card">Card</a>, String]
```


## load

```moonbit
:::source,Yoorkin/rabbit-tea/example/todoMVC/editor/editor.mbt,25:::fn load(index : Int?) -> (<a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[<a href="Yoorkin/rabbit-tea/example/todoMVC/editor#Msg">Msg</a>], <a href="Yoorkin/rabbit-tea/example/todoMVC/editor#Model">Model</a>)
```


## update

```moonbit
:::source,Yoorkin/rabbit-tea/example/todoMVC/editor/editor.mbt,49:::fn update(msg : <a href="Yoorkin/rabbit-tea/example/todoMVC/editor#Msg">Msg</a>, model : <a href="Yoorkin/rabbit-tea/example/todoMVC/editor#Model">Model</a>) -> (<a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[<a href="Yoorkin/rabbit-tea/example/todoMVC/editor#Msg">Msg</a>], <a href="Yoorkin/rabbit-tea/example/todoMVC/editor#Model">Model</a>)
```


## view

```moonbit
:::source,Yoorkin/rabbit-tea/example/todoMVC/editor/editor.mbt,97:::fn view(model : <a href="Yoorkin/rabbit-tea/example/todoMVC/editor#Model">Model</a>) -> <a href="Yoorkin/rabbit-tea/html#T">@Yoorkin/rabbit-tea/html.T</a>[<a href="Yoorkin/rabbit-tea/example/todoMVC/editor#Msg">Msg</a>]
```

