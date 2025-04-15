# Documentation
|Type|description|
|---|---|
|[Byte](#Byte)||

|Value|description|
|---|---|
|[max\_value](#max_value)||
|[min\_value](#min_value)||
|[to\_uint64](#to_uint64)||

## max\_value

```moonbit
:::source,moonbitlang/core/byte/byte.mbt,16:::let max_value : Byte
```


## min\_value

```moonbit
:::source,moonbitlang/core/byte/byte.mbt,19:::let min_value : Byte
```


## to\_uint64

```moonbit
:::source,moonbitlang/core/byte/byte.mbt,38:::fn to_uint64(self : Byte) -> UInt64
```

 Converts a byte value to an unsigned 64-bit integer.

 Parameters:

 * `byte` : The byte value to be converted.

 Returns an unsigned 64-bit integer representation of the byte value.

 Example:

 ```moonbit
 test "to_uint64" {
   let b = b'\xFF'
   inspect!(b.to_uint64(), content="255")
 }
 ```

## Byte


#### mooncakes-io-method-mark-Methods
- #### to\_uint64
  ```moonbit
  :::source,moonbitlang/core/byte/byte.mbt,38:::fn <a href="moonbitlang/core/byte#Byte">Byte</a>::to_uint64(self : Byte) -> UInt64
  ```
  > 
  >  Converts a byte value to an unsigned 64-bit integer.
  > 
  >  Parameters:
  > 
  >  * `byte` : The byte value to be converted.
  > 
  >  Returns an unsigned 64-bit integer representation of the byte value.
  > 
  >  Example:
  > 
  >  ```moonbit
  >  test "to_uint64" {
  >    let b = b'\xFF'
  >    inspect!(b.to_uint64(), content="255")
  >  }
  >  ```
