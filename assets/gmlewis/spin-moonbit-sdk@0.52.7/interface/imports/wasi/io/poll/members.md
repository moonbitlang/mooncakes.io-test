A poll API intended to let users wait for I/O events on multiple handles
at once.
---
# Documentation
|Type|description|
|---|---|
|[Pollable](#Pollable)||

|Value|description|
|---|---|
|[poll](#poll)||

## Pollable

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll/top.mbt,5:::pub(all) type Pollable Int
```

 `pollable` represents a single I/O event which may be ready, or not.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll/top.mbt,5:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll#Pollable">Pollable</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll/top.mbt,5:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll#Pollable">Pollable</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll#Pollable">Pollable</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll/top.mbt,5:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll#Pollable">Pollable</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll/top.mbt,5:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll#Pollable">Pollable</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### block
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll/top.mbt,30:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll#Pollable">Pollable</a>::block(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll#Pollable">Pollable</a>) -> Unit
  ```
  > 
  >  `block` returns immediately if the pollable is ready, and otherwise
  > blocks until ready.
  > 
  >  This function is equivalent to calling `poll.poll` on a list
  > containing only this pollable.
- #### drop
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll/top.mbt,11:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll#Pollable">Pollable</a>::drop(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll#Pollable">Pollable</a>) -> Unit
  ```
  > 
- #### ready
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll/top.mbt,19:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll#Pollable">Pollable</a>::ready(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll#Pollable">Pollable</a>) -> Bool
  ```
  > 
  >  Return the readiness of a pollable. This function never blocks.
  > 
  >  Returns `true` when the pollable is ready, and `false` otherwise.

## poll

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll/top.mbt,53:::fn poll(in_ : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll#Pollable">Pollable</a>]) -> <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[UInt]
```

 Poll for completion on a set of pollables.

 This function takes a list of pollables, which identify I/O sources of
interest, and waits until one or more of the events is ready for I/O.

 The result `list<u32>` contains one or more indices of handles in the
argument list that is ready for I/O.

 If the list contains more elements than can be indexed with a `u32`
value, this function traps.

 A timeout can be implemented by adding a pollable from the
wasi-clocks API to the list.

 This function does not return a `result`; polling in itself does not
do any I/O so it doesn't fail. If any of the I/O sources identified by
the pollables has an error, it is indicated by marking the source as
being reaedy for I/O.
