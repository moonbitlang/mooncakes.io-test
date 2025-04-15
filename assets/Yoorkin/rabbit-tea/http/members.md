# Documentation
|Type|description|
|---|---|
|[Body](#Body)||
|[Expecting](#Expecting)||
|[Decoder](#Decoder)| |

|Value|description|
|---|---|
|[delete](#delete)| Create a command to send a PUT request.|
|[get](#get)| Create a command to send a GET request.|
|[patch](#patch)| Create a command to send a PATCH request.|
|[post](#post)| Create a command to send a POST request.|

## Body

```moonbit
:::source,Yoorkin/rabbit-tea/http/http.mbt,11:::pub(all) enum Body {
  Json(<a href="moonbitlang/core/json#Json">Json</a>)
  Text(String)
  Empty
}
```


## Expecting

```moonbit
:::source,Yoorkin/rabbit-tea/http/http.mbt,5:::pub(all) enum Expecting[Msg, Model] {
  Json((<a href="moonbitlang/core/result#Result">Result</a>[Model, String]) -> Msg, (<a href="moonbitlang/core/json#Json">Json</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[Model, String])
  Text((<a href="moonbitlang/core/result#Result">Result</a>[String, String]) -> Msg)
}
```


## Decoder

```moonbit
:::source,Yoorkin/rabbit-tea/http/http.mbt,2:::type Decoder[Model] = (<a href="moonbitlang/core/json#Json">Json</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[Model, String]
```
 

## delete

```moonbit
:::source,Yoorkin/rabbit-tea/http/http.mbt,118:::fn delete[Msg, Model](url : String, expect~ : <a href="Yoorkin/rabbit-tea/http#Expecting">Expecting</a>[Msg, Model]) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[Msg]
```
 Create a command to send a PUT request.

## get

```moonbit
:::source,Yoorkin/rabbit-tea/http/http.mbt,110:::fn get[Msg, Model](url : String, expect~ : <a href="Yoorkin/rabbit-tea/http#Expecting">Expecting</a>[Msg, Model]) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[Msg]
```
 Create a command to send a GET request.

## patch

```moonbit
:::source,Yoorkin/rabbit-tea/http/http.mbt,135:::fn patch[Msg, Model](url : String, body : <a href="Yoorkin/rabbit-tea/http#Body">Body</a>, expect~ : <a href="Yoorkin/rabbit-tea/http#Expecting">Expecting</a>[Msg, Model]) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[Msg]
```
 Create a command to send a PATCH request.

## post

```moonbit
:::source,Yoorkin/rabbit-tea/http/http.mbt,126:::fn post[Msg, Model](url : String, body : <a href="Yoorkin/rabbit-tea/http#Body">Body</a>, expect~ : <a href="Yoorkin/rabbit-tea/http#Expecting">Expecting</a>[Msg, Model]) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[Msg]
```
 Create a command to send a POST request.
