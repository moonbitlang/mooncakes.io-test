# Documentation
|Trait|description|
|---|---|
|[@gmlewis/spin-moonbit-sdk/ffi.Any](#@gmlewis/spin-moonbit-sdk/ffi.Any)||

|Type|description|
|---|---|
|[Cleanup](#Cleanup)||

|Value|description|
|---|---|
|[bytes2ptr](#bytes2ptr)||
|[copy](#copy)||
|[double\_array2ptr](#double_array2ptr)||
|[extend16](#extend16)||
|[extend8](#extend8)||
|[f32\_to\_i32](#f32_to_i32)||
|[f32\_to\_i64](#f32_to_i64)||
|[float\_array2ptr](#float_array2ptr)||
|[free](#free)||
|[int64\_array2ptr](#int64_array2ptr)||
|[int\_array2ptr](#int_array2ptr)||
|[load16](#load16)||
|[load16\_u](#load16_u)||
|[load32](#load32)||
|[load64](#load64)||
|[load8](#load8)||
|[load8\_u](#load8_u)||
|[loadf32](#loadf32)||
|[loadf64](#loadf64)||
|[malloc](#malloc)||
|[ptr2bytes](#ptr2bytes)||
|[ptr2float\_array](#ptr2float_array)||
|[ptr2int\_array](#ptr2int_array)||
|[ptr2str](#ptr2str)||
|[ptr2uint\_array](#ptr2uint_array)||
|[store16](#store16)||
|[store32](#store32)||
|[store64](#store64)||
|[store8](#store8)||
|[storef32](#storef32)||
|[storef64](#storef64)||
|[str2ptr](#str2ptr)||
|[uint64\_array2ptr](#uint64_array2ptr)||
|[uint\_array2ptr](#uint_array2ptr)||

## @gmlewis/spin-moonbit-sdk/ffi.Any

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,172:::pub(open) trait @gmlewis/spin-moonbit-sdk/ffi.Any {
}
```


## Cleanup

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,175:::pub(all) struct Cleanup {
  address : Int
  size : Int
  align : Int
}
```


## bytes2ptr

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,117:::fn bytes2ptr(_bytes : Bytes) -> Int
```


## copy

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,102:::fn copy(_dest : Int, _src : Int) -> Unit
```


## double\_array2ptr

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,152:::fn double_array2ptr(_array : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Double]) -> Int
```


## extend16

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,2:::fn extend16(_value : Int) -> Int
```


## extend8

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,7:::fn extend8(_value : Int) -> Int
```


## f32\_to\_i32

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,82:::fn f32_to_i32(_value : Float) -> Int
```


## f32\_to\_i64

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,87:::fn f32_to_i64(_value : Float) -> Int64
```


## float\_array2ptr

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,147:::fn float_array2ptr(_array : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Float]) -> Int
```


## free

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,97:::fn free(_position : Int) -> Unit
```


## int64\_array2ptr

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,142:::fn int64_array2ptr(_array : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Int64]) -> Int
```


## int\_array2ptr

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,137:::fn int_array2ptr(_array : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Int]) -> Int
```


## load16

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,32:::fn load16(_offset : Int) -> Int
```


## load16\_u

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,37:::fn load16_u(_offset : Int) -> Int
```


## load32

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,47:::fn load32(_offset : Int) -> Int
```


## load64

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,57:::fn load64(_offset : Int) -> Int64
```


## load8

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,22:::fn load8(_offset : Int) -> Int
```


## load8\_u

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,17:::fn load8_u(_offset : Int) -> Int
```


## loadf32

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,67:::fn loadf32(_offset : Int) -> Float
```


## loadf64

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,77:::fn loadf64(_offset : Int) -> Double
```


## malloc

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,92:::fn malloc(_size : Int) -> Int
```


## ptr2bytes

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,122:::fn ptr2bytes(_ptr : Int) -> Bytes
```


## ptr2float\_array

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,167:::fn ptr2float_array(_ptr : Int) -> <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Float]
```


## ptr2int\_array

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,162:::fn ptr2int_array(_ptr : Int) -> <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[Int]
```


## ptr2str

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,112:::fn ptr2str(_ptr : Int) -> String
```


## ptr2uint\_array

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,157:::fn ptr2uint_array(_ptr : Int) -> <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[UInt]
```


## store16

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,27:::fn store16(_offset : Int, _value : Int) -> Unit
```


## store32

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,42:::fn store32(_offset : Int, _value : Int) -> Unit
```


## store64

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,52:::fn store64(_offset : Int, _value : Int64) -> Unit
```


## store8

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,12:::fn store8(_offset : Int, _value : Int) -> Unit
```


## storef32

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,62:::fn storef32(_offset : Int, _value : Float) -> Unit
```


## storef64

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,72:::fn storef64(_offset : Int, _value : Double) -> Unit
```


## str2ptr

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,107:::fn str2ptr(_str : String) -> Int
```


## uint64\_array2ptr

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,132:::fn uint64_array2ptr(_array : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[UInt64]) -> Int
```


## uint\_array2ptr

```moonbit
:::source,gmlewis/spin-moonbit-sdk/ffi/top_notwasm.mbt,127:::fn uint_array2ptr(_array : <a href="moonbitlang/core/array#FixedArray">FixedArray</a>[UInt]) -> Int
```

