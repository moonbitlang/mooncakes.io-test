# Documentation
|Type|description|
|---|---|
|[Protocol](#Protocol)||
|[Url](#Url)| Url|
|[UrlRequest](#UrlRequest)| Represent the URL change request from the user, trigger by \`@html.a\` tag.|

|Value|description|
|---|---|
|[parse](#parse)||
|[to\_string](#to_string)||

## Protocol

```moonbit
:::source,Yoorkin/rabbit-tea/url/url.mbt,29:::pub(all) enum Protocol {
  Http
  Https
  Other(String)
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,Yoorkin/rabbit-tea/url/url.mbt,33:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for <a href="Yoorkin/rabbit-tea/url#Protocol">Protocol</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/url/url.mbt,33:::fn compare(<a href="Yoorkin/rabbit-tea/url#Protocol">Protocol</a>, <a href="Yoorkin/rabbit-tea/url#Protocol">Protocol</a>) -> Int
    ```
    > automatically derived
- ```moonbit
  :::source,Yoorkin/rabbit-tea/url/url.mbt,33:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="Yoorkin/rabbit-tea/url#Protocol">Protocol</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/url/url.mbt,33:::fn op_equal(<a href="Yoorkin/rabbit-tea/url#Protocol">Protocol</a>, <a href="Yoorkin/rabbit-tea/url#Protocol">Protocol</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,Yoorkin/rabbit-tea/url/url.mbt,33:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="Yoorkin/rabbit-tea/url#Protocol">Protocol</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/url/url.mbt,33:::fn output(<a href="Yoorkin/rabbit-tea/url#Protocol">Protocol</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## Url

```moonbit
:::source,Yoorkin/rabbit-tea/url/url.mbt,19:::pub(all) struct Url {
  protocol : <a href="Yoorkin/rabbit-tea/url#Protocol">Protocol</a>
  host : String
  port : Int?
  path : String
  query : String?
  fragment : String?
}
```
 Url
 
 ```text
  https://example.com:8042/over/there?name=ferret#nose
  \___/   \______________/\_________/ \_________/ \__/
    |            |            |            |        |
  scheme     authority       path        query   fragment
 ```
 
 This diagram is from https://package.elm-lang.org/packages/elm/url/latest/Url

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,Yoorkin/rabbit-tea/url/url.mbt,26:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for <a href="Yoorkin/rabbit-tea/url#Url">Url</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/url/url.mbt,26:::fn compare(<a href="Yoorkin/rabbit-tea/url#Url">Url</a>, <a href="Yoorkin/rabbit-tea/url#Url">Url</a>) -> Int
    ```
    > automatically derived
- ```moonbit
  :::source,Yoorkin/rabbit-tea/url/url.mbt,26:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="Yoorkin/rabbit-tea/url#Url">Url</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/url/url.mbt,26:::fn op_equal(<a href="Yoorkin/rabbit-tea/url#Url">Url</a>, <a href="Yoorkin/rabbit-tea/url#Url">Url</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,Yoorkin/rabbit-tea/url/url.mbt,26:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="Yoorkin/rabbit-tea/url#Url">Url</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/url/url.mbt,26:::fn output(<a href="Yoorkin/rabbit-tea/url#Url">Url</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### to\_string
  ```moonbit
  :::source,Yoorkin/rabbit-tea/url/url.mbt,36:::fn <a href="Yoorkin/rabbit-tea/url#Url">Url</a>::to_string(self : <a href="Yoorkin/rabbit-tea/url#Url">Url</a>) -> String
  ```
  > 

## UrlRequest

```moonbit
:::source,Yoorkin/rabbit-tea/url/url.mbt,4:::pub(all) enum UrlRequest {
  Internal(<a href="Yoorkin/rabbit-tea/url#Url">Url</a>)
  External(String)
}
```
 Represent the URL change request from the user, trigger by `@html.a` tag.
The `Internal` means the target URL is in the same domain.
The `External` means the target URL is in another site.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,Yoorkin/rabbit-tea/url/url.mbt,7:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for <a href="Yoorkin/rabbit-tea/url#UrlRequest">UrlRequest</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/url/url.mbt,7:::fn compare(<a href="Yoorkin/rabbit-tea/url#UrlRequest">UrlRequest</a>, <a href="Yoorkin/rabbit-tea/url#UrlRequest">UrlRequest</a>) -> Int
    ```
    > automatically derived
- ```moonbit
  :::source,Yoorkin/rabbit-tea/url/url.mbt,7:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="Yoorkin/rabbit-tea/url#UrlRequest">UrlRequest</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/url/url.mbt,7:::fn op_equal(<a href="Yoorkin/rabbit-tea/url#UrlRequest">UrlRequest</a>, <a href="Yoorkin/rabbit-tea/url#UrlRequest">UrlRequest</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,Yoorkin/rabbit-tea/url/url.mbt,7:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="Yoorkin/rabbit-tea/url#UrlRequest">UrlRequest</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/url/url.mbt,7:::fn output(<a href="Yoorkin/rabbit-tea/url#UrlRequest">UrlRequest</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## parse

```moonbit
:::source,Yoorkin/rabbit-tea/url/url.mbt,58:::fn parse(url : String) -> <a href="Yoorkin/rabbit-tea/url#Url">Url</a>!<a href="moonbitlang/core/error#Error">Error</a>
```


## to\_string

```moonbit
:::source,Yoorkin/rabbit-tea/url/url.mbt,36:::fn to_string(self : <a href="Yoorkin/rabbit-tea/url#Url">Url</a>) -> String
```

