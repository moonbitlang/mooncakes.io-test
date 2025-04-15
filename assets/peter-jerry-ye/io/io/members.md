# Documentation
|Type|description|
|---|---|
|[Pollable](#Pollable)||

|Value|description|
|---|---|
|[event\_loop](#event_loop)||
|[flush](#flush)||
|[pipe](#pipe)||
|[print](#print)||
|[println](#println)||
|[println\_sync](#println_sync)||
|[read\_all](#read_all)||
|[read\_all\_sync](#read_all_sync)||
|[read\_line](#read_line)||
|[read\_line\_sync](#read_line_sync)||
|[stderr](#stderr)||
|[stderr\_stream](#stderr_stream)||
|[stdin](#stdin)||
|[stdin\_stream](#stdin_stream)||
|[stdout](#stdout)||
|[stdout\_stream](#stdout_stream)||
|[write](#write)||
|[write\_sync](#write_sync)||

## Pollable

```moonbit
:::source,peter-jerry-ye/io/io/defs.mbt,16:::pub(all) type Pollable <a href="peter-jerry-ye/wasi-imports/interface/wasi/io/poll#Pollable">@peter-jerry-ye/wasi-imports/interface/wasi/io/poll.Pollable</a>
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,peter-jerry-ye/io/io/defs.mbt,19:::impl <a href="peter-jerry-ye/async/loop#Sync">@peter-jerry-ye/async/loop.Sync</a> for <a href="peter-jerry-ye/io/io#Pollable">Pollable</a>
  ```
  > 
  * ```moonbit
    :::source,peter-jerry-ye/io/io/defs.mbt,19:::fn sync(array : <a href="moonbitlang/core/array#Array">Array</a>[<a href="peter-jerry-ye/io/io#Pollable">Pollable</a>]) -> <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[UInt]
    ```
    > 

## event\_loop

```moonbit
:::source,peter-jerry-ye/io/io/utils.mbt,16:::let event_loop : <a href="peter-jerry-ye/async/loop#T">@peter-jerry-ye/async/loop.T</a>[<a href="peter-jerry-ye/io/io#Pollable">Pollable</a>]
```


## flush

```moonbit
:::source,peter-jerry-ye/io/io/utils.mbt,167:::fn flush(stream : <a href="peter-jerry-ye/wasi-imports/interface/wasi/io/streams#OutputStream">@peter-jerry-ye/wasi-imports/interface/wasi/io/streams.OutputStream</a>) -> Unit!<a href="moonbitlang/core/error#Error">Error</a>
```


## pipe

```moonbit
:::source,peter-jerry-ye/io/io/utils.mbt,172:::fn pipe(input : <a href="peter-jerry-ye/wasi-imports/interface/wasi/io/streams#InputStream">@peter-jerry-ye/wasi-imports/interface/wasi/io/streams.InputStream</a>, output : <a href="peter-jerry-ye/wasi-imports/interface/wasi/io/streams#OutputStream">@peter-jerry-ye/wasi-imports/interface/wasi/io/streams.OutputStream</a>, buffer_size~ : UInt64 = .., event_loop~ : <a href="peter-jerry-ye/async/loop#T">@peter-jerry-ye/async/loop.T</a>[<a href="peter-jerry-ye/io/io#Pollable">Pollable</a>] = ..) -> Unit!<a href="moonbitlang/core/error#Error">Error</a>
```


## print

```moonbit
:::source,peter-jerry-ye/io/io/utils.mbt,193:::fn print(string : String, stream~ : <a href="peter-jerry-ye/wasi-imports/interface/wasi/io/streams#OutputStream">@peter-jerry-ye/wasi-imports/interface/wasi/io/streams.OutputStream</a> = .., flush~ : Bool = .., event_loop~ : <a href="peter-jerry-ye/async/loop#T">@peter-jerry-ye/async/loop.T</a>[<a href="peter-jerry-ye/io/io#Pollable">Pollable</a>] = ..) -> Unit!<a href="moonbitlang/core/error#Error">Error</a>
```


## println

```moonbit
:::source,peter-jerry-ye/io/io/utils.mbt,206:::fn println(string : String, stream~ : <a href="peter-jerry-ye/wasi-imports/interface/wasi/io/streams#OutputStream">@peter-jerry-ye/wasi-imports/interface/wasi/io/streams.OutputStream</a> = .., flush~ : Bool = .., event_loop~ : <a href="peter-jerry-ye/async/loop#T">@peter-jerry-ye/async/loop.T</a>[<a href="peter-jerry-ye/io/io#Pollable">Pollable</a>] = ..) -> Unit!<a href="moonbitlang/core/error#Error">Error</a>
```


## println\_sync

```moonbit
:::source,peter-jerry-ye/io/io/utils.mbt,220:::fn println_sync(string : String, stream~ : <a href="peter-jerry-ye/wasi-imports/interface/wasi/io/streams#OutputStream">@peter-jerry-ye/wasi-imports/interface/wasi/io/streams.OutputStream</a> = ..) -> Unit!<a href="moonbitlang/core/error#Error">Error</a>
```


## read\_all

```moonbit
:::source,peter-jerry-ye/io/io/utils.mbt,72:::fn read_all(stream~ : <a href="peter-jerry-ye/wasi-imports/interface/wasi/io/streams#InputStream">@peter-jerry-ye/wasi-imports/interface/wasi/io/streams.InputStream</a> = .., buffer_size~ : UInt64 = .., event_loop~ : <a href="peter-jerry-ye/async/loop#T">@peter-jerry-ye/async/loop.T</a>[<a href="peter-jerry-ye/io/io#Pollable">Pollable</a>] = ..) -> <a href="moonbitlang/core/buffer#T">@moonbitlang/core/buffer.T</a>!<a href="moonbitlang/core/error#Error">Error</a>
```


## read\_all\_sync

```moonbit
:::source,peter-jerry-ye/io/io/utils.mbt,98:::fn read_all_sync(stream~ : <a href="peter-jerry-ye/wasi-imports/interface/wasi/io/streams#InputStream">@peter-jerry-ye/wasi-imports/interface/wasi/io/streams.InputStream</a> = .., buffer_size~ : UInt64 = ..) -> <a href="moonbitlang/core/buffer#T">@moonbitlang/core/buffer.T</a>!<a href="moonbitlang/core/error#Error">Error</a>
```


## read\_line

```moonbit
:::source,peter-jerry-ye/io/io/utils.mbt,19:::fn read_line(stream~ : <a href="peter-jerry-ye/wasi-imports/interface/wasi/io/streams#InputStream">@peter-jerry-ye/wasi-imports/interface/wasi/io/streams.InputStream</a> = .., event_loop~ : <a href="peter-jerry-ye/async/loop#T">@peter-jerry-ye/async/loop.T</a>[<a href="peter-jerry-ye/io/io#Pollable">Pollable</a>] = ..) -> String!<a href="moonbitlang/core/error#Error">Error</a>
```


## read\_line\_sync

```moonbit
:::source,peter-jerry-ye/io/io/utils.mbt,48:::fn read_line_sync(stream~ : <a href="peter-jerry-ye/wasi-imports/interface/wasi/io/streams#InputStream">@peter-jerry-ye/wasi-imports/interface/wasi/io/streams.InputStream</a> = ..) -> String!<a href="moonbitlang/core/error#Error">Error</a>
```


## stderr

```moonbit
:::source,peter-jerry-ye/io/io/defs.mbt,34:::let stderr : <a href="peter-jerry-ye/wasi-imports/interface/wasi/io/streams#OutputStream">@peter-jerry-ye/wasi-imports/interface/wasi/io/streams.OutputStream</a>
```


## stderr\_stream

```moonbit
:::source,peter-jerry-ye/io/io/impl.mbt,97:::let stderr_stream : <a href="peter-jerry-ye/async/stream#OutputStream">@peter-jerry-ye/async/stream.OutputStream</a>
```


## stdin

```moonbit
:::source,peter-jerry-ye/io/io/defs.mbt,28:::let stdin : <a href="peter-jerry-ye/wasi-imports/interface/wasi/io/streams#InputStream">@peter-jerry-ye/wasi-imports/interface/wasi/io/streams.InputStream</a>
```


## stdin\_stream

```moonbit
:::source,peter-jerry-ye/io/io/impl.mbt,87:::let stdin_stream : <a href="peter-jerry-ye/async/stream#InputStream">@peter-jerry-ye/async/stream.InputStream</a>
```


## stdout

```moonbit
:::source,peter-jerry-ye/io/io/defs.mbt,31:::let stdout : <a href="peter-jerry-ye/wasi-imports/interface/wasi/io/streams#OutputStream">@peter-jerry-ye/wasi-imports/interface/wasi/io/streams.OutputStream</a>
```


## stdout\_stream

```moonbit
:::source,peter-jerry-ye/io/io/impl.mbt,92:::let stdout_stream : <a href="peter-jerry-ye/async/stream#OutputStream">@peter-jerry-ye/async/stream.OutputStream</a>
```


## write

```moonbit
:::source,peter-jerry-ye/io/io/utils.mbt,117:::fn write(contents : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Byte], stream : <a href="peter-jerry-ye/wasi-imports/interface/wasi/io/streams#OutputStream">@peter-jerry-ye/wasi-imports/interface/wasi/io/streams.OutputStream</a>, event_loop~ : <a href="peter-jerry-ye/async/loop#T">@peter-jerry-ye/async/loop.T</a>[<a href="peter-jerry-ye/io/io#Pollable">Pollable</a>] = ..) -> Unit!<a href="moonbitlang/core/error#Error">Error</a>
```


## write\_sync

```moonbit
:::source,peter-jerry-ye/io/io/utils.mbt,146:::fn write_sync(contents : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Byte], stream : <a href="peter-jerry-ye/wasi-imports/interface/wasi/io/streams#OutputStream">@peter-jerry-ye/wasi-imports/interface/wasi/io/streams.OutputStream</a>) -> Unit!<a href="moonbitlang/core/error#Error">Error</a>
```

