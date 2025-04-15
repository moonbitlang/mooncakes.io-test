# Documentation
|Type|description|
|---|---|
|[IllegalArgument](#IllegalArgument)||

|Value|description|
|---|---|
|[bytes](#bytes)||
|[bytes\_sync](#bytes_sync)||
|[fetch](#fetch)||
|[fetch\_sync](#fetch_sync)||
|[headers](#headers)||
|[json](#json)||
|[json\_sync](#json_sync)||
|[request](#request)||
|[response](#response)||
|[text](#text)||
|[text\_sync](#text_sync)||

## IllegalArgument

```moonbit
:::source,peter-jerry-ye/io/http/utils.mbt,226:::pub type! IllegalArgument String

```


## bytes

```moonbit
:::source,peter-jerry-ye/io/http/utils.mbt,63:::fn bytes(body : <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#IncomingBody">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.IncomingBody</a>, event_loop~ : <a href="peter-jerry-ye/async/loop#T">@peter-jerry-ye/async/loop.T</a>[<a href="peter-jerry-ye/io/io#Pollable">@peter-jerry-ye/io/io.Pollable</a>] = ..) -> (<a href="peter-jerry-ye/async/promise#T">@peter-jerry-ye/async/promise.T</a>[Bytes], <a href="peter-jerry-ye/async/promise#T">@peter-jerry-ye/async/promise.T</a>[<a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#Fields">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.Fields</a>?])
```

 Consume the body and return the bytes
 
 The body is finished after this function is called.  
This function fails if the body stream is already consumed
 
 @return a tuple of the bytes and the trailers

## bytes\_sync

```moonbit
:::source,peter-jerry-ye/io/http/utils.mbt,92:::fn bytes_sync(body : <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#IncomingBody">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.IncomingBody</a>) -> (Bytes, <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#Fields">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.Fields</a>?)!<a href="moonbitlang/core/error#Error">Error</a>
```


## fetch

```moonbit
:::source,peter-jerry-ye/io/http/utils.mbt,16:::fn fetch(request : <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#OutgoingRequest">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.OutgoingRequest</a>, options? : <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#RequestOptions">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.RequestOptions</a>, event_loop~ : <a href="peter-jerry-ye/async/loop#T">@peter-jerry-ye/async/loop.T</a>[<a href="peter-jerry-ye/io/io#Pollable">@peter-jerry-ye/io/io.Pollable</a>] = ..) -> <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#IncomingResponse">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.IncomingResponse</a>!<a href="moonbitlang/core/error#Error">Error</a>
```


## fetch\_sync

```moonbit
:::source,peter-jerry-ye/io/http/utils.mbt,36:::fn fetch_sync(request : <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#OutgoingRequest">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.OutgoingRequest</a>, options? : <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#RequestOptions">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.RequestOptions</a>) -> <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#IncomingResponse">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.IncomingResponse</a>!<a href="moonbitlang/core/error#Error">Error</a>
```


## headers

```moonbit
:::source,peter-jerry-ye/io/http/utils.mbt,177:::fn headers(headers : <a href="moonbitlang/core/builtin#Map">Map</a>[String, <a href="moonbitlang/core/array#Array">Array</a>[Bytes]]) -> <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#Fields">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.Fields</a>
```


## json

```moonbit
:::source,peter-jerry-ye/io/http/utils.mbt,153:::fn json(body : <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#IncomingBody">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.IncomingBody</a>, event_loop~ : <a href="peter-jerry-ye/async/loop#T">@peter-jerry-ye/async/loop.T</a>[<a href="peter-jerry-ye/io/io#Pollable">@peter-jerry-ye/io/io.Pollable</a>] = ..) -> (<a href="peter-jerry-ye/async/promise#T">@peter-jerry-ye/async/promise.T</a>[<a href="moonbitlang/core/json#Json">Json</a>], <a href="peter-jerry-ye/async/promise#T">@peter-jerry-ye/async/promise.T</a>[<a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#Fields">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.Fields</a>?])
```

 Consume the body and return the content as json
 
 The body is finished after this function is called.  
This function fails if the body stream is already consumed
 
 TODO: stream parsing
 
 @return a tuple of the json and the trailers

## json\_sync

```moonbit
:::source,peter-jerry-ye/io/http/utils.mbt,171:::fn json_sync(body : <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#IncomingBody">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.IncomingBody</a>) -> (<a href="moonbitlang/core/json#Json">Json</a>, <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#Fields">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.Fields</a>?)!<a href="moonbitlang/core/error#Error">Error</a>
```


## request

```moonbit
:::source,peter-jerry-ye/io/http/utils.mbt,186:::fn request(authority : String, path~ : String = .., headers~ : <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#Fields">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.Fields</a> = .., method_~ : <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#Method">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.Method</a> = .., scheme? : <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#Scheme">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.Scheme</a>) -> <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#OutgoingRequest">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.OutgoingRequest</a>!<a href="peter-jerry-ye/io/http#IllegalArgument">IllegalArgument</a>
```


## response

```moonbit
:::source,peter-jerry-ye/io/http/utils.mbt,210:::fn response(status : UInt, headers~ : <a href="moonbitlang/core/builtin#Map">Map</a>[String, <a href="moonbitlang/core/array#Array">Array</a>[Bytes]] = ..) -> <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#OutgoingResponse">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.OutgoingResponse</a>!<a href="peter-jerry-ye/io/http#IllegalArgument">IllegalArgument</a>
```


## text

```moonbit
:::source,peter-jerry-ye/io/http/utils.mbt,120:::fn text(body : <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#IncomingBody">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.IncomingBody</a>, event_loop~ : <a href="peter-jerry-ye/async/loop#T">@peter-jerry-ye/async/loop.T</a>[<a href="peter-jerry-ye/io/io#Pollable">@peter-jerry-ye/io/io.Pollable</a>] = ..) -> (<a href="peter-jerry-ye/async/promise#T">@peter-jerry-ye/async/promise.T</a>[String], <a href="peter-jerry-ye/async/promise#T">@peter-jerry-ye/async/promise.T</a>[<a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#Fields">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.Fields</a>?])
```

 Consume the body and return the content as text
 
 The body is finished after this function is called.  
This function fails if the body stream is already consumed
 
 TODO: stream encoding
 
 @return a tuple of the text and the trailers

## text\_sync

```moonbit
:::source,peter-jerry-ye/io/http/utils.mbt,139:::fn text_sync(body : <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#IncomingBody">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.IncomingBody</a>) -> (String, <a href="peter-jerry-ye/wasi-imports/interface/wasi/http/types#Fields">@peter-jerry-ye/wasi-imports/interface/wasi/http/types.Fields</a>?)!<a href="moonbitlang/core/error#Error">Error</a>
```

