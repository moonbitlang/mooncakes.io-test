# Documentation
|Type|description|
|---|---|
|[UInt](#UInt)||

|Value|description|
|---|---|
|[default](#default)||
|[max\_value](#max_value)||
|[min\_value](#min_value)||
|[to\_be\_bytes](#to_be_bytes)| Converts the UInt to a Bytes in big-endian byte order.|
|[to\_int64](#to_int64)||
|[to\_le\_bytes](#to_le_bytes)| Converts the UInt to a Bytes in little-endian byte order.|

## default

```moonbit
:::source,moonbitlang/core/uint/uint.mbt,33:::fn default() -> UInt
```

 same as `UInt::default`

## max\_value

```moonbit
:::source,moonbitlang/core/uint/uint.mbt,19:::let max_value : UInt
```


## min\_value

```moonbit
:::source,moonbitlang/core/uint/uint.mbt,16:::let min_value : UInt
```


## to\_be\_bytes

```moonbit
:::source,moonbitlang/core/uint/uint.mbt,38:::fn to_be_bytes(self : UInt) -> Bytes
```
 Converts the UInt to a Bytes in big-endian byte order.

## to\_int64

```moonbit
:::source,moonbitlang/core/uint/uint.mbt,22:::fn to_int64(self : UInt) -> Int64
```


## to\_le\_bytes

```moonbit
:::source,moonbitlang/core/uint/uint.mbt,48:::fn to_le_bytes(self : UInt) -> Bytes
```
 Converts the UInt to a Bytes in little-endian byte order.

## UInt


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/uint/uint.mbt,27:::impl <a href="moonbitlang/core/builtin#Default">Default</a> for UInt
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/uint/uint.mbt,27:::fn default() -> UInt
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### to\_be\_bytes
  ```moonbit
  :::source,moonbitlang/core/uint/uint.mbt,38:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::to_be_bytes(self : UInt) -> Bytes
  ```
  >  Converts the UInt to a Bytes in big-endian byte order.
- #### to\_int64
  ```moonbit
  :::source,moonbitlang/core/uint/uint.mbt,22:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::to_int64(self : UInt) -> Int64
  ```
  > 
- #### to\_le\_bytes
  ```moonbit
  :::source,moonbitlang/core/uint/uint.mbt,48:::fn <a href="moonbitlang/core/uint#UInt">UInt</a>::to_le_bytes(self : UInt) -> Bytes
  ```
  >  Converts the UInt to a Bytes in little-endian byte order.
