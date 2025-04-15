# Documentation
|Type|description|
|---|---|
|[ByteFunc](#ByteFunc)||

|Value|description|
|---|---|
|[consume](#consume)||
|[consume\_func](#consume_func)||
|[dump\_headers](#dump_headers)||
|[get\_body\_bytes](#get_body_bytes)||
|[get\_content\_length](#get_content_length)||
|[make\_404\_response](#make_404_response)||
|[make\_500\_response](#make_500_response)||
|[make\_response](#make_response)||
|[make\_response\_str](#make_response_str)||
|[new\_request](#new_request)||
|[println](#println)||
|[random\_int](#random_int)||
|[respond\_404](#respond_404)||
|[respond\_500](#respond_500)||
|[respond\_bytes](#respond_bytes)||
|[respond\_str](#respond_str)||
|[send\_request](#send_request)||
|[split\_path](#split_path)||
|[stream](#stream)||
|[stream\_func](#stream_func)||

## ByteFunc

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/consume.mbt,3:::type ByteFunc
```

 `ByteFunc` is a function that operates on a stream of bytes, one byte at a time.

## consume

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/consume.mbt,12:::fn consume(request : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#OutgoingRequest">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.OutgoingRequest</a>, hash : <a href="gmlewis/spin-moonbit-sdk/common#HashFunc">@gmlewis/spin-moonbit-sdk/common.HashFunc</a>?, debug~ : Bool = ..) -> <a href="moonbitlang/core/result#Result">Result</a>[(Int64, String), <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.ErrorCode</a>]
```

 `consume` performs the provided `request`
then consumes its output and optionally calculates
the stream's hash, reporting the byte count and hash back to the caller.

## consume\_func

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/consume.mbt,37:::fn consume_func(request : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#OutgoingRequest">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.OutgoingRequest</a>, byte_func : <a href="gmlewis/spin-moonbit-sdk/util#ByteFunc">ByteFunc</a>?, debug~ : Bool = ..) -> <a href="moonbitlang/core/result#Result">Result</a>[Int64, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.ErrorCode</a>]
```

 `consume_func` performs the provided `request`
then consumes its output and runs the optional
`byte_func` on each byte, then returns the content length
back to the caller.

## dump\_headers

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/dump-headers.mbt,3:::fn dump_headers(headers : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#Fields">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.Fields</a>) -> Unit
```

 `dump_headers` dumps the headers to stderr as INFO lines.

## get\_body\_bytes

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/get-body-bytes.mbt,3:::fn get_body_bytes(request : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#IncomingRequest">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.IncomingRequest</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[Bytes, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#StreamError">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams.StreamError</a>]
```

 `get_body_bytes` returns the incoming request body as `Bytes`.

## get\_content\_length

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/send-request.mbt,92:::fn get_content_length(fields : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#Fields">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.Fields</a>) -> Int
```


## make\_404\_response

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/make-response.mbt,56:::fn make_404_response() -> <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#OutgoingResponse">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.OutgoingResponse</a>
```

 `make_404_response` makes a new `OutgoingResponse` with "404 Not Found".

## make\_500\_response

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/make-response.mbt,68:::fn make_500_response() -> <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#OutgoingResponse">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.OutgoingResponse</a>
```

 `make_500_response` makes a new `OutgoingResponse` with "500 Internal Server Error".

## make\_response

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/make-response.mbt,3:::fn make_response(body : Bytes, content_type~ : Bytes = .., status_code~ : UInt = ..) -> <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#OutgoingResponse">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.OutgoingResponse</a>
```

 `make_response` makes a new `OutgoingResponse`.

## make\_response\_str

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/make-response.mbt,34:::fn make_response_str(body : String, content_type~ : Bytes = .., status_code~ : UInt = ..) -> <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#OutgoingResponse">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.OutgoingResponse</a>
```

 `make_response_str` makes a new `OutgoingResponse` from the provided `String`.

## new\_request

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/new-request.mbt,3:::fn new_request(http_method : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#Method">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.Method</a>, url : String, fields~ : <a href="moonbitlang/core/array#Array">Array</a>[(String, Bytes)] = ..) -> <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#OutgoingRequest">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.OutgoingRequest</a>
```

 `new_request` creates a new outgoing request.

## println

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/println.mbt,3:::fn println(s : String) -> Unit
```

 `println` prints a string to wasi stdout with a newline.

## random\_int

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/random-int.mbt,3:::fn random_int(n : Int) -> Int
```

 `random_int` returns a random Int between \[0..n). If n\<=1, 0 is always returned.

## respond\_404

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/make-response.mbt,62:::fn respond_404(response_out : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#ResponseOutparam">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.ResponseOutparam</a>) -> Unit
```

 `respond_404` sets response\_out to an `OutgoingResponse` with "404 Not Found".

## respond\_500

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/make-response.mbt,74:::fn respond_500(response_out : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#ResponseOutparam">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.ResponseOutparam</a>) -> Unit
```

 `respond_500` sets response\_out to an `OutgoingResponse` with "500 Internal Server Error".

## respond\_bytes

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/make-response.mbt,23:::fn respond_bytes(response_out : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#ResponseOutparam">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.ResponseOutparam</a>, body : Bytes, content_type~ : Bytes = .., status_code~ : UInt = ..) -> Unit
```

 `respond_bytes` sets response\_out to an `OutgoingResponse` from the provided `Bytes`.

## respond\_str

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/make-response.mbt,45:::fn respond_str(response_out : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#ResponseOutparam">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.ResponseOutparam</a>, body : String, content_type~ : Bytes = .., status_code~ : UInt = ..) -> Unit
```

 `respond_str` sets response\_out to an `OutgoingResponse` from the provided `String`.

## send\_request

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/send-request.mbt,33:::fn send_request(request : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#OutgoingRequest">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.OutgoingRequest</a>, debug~ : Bool = ..) -> <a href="moonbitlang/core/result#Result">Result</a>[Bytes, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.ErrorCode</a>]
```

 `send_request` sends an outgoing request and waits for the response.

## split\_path

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/split-path.mbt,3:::fn split_path(request : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#IncomingRequest">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.IncomingRequest</a>) -> (<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#Method">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.Method</a>, <a href="moonbitlang/core/array#Array">Array</a>[String])
```

 `split_path` splits an incoming request into its method and path parts by splitting on "/".

## stream

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/stream.mbt,5:::fn stream(request : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#OutgoingRequest">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.OutgoingRequest</a>, response_out : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#ResponseOutparam">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.ResponseOutparam</a>, hash : <a href="gmlewis/spin-moonbit-sdk/common#HashFunc">@gmlewis/spin-moonbit-sdk/common.HashFunc</a>?, debug~ : Bool = ..) -> <a href="moonbitlang/core/result#Result">Result</a>[(Int64, String), <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.ErrorCode</a>]
```

 `stream` performs the provided `request`
then streams its output to the provided `response_out` and optionally calculates
the stream's hash, reporting the byte count and hash back to the caller.

## stream\_func

```moonbit
:::source,gmlewis/spin-moonbit-sdk/util/stream.mbt,31:::fn stream_func(request : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#OutgoingRequest">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.OutgoingRequest</a>, response_out : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#ResponseOutparam">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.ResponseOutparam</a>, byte_func : <a href="gmlewis/spin-moonbit-sdk/util#ByteFunc">ByteFunc</a>?, debug~ : Bool = ..) -> <a href="moonbitlang/core/result#Result">Result</a>[Int64, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/http/types.ErrorCode</a>]
```

 `stream_func` performs the provided `request`
then streams its output to the provided `response_out` and runs the
provided `byte_func` on each byte, then returns the content length
back to the caller.
