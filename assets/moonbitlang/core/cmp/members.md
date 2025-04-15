# Documentation
|Value|description|
|---|---|
|[maximum\_by\_key](#maximum_by_key)| Returns the element that gives the maximum value from the specified function.|
|[minimum\_by\_key](#minimum_by_key)| Returns the element that gives the minimum value from the specified function.|

## maximum\_by\_key

```moonbit
:::source,moonbitlang/core/cmp/cmp.mbt,25:::fn maximum_by_key[T, K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](x : T, y : T, f : (T) -> K) -> T
```
 Returns the element that gives the maximum value from the specified function.

 Returns the second argument if the comparison determines them to be equal.

 #### Examples

 ```
 inspect!(@cmp.maximum_by_key(-2, 1, @int.abs), content="-2")
 inspect!(@cmp.maximum_by_key(-2, 2, @int.abs), content="2")
 ```

## minimum\_by\_key

```moonbit
:::source,moonbitlang/core/cmp/cmp.mbt,43:::fn minimum_by_key[T, K : <a href="moonbitlang/core/builtin#Compare">Compare</a> + <a href="moonbitlang/core/builtin#Eq">Eq</a>](x : T, y : T, f : (T) -> K) -> T
```
 Returns the element that gives the minimum value from the specified function.

 Returns the first argument if the comparison determines them to be equal.

 #### Examples

 ```
 inspect!(@cmp.minimum_by_key(-2, 1, @int.abs), content="1")
 inspect!(@cmp.minimum_by_key(-2, 2, @int.abs), content="-2")
 ```
