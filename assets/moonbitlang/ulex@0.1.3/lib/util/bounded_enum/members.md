# Documentation
|Trait|description|
|---|---|
|[@moonbitlang/ulex/lib/util/bounded\_enum.BoundedEnum](#@moonbitlang/ulex/lib/util/bounded_enum.BoundedEnum)||

|Type|description|
|---|---|
|[T](#T)||

## @moonbitlang/ulex/lib/util/bounded\_enum.BoundedEnum

```moonbit
:::source,moonbitlang/ulex/lib/util/bounded_enum/bounded_enum.mbt,2:::pub(open) trait @moonbitlang/ulex/lib/util/bounded_enum.BoundedEnum : <a href="moonbitlang/core/builtin#Compare">Compare</a> {
  pred(Self) -> Self
  succ(Self) -> Self
  lower_bound() -> Self
  upper_bound() -> Self
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/bounded_enum/impl_for_char.mbt,2:::impl <a href="moonbitlang/ulex/lib/util/bounded_enum#BoundedEnum">BoundedEnum</a> for Char
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/bounded_enum/impl_for_char.mbt,12:::fn lower_bound() -> Char
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/bounded_enum/impl_for_char.mbt,2:::fn pred(self : Char) -> Char
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/bounded_enum/impl_for_char.mbt,7:::fn succ(self : Char) -> Char
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/bounded_enum/impl_for_char.mbt,17:::fn upper_bound() -> Char
    ```
    > 

## T

```moonbit
:::source,moonbitlang/ulex/lib/util/bounded_enum/bounded_enum.mbt,10:::type T = <a href="moonbitlang/ulex/lib/util/bounded_enum#BoundedEnum">BoundedEnum</a>
```

