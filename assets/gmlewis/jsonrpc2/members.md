# gmlewis/jsonrpc2
[![check](https://github.com/gmlewis/moonbit-jsonrpc2/actions/workflows/check.yml/badge.svg)](https://github.com/gmlewis/moonbit-jsonrpc2/actions/workflows/check.yml)

This is a simple abstraction for the JSON-RPC 2.0 specification:
https://www.jsonrpc.org/specification
based on the Go implementation: https://pkg.go.dev/golang.org/x/exp/jsonrpc2
which has copyright:
```
// Copyright 2018 The Go Authors. All rights reserved.
// Use of this source code is governed by a BSD-style
// license that can be found in the LICENSE file.
```

## Status

The code has been updated to support compiler:

```bash
$ moon version --all
moon 0.1.20250407 (24afaca 2025-04-07) ~/.moon/bin/moon
moonc v0.1.20250410+15d580434 ~/.moon/bin/moonc
moonrun 0.1.20250407 (24afaca 2025-04-07) ~/.moon/bin/moonrun
```

---
# Documentation
|Trait|description|
|---|---|
|[@gmlewis/jsonrpc2.Framer](#@gmlewis/jsonrpc2.Framer)||
|[@gmlewis/jsonrpc2.Reader](#@gmlewis/jsonrpc2.Reader)||
|[@gmlewis/jsonrpc2.Writer](#@gmlewis/jsonrpc2.Writer)||

|Type|description|
|---|---|
|[HeaderFramer](#HeaderFramer)||
|[HeaderReader](#HeaderReader)||
|[HeaderWriter](#HeaderWriter)||
|[ID](#ID)||
|[LineFramer](#LineFramer)||
|[LineReader](#LineReader)||
|[LineWriter](#LineWriter)||
|[Message](#Message)||
|[RawFramer](#RawFramer)||
|[RawReader](#RawReader)||
|[RawWriter](#RawWriter)||
|[Request](#Request)||
|[Response](#Response)||
|[WireError](#WireError)||

|Value|description|
|---|---|
|[as\_batch\_request](#as_batch_request)||
|[as\_batch\_response](#as_batch_response)||
|[as\_call](#as_call)||
|[as\_notification](#as_notification)||
|[as\_request](#as_request)||
|[as\_response](#as_response)||
|[header\_framer](#header_framer)||
|[line\_framer](#line_framer)||
|[new\_batch\_request](#new_batch_request)||
|[new\_batch\_response](#new_batch_response)||
|[new\_call](#new_call)||
|[new\_notification](#new_notification)||
|[new\_response](#new_response)||
|[raw\_framer](#raw_framer)||

## @gmlewis/jsonrpc2.Framer

```moonbit
:::source,gmlewis/jsonrpc2/framer.mbt,36:::pub trait @gmlewis/jsonrpc2.Framer {
  reader(Self, <a href="gmlewis/io#ByteReader">@gmlewis/io.ByteReader</a>) -> <a href="gmlewis/jsonrpc2#Reader">Reader</a>
  writer(Self, <a href="gmlewis/io#Writer">@gmlewis/io.Writer</a>) -> <a href="gmlewis/jsonrpc2#Writer">Writer</a>
}
```

 Framer wraps low level byte readers and writers into jsonrpc2 message
readers and writers.
It is responsible for the framing and encoding of messages into wire form.

## @gmlewis/jsonrpc2.Reader

```moonbit
:::source,gmlewis/jsonrpc2/framer.mbt,15:::pub trait @gmlewis/jsonrpc2.Reader {
  read(Self) -> (<a href="gmlewis/jsonrpc2#Message">Message</a>?, Int64, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
}
```

 Reader abstracts the transport mechanics from the JSON RPC protocol.
A Conn reads messages from the reader it was provided on construction,
and assumes that each call to Read fully transfers a single message,
or returns an error.
A reader is not safe for concurrent use, it is expected it will be used by
a single Conn in a safe manner.

## @gmlewis/jsonrpc2.Writer

```moonbit
:::source,gmlewis/jsonrpc2/framer.mbt,27:::pub trait @gmlewis/jsonrpc2.Writer {
  write(Self, <a href="gmlewis/jsonrpc2#Message">Message</a>) -> (Int64, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
}
```

 Writer abstracts the transport mechanics from the JSON RPC protocol.
A Conn writes messages using the writer it was provided on construction,
and assumes that each call to Write fully transfers a single message,
or returns an error.
A writer is not safe for concurrent use, it is expected it will be used by
a single Conn in a safe manner.

## HeaderFramer

```moonbit
:::source,gmlewis/jsonrpc2/header-framer.mbt,10:::pub struct HeaderFramer {
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/jsonrpc2/header-framer.mbt,23:::impl <a href="gmlewis/jsonrpc2#Framer">Framer</a> for <a href="gmlewis/jsonrpc2#HeaderFramer">HeaderFramer</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/header-framer.mbt,23:::fn reader(_self : <a href="gmlewis/jsonrpc2#HeaderFramer">HeaderFramer</a>, in_ : <a href="gmlewis/io#ByteReader">@gmlewis/io.ByteReader</a>) -> <a href="gmlewis/jsonrpc2#Reader">Reader</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/header-framer.mbt,28:::fn writer(_self : <a href="gmlewis/jsonrpc2#HeaderFramer">HeaderFramer</a>, out : <a href="gmlewis/io#Writer">@gmlewis/io.Writer</a>) -> <a href="gmlewis/jsonrpc2#Writer">Writer</a>
    ```
    > 

## HeaderReader

```moonbit
:::source,gmlewis/jsonrpc2/header-framer.mbt,13:::pub struct HeaderReader {
  in_ : <a href="gmlewis/io#ByteReader">@gmlewis/io.ByteReader</a>
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/jsonrpc2/header-framer.mbt,33:::impl <a href="gmlewis/jsonrpc2#Reader">Reader</a> for <a href="gmlewis/jsonrpc2#HeaderReader">HeaderReader</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/header-framer.mbt,33:::fn read(self : <a href="gmlewis/jsonrpc2#HeaderReader">HeaderReader</a>) -> (<a href="gmlewis/jsonrpc2#Message">Message</a>?, Int64, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
    ```
    > 

## HeaderWriter

```moonbit
:::source,gmlewis/jsonrpc2/header-framer.mbt,18:::pub struct HeaderWriter {
  out : <a href="gmlewis/io#Writer">@gmlewis/io.Writer</a>
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/jsonrpc2/header-framer.mbt,102:::impl <a href="gmlewis/jsonrpc2#Writer">Writer</a> for <a href="gmlewis/jsonrpc2#HeaderWriter">HeaderWriter</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/header-framer.mbt,102:::fn write(self : <a href="gmlewis/jsonrpc2#HeaderWriter">HeaderWriter</a>, msg : <a href="gmlewis/jsonrpc2#Message">Message</a>) -> (Int64, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
    ```
    > 

## ID

```moonbit
:::source,gmlewis/jsonrpc2/id.mbt,3:::pub enum ID {
  Number(Int64)
  String(String)
}
```

 ID is used to identify the request and tie it to the response.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/jsonrpc2/id.mbt,8:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/jsonrpc2#ID">ID</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/id.mbt,8:::fn op_equal(<a href="gmlewis/jsonrpc2#ID">ID</a>, <a href="gmlewis/jsonrpc2#ID">ID</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/jsonrpc2/id.mbt,8:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/jsonrpc2#ID">ID</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/id.mbt,8:::fn output(<a href="gmlewis/jsonrpc2#ID">ID</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/jsonrpc2/id.mbt,21:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="gmlewis/jsonrpc2#ID">ID</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/id.mbt,21:::fn to_json(self : <a href="gmlewis/jsonrpc2#ID">ID</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,gmlewis/jsonrpc2/id.mbt,29:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="gmlewis/jsonrpc2#ID">ID</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/id.mbt,29:::fn from_json(json : <a href="moonbitlang/core/json#Json">Json</a>, path : <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="gmlewis/jsonrpc2#ID">ID</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### number
  ```moonbit
  :::source,gmlewis/jsonrpc2/id.mbt,11:::fn <a href="gmlewis/jsonrpc2#ID">ID</a>::number(n : Int64) -> <a href="gmlewis/jsonrpc2#ID">ID</a>
  ```
  > 
- #### string
  ```moonbit
  :::source,gmlewis/jsonrpc2/id.mbt,16:::fn <a href="gmlewis/jsonrpc2#ID">ID</a>::string(s : String) -> <a href="gmlewis/jsonrpc2#ID">ID</a>
  ```
  > 

## LineFramer

```moonbit
:::source,gmlewis/jsonrpc2/line-framer.mbt,10:::pub struct LineFramer {
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/jsonrpc2/line-framer.mbt,23:::impl <a href="gmlewis/jsonrpc2#Framer">Framer</a> for <a href="gmlewis/jsonrpc2#LineFramer">LineFramer</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/line-framer.mbt,23:::fn reader(_self : <a href="gmlewis/jsonrpc2#LineFramer">LineFramer</a>, in_ : <a href="gmlewis/io#ByteReader">@gmlewis/io.ByteReader</a>) -> <a href="gmlewis/jsonrpc2#Reader">Reader</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/line-framer.mbt,28:::fn writer(_self : <a href="gmlewis/jsonrpc2#LineFramer">LineFramer</a>, out : <a href="gmlewis/io#Writer">@gmlewis/io.Writer</a>) -> <a href="gmlewis/jsonrpc2#Writer">Writer</a>
    ```
    > 

## LineReader

```moonbit
:::source,gmlewis/jsonrpc2/line-framer.mbt,13:::pub struct LineReader {
  in_ : <a href="gmlewis/io#ByteReader">@gmlewis/io.ByteReader</a>
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/jsonrpc2/line-framer.mbt,33:::impl <a href="gmlewis/jsonrpc2#Reader">Reader</a> for <a href="gmlewis/jsonrpc2#LineReader">LineReader</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/line-framer.mbt,33:::fn read(self : <a href="gmlewis/jsonrpc2#LineReader">LineReader</a>) -> (<a href="gmlewis/jsonrpc2#Message">Message</a>?, Int64, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
    ```
    > 

## LineWriter

```moonbit
:::source,gmlewis/jsonrpc2/line-framer.mbt,18:::pub struct LineWriter {
  out : <a href="gmlewis/io#Writer">@gmlewis/io.Writer</a>
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/jsonrpc2/line-framer.mbt,50:::impl <a href="gmlewis/jsonrpc2#Writer">Writer</a> for <a href="gmlewis/jsonrpc2#LineWriter">LineWriter</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/line-framer.mbt,50:::fn write(self : <a href="gmlewis/jsonrpc2#LineWriter">LineWriter</a>, msg : <a href="gmlewis/jsonrpc2#Message">Message</a>) -> (Int64, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
    ```
    > 

## Message

```moonbit
:::source,gmlewis/jsonrpc2/message.mbt,6:::pub enum Message {
  Request(<a href="gmlewis/jsonrpc2#Request">Request</a>)
  Response(<a href="gmlewis/jsonrpc2#Response">Response</a>)
  BatchRequest(<a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/jsonrpc2#Request">Request</a>])
  BatchResponse(<a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/jsonrpc2#Response">Response</a>])
}
```

 Message covers all jsonrpc2 message types.
They share no common functionality, but are a closed set of concrete types
that are allowed to implement this interface. The message types are Request
and Response.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/jsonrpc2/message.mbt,15:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/jsonrpc2#Message">Message</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/message.mbt,15:::fn op_equal(<a href="gmlewis/jsonrpc2#Message">Message</a>, <a href="gmlewis/jsonrpc2#Message">Message</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/jsonrpc2/message.mbt,15:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/jsonrpc2#Message">Message</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/message.mbt,15:::fn output(<a href="gmlewis/jsonrpc2#Message">Message</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/jsonrpc2/message.mbt,18:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="gmlewis/jsonrpc2#Message">Message</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/message.mbt,18:::fn to_json(self : <a href="gmlewis/jsonrpc2#Message">Message</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,gmlewis/jsonrpc2/message.mbt,28:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="gmlewis/jsonrpc2#Message">Message</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/message.mbt,28:::fn from_json(json : <a href="moonbitlang/core/json#Json">Json</a>, path : <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="gmlewis/jsonrpc2#Message">Message</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### as\_batch\_request
  ```moonbit
  :::source,gmlewis/jsonrpc2/message.mbt,122:::fn <a href="gmlewis/jsonrpc2#Message">Message</a>::as_batch_request(self : <a href="gmlewis/jsonrpc2#Message">Message</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/jsonrpc2#Request">Request</a>]?
  ```
  > 
  >  as\_batch\_request returns the message as a batch request if it is one.
- #### as\_batch\_response
  ```moonbit
  :::source,gmlewis/jsonrpc2/message.mbt,132:::fn <a href="gmlewis/jsonrpc2#Message">Message</a>::as_batch_response(self : <a href="gmlewis/jsonrpc2#Message">Message</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/jsonrpc2#Response">Response</a>]?
  ```
  > 
  >  as\_batch\_response returns the message as a batch response if it is one.
- #### as\_call
  ```moonbit
  :::source,gmlewis/jsonrpc2/message.mbt,89:::fn <a href="gmlewis/jsonrpc2#Message">Message</a>::as_call(self : <a href="gmlewis/jsonrpc2#Message">Message</a>) -> <a href="gmlewis/jsonrpc2#Request">Request</a>?
  ```
  > 
- #### as\_notification
  ```moonbit
  :::source,gmlewis/jsonrpc2/message.mbt,96:::fn <a href="gmlewis/jsonrpc2#Message">Message</a>::as_notification(self : <a href="gmlewis/jsonrpc2#Message">Message</a>) -> <a href="gmlewis/jsonrpc2#Request">Request</a>?
  ```
  > 
- #### as\_request
  ```moonbit
  :::source,gmlewis/jsonrpc2/message.mbt,103:::fn <a href="gmlewis/jsonrpc2#Message">Message</a>::as_request(self : <a href="gmlewis/jsonrpc2#Message">Message</a>) -> <a href="gmlewis/jsonrpc2#Request">Request</a>?
  ```
  > 
- #### as\_response
  ```moonbit
  :::source,gmlewis/jsonrpc2/message.mbt,112:::fn <a href="gmlewis/jsonrpc2#Message">Message</a>::as_response(self : <a href="gmlewis/jsonrpc2#Message">Message</a>) -> <a href="gmlewis/jsonrpc2#Response">Response</a>?
  ```
  > 

## RawFramer

```moonbit
:::source,gmlewis/jsonrpc2/raw-framer.mbt,10:::pub struct RawFramer {
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/jsonrpc2/raw-framer.mbt,23:::impl <a href="gmlewis/jsonrpc2#Framer">Framer</a> for <a href="gmlewis/jsonrpc2#RawFramer">RawFramer</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/raw-framer.mbt,23:::fn reader(_self : <a href="gmlewis/jsonrpc2#RawFramer">RawFramer</a>, in_ : <a href="gmlewis/io#ByteReader">@gmlewis/io.ByteReader</a>) -> <a href="gmlewis/jsonrpc2#Reader">Reader</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/raw-framer.mbt,28:::fn writer(_self : <a href="gmlewis/jsonrpc2#RawFramer">RawFramer</a>, out : <a href="gmlewis/io#Writer">@gmlewis/io.Writer</a>) -> <a href="gmlewis/jsonrpc2#Writer">Writer</a>
    ```
    > 

## RawReader

```moonbit
:::source,gmlewis/jsonrpc2/raw-framer.mbt,13:::type RawReader
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/jsonrpc2/raw-framer.mbt,33:::impl <a href="gmlewis/jsonrpc2#Reader">Reader</a> for <a href="gmlewis/jsonrpc2#RawReader">RawReader</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/raw-framer.mbt,33:::fn read(self : <a href="gmlewis/jsonrpc2#RawReader">RawReader</a>) -> (<a href="gmlewis/jsonrpc2#Message">Message</a>?, Int64, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
    ```
    > 

## RawWriter

```moonbit
:::source,gmlewis/jsonrpc2/raw-framer.mbt,18:::type RawWriter
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/jsonrpc2/raw-framer.mbt,47:::impl <a href="gmlewis/jsonrpc2#Writer">Writer</a> for <a href="gmlewis/jsonrpc2#RawWriter">RawWriter</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/raw-framer.mbt,47:::fn write(self : <a href="gmlewis/jsonrpc2#RawWriter">RawWriter</a>, msg : <a href="gmlewis/jsonrpc2#Message">Message</a>) -> (Int64, <a href="gmlewis/io#IOError">@gmlewis/io.IOError</a>?)
    ```
    > 

## Request

```moonbit
:::source,gmlewis/jsonrpc2/request.mbt,5:::pub(all) struct Request {
  id : <a href="gmlewis/jsonrpc2#ID">ID</a>?
  method_ : String
  params : <a href="moonbitlang/core/json#Json">Json</a>
}
```

 A Request is a message sent to a peer to request behavior.
If it has an ID then it is a call and therefore requests a response,
otherwise it is a notification which receives no response.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/jsonrpc2/request.mbt,13:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/jsonrpc2#Request">Request</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/request.mbt,13:::fn op_equal(<a href="gmlewis/jsonrpc2#Request">Request</a>, <a href="gmlewis/jsonrpc2#Request">Request</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/jsonrpc2/request.mbt,13:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/jsonrpc2#Request">Request</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/request.mbt,13:::fn output(<a href="gmlewis/jsonrpc2#Request">Request</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/jsonrpc2/request.mbt,16:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="gmlewis/jsonrpc2#Request">Request</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/request.mbt,16:::fn to_json(self : <a href="gmlewis/jsonrpc2#Request">Request</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,gmlewis/jsonrpc2/request.mbt,31:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="gmlewis/jsonrpc2#Request">Request</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/request.mbt,31:::fn from_json(json : <a href="moonbitlang/core/json#Json">Json</a>, path : <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="gmlewis/jsonrpc2#Request">Request</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > 

## Response

```moonbit
:::source,gmlewis/jsonrpc2/response.mbt,4:::pub(all) struct Response {
  id : <a href="gmlewis/jsonrpc2#ID">ID</a>
  result : <a href="moonbitlang/core/result#Result">Result</a>[<a href="moonbitlang/core/json#Json">Json</a>, <a href="gmlewis/jsonrpc2#WireError">WireError</a>]
}
```

 Response is a Message used as a reply to a call Request.
It will have the same ID as the call it is a response to.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/jsonrpc2/response.mbt,9:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/jsonrpc2#Response">Response</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/response.mbt,9:::fn op_equal(<a href="gmlewis/jsonrpc2#Response">Response</a>, <a href="gmlewis/jsonrpc2#Response">Response</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/jsonrpc2/response.mbt,9:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/jsonrpc2#Response">Response</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/response.mbt,9:::fn output(<a href="gmlewis/jsonrpc2#Response">Response</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/jsonrpc2/response.mbt,20:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="gmlewis/jsonrpc2#Response">Response</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/response.mbt,20:::fn to_json(self : <a href="gmlewis/jsonrpc2#Response">Response</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,gmlewis/jsonrpc2/response.mbt,34:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="gmlewis/jsonrpc2#Response">Response</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/response.mbt,34:::fn from_json(json : <a href="moonbitlang/core/json#Json">Json</a>, path : <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="gmlewis/jsonrpc2#Response">Response</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > 

## WireError

```moonbit
:::source,gmlewis/jsonrpc2/response.mbt,13:::pub(all) struct WireError {
  code : Int
  message : String
  data : <a href="moonbitlang/core/json#Json">Json</a>?
}
```

 WireError is a jsonrpc2 error message.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/jsonrpc2/response.mbt,17:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/jsonrpc2#WireError">WireError</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/response.mbt,17:::fn op_equal(<a href="gmlewis/jsonrpc2#WireError">WireError</a>, <a href="gmlewis/jsonrpc2#WireError">WireError</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/jsonrpc2/response.mbt,17:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/jsonrpc2#WireError">WireError</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/response.mbt,17:::fn output(<a href="gmlewis/jsonrpc2#WireError">WireError</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/jsonrpc2/response.mbt,17:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="gmlewis/jsonrpc2#WireError">WireError</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/response.mbt,17:::fn to_json(<a href="gmlewis/jsonrpc2#WireError">WireError</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/jsonrpc2/response.mbt,17:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="gmlewis/jsonrpc2#WireError">WireError</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/jsonrpc2/response.mbt,17:::fn from_json(<a href="moonbitlang/core/json#Json">Json</a>, <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="gmlewis/jsonrpc2#WireError">WireError</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > automatically derived

## as\_batch\_request

```moonbit
:::source,gmlewis/jsonrpc2/message.mbt,122:::fn as_batch_request(self : <a href="gmlewis/jsonrpc2#Message">Message</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/jsonrpc2#Request">Request</a>]?
```

 as\_batch\_request returns the message as a batch request if it is one.

## as\_batch\_response

```moonbit
:::source,gmlewis/jsonrpc2/message.mbt,132:::fn as_batch_response(self : <a href="gmlewis/jsonrpc2#Message">Message</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/jsonrpc2#Response">Response</a>]?
```

 as\_batch\_response returns the message as a batch response if it is one.

## as\_call

```moonbit
:::source,gmlewis/jsonrpc2/message.mbt,89:::fn as_call(self : <a href="gmlewis/jsonrpc2#Message">Message</a>) -> <a href="gmlewis/jsonrpc2#Request">Request</a>?
```


## as\_notification

```moonbit
:::source,gmlewis/jsonrpc2/message.mbt,96:::fn as_notification(self : <a href="gmlewis/jsonrpc2#Message">Message</a>) -> <a href="gmlewis/jsonrpc2#Request">Request</a>?
```


## as\_request

```moonbit
:::source,gmlewis/jsonrpc2/message.mbt,103:::fn as_request(self : <a href="gmlewis/jsonrpc2#Message">Message</a>) -> <a href="gmlewis/jsonrpc2#Request">Request</a>?
```


## as\_response

```moonbit
:::source,gmlewis/jsonrpc2/message.mbt,112:::fn as_response(self : <a href="gmlewis/jsonrpc2#Message">Message</a>) -> <a href="gmlewis/jsonrpc2#Response">Response</a>?
```


## header\_framer

```moonbit
:::source,gmlewis/jsonrpc2/header-framer.mbt,5:::fn header_framer() -> <a href="gmlewis/jsonrpc2#Framer">Framer</a>
```

 header\_framer returns a new Framer.
The messages are sent with HTTP content length and MIME type headers.
This is the format used by LSP and others.

## line\_framer

```moonbit
:::source,gmlewis/jsonrpc2/line-framer.mbt,5:::fn line_framer() -> <a href="gmlewis/jsonrpc2#Framer">Framer</a>
```

 line\_framer returns a new Framer.
The messages are sent with a terminating cr+newline, and rely on json decode consistency
to determine message boundaries.

## new\_batch\_request

```moonbit
:::source,gmlewis/jsonrpc2/message.mbt,75:::fn new_batch_request(messages : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/jsonrpc2#Message">Message</a>]) -> <a href="gmlewis/jsonrpc2#Message">Message</a>
```

 new\_batch\_request constructs a new batch request message for the supplied
requests.

## new\_batch\_response

```moonbit
:::source,gmlewis/jsonrpc2/message.mbt,83:::fn new_batch_response(messages : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/jsonrpc2#Message">Message</a>]) -> <a href="gmlewis/jsonrpc2#Message">Message</a>
```

 new\_batch\_response constructs a new batch response message for the supplied
responses.

## new\_call

```moonbit
:::source,gmlewis/jsonrpc2/message.mbt,62:::fn new_call(id : <a href="gmlewis/jsonrpc2#ID">ID</a>, method_ : String, params : <a href="moonbitlang/core/json#Json">Json</a>) -> <a href="gmlewis/jsonrpc2#Message">Message</a>
```

 new\_call constructs a new call message for the supplied ID, method and
parameters.

## new\_notification

```moonbit
:::source,gmlewis/jsonrpc2/message.mbt,55:::fn new_notification(method_ : String, params : <a href="moonbitlang/core/json#Json">Json</a>) -> <a href="gmlewis/jsonrpc2#Message">Message</a>
```

 new\_notification constructs a new notification message for the supplied
method and parameters.

## new\_response

```moonbit
:::source,gmlewis/jsonrpc2/message.mbt,68:::fn new_response(id : <a href="gmlewis/jsonrpc2#ID">ID</a>, result : <a href="moonbitlang/core/result#Result">Result</a>[<a href="moonbitlang/core/json#Json">Json</a>, <a href="gmlewis/jsonrpc2#WireError">WireError</a>]) -> <a href="gmlewis/jsonrpc2#Message">Message</a>
```

 new\_response constructs a new Response message.

## raw\_framer

```moonbit
:::source,gmlewis/jsonrpc2/raw-framer.mbt,5:::fn raw_framer() -> <a href="gmlewis/jsonrpc2#Framer">Framer</a>
```

 raw\_framer returns a new Framer.
The messages are sent with no wrapping, and rely on json decode consistency
to determine message boundaries.
