# Documentation
|Type|description|
|---|---|
|[EofChar](#EofChar)||
|[EofCharRepr](#EofCharRepr)||
|[EofCharSet](#EofCharSet)||
|[T](#T)||

|Value|description|
|---|---|
|[any](#any)| The set of all characters.|
|[complement](#complement)||
|[contains](#contains)||
|[difference](#difference)||
|[disjoint](#disjoint)||
|[empty](#empty)||
|[eof](#eof)| The pseudo-character indicating the end of the input.|
|[intersection](#intersection)||
|[is\_empty](#is_empty)||
|[iter](#iter)||
|[iter\_ranges](#iter_ranges)||
|[negated](#negated)||
|[of\_array](#of_array)||
|[range](#range)||
|[singleton](#singleton)||
|[slice](#slice)||
|[subset](#subset)||
|[union](#union)||

## EofChar

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,2:::type EofChar
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,2:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,2:::fn compare(<a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>, <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>) -> Int
    ```
    > automatically derived
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,2:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,2:::fn op_equal(<a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>, <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,2:::impl <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,2:::fn hash_combine(<a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>, <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,2:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,2:::fn output(<a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,2:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,2:::fn to_json(<a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > automatically derived
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,11:::impl <a href="moonbitlang/ulex/lib/util/bounded_enum#BoundedEnum">@moonbitlang/ulex/lib/util/bounded_enum.BoundedEnum</a> for <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,11:::fn lower_bound() -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,21:::fn pred(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,27:::fn succ(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,16:::fn upper_bound() -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### char
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,38:::fn <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>::char(x : Char) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>
  ```
  > 
- #### eof
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,33:::fn <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>::eof() -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>
  ```
  > 
- #### repr
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,43:::fn <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>::repr(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharRepr">EofCharRepr</a>
  ```
  > 

## EofCharRepr

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char.mbt,5:::pub enum EofCharRepr {
  Eof
  Char(Char)
}
```


## EofCharSet

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,5:::type EofCharSet
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,5:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,5:::fn compare(<a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> Int
    ```
    > automatically derived
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,5:::impl <a href="moonbitlang/core/builtin#Default">Default</a> for <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,5:::fn default() -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
    ```
    > automatically derived
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,5:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,5:::fn op_equal(<a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,5:::impl <a href="moonbitlang/core/builtin#Hash">Hash</a> for <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,5:::fn hash_combine(<a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,122:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,122:::fn output(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,134:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,134:::fn to_json(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### complement
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,72:::fn <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>::complement(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
  ```
  > 
- #### contains
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,43:::fn <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>::contains(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, x : Char) -> Bool
  ```
  > 
- #### difference
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,77:::fn <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>::difference(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, other : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
  ```
  > 
- #### disjoint
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,87:::fn <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>::disjoint(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, other : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> Bool
  ```
  > 
- #### intersection
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,67:::fn <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>::intersection(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, other : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
  ```
  > 
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,38:::fn <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>::is_empty(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> Bool
  ```
  > 
- #### iter
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,117:::fn <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>::iter(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[<a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>]
  ```
  > 
- #### iter\_ranges
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,112:::fn <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>::iter_ranges(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[(<a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>, <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>)]
  ```
  > 
- #### land
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,107:::fn <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>::land(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, other : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
  ```
  > 
- #### negated
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,33:::fn <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>::negated(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
  ```
  > 
- #### op\_add
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,97:::fn <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>::op_add(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, other : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
  ```
  > 
- #### op\_neg
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,92:::fn <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>::op_neg(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
  ```
  > 
- #### op\_sub
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,102:::fn <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>::op_sub(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, other : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
  ```
  > 
- #### slice
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,48:::fn <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>::slice(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, min? : Char, max? : Char) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
  ```
  > 
- #### subset
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,82:::fn <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>::subset(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, other : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> Bool
  ```
  > 
- #### union
  ```moonbit
  :::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,62:::fn <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>::union(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, other : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
  ```
  > 

## T

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,2:::type T = <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
```


## any

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,25:::let any : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
```
 The set of all characters.
Does not include the EOF character.

## complement

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,72:::fn complement(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
```


## contains

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,43:::fn contains(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, x : Char) -> Bool
```


## difference

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,77:::fn difference(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, other : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
```


## disjoint

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,87:::fn disjoint(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, other : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> Bool
```


## empty

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,8:::let empty : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
```


## eof

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,16:::let eof : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
```
 The pseudo-character indicating the end of the input.

## intersection

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,67:::fn intersection(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, other : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
```


## is\_empty

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,38:::fn is_empty(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> Bool
```


## iter

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,117:::fn iter(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[<a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>]
```


## iter\_ranges

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,112:::fn iter_ranges(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[(<a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>, <a href="moonbitlang/ulex/lib/util/eof_char_set#EofChar">EofChar</a>)]
```


## negated

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,33:::fn negated(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
```


## of\_array

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,28:::fn of_array(arr : <a href="moonbitlang/core/array#Array">Array</a>[Char]) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
```


## range

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,19:::fn range(min : Char, max : Char) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
```


## singleton

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,11:::fn singleton(x : Char) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
```


## slice

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,48:::fn slice(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, min? : Char, max? : Char) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
```


## subset

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,82:::fn subset(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, other : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> Bool
```


## union

```moonbit
:::source,moonbitlang/ulex/lib/util/eof_char_set/eof_char_set.mbt,62:::fn union(self : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>, other : <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>) -> <a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">EofCharSet</a>
```

