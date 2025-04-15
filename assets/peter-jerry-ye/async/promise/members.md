# Documentation
|Type|description|
|---|---|
|[AggregateError](#AggregateError)||
|[Resolver](#Resolver)||
|[T](#T)||

|Value|description|
|---|---|
|[all](#all)||
|[any](#any)||
|[await](#await)||
|[bind](#bind)||
|[finally](#finally)||
|[future](#future)||
|[get](#get)||
|[make](#make)||
|[on\_failure](#on_failure)||
|[on\_success](#on_success)||
|[reject](#reject)||
|[resolve](#resolve)||
|[spawn](#spawn)||
|[try\_complete](#try_complete)||
|[zip](#zip)||
|[zip\_with](#zip_with)||

## AggregateError

```moonbit
:::source,peter-jerry-ye/async/promise/top.mbt,178:::pub type! AggregateError <a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/core/error#Error">Error</a>]

```


## Resolver

```moonbit
:::source,peter-jerry-ye/async/promise/top.mbt,31:::type Resolver[A]
```


#### mooncakes-io-method-mark-Methods
- #### future
  ```moonbit
  :::source,peter-jerry-ye/async/promise/top.mbt,94:::fn <a href="peter-jerry-ye/async/promise#Resolver">Resolver</a>::future[A](self : <a href="peter-jerry-ye/async/promise#Resolver">Resolver</a>[A]) -> <a href="peter-jerry-ye/async/promise#T">T</a>[A]
  ```
  > 
- #### reject
  ```moonbit
  :::source,peter-jerry-ye/async/promise/top.mbt,76:::fn <a href="peter-jerry-ye/async/promise#Resolver">Resolver</a>::reject[A](self : <a href="peter-jerry-ye/async/promise#Resolver">Resolver</a>[A], err : <a href="moonbitlang/core/error#Error">Error</a>) -> Unit
  ```
  > 
- #### resolve
  ```moonbit
  :::source,peter-jerry-ye/async/promise/top.mbt,71:::fn <a href="peter-jerry-ye/async/promise#Resolver">Resolver</a>::resolve[A](self : <a href="peter-jerry-ye/async/promise#Resolver">Resolver</a>[A], result : A) -> Unit
  ```
  > 
- #### try\_complete
  ```moonbit
  :::source,peter-jerry-ye/async/promise/top.mbt,58:::fn <a href="peter-jerry-ye/async/promise#Resolver">Resolver</a>::try_complete[A](self : <a href="peter-jerry-ye/async/promise#Resolver">Resolver</a>[A], result : () -> A!<a href="moonbitlang/core/error#Error">Error</a>) -> Bool
  ```
  > 

## T

```moonbit
:::source,peter-jerry-ye/async/promise/top.mbt,26:::type T[A]
```


#### mooncakes-io-method-mark-Methods
- #### await
  ```moonbit
  :::source,peter-jerry-ye/async/promise/top.mbt,216:::fn <a href="peter-jerry-ye/async/promise#T">T</a>::await[A](self : <a href="peter-jerry-ye/async/promise#T">T</a>[A]) -> A!<a href="moonbitlang/core/error#Error">Error</a>
  ```
  > 
- #### bind
  ```moonbit
  :::source,peter-jerry-ye/async/promise/top.mbt,125:::fn <a href="peter-jerry-ye/async/promise#T">T</a>::bind[A, B](self : <a href="peter-jerry-ye/async/promise#T">T</a>[A], callback : (A) -> <a href="peter-jerry-ye/async/promise#T">T</a>[B]) -> <a href="peter-jerry-ye/async/promise#T">T</a>[B]
  ```
  > 
- #### finally
  ```moonbit
  :::source,peter-jerry-ye/async/promise/top.mbt,146:::fn <a href="peter-jerry-ye/async/promise#T">T</a>::finally[A](self : <a href="peter-jerry-ye/async/promise#T">T</a>[A], callback : () -> Unit) -> <a href="peter-jerry-ye/async/promise#T">T</a>[A]
  ```
  > 
- #### get
  ```moonbit
  :::source,peter-jerry-ye/async/promise/top.mbt,49:::fn <a href="peter-jerry-ye/async/promise#T">T</a>::get[A](self : <a href="peter-jerry-ye/async/promise#T">T</a>[A]) -> <a href="moonbitlang/core/result#Result">Result</a>[A, <a href="moonbitlang/core/error#Error">Error</a>]?
  ```
  > 
- #### on\_failure
  ```moonbit
  :::source,peter-jerry-ye/async/promise/top.mbt,112:::fn <a href="peter-jerry-ye/async/promise#T">T</a>::on_failure[A](self : <a href="peter-jerry-ye/async/promise#T">T</a>[A], callback : (<a href="moonbitlang/core/error#Error">Error</a>) -> Unit) -> Unit
  ```
  > 
- #### on\_success
  ```moonbit
  :::source,peter-jerry-ye/async/promise/top.mbt,99:::fn <a href="peter-jerry-ye/async/promise#T">T</a>::on_success[A](self : <a href="peter-jerry-ye/async/promise#T">T</a>[A], callback : (A) -> Unit) -> Unit
  ```
  > 
- #### zip
  ```moonbit
  :::source,peter-jerry-ye/async/promise/top.mbt,200:::fn <a href="peter-jerry-ye/async/promise#T">T</a>::zip[A, B](self : <a href="peter-jerry-ye/async/promise#T">T</a>[A], that : <a href="peter-jerry-ye/async/promise#T">T</a>[B]) -> <a href="peter-jerry-ye/async/promise#T">T</a>[(A, B)]
  ```
  > 
- #### zip\_with
  ```moonbit
  :::source,peter-jerry-ye/async/promise/top.mbt,205:::fn <a href="peter-jerry-ye/async/promise#T">T</a>::zip_with[A, B, C](self : <a href="peter-jerry-ye/async/promise#T">T</a>[A], that : <a href="peter-jerry-ye/async/promise#T">T</a>[B], f : (A, B) -> C) -> <a href="peter-jerry-ye/async/promise#T">T</a>[C]
  ```
  > 

## all

```moonbit
:::source,peter-jerry-ye/async/promise/top.mbt,159:::fn all[A](promises : <a href="moonbitlang/core/array#Array">Array</a>[<a href="peter-jerry-ye/async/promise#T">T</a>[A]]) -> <a href="peter-jerry-ye/async/promise#T">T</a>[<a href="moonbitlang/core/array#Array">Array</a>[A]]
```


## any

```moonbit
:::source,peter-jerry-ye/async/promise/top.mbt,181:::fn any[A](promises : <a href="moonbitlang/core/array#Array">Array</a>[<a href="peter-jerry-ye/async/promise#T">T</a>[A]]) -> <a href="peter-jerry-ye/async/promise#T">T</a>[A]
```


## await

```moonbit
:::source,peter-jerry-ye/async/promise/top.mbt,216:::fn await[A](self : <a href="peter-jerry-ye/async/promise#T">T</a>[A]) -> A!<a href="moonbitlang/core/error#Error">Error</a>
```


## bind

```moonbit
:::source,peter-jerry-ye/async/promise/top.mbt,125:::fn bind[A, B](self : <a href="peter-jerry-ye/async/promise#T">T</a>[A], callback : (A) -> <a href="peter-jerry-ye/async/promise#T">T</a>[B]) -> <a href="peter-jerry-ye/async/promise#T">T</a>[B]
```


## finally

```moonbit
:::source,peter-jerry-ye/async/promise/top.mbt,146:::fn finally[A](self : <a href="peter-jerry-ye/async/promise#T">T</a>[A], callback : () -> Unit) -> <a href="peter-jerry-ye/async/promise#T">T</a>[A]
```


## future

```moonbit
:::source,peter-jerry-ye/async/promise/top.mbt,94:::fn future[A](self : <a href="peter-jerry-ye/async/promise#Resolver">Resolver</a>[A]) -> <a href="peter-jerry-ye/async/promise#T">T</a>[A]
```


## get

```moonbit
:::source,peter-jerry-ye/async/promise/top.mbt,49:::fn get[A](self : <a href="peter-jerry-ye/async/promise#T">T</a>[A]) -> <a href="moonbitlang/core/result#Result">Result</a>[A, <a href="moonbitlang/core/error#Error">Error</a>]?
```


## make

```moonbit
:::source,peter-jerry-ye/async/promise/top.mbt,34:::fn make[A]() -> <a href="peter-jerry-ye/async/promise#Resolver">Resolver</a>[A]
```


## on\_failure

```moonbit
:::source,peter-jerry-ye/async/promise/top.mbt,112:::fn on_failure[A](self : <a href="peter-jerry-ye/async/promise#T">T</a>[A], callback : (<a href="moonbitlang/core/error#Error">Error</a>) -> Unit) -> Unit
```


## on\_success

```moonbit
:::source,peter-jerry-ye/async/promise/top.mbt,99:::fn on_success[A](self : <a href="peter-jerry-ye/async/promise#T">T</a>[A], callback : (A) -> Unit) -> Unit
```


## reject

```moonbit
:::source,peter-jerry-ye/async/promise/top.mbt,44:::fn reject[A](err : <a href="moonbitlang/core/error#Error">Error</a>) -> <a href="peter-jerry-ye/async/promise#T">T</a>[A]
```


## resolve

```moonbit
:::source,peter-jerry-ye/async/promise/top.mbt,39:::fn resolve[A](a : A) -> <a href="peter-jerry-ye/async/promise#T">T</a>[A]
```


## spawn

```moonbit
:::source,peter-jerry-ye/async/promise/top.mbt,224:::fn spawn[A](cb : ((() -> Unit) -> Unit) -> A!<a href="moonbitlang/core/error#Error">Error</a>) -> <a href="peter-jerry-ye/async/promise#T">T</a>[A]
```


## try\_complete

```moonbit
:::source,peter-jerry-ye/async/promise/top.mbt,58:::fn try_complete[A](self : <a href="peter-jerry-ye/async/promise#Resolver">Resolver</a>[A], result : () -> A!<a href="moonbitlang/core/error#Error">Error</a>) -> Bool
```


## zip

```moonbit
:::source,peter-jerry-ye/async/promise/top.mbt,200:::fn zip[A, B](self : <a href="peter-jerry-ye/async/promise#T">T</a>[A], that : <a href="peter-jerry-ye/async/promise#T">T</a>[B]) -> <a href="peter-jerry-ye/async/promise#T">T</a>[(A, B)]
```


## zip\_with

```moonbit
:::source,peter-jerry-ye/async/promise/top.mbt,205:::fn zip_with[A, B, C](self : <a href="peter-jerry-ye/async/promise#T">T</a>[A], that : <a href="peter-jerry-ye/async/promise#T">T</a>[B], f : (A, B) -> C) -> <a href="peter-jerry-ye/async/promise#T">T</a>[C]
```

