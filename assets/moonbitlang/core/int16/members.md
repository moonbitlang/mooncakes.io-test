# Documentation
|Type|description|
|---|---|
|[Int16](#Int16)||

|Value|description|
|---|---|
|[max\_value](#max_value)||
|[min\_value](#min_value)||

## max\_value

```moonbit
:::source,moonbitlang/core/int16/int16.mbt,16:::let max_value : Int16
```


## min\_value

```moonbit
:::source,moonbitlang/core/int16/int16.mbt,19:::let min_value : Int16
```


## Int16


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/int16/int16.mbt,22:::impl <a href="moonbitlang/core/builtin#Add">Add</a> for Int16
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/int16/int16.mbt,22:::fn op_add(self : Int16, that : Int16) -> Int16
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/int16/int16.mbt,77:::impl <a href="moonbitlang/core/builtin#BitAnd">BitAnd</a> for Int16
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/int16/int16.mbt,77:::fn land(self : Int16, that : Int16) -> Int16
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/int16/int16.mbt,72:::impl <a href="moonbitlang/core/builtin#BitOr">BitOr</a> for Int16
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/int16/int16.mbt,72:::fn lor(self : Int16, that : Int16) -> Int16
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/int16/int16.mbt,82:::impl <a href="moonbitlang/core/builtin#BitXOr">BitXOr</a> for Int16
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/int16/int16.mbt,82:::fn lxor(self : Int16, that : Int16) -> Int16
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/int16/int16.mbt,47:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for Int16
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/int16/int16.mbt,47:::fn compare(self : Int16, that : Int16) -> Int
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/int16/int16.mbt,87:::impl <a href="moonbitlang/core/builtin#Default">Default</a> for Int16
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/int16/int16.mbt,87:::fn default() -> Int16
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/int16/int16.mbt,37:::impl <a href="moonbitlang/core/builtin#Div">Div</a> for Int16
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/int16/int16.mbt,37:::fn op_div(self : Int16, that : Int16) -> Int16
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/int16/int16.mbt,42:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for Int16
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/int16/int16.mbt,42:::fn op_equal(self : Int16, that : Int16) -> Bool
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/int16/int16.mbt,52:::impl <a href="moonbitlang/core/builtin#Hash">Hash</a> for Int16
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/int16/int16.mbt,52:::fn hash(self : Int16) -> Int
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/core/int16/int16.mbt,57:::fn hash_combine(self : Int16, hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/int16/int16.mbt,32:::impl <a href="moonbitlang/core/builtin#Mul">Mul</a> for Int16
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/int16/int16.mbt,32:::fn op_mul(self : Int16, that : Int16) -> Int16
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/int16/int16.mbt,62:::impl <a href="moonbitlang/core/builtin#Shl">Shl</a> for Int16
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/int16/int16.mbt,62:::fn op_shl(self : Int16, that : Int) -> Int16
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/int16/int16.mbt,67:::impl <a href="moonbitlang/core/builtin#Shr">Shr</a> for Int16
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/int16/int16.mbt,67:::fn op_shr(self : Int16, that : Int) -> Int16
    ```
    > 
- ```moonbit
  :::source,moonbitlang/core/int16/int16.mbt,27:::impl <a href="moonbitlang/core/builtin#Sub">Sub</a> for Int16
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/int16/int16.mbt,27:::fn op_sub(self : Int16, that : Int16) -> Int16
    ```
    > 
