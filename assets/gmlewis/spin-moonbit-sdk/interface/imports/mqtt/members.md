# Documentation
|Type|description|
|---|---|
|[Connection](#Connection)||
|[Error\_](#Error_)||
|[Qos](#Qos)||

|Value|description|
|---|---|
|[ordinal](#ordinal)||

## Connection

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,40:::pub(all) type Connection Int
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,40:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Connection">Connection</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,40:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Connection">Connection</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Connection">Connection</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,40:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Connection">Connection</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,40:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Connection">Connection</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### drop
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,46:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Connection">Connection</a>::drop(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Connection">Connection</a>) -> Unit
  ```
  > 
- #### open
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,52:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Connection">Connection</a>::open(address : String, username : String, password : String, keep_alive_interval_in_secs : UInt64) -> <a href="moonbitlang/core/result#Result">Result</a>[<a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Connection">Connection</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Error_">Error_</a>]
  ```
  > 
  >  Open a connection to the Mqtt instance at `address`.
- #### publish
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,98:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Connection">Connection</a>::publish(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Connection">Connection</a>, topic : String, payload : Bytes, qos : <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Qos">Qos</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Error_">Error_</a>]
  ```
  > 
  >  Publish an Mqtt message to the specified `topic`.

## Error\_

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,5:::pub(all) enum Error_ {
  InvalidAddress
  TooManyConnections
  ConnectionFailed(String)
  Other(String)
}
```

 Errors related to interacting with Mqtt

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,10:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Error_">Error_</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,10:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Error_">Error_</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Error_">Error_</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,10:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Error_">Error_</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,10:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Error_">Error_</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## Qos

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,14:::pub(all) enum Qos {
  AT_MOST_ONCE
  AT_LEAST_ONCE
  EXACTLY_ONCE
}
```

 QoS for publishing Mqtt messages

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,18:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Qos">Qos</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,18:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Qos">Qos</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Qos">Qos</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,18:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Qos">Qos</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,18:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Qos">Qos</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### from
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,30:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Qos">Qos</a>::from(self : Int) -> <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Qos">Qos</a>
  ```
  > 
- #### ordinal
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,21:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Qos">Qos</a>::ordinal(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Qos">Qos</a>) -> Int
  ```
  > 

## ordinal

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/mqtt/top.mbt,21:::fn ordinal(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/mqtt#Qos">Qos</a>) -> Int
```

