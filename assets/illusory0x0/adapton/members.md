# Documentation
|Trait|description|
|---|---|
|[@illusory0x0/adapton.Source](#@illusory0x0/adapton.Source)||

|Type|description|
|---|---|
|[Cell](#Cell)||
|[Thunk](#Thunk)||

|Value|description|
|---|---|
|[clear\_memo](#clear_memo)||
|[memo](#memo)||
|[memo\_rec](#memo_rec)||

## @illusory0x0/adapton.Source

```moonbit
:::source,illusory0x0/adapton/adapton.mbt,46:::trait @illusory0x0/adapton.Source
```


## Cell

```moonbit
:::source,illusory0x0/adapton/adapton.mbt,13:::type Cell[A]
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,illusory0x0/adapton/adapton.mbt,127:::impl[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="illusory0x0/adapton#Source">Source</a> for <a href="illusory0x0/adapton#Cell">Cell</a>[A]
  ```
  > 
  * ```moonbit
    :::source,illusory0x0/adapton/adapton.mbt,127:::fn id[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="illusory0x0/adapton#Cell">Cell</a>[A]) -> Int
    ```
    > 
  * ```moonbit
    :::source,illusory0x0/adapton/adapton.mbt,309:::fn incoming_edges[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="illusory0x0/adapton#Cell">Cell</a>[A]) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="illusory0x0/adapton#Target">Target</a>]
    ```
    > 
  * ```moonbit
    :::source,illusory0x0/adapton/adapton.mbt,299:::fn to_node[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="illusory0x0/adapton#Cell">Cell</a>[A]) -> <a href="illusory0x0/adapton#Target">Target</a>?
    ```
    > 
- ```moonbit
  :::source,illusory0x0/adapton/adapton.mbt,137:::impl[A] <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="illusory0x0/adapton#Cell">Cell</a>[A]
  ```
  > 
  * ```moonbit
    :::source,illusory0x0/adapton/adapton.mbt,137:::fn op_equal[A](self : <a href="illusory0x0/adapton#Cell">Cell</a>[A], other : <a href="illusory0x0/adapton#Cell">Cell</a>[A]) -> Bool
    ```
    > 
- ```moonbit
  :::source,illusory0x0/adapton/adapton.mbt,147:::impl[A] <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="illusory0x0/adapton#Cell">Cell</a>[A]
  ```
  > 
  * ```moonbit
    :::source,illusory0x0/adapton/adapton.mbt,147:::fn hash_combine[A](self : <a href="illusory0x0/adapton#Cell">Cell</a>[A], hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### get
  ```moonbit
  :::source,illusory0x0/adapton/adapton.mbt,212:::fn <a href="illusory0x0/adapton#Cell">Cell</a>::get[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="illusory0x0/adapton#Cell">Cell</a>[A]) -> A
  ```
  > 
- #### modify
  ```moonbit
  :::source,illusory0x0/adapton/adapton.mbt,188:::fn <a href="illusory0x0/adapton#Cell">Cell</a>::modify[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="illusory0x0/adapton#Cell">Cell</a>[A], f : (A) -> A) -> Unit
  ```
  > 
- #### new
  ```moonbit
  :::source,illusory0x0/adapton/adapton.mbt,173:::fn <a href="illusory0x0/adapton#Cell">Cell</a>::new[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](value : A) -> <a href="illusory0x0/adapton#Cell">Cell</a>[A]
  ```
  > 
- #### set
  ```moonbit
  :::source,illusory0x0/adapton/adapton.mbt,178:::fn <a href="illusory0x0/adapton#Cell">Cell</a>::set[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="illusory0x0/adapton#Cell">Cell</a>[A], value : A) -> Unit
  ```
  > 

## Thunk

```moonbit
:::source,illusory0x0/adapton/adapton.mbt,20:::type Thunk[A]
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,illusory0x0/adapton/adapton.mbt,122:::impl[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="illusory0x0/adapton#Source">Source</a> for <a href="illusory0x0/adapton#Thunk">Thunk</a>[A]
  ```
  > 
  * ```moonbit
    :::source,illusory0x0/adapton/adapton.mbt,122:::fn id[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="illusory0x0/adapton#Thunk">Thunk</a>[A]) -> Int
    ```
    > 
  * ```moonbit
    :::source,illusory0x0/adapton/adapton.mbt,314:::fn incoming_edges[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="illusory0x0/adapton#Thunk">Thunk</a>[A]) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="illusory0x0/adapton#Target">Target</a>]
    ```
    > 
  * ```moonbit
    :::source,illusory0x0/adapton/adapton.mbt,304:::fn to_node[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="illusory0x0/adapton#Thunk">Thunk</a>[A]) -> <a href="illusory0x0/adapton#Target">Target</a>?
    ```
    > 
- ```moonbit
  :::source,illusory0x0/adapton/adapton.mbt,132:::impl[A] <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="illusory0x0/adapton#Thunk">Thunk</a>[A]
  ```
  > 
  * ```moonbit
    :::source,illusory0x0/adapton/adapton.mbt,132:::fn op_equal[A](self : <a href="illusory0x0/adapton#Thunk">Thunk</a>[A], other : <a href="illusory0x0/adapton#Thunk">Thunk</a>[A]) -> Bool
    ```
    > 
- ```moonbit
  :::source,illusory0x0/adapton/adapton.mbt,142:::impl[A] <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="illusory0x0/adapton#Thunk">Thunk</a>[A]
  ```
  > 
  * ```moonbit
    :::source,illusory0x0/adapton/adapton.mbt,142:::fn hash_combine[A](self : <a href="illusory0x0/adapton#Thunk">Thunk</a>[A], hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### get
  ```moonbit
  :::source,illusory0x0/adapton/adapton.mbt,196:::fn <a href="illusory0x0/adapton#Thunk">Thunk</a>::get[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="illusory0x0/adapton#Thunk">Thunk</a>[A]) -> A
  ```
  > 
- #### new
  ```moonbit
  :::source,illusory0x0/adapton/adapton.mbt,161:::fn <a href="illusory0x0/adapton#Thunk">Thunk</a>::new[A : <a href="moonbitlang/core/builtin#Eq">Eq</a>](thunk : () -> A) -> <a href="illusory0x0/adapton#Thunk">Thunk</a>[A]
  ```
  > 

## clear\_memo

```moonbit
:::source,illusory0x0/adapton/adapton.mbt,230:::fn clear_memo() -> Unit
```


## memo

```moonbit
:::source,illusory0x0/adapton/adapton.mbt,238:::fn memo[A : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, B : <a href="moonbitlang/core/builtin#Eq">Eq</a>](f : (A) -> B) -> ((A) -> <a href="illusory0x0/adapton#Thunk">Thunk</a>[B])
```


## memo\_rec

```moonbit
:::source,illusory0x0/adapton/adapton.mbt,254:::fn memo_rec[A : <a href="moonbitlang/core/builtin#Hash">Hash</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>, B : <a href="moonbitlang/core/builtin#Eq">Eq</a>](f : ((A) -> <a href="illusory0x0/adapton#Thunk">Thunk</a>[B], A) -> B) -> ((A) -> <a href="illusory0x0/adapton#Thunk">Thunk</a>[B])
```

