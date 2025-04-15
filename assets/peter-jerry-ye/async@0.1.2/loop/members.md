# Documentation
|Trait|description|
|---|---|
|[@peter-jerry-ye/async/loop.Sync](#@peter-jerry-ye/async/loop.Sync)||

|Type|description|
|---|---|
|[Handler](#Handler)||
|[T](#T)||

|Value|description|
|---|---|
|[new](#new)||
|[on\_ready](#on_ready)||
|[run](#run)||
|[run\_until](#run_until)||
|[sync](#sync)||

## @peter-jerry-ye/async/loop.Sync

```moonbit
:::source,peter-jerry-ye/async/loop/types.mbt,20:::pub(open) trait @peter-jerry-ye/async/loop.Sync {
  sync(<a href="moonbitlang/core/array#Array">Array</a>[Self]) -> <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[UInt]
}
```

 Types that can be synced.
 
 It should be able to sync an array of itself
and return the indices of finished items.

## Handler

```moonbit
:::source,peter-jerry-ye/async/loop/types.mbt,30:::type Handler
```


#### mooncakes-io-method-mark-Methods
- #### is\_stopped
  ```moonbit
  :::source,peter-jerry-ye/async/loop/handler.mbt,35:::fn <a href="peter-jerry-ye/async/loop#Handler">Handler</a>::is_stopped(self : <a href="peter-jerry-ye/async/loop#Handler">Handler</a>) -> Bool
  ```
  > 
- #### make
  ```moonbit
  :::source,peter-jerry-ye/async/loop/handler.mbt,16:::fn <a href="peter-jerry-ye/async/loop#Handler">Handler</a>::make(action~ : (<a href="peter-jerry-ye/async/loop#Handler">Handler</a>) -> Unit, stop_action~ : () -> Unit = ..) -> <a href="peter-jerry-ye/async/loop#Handler">Handler</a>
  ```
  > 
- #### start
  ```moonbit
  :::source,peter-jerry-ye/async/loop/handler.mbt,24:::fn <a href="peter-jerry-ye/async/loop#Handler">Handler</a>::start(self : <a href="peter-jerry-ye/async/loop#Handler">Handler</a>) -> Unit
  ```
  > 
- #### stop
  ```moonbit
  :::source,peter-jerry-ye/async/loop/handler.mbt,29:::fn <a href="peter-jerry-ye/async/loop#Handler">Handler</a>::stop(self : <a href="peter-jerry-ye/async/loop#Handler">Handler</a>) -> Unit
  ```
  > 

## T

```moonbit
:::source,peter-jerry-ye/async/loop/types.mbt,25:::type T[A]
```


#### mooncakes-io-method-mark-Methods
- #### on\_ready
  ```moonbit
  :::source,peter-jerry-ye/async/loop/core.mbt,60:::fn <a href="peter-jerry-ye/async/loop#T">T</a>::on_ready[A : <a href="peter-jerry-ye/async/loop#Sync">Sync</a>](self : <a href="peter-jerry-ye/async/loop#T">T</a>[A], subscribe : A, action : (<a href="peter-jerry-ye/async/loop#Handler">Handler</a>) -> Unit, stop_action~ : () -> Unit = ..) -> Unit
  ```
  > 
- #### run
  ```moonbit
  :::source,peter-jerry-ye/async/loop/core.mbt,99:::fn <a href="peter-jerry-ye/async/loop#T">T</a>::run[A : <a href="peter-jerry-ye/async/loop#Sync">Sync</a>](self : <a href="peter-jerry-ye/async/loop#T">T</a>[A]) -> Unit
  ```
  > 
- #### run\_until
  ```moonbit
  :::source,peter-jerry-ye/async/loop/core.mbt,92:::fn <a href="peter-jerry-ye/async/loop#T">T</a>::run_until[A : <a href="peter-jerry-ye/async/loop#Sync">Sync</a>](self : <a href="peter-jerry-ye/async/loop#T">T</a>[A], done : () -> Bool) -> Unit
  ```
  > 
- #### sync
  ```moonbit
  :::source,peter-jerry-ye/async/loop/core.mbt,82:::fn <a href="peter-jerry-ye/async/loop#T">T</a>::sync[A : <a href="peter-jerry-ye/async/loop#Sync">Sync</a>](self : <a href="peter-jerry-ye/async/loop#T">T</a>[A], subscribe : A) -> Unit
  ```
  > 

## new

```moonbit
:::source,peter-jerry-ye/async/loop/core.mbt,16:::fn new[A : <a href="peter-jerry-ye/async/loop#Sync">Sync</a>]() -> <a href="peter-jerry-ye/async/loop#T">T</a>[A]
```


## on\_ready

```moonbit
:::source,peter-jerry-ye/async/loop/core.mbt,60:::fn on_ready[A : <a href="peter-jerry-ye/async/loop#Sync">Sync</a>](self : <a href="peter-jerry-ye/async/loop#T">T</a>[A], subscribe : A, action : (<a href="peter-jerry-ye/async/loop#Handler">Handler</a>) -> Unit, stop_action~ : () -> Unit = ..) -> Unit
```


## run

```moonbit
:::source,peter-jerry-ye/async/loop/core.mbt,99:::fn run[A : <a href="peter-jerry-ye/async/loop#Sync">Sync</a>](self : <a href="peter-jerry-ye/async/loop#T">T</a>[A]) -> Unit
```


## run\_until

```moonbit
:::source,peter-jerry-ye/async/loop/core.mbt,92:::fn run_until[A : <a href="peter-jerry-ye/async/loop#Sync">Sync</a>](self : <a href="peter-jerry-ye/async/loop#T">T</a>[A], done : () -> Bool) -> Unit
```


## sync

```moonbit
:::source,peter-jerry-ye/async/loop/core.mbt,82:::fn sync[A : <a href="peter-jerry-ye/async/loop#Sync">Sync</a>](self : <a href="peter-jerry-ye/async/loop#T">T</a>[A], subscribe : A) -> Unit
```

