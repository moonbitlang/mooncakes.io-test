# Documentation
|Type|description|
|---|---|
|[Tree](#Tree)||
|[T](#T)||

|Value|description|
|---|---|
|[complement](#complement)||
|[contains](#contains)||
|[difference](#difference)||
|[empty](#empty)||
|[intersection](#intersection)||
|[interval](#interval)||
|[is\_empty](#is_empty)||
|[iter](#iter)||
|[iter\_intervals](#iter_intervals)||
|[of](#of)||
|[singleton](#singleton)||
|[slice](#slice)||
|[union](#union)||

## Tree

```moonbit
:::source,moonbitlang/ulex/lib/util/diet/types.mbt,5:::type Tree[T]
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/diet/traits_impl.mbt,21:::impl[N : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Compare">Compare</a> for <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/diet/traits_impl.mbt,21:::fn compare[N : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N], other : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/diet/traits_impl.mbt,2:::impl[N] <a href="moonbitlang/core/builtin#Default">Default</a> for <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/diet/traits_impl.mbt,2:::fn default[N]() -> <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]
    ```
    > 
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/diet/traits_impl.mbt,7:::impl[N : <a href="moonbitlang/core/builtin#Eq">Eq</a>] <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/diet/traits_impl.mbt,7:::fn op_equal[N : <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N], other : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/diet/traits_impl.mbt,40:::impl[N : <a href="moonbitlang/core/builtin#Hash">Hash</a>] <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/diet/traits_impl.mbt,40:::fn hash_combine[N : <a href="moonbitlang/core/builtin#Hash">Hash</a>](self : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N], hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### complement
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/diet/ops.mbt,105:::fn <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>::complement[N : <a href="moonbitlang/ulex/lib/util/bounded_enum#BoundedEnum">@moonbitlang/ulex/lib/util/bounded_enum.BoundedEnum</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]) -> <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]
  ```
  > 
- #### contains
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/diet/ops.mbt,10:::fn <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>::contains[N : <a href="moonbitlang/ulex/lib/util/bounded_enum#BoundedEnum">@moonbitlang/ulex/lib/util/bounded_enum.BoundedEnum</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N], x : N) -> Bool
  ```
  > 
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/diet/ops.mbt,2:::fn <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>::is_empty[N](self : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]) -> Bool
  ```
  > 
- #### iter
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/diet/iter.mbt,21:::fn <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>::iter[N : <a href="moonbitlang/ulex/lib/util/bounded_enum#BoundedEnum">@moonbitlang/ulex/lib/util/bounded_enum.BoundedEnum</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[N]
  ```
  > 
- #### iter\_intervals
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/diet/iter.mbt,2:::fn <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>::iter_intervals[N](self : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[(N, N)]
  ```
  > 
- #### slice
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/diet/slice.mbt,50:::fn <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>::slice[N : <a href="moonbitlang/ulex/lib/util/bounded_enum#BoundedEnum">@moonbitlang/ulex/lib/util/bounded_enum.BoundedEnum</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N], min? : N, max? : N) -> <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]
  ```
  > 

## T

```moonbit
:::source,moonbitlang/ulex/lib/util/diet/types.mbt,2:::type T[T] = <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[T]
```


## complement

```moonbit
:::source,moonbitlang/ulex/lib/util/diet/ops.mbt,105:::fn complement[N : <a href="moonbitlang/ulex/lib/util/bounded_enum#BoundedEnum">@moonbitlang/ulex/lib/util/bounded_enum.BoundedEnum</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]) -> <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]
```


## contains

```moonbit
:::source,moonbitlang/ulex/lib/util/diet/ops.mbt,10:::fn contains[N : <a href="moonbitlang/ulex/lib/util/bounded_enum#BoundedEnum">@moonbitlang/ulex/lib/util/bounded_enum.BoundedEnum</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N], x : N) -> Bool
```


## difference

```moonbit
:::source,moonbitlang/ulex/lib/util/diet/ops.mbt,134:::fn difference[N : <a href="moonbitlang/ulex/lib/util/bounded_enum#BoundedEnum">@moonbitlang/ulex/lib/util/bounded_enum.BoundedEnum</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](t1 : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N], t2 : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]) -> <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]
```


## empty

```moonbit
:::source,moonbitlang/ulex/lib/util/diet/builders.mbt,2:::fn empty[N]() -> <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]
```


## intersection

```moonbit
:::source,moonbitlang/ulex/lib/util/diet/ops.mbt,80:::fn intersection[N : <a href="moonbitlang/ulex/lib/util/bounded_enum#BoundedEnum">@moonbitlang/ulex/lib/util/bounded_enum.BoundedEnum</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](t1 : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N], t2 : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]) -> <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]
```


## interval

```moonbit
:::source,moonbitlang/ulex/lib/util/diet/builders.mbt,12:::fn interval[N](min : N, max : N) -> <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]
```


## is\_empty

```moonbit
:::source,moonbitlang/ulex/lib/util/diet/ops.mbt,2:::fn is_empty[N](self : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]) -> Bool
```


## iter

```moonbit
:::source,moonbitlang/ulex/lib/util/diet/iter.mbt,21:::fn iter[N : <a href="moonbitlang/ulex/lib/util/bounded_enum#BoundedEnum">@moonbitlang/ulex/lib/util/bounded_enum.BoundedEnum</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[N]
```


## iter\_intervals

```moonbit
:::source,moonbitlang/ulex/lib/util/diet/iter.mbt,2:::fn iter_intervals[N](self : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[(N, N)]
```


## of

```moonbit
:::source,moonbitlang/ulex/lib/util/diet/builders.mbt,17:::fn of[N : <a href="moonbitlang/ulex/lib/util/bounded_enum#BoundedEnum">@moonbitlang/ulex/lib/util/bounded_enum.BoundedEnum</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](array : <a href="moonbitlang/core/array#Array">Array</a>[N]) -> <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]
```


## singleton

```moonbit
:::source,moonbitlang/ulex/lib/util/diet/builders.mbt,7:::fn singleton[N](x : N) -> <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]
```


## slice

```moonbit
:::source,moonbitlang/ulex/lib/util/diet/slice.mbt,50:::fn slice[N : <a href="moonbitlang/ulex/lib/util/bounded_enum#BoundedEnum">@moonbitlang/ulex/lib/util/bounded_enum.BoundedEnum</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](self : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N], min? : N, max? : N) -> <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]
```


## union

```moonbit
:::source,moonbitlang/ulex/lib/util/diet/ops.mbt,25:::fn union[N : <a href="moonbitlang/ulex/lib/util/bounded_enum#BoundedEnum">@moonbitlang/ulex/lib/util/bounded_enum.BoundedEnum</a> + <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](t1 : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N], t2 : <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]) -> <a href="moonbitlang/ulex/lib/util/diet#Tree">Tree</a>[N]
```

