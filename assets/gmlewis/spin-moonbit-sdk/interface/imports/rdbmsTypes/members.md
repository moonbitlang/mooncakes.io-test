# Documentation
|Type|description|
|---|---|
|[Column](#Column)||
|[DbDataType](#DbDataType)||
|[DbValue](#DbValue)||
|[Error\_](#Error_)||
|[ParameterValue](#ParameterValue)||
|[RowSet](#RowSet)||

|Value|description|
|---|---|
|[ordinal](#ordinal)||

## Column

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,114:::pub(all) struct Column {
  name : String
  data_type : <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#DbDataType">DbDataType</a>
}
```

 A database column

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,117:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#Column">Column</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,117:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#Column">Column</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#Column">Column</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,117:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#Column">Column</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,117:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#Column">Column</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## DbDataType

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,15:::pub(all) enum DbDataType {
  BOOLEAN
  INT8
  INT16
  INT32
  INT64
  UINT8
  UINT16
  UINT32
  UINT64
  FLOATING32
  FLOATING64
  STR
  BINARY
  OTHER
}
```

 Data types for a database column

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,30:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#DbDataType">DbDataType</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,30:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#DbDataType">DbDataType</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#DbDataType">DbDataType</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,30:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#DbDataType">DbDataType</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,30:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#DbDataType">DbDataType</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### from
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,53:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#DbDataType">DbDataType</a>::from(self : Int) -> <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#DbDataType">DbDataType</a>
  ```
  > 
- #### ordinal
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,33:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#DbDataType">DbDataType</a>::ordinal(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#DbDataType">DbDataType</a>) -> Int
  ```
  > 

## DbValue

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,75:::pub(all) enum DbValue {
  Boolean(Bool)
  Int8(Int)
  Int16(Int)
  Int32(Int)
  Int64(Int64)
  Uint8(Byte)
  Uint16(UInt)
  Uint32(UInt)
  Uint64(UInt64)
  Floating32(Double)
  Floating64(Double)
  Str(String)
  Binary(Bytes)
  DbNull
  Unsupported
}
```

 Database values

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,91:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#DbValue">DbValue</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,91:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#DbValue">DbValue</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#DbValue">DbValue</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,91:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#DbValue">DbValue</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,91:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#DbValue">DbValue</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## Error\_

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,5:::pub(all) enum Error_ {
  ConnectionFailed(String)
  BadParameter(String)
  QueryFailed(String)
  ValueConversionFailed(String)
  Other(String)
}
```

 Errors related to interacting with a database.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,11:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#Error_">Error_</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,11:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#Error_">Error_</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#Error_">Error_</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,11:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#Error_">Error_</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,11:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#Error_">Error_</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## ParameterValue

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,95:::pub(all) enum ParameterValue {
  Boolean(Bool)
  Int8(Int)
  Int16(Int)
  Int32(Int)
  Int64(Int64)
  Uint8(Byte)
  Uint16(UInt)
  Uint32(UInt)
  Uint64(UInt64)
  Floating32(Double)
  Floating64(Double)
  Str(String)
  Binary(Bytes)
  DbNull
}
```

 Values used in parameterized queries

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,110:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#ParameterValue">ParameterValue</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,110:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#ParameterValue">ParameterValue</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#ParameterValue">ParameterValue</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,110:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#ParameterValue">ParameterValue</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,110:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#ParameterValue">ParameterValue</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## RowSet

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,121:::pub(all) struct RowSet {
  columns : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#Column">Column</a>]
  rows : <a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#DbValue">DbValue</a>]]
}
```

 A set of database rows

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,124:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#RowSet">RowSet</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,124:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#RowSet">RowSet</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#RowSet">RowSet</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,124:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#RowSet">RowSet</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,124:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#RowSet">RowSet</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## ordinal

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes/top.mbt,33:::fn ordinal(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#DbDataType">DbDataType</a>) -> Int
```

