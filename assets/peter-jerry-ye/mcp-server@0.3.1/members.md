# Documentation
|Type|description|
|---|---|
|[Content](#Content)||
|[LogLevel](#LogLevel)||
|[PromptArgument](#PromptArgument)||
|[PromptMessage](#PromptMessage)||
|[Response](#Response)||
|[Role](#Role)||
|[Root](#Root)||
|[Server](#Server)||

|Value|description|
|---|---|
|[add\_prompt](#add_prompt)||
|[add\_tool](#add_tool)||
|[list\_roots](#list_roots)||
|[log](#log)||
|[new](#new)||
|[prompt\_argument](#prompt_argument)||
|[remove\_prompt](#remove_prompt)||
|[remove\_tool](#remove_tool)||
|[serve](#serve)||

## Content

```moonbit
:::source,peter-jerry-ye/mcp-server/types.mbt,83:::pub(all) enum Content {
  Text(String)
  Image(String, String)
  Resource(String, String, String)
}
```


## LogLevel

```moonbit
:::source,peter-jerry-ye/mcp-server/types.mbt,29:::pub(all) enum LogLevel {
  Debug
  Info
  Notice
  Warning
  Error
  Critical
  Alert
  Emergency
}
```

 RFC 5424

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,peter-jerry-ye/mcp-server/types.mbt,38:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="peter-jerry-ye/mcp-server#LogLevel">LogLevel</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/mcp-server/types.mbt,38:::fn op_equal(<a href="peter-jerry-ye/mcp-server#LogLevel">LogLevel</a>, <a href="peter-jerry-ye/mcp-server#LogLevel">LogLevel</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,peter-jerry-ye/mcp-server/types.mbt,38:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="peter-jerry-ye/mcp-server#LogLevel">LogLevel</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/mcp-server/types.mbt,38:::fn output(<a href="peter-jerry-ye/mcp-server#LogLevel">LogLevel</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## PromptArgument

```moonbit
:::source,peter-jerry-ye/mcp-server/types.mbt,67:::type PromptArgument
```


## PromptMessage

```moonbit
:::source,peter-jerry-ye/mcp-server/types.mbt,61:::pub(all) struct PromptMessage {
  role : <a href="peter-jerry-ye/mcp-server#Role">Role</a>
  message : <a href="peter-jerry-ye/mcp-server#Content">Content</a>
}
```


## Response

```moonbit
:::source,peter-jerry-ye/mcp-server/types.mbt,90:::pub(all) struct Response {
  isError : Bool
  payload : <a href="moonbitlang/core/array#Array">Array</a>[<a href="peter-jerry-ye/mcp-server#Content">Content</a>]
}
```


## Role

```moonbit
:::source,peter-jerry-ye/mcp-server/types.mbt,55:::pub(all) enum Role {
  User
  Assistant
}
```


## Root

```moonbit
:::source,peter-jerry-ye/mcp-server/types.mbt,96:::pub struct Root {
  uri : String
  name : String?
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,peter-jerry-ye/mcp-server/types.mbt,99:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="peter-jerry-ye/mcp-server#Root">Root</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/mcp-server/types.mbt,99:::fn op_equal(<a href="peter-jerry-ye/mcp-server#Root">Root</a>, <a href="peter-jerry-ye/mcp-server#Root">Root</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,peter-jerry-ye/mcp-server/types.mbt,99:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="peter-jerry-ye/mcp-server#Root">Root</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/mcp-server/types.mbt,99:::fn output(<a href="peter-jerry-ye/mcp-server#Root">Root</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## Server

```moonbit
:::source,peter-jerry-ye/mcp-server/server.mbt,16:::type Server
```


#### mooncakes-io-method-mark-Methods
- #### add\_prompt
  ```moonbit
  :::source,peter-jerry-ye/mcp-server/server.mbt,400:::fn <a href="peter-jerry-ye/mcp-server#Server">Server</a>::add_prompt(self : <a href="peter-jerry-ye/mcp-server#Server">Server</a>, name~ : String, description~ : String, arguments~ : <a href="moonbitlang/core/array#Array">Array</a>[<a href="peter-jerry-ye/mcp-server#PromptArgument">PromptArgument</a>] = .., cb~ : (<a href="moonbitlang/core/builtin#Map">Map</a>[String, <a href="moonbitlang/core/json#Json">Json</a>]) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="peter-jerry-ye/mcp-server#PromptMessage">PromptMessage</a>]) -> Unit
  ```
  > 
- #### add\_tool
  ```moonbit
  :::source,peter-jerry-ye/mcp-server/server.mbt,368:::fn <a href="peter-jerry-ye/mcp-server#Server">Server</a>::add_tool(self : <a href="peter-jerry-ye/mcp-server#Server">Server</a>, name~ : String, description~ : String, inputSchema~ : <a href="peter-jerry-ye/mcp-server/schema#T">@peter-jerry-ye/mcp-server/schema.T</a>, cb~ : (<a href="moonbitlang/core/json#Json">Json</a>, <a href="peter-jerry-ye/mcp-server#Server">Server</a>) -> <a href="peter-jerry-ye/mcp-server#Response">Response</a>) -> Unit
  ```
  > 
- #### list\_roots
  ```moonbit
  :::source,peter-jerry-ye/mcp-server/server.mbt,432:::fn <a href="peter-jerry-ye/mcp-server#Server">Server</a>::list_roots(self : <a href="peter-jerry-ye/mcp-server#Server">Server</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="peter-jerry-ye/mcp-server#Root">Root</a>]!<a href="moonbitlang/core/error#Error">Error</a>
  ```
  > 
- #### log
  ```moonbit
  :::source,peter-jerry-ye/mcp-server/server.mbt,355:::fn <a href="peter-jerry-ye/mcp-server#Server">Server</a>::log(self : <a href="peter-jerry-ye/mcp-server#Server">Server</a>, message : <a href="moonbitlang/core/json#Json">Json</a>, level~ : <a href="peter-jerry-ye/mcp-server#LogLevel">LogLevel</a> = ..) -> Unit
  ```
  > 
- #### remove\_prompt
  ```moonbit
  :::source,peter-jerry-ye/mcp-server/server.mbt,419:::fn <a href="peter-jerry-ye/mcp-server#Server">Server</a>::remove_prompt(self : <a href="peter-jerry-ye/mcp-server#Server">Server</a>, name : String) -> Unit
  ```
  > 
- #### remove\_tool
  ```moonbit
  :::source,peter-jerry-ye/mcp-server/server.mbt,387:::fn <a href="peter-jerry-ye/mcp-server#Server">Server</a>::remove_tool(self : <a href="peter-jerry-ye/mcp-server#Server">Server</a>, name : String) -> Unit
  ```
  > 
- #### serve
  ```moonbit
  :::source,peter-jerry-ye/mcp-server/server.mbt,44:::fn <a href="peter-jerry-ye/mcp-server#Server">Server</a>::serve(self : <a href="peter-jerry-ye/mcp-server#Server">Server</a>, stdin~ : <a href="peter-jerry-ye/async/stream#Reader">@peter-jerry-ye/async/stream.Reader</a>, stdout~ : <a href="peter-jerry-ye/async/stream#Writer">@peter-jerry-ye/async/stream.Writer</a>, stderr~ : <a href="peter-jerry-ye/async/stream#Writer">@peter-jerry-ye/async/stream.Writer</a>) -> Unit
  ```
  > 

## add\_prompt

```moonbit
:::source,peter-jerry-ye/mcp-server/server.mbt,400:::fn add_prompt(self : <a href="peter-jerry-ye/mcp-server#Server">Server</a>, name~ : String, description~ : String, arguments~ : <a href="moonbitlang/core/array#Array">Array</a>[<a href="peter-jerry-ye/mcp-server#PromptArgument">PromptArgument</a>] = .., cb~ : (<a href="moonbitlang/core/builtin#Map">Map</a>[String, <a href="moonbitlang/core/json#Json">Json</a>]) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="peter-jerry-ye/mcp-server#PromptMessage">PromptMessage</a>]) -> Unit
```


## add\_tool

```moonbit
:::source,peter-jerry-ye/mcp-server/server.mbt,368:::fn add_tool(self : <a href="peter-jerry-ye/mcp-server#Server">Server</a>, name~ : String, description~ : String, inputSchema~ : <a href="peter-jerry-ye/mcp-server/schema#T">@peter-jerry-ye/mcp-server/schema.T</a>, cb~ : (<a href="moonbitlang/core/json#Json">Json</a>, <a href="peter-jerry-ye/mcp-server#Server">Server</a>) -> <a href="peter-jerry-ye/mcp-server#Response">Response</a>) -> Unit
```


## list\_roots

```moonbit
:::source,peter-jerry-ye/mcp-server/server.mbt,432:::fn list_roots(self : <a href="peter-jerry-ye/mcp-server#Server">Server</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="peter-jerry-ye/mcp-server#Root">Root</a>]!<a href="moonbitlang/core/error#Error">Error</a>
```


## log

```moonbit
:::source,peter-jerry-ye/mcp-server/server.mbt,355:::fn log(self : <a href="peter-jerry-ye/mcp-server#Server">Server</a>, message : <a href="moonbitlang/core/json#Json">Json</a>, level~ : <a href="peter-jerry-ye/mcp-server#LogLevel">LogLevel</a> = ..) -> Unit
```


## new

```moonbit
:::source,peter-jerry-ye/mcp-server/server.mbt,29:::fn new(seed : Bytes) -> <a href="peter-jerry-ye/mcp-server#Server">Server</a>
```


## prompt\_argument

```moonbit
:::source,peter-jerry-ye/mcp-server/types.mbt,74:::fn prompt_argument(name : String, description? : String, required? : Bool) -> <a href="peter-jerry-ye/mcp-server#PromptArgument">PromptArgument</a>
```


## remove\_prompt

```moonbit
:::source,peter-jerry-ye/mcp-server/server.mbt,419:::fn remove_prompt(self : <a href="peter-jerry-ye/mcp-server#Server">Server</a>, name : String) -> Unit
```


## remove\_tool

```moonbit
:::source,peter-jerry-ye/mcp-server/server.mbt,387:::fn remove_tool(self : <a href="peter-jerry-ye/mcp-server#Server">Server</a>, name : String) -> Unit
```


## serve

```moonbit
:::source,peter-jerry-ye/mcp-server/server.mbt,44:::fn serve(self : <a href="peter-jerry-ye/mcp-server#Server">Server</a>, stdin~ : <a href="peter-jerry-ye/async/stream#Reader">@peter-jerry-ye/async/stream.Reader</a>, stdout~ : <a href="peter-jerry-ye/async/stream#Writer">@peter-jerry-ye/async/stream.Writer</a>, stderr~ : <a href="peter-jerry-ye/async/stream#Writer">@peter-jerry-ye/async/stream.Writer</a>) -> Unit
```

