# Documentation
|Type|description|
|---|---|
|[Int64](#Int64)||

|Value|description|
|---|---|
|[abs](#abs)||
|[from\_int](#from_int)||
|[max\_value](#max_value)||
|[min\_value](#min_value)||
|[to\_be\_bytes](#to_be_bytes)| Converts the Int64 to a Bytes in big-endian byte order.|
|[to\_le\_bytes](#to_le_bytes)| Converts the Int64 to a Bytes in little-endian byte order.|

## abs

```moonbit
:::source,moonbitlang/core/int64/int64.mbt,65:::fn abs(self : Int64) -> Int64
```

 Computes the absolute value of a 64-bit integer.

 Parameters:

 * `self` : The 64-bit integer whose absolute value is to be computed.

 Returns the absolute value of the input integer.

 Example:

 ```moonbit
 test "abs" {
   inspect!(42L.abs(), content="42")
   inspect!((-42L).abs(), content="42")
   inspect!(0L.abs(), content="0")
 }
 ```

## from\_int

```moonbit
:::source,moonbitlang/core/int64/int64.mbt,43:::fn from_int(i : Int) -> Int64
```

 same as `Int64::from_int`

## max\_value

```moonbit
:::source,moonbitlang/core/int64/int64.mbt,16:::let max_value : Int64
```


## min\_value

```moonbit
:::source,moonbitlang/core/int64/int64.mbt,19:::let min_value : Int64
```


## to\_be\_bytes

```moonbit
:::source,moonbitlang/core/int64/int64.mbt,74:::fn to_be_bytes(self : Int64) -> Bytes
```
 Converts the Int64 to a Bytes in big-endian byte order.

## to\_le\_bytes

```moonbit
:::source,moonbitlang/core/int64/int64.mbt,79:::fn to_le_bytes(self : Int64) -> Bytes
```
 Converts the Int64 to a Bytes in little-endian byte order.

## Int64


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/int64/xxhash.mbt,33:::impl <a href="moonbitlang/core/builtin#Hash">Hash</a> for Int64
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/int64/xxhash.mbt,33:::fn hash(self : Int64) -> Int
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/core/int64/xxhash.mbt,53:::fn hash_combine(self : Int64, hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### abs
  ```moonbit
  :::source,moonbitlang/core/int64/int64.mbt,65:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::abs(self : Int64) -> Int64
  ```
  > 
  >  Computes the absolute value of a 64-bit integer.
  > 
  >  Parameters:
  > 
  >  * `self` : The 64-bit integer whose absolute value is to be computed.
  > 
  >  Returns the absolute value of the input integer.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "abs" {
  >    inspect!(42L.abs(), content="42")
  >    inspect!((-42L).abs(), content="42")
  >    inspect!(0L.abs(), content="0")
  >  }
  >  ```
- #### from\_int
  ```moonbit
  :::source,moonbitlang/core/int64/int64.mbt,37:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::from_int(i : Int) -> Int64
  ```
  > 
  >  Converts a 32-bit integer (`Int`) to a 64-bit integer (`Int64`).
  > 
  >  Parameters:
  > 
  >  * `i` : The integer value to be converted.
  > 
  >  Returns the converted 64-bit integer (`Int64`) value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "Int64::from_int" {
  >    inspect!(@int64.from_int(42), content="42")
  >  }
  >  ```
- #### to\_be\_bytes
  ```moonbit
  :::source,moonbitlang/core/int64/int64.mbt,74:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::to_be_bytes(self : Int64) -> Bytes
  ```
  >  Converts the Int64 to a Bytes in big-endian byte order.
- #### to\_le\_bytes
  ```moonbit
  :::source,moonbitlang/core/int64/int64.mbt,79:::fn <a href="moonbitlang/core/int64#Int64">Int64</a>::to_le_bytes(self : Int64) -> Bytes
  ```
  >  Converts the Int64 to a Bytes in little-endian byte order.
