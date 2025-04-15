# Documentation
|Type|description|
|---|---|
|[Id](#Id)||
|[Message](#Message)| https://www.jsonrpc.org/specification|
|[RPCError](#RPCError)||

## Id

```moonbit
:::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,143:::pub(all) enum Id {
  String(String)
  Number(Double)
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,146:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="peter-jerry-ye/mcp-server/rpc#Id">Id</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,146:::fn op_equal(<a href="peter-jerry-ye/mcp-server/rpc#Id">Id</a>, <a href="peter-jerry-ye/mcp-server/rpc#Id">Id</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,146:::impl <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="peter-jerry-ye/mcp-server/rpc#Id">Id</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,146:::fn hash_combine(<a href="peter-jerry-ye/mcp-server/rpc#Id">Id</a>, <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,146:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="peter-jerry-ye/mcp-server/rpc#Id">Id</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,146:::fn output(<a href="peter-jerry-ye/mcp-server/rpc#Id">Id</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,158:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="peter-jerry-ye/mcp-server/rpc#Id">Id</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,158:::fn to_json(self : <a href="peter-jerry-ye/mcp-server/rpc#Id">Id</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,149:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="peter-jerry-ye/mcp-server/rpc#Id">Id</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,149:::fn from_json(json : <a href="moonbitlang/core/json#Json">Json</a>, path : <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="peter-jerry-ye/mcp-server/rpc#Id">Id</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > 

## Message

```moonbit
:::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,16:::pub(all) enum Message {
  Request(<a href="peter-jerry-ye/mcp-server/rpc#Id">Id</a>, String, <a href="moonbitlang/core/builtin#Map">Map</a>[String, <a href="moonbitlang/core/json#Json">Json</a>])
  Notification(String, <a href="moonbitlang/core/builtin#Map">Map</a>[String, <a href="moonbitlang/core/json#Json">Json</a>])
  Response(<a href="peter-jerry-ye/mcp-server/rpc#Id">Id</a>, <a href="moonbitlang/core/result#Result">Result</a>[<a href="moonbitlang/core/builtin#Map">Map</a>[String, <a href="moonbitlang/core/json#Json">Json</a>], <a href="peter-jerry-ye/mcp-server/rpc#RPCError">RPCError</a>])
}
```
 https://www.jsonrpc.org/specification

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,20:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="peter-jerry-ye/mcp-server/rpc#Message">Message</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,20:::fn op_equal(<a href="peter-jerry-ye/mcp-server/rpc#Message">Message</a>, <a href="peter-jerry-ye/mcp-server/rpc#Message">Message</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,20:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="peter-jerry-ye/mcp-server/rpc#Message">Message</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,20:::fn output(<a href="peter-jerry-ye/mcp-server/rpc#Message">Message</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,81:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="peter-jerry-ye/mcp-server/rpc#Message">Message</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,81:::fn to_json(self : <a href="peter-jerry-ye/mcp-server/rpc#Message">Message</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,23:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="peter-jerry-ye/mcp-server/rpc#Message">Message</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,23:::fn from_json(json : <a href="moonbitlang/core/json#Json">Json</a>, path : <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="peter-jerry-ye/mcp-server/rpc#Message">Message</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > 

## RPCError

```moonbit
:::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,120:::pub(all) struct RPCError {
  code : Int
  message : String
  data : <a href="moonbitlang/core/json#Json">Json</a>?
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,124:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="peter-jerry-ye/mcp-server/rpc#RPCError">RPCError</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,124:::fn op_equal(<a href="peter-jerry-ye/mcp-server/rpc#RPCError">RPCError</a>, <a href="peter-jerry-ye/mcp-server/rpc#RPCError">RPCError</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,124:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="peter-jerry-ye/mcp-server/rpc#RPCError">RPCError</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,124:::fn output(<a href="peter-jerry-ye/mcp-server/rpc#RPCError">RPCError</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,124:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="peter-jerry-ye/mcp-server/rpc#RPCError">RPCError</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,124:::fn to_json(<a href="peter-jerry-ye/mcp-server/rpc#RPCError">RPCError</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > automatically derived
- ```moonbit
  :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,124:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="peter-jerry-ye/mcp-server/rpc#RPCError">RPCError</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/mcp-server/rpc/rpc.mbt,124:::fn from_json(<a href="moonbitlang/core/json#Json">Json</a>, <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="peter-jerry-ye/mcp-server/rpc#RPCError">RPCError</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > automatically derived
