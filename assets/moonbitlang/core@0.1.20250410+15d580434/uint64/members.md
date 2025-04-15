# Documentation
|Type|description|
|---|---|
|[UInt64](#UInt64)||

|Value|description|
|---|---|
|[max\_value](#max_value)||
|[min\_value](#min_value)||
|[to\_be\_bytes](#to_be_bytes)| Converts the UInt64 to a Bytes in big-endian byte order.|
|[to\_le\_bytes](#to_le_bytes)| Converts the UInt64 to a Bytes in little-endian byte order.|

## max\_value

```moonbit
:::source,moonbitlang/core/uint64/uint64.mbt,19:::let max_value : UInt64
```


## min\_value

```moonbit
:::source,moonbitlang/core/uint64/uint64.mbt,16:::let min_value : UInt64
```


## to\_be\_bytes

```moonbit
:::source,moonbitlang/core/uint64/uint64.mbt,22:::fn to_be_bytes(self : UInt64) -> Bytes
```
 Converts the UInt64 to a Bytes in big-endian byte order.

## to\_le\_bytes

```moonbit
:::source,moonbitlang/core/uint64/uint64.mbt,36:::fn to_le_bytes(self : UInt64) -> Bytes
```
 Converts the UInt64 to a Bytes in little-endian byte order.

## UInt64


#### mooncakes-io-method-mark-Methods
- #### to\_be\_bytes
  ```moonbit
  :::source,moonbitlang/core/uint64/uint64.mbt,22:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::to_be_bytes(self : UInt64) -> Bytes
  ```
  >  Converts the UInt64 to a Bytes in big-endian byte order.
- #### to\_le\_bytes
  ```moonbit
  :::source,moonbitlang/core/uint64/uint64.mbt,36:::fn <a href="moonbitlang/core/uint64#UInt64">UInt64</a>::to_le_bytes(self : UInt64) -> Bytes
  ```
  >  Converts the UInt64 to a Bytes in little-endian byte order.
