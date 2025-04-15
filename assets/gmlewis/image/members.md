# gmlewis/image
[![check](https://github.com/gmlewis/moonbit-image/actions/workflows/check.yml/badge.svg)](https://github.com/gmlewis/moonbit-image/actions/workflows/check.yml)

This is a simple image representation based on Go's implementation:
https://cs.opensource.google/go/go/+/refs/tags/go1.23.3:src/image/image.go
which has the copyright notice:

```
// Copyright 2009 The Go Authors. All rights reserved.
// Use of this source code is governed by a BSD-style
// license that can be found in the LICENSE file.
```

## Status

The code has been updated to support compiler:

```bash
$ moon version --all
moon 0.1.20250407 (24afaca 2025-04-07) ~/.moon/bin/moon
moonc v0.1.20250410+15d580434 ~/.moon/bin/moonc
moonrun 0.1.20250407 (24afaca 2025-04-07) ~/.moon/bin/moonrun
```

---
# Documentation
|Trait|description|
|---|---|
|[@gmlewis/image.Image](#@gmlewis/image.Image)||
|[@gmlewis/image.RGBA64Image](#@gmlewis/image.RGBA64Image)||

|Type|description|
|---|---|
|[Alpha](#Alpha)||
|[Alpha16](#Alpha16)||
|[CMYK](#CMYK)||
|[Config](#Config)||
|[Gray](#Gray)||
|[Gray16](#Gray16)||
|[NRGBA](#NRGBA)||
|[NRGBA64](#NRGBA64)||
|[Paletted](#Paletted)||
|[Point](#Point)||
|[RGBA](#RGBA)||
|[RGBA64](#RGBA64)||
|[Rectangle](#Rectangle)||
|[SizeError](#SizeError)||
|[Image](#Image)||

|Value|description|
|---|---|
|[add](#add)||
|[add2\_non\_neg](#add2_non_neg)||
|[alpha16\_at](#alpha16_at)||
|[alpha\_at](#alpha_at)||
|[canon](#canon)||
|[cmyk\_at](#cmyk_at)||
|[copy](#copy)||
|[div](#div)||
|[dx](#dx)||
|[dy](#dy)||
|[empty](#empty)||
|[gray16\_at](#gray16_at)||
|[gray\_at](#gray_at)||
|[inset](#inset)||
|[intersect](#intersect)||
|[is\_in](#is_in)||
|[mod](#mod)||
|[mul](#mul)||
|[mul3\_non\_neg](#mul3_non_neg)||
|[nrgba64\_at](#nrgba64_at)||
|[nrgba\_at](#nrgba_at)||
|[op\_add](#op_add)||
|[op\_equal](#op_equal)||
|[op\_sub](#op_sub)||
|[overlaps](#overlaps)||
|[pt](#pt)||
|[rect](#rect)||
|[rgba64\_at](#rgba64_at)||
|[rgba\_at](#rgba_at)||
|[set\_alpha](#set_alpha)||
|[set\_alpha16](#set_alpha16)||
|[set\_cmyk](#set_cmyk)||
|[set\_color\_index](#set_color_index)||
|[set\_gray](#set_gray)||
|[set\_gray16](#set_gray16)||
|[set\_nrgba](#set_nrgba)||
|[set\_nrgba64](#set_nrgba64)||
|[set\_rgba](#set_rgba)||
|[size](#size)||
|[sub](#sub)||
|[to\_string](#to_string)||
|[union](#union)||

## @gmlewis/image.Image

```moonbit
:::source,gmlewis/image/image.mbt,45:::pub(open) trait @gmlewis/image.Image {
  color_model(Self) -> <a href="gmlewis/image/color#Model">@gmlewis/image/color.Model</a>
  bounds(Self) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
  at(Self, Int, Int) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
  opaque(Self) -> Bool
  set(Self, Int, Int, <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
  sub_image(Self, <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Image">Image</a>
  raw_data(Self) -> <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
  get_bytes_per_pixel(Self) -> Int
  get_stride(Self) -> Int
  pix_offset(Self, Int, Int) -> Int
  color_index_at(Self, Int, Int) -> Byte
}
```

 Image is a finite rectangular grid of \[color.Color\] values taken from a color
model.

## @gmlewis/image.RGBA64Image

```moonbit
:::source,gmlewis/image/image.mbt,85:::pub(open) trait @gmlewis/image.RGBA64Image {
  rgba64_at(Self, Int, Int) -> <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>
  color_model(Self) -> <a href="gmlewis/image/color#Model">@gmlewis/image/color.Model</a>
  bounds(Self) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
  at(Self, Int, Int) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
}
```

 RGBA64Image is an \[Image\] whose pixels can be converted directly to a
color.RGBA64.

## Alpha

```moonbit
:::source,gmlewis/image/image.mbt,873:::pub(all) struct Alpha {
  pix : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
  stride : Int
  rect : <a href="gmlewis/image#Rectangle">Rectangle</a>
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/image.mbt,893:::impl <a href="gmlewis/image#Image">Image</a> for <a href="gmlewis/image#Alpha">Alpha</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,928:::fn at(self : <a href="gmlewis/image#Alpha">Alpha</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,918:::fn bounds(self : <a href="gmlewis/image#Alpha">Alpha</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,908:::fn color_index_at(_self : <a href="gmlewis/image#Alpha">Alpha</a>, _x : Int, _y : Int) -> Byte
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,913:::fn color_model(_self : <a href="gmlewis/image#Alpha">Alpha</a>) -> <a href="gmlewis/image/color#Model">@gmlewis/image/color.Model</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,898:::fn get_bytes_per_pixel(_self : <a href="gmlewis/image#Alpha">Alpha</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,903:::fn get_stride(self : <a href="gmlewis/image#Alpha">Alpha</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1010:::fn opaque(self : <a href="gmlewis/image#Alpha">Alpha</a>) -> Bool
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,951:::fn pix_offset(self : <a href="gmlewis/image#Alpha">Alpha</a>, x : Int, y : Int) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,893:::fn raw_data(self : <a href="gmlewis/image#Alpha">Alpha</a>) -> <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,961:::fn set(self : <a href="gmlewis/image#Alpha">Alpha</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,996:::fn sub_image(self : <a href="gmlewis/image#Alpha">Alpha</a>, r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Image">Image</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### alpha\_at
  ```moonbit
  :::source,gmlewis/image/image.mbt,940:::fn <a href="gmlewis/image#Alpha">Alpha</a>::alpha_at(self : <a href="gmlewis/image#Alpha">Alpha</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#Alpha">@gmlewis/image/color.Alpha</a>
  ```
  > 
- #### new
  ```moonbit
  :::source,gmlewis/image/image.mbt,1030:::fn <a href="gmlewis/image#Alpha">Alpha</a>::new(r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Alpha">Alpha</a>!<a href="gmlewis/image#SizeError">SizeError</a>
  ```
  > 
- #### new\_empty
  ```moonbit
  :::source,gmlewis/image/image.mbt,888:::fn <a href="gmlewis/image#Alpha">Alpha</a>::new_empty() -> <a href="gmlewis/image#Alpha">Alpha</a>
  ```
  > 
- #### op\_get
  ```moonbit
  :::source,gmlewis/image/image.mbt,923:::fn <a href="gmlewis/image#Alpha">Alpha</a>::op_get(self : <a href="gmlewis/image#Alpha">Alpha</a>, p : <a href="gmlewis/image#Point">Point</a>) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
  ```
  > 
- #### op\_set
  ```moonbit
  :::source,gmlewis/image/image.mbt,956:::fn <a href="gmlewis/image#Alpha">Alpha</a>::op_set(self : <a href="gmlewis/image#Alpha">Alpha</a>, p : <a href="gmlewis/image#Point">Point</a>, c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
  ```
  > 
- #### rgba64\_at
  ```moonbit
  :::source,gmlewis/image/image.mbt,933:::fn <a href="gmlewis/image#Alpha">Alpha</a>::rgba64_at(self : <a href="gmlewis/image#Alpha">Alpha</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>
  ```
  > 
- #### set\_alpha
  ```moonbit
  :::source,gmlewis/image/image.mbt,985:::fn <a href="gmlewis/image#Alpha">Alpha</a>::set_alpha(self : <a href="gmlewis/image#Alpha">Alpha</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#Alpha">@gmlewis/image/color.Alpha</a>) -> Unit
  ```
  > 
- #### set\_rgba64
  ```moonbit
  :::source,gmlewis/image/image.mbt,971:::fn <a href="gmlewis/image#Alpha">Alpha</a>::set_rgba64(self : <a href="gmlewis/image#Alpha">Alpha</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>) -> Unit
  ```
  > 

## Alpha16

```moonbit
:::source,gmlewis/image/image.mbt,1040:::pub(all) struct Alpha16 {
  pix : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
  stride : Int
  rect : <a href="gmlewis/image#Rectangle">Rectangle</a>
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/image.mbt,1060:::impl <a href="gmlewis/image#Image">Image</a> for <a href="gmlewis/image#Alpha16">Alpha16</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1095:::fn at(self : <a href="gmlewis/image#Alpha16">Alpha16</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1085:::fn bounds(self : <a href="gmlewis/image#Alpha16">Alpha16</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1075:::fn color_index_at(_self : <a href="gmlewis/image#Alpha16">Alpha16</a>, _x : Int, _y : Int) -> Byte
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1080:::fn color_model(_self : <a href="gmlewis/image#Alpha16">Alpha16</a>) -> <a href="gmlewis/image/color#Model">@gmlewis/image/color.Model</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1065:::fn get_bytes_per_pixel(_self : <a href="gmlewis/image#Alpha16">Alpha16</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1070:::fn get_stride(self : <a href="gmlewis/image#Alpha16">Alpha16</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1185:::fn opaque(self : <a href="gmlewis/image#Alpha16">Alpha16</a>) -> Bool
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1118:::fn pix_offset(self : <a href="gmlewis/image#Alpha16">Alpha16</a>, x : Int, y : Int) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1060:::fn raw_data(self : <a href="gmlewis/image#Alpha16">Alpha16</a>) -> <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1128:::fn set(self : <a href="gmlewis/image#Alpha16">Alpha16</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1171:::fn sub_image(self : <a href="gmlewis/image#Alpha16">Alpha16</a>, r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Image">Image</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### alpha16\_at
  ```moonbit
  :::source,gmlewis/image/image.mbt,1106:::fn <a href="gmlewis/image#Alpha16">Alpha16</a>::alpha16_at(self : <a href="gmlewis/image#Alpha16">Alpha16</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#Alpha16">@gmlewis/image/color.Alpha16</a>
  ```
  > 
- #### new
  ```moonbit
  :::source,gmlewis/image/image.mbt,1205:::fn <a href="gmlewis/image#Alpha16">Alpha16</a>::new(r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Alpha16">Alpha16</a>!<a href="gmlewis/image#SizeError">SizeError</a>
  ```
  > 
- #### new\_empty
  ```moonbit
  :::source,gmlewis/image/image.mbt,1055:::fn <a href="gmlewis/image#Alpha16">Alpha16</a>::new_empty() -> <a href="gmlewis/image#Alpha16">Alpha16</a>
  ```
  > 
- #### op\_get
  ```moonbit
  :::source,gmlewis/image/image.mbt,1090:::fn <a href="gmlewis/image#Alpha16">Alpha16</a>::op_get(self : <a href="gmlewis/image#Alpha16">Alpha16</a>, p : <a href="gmlewis/image#Point">Point</a>) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
  ```
  > 
- #### op\_set
  ```moonbit
  :::source,gmlewis/image/image.mbt,1123:::fn <a href="gmlewis/image#Alpha16">Alpha16</a>::op_set(self : <a href="gmlewis/image#Alpha16">Alpha16</a>, p : <a href="gmlewis/image#Point">Point</a>, c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
  ```
  > 
- #### rgba64\_at
  ```moonbit
  :::source,gmlewis/image/image.mbt,1100:::fn <a href="gmlewis/image#Alpha16">Alpha16</a>::rgba64_at(self : <a href="gmlewis/image#Alpha16">Alpha16</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>
  ```
  > 
- #### set\_alpha16
  ```moonbit
  :::source,gmlewis/image/image.mbt,1154:::fn <a href="gmlewis/image#Alpha16">Alpha16</a>::set_alpha16(self : <a href="gmlewis/image#Alpha16">Alpha16</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#Alpha16">@gmlewis/image/color.Alpha16</a>) -> Unit
  ```
  > 
- #### set\_rgba64
  ```moonbit
  :::source,gmlewis/image/image.mbt,1139:::fn <a href="gmlewis/image#Alpha16">Alpha16</a>::set_rgba64(self : <a href="gmlewis/image#Alpha16">Alpha16</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>) -> Unit
  ```
  > 

## CMYK

```moonbit
:::source,gmlewis/image/image.mbt,1528:::pub(all) struct CMYK {
  pix : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
  stride : Int
  rect : <a href="gmlewis/image#Rectangle">Rectangle</a>
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/image.mbt,1548:::impl <a href="gmlewis/image#Image">Image</a> for <a href="gmlewis/image#CMYK">CMYK</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1583:::fn at(self : <a href="gmlewis/image#CMYK">CMYK</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1573:::fn bounds(self : <a href="gmlewis/image#CMYK">CMYK</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1563:::fn color_index_at(_self : <a href="gmlewis/image#CMYK">CMYK</a>, _x : Int, _y : Int) -> Byte
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1568:::fn color_model(_self : <a href="gmlewis/image#CMYK">CMYK</a>) -> <a href="gmlewis/image/color#Model">@gmlewis/image/color.Model</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1553:::fn get_bytes_per_pixel(_self : <a href="gmlewis/image#CMYK">CMYK</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1558:::fn get_stride(self : <a href="gmlewis/image#CMYK">CMYK</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1678:::fn opaque(_self : <a href="gmlewis/image#CMYK">CMYK</a>) -> Bool
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1610:::fn pix_offset(self : <a href="gmlewis/image#CMYK">CMYK</a>, x : Int, y : Int) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1548:::fn raw_data(self : <a href="gmlewis/image#CMYK">CMYK</a>) -> <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1615:::fn set(self : <a href="gmlewis/image#CMYK">CMYK</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1664:::fn sub_image(self : <a href="gmlewis/image#CMYK">CMYK</a>, r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Image">Image</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### cmyk\_at
  ```moonbit
  :::source,gmlewis/image/image.mbt,1594:::fn <a href="gmlewis/image#CMYK">CMYK</a>::cmyk_at(self : <a href="gmlewis/image#CMYK">CMYK</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#CMYK">@gmlewis/image/color.CMYK</a>
  ```
  > 
- #### new
  ```moonbit
  :::source,gmlewis/image/image.mbt,1684:::fn <a href="gmlewis/image#CMYK">CMYK</a>::new(r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#CMYK">CMYK</a>!<a href="gmlewis/image#SizeError">SizeError</a>
  ```
  > 
- #### new\_empty
  ```moonbit
  :::source,gmlewis/image/image.mbt,1543:::fn <a href="gmlewis/image#CMYK">CMYK</a>::new_empty() -> <a href="gmlewis/image#CMYK">CMYK</a>
  ```
  > 
- #### op\_get
  ```moonbit
  :::source,gmlewis/image/image.mbt,1578:::fn <a href="gmlewis/image#CMYK">CMYK</a>::op_get(self : <a href="gmlewis/image#CMYK">CMYK</a>, p : <a href="gmlewis/image#Point">Point</a>) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
  ```
  > 
- #### rgba64\_at
  ```moonbit
  :::source,gmlewis/image/image.mbt,1588:::fn <a href="gmlewis/image#CMYK">CMYK</a>::rgba64_at(self : <a href="gmlewis/image#CMYK">CMYK</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>
  ```
  > 
- #### set\_cmyk
  ```moonbit
  :::source,gmlewis/image/image.mbt,1650:::fn <a href="gmlewis/image#CMYK">CMYK</a>::set_cmyk(self : <a href="gmlewis/image#CMYK">CMYK</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#CMYK">@gmlewis/image/color.CMYK</a>) -> Unit
  ```
  > 
- #### set\_rgba64
  ```moonbit
  :::source,gmlewis/image/image.mbt,1628:::fn <a href="gmlewis/image#CMYK">CMYK</a>::set_rgba64(self : <a href="gmlewis/image#CMYK">CMYK</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>) -> Unit
  ```
  > 

## Config

```moonbit
:::source,gmlewis/image/image.mbt,31:::pub(all) struct Config {
  color_model : <a href="gmlewis/image/color#Model">@gmlewis/image/color.Model</a>
  width : Int
  height : Int
}
```

 Config holds an image's color model and dimensions.

#### mooncakes-io-method-mark-Methods
- #### new\_empty
  ```moonbit
  :::source,gmlewis/image/image.mbt,38:::fn <a href="gmlewis/image#Config">Config</a>::new_empty() -> <a href="gmlewis/image#Config">Config</a>
  ```
  > 

## Gray

```moonbit
:::source,gmlewis/image/image.mbt,1215:::pub(all) struct Gray {
  pix : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
  stride : Int
  rect : <a href="gmlewis/image#Rectangle">Rectangle</a>
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/image.mbt,1235:::impl <a href="gmlewis/image#Image">Image</a> for <a href="gmlewis/image#Gray">Gray</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1270:::fn at(self : <a href="gmlewis/image#Gray">Gray</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1260:::fn bounds(self : <a href="gmlewis/image#Gray">Gray</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1250:::fn color_index_at(_self : <a href="gmlewis/image#Gray">Gray</a>, _x : Int, _y : Int) -> Byte
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1255:::fn color_model(_self : <a href="gmlewis/image#Gray">Gray</a>) -> <a href="gmlewis/image/color#Model">@gmlewis/image/color.Model</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1240:::fn get_bytes_per_pixel(_self : <a href="gmlewis/image#Gray">Gray</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1245:::fn get_stride(self : <a href="gmlewis/image#Gray">Gray</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1354:::fn opaque(_self : <a href="gmlewis/image#Gray">Gray</a>) -> Bool
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1293:::fn pix_offset(self : <a href="gmlewis/image#Gray">Gray</a>, x : Int, y : Int) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1235:::fn raw_data(self : <a href="gmlewis/image#Gray">Gray</a>) -> <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1303:::fn set(self : <a href="gmlewis/image#Gray">Gray</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1340:::fn sub_image(self : <a href="gmlewis/image#Gray">Gray</a>, r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Image">Image</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### gray\_at
  ```moonbit
  :::source,gmlewis/image/image.mbt,1282:::fn <a href="gmlewis/image#Gray">Gray</a>::gray_at(self : <a href="gmlewis/image#Gray">Gray</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#Gray">@gmlewis/image/color.Gray</a>
  ```
  > 
- #### new
  ```moonbit
  :::source,gmlewis/image/image.mbt,1360:::fn <a href="gmlewis/image#Gray">Gray</a>::new(r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Gray">Gray</a>!<a href="gmlewis/image#SizeError">SizeError</a>
  ```
  > 
- #### new\_empty
  ```moonbit
  :::source,gmlewis/image/image.mbt,1230:::fn <a href="gmlewis/image#Gray">Gray</a>::new_empty() -> <a href="gmlewis/image#Gray">Gray</a>
  ```
  > 
- #### op\_get
  ```moonbit
  :::source,gmlewis/image/image.mbt,1265:::fn <a href="gmlewis/image#Gray">Gray</a>::op_get(self : <a href="gmlewis/image#Gray">Gray</a>, p : <a href="gmlewis/image#Point">Point</a>) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
  ```
  > 
- #### op\_set
  ```moonbit
  :::source,gmlewis/image/image.mbt,1298:::fn <a href="gmlewis/image#Gray">Gray</a>::op_set(self : <a href="gmlewis/image#Gray">Gray</a>, p : <a href="gmlewis/image#Point">Point</a>, c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
  ```
  > 
- #### rgba64\_at
  ```moonbit
  :::source,gmlewis/image/image.mbt,1275:::fn <a href="gmlewis/image#Gray">Gray</a>::rgba64_at(self : <a href="gmlewis/image#Gray">Gray</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>
  ```
  > 
- #### set\_gray
  ```moonbit
  :::source,gmlewis/image/image.mbt,1329:::fn <a href="gmlewis/image#Gray">Gray</a>::set_gray(self : <a href="gmlewis/image#Gray">Gray</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#Gray">@gmlewis/image/color.Gray</a>) -> Unit
  ```
  > 
- #### set\_rgba64
  ```moonbit
  :::source,gmlewis/image/image.mbt,1313:::fn <a href="gmlewis/image#Gray">Gray</a>::set_rgba64(self : <a href="gmlewis/image#Gray">Gray</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>) -> Unit
  ```
  > 

## Gray16

```moonbit
:::source,gmlewis/image/image.mbt,1370:::pub(all) struct Gray16 {
  pix : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
  stride : Int
  rect : <a href="gmlewis/image#Rectangle">Rectangle</a>
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/image.mbt,1390:::impl <a href="gmlewis/image#Image">Image</a> for <a href="gmlewis/image#Gray16">Gray16</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1425:::fn at(self : <a href="gmlewis/image#Gray16">Gray16</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1415:::fn bounds(self : <a href="gmlewis/image#Gray16">Gray16</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1405:::fn color_index_at(_self : <a href="gmlewis/image#Gray16">Gray16</a>, _x : Int, _y : Int) -> Byte
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1410:::fn color_model(_self : <a href="gmlewis/image#Gray16">Gray16</a>) -> <a href="gmlewis/image/color#Model">@gmlewis/image/color.Model</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1395:::fn get_bytes_per_pixel(_self : <a href="gmlewis/image#Gray16">Gray16</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1400:::fn get_stride(self : <a href="gmlewis/image#Gray16">Gray16</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1512:::fn opaque(_self : <a href="gmlewis/image#Gray16">Gray16</a>) -> Bool
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1448:::fn pix_offset(self : <a href="gmlewis/image#Gray16">Gray16</a>, x : Int, y : Int) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1390:::fn raw_data(self : <a href="gmlewis/image#Gray16">Gray16</a>) -> <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1458:::fn set(self : <a href="gmlewis/image#Gray16">Gray16</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1498:::fn sub_image(self : <a href="gmlewis/image#Gray16">Gray16</a>, r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Image">Image</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### gray16\_at
  ```moonbit
  :::source,gmlewis/image/image.mbt,1436:::fn <a href="gmlewis/image#Gray16">Gray16</a>::gray16_at(self : <a href="gmlewis/image#Gray16">Gray16</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#Gray16">@gmlewis/image/color.Gray16</a>
  ```
  > 
- #### new
  ```moonbit
  :::source,gmlewis/image/image.mbt,1518:::fn <a href="gmlewis/image#Gray16">Gray16</a>::new(r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Gray16">Gray16</a>!<a href="gmlewis/image#SizeError">SizeError</a>
  ```
  > 
- #### new\_empty
  ```moonbit
  :::source,gmlewis/image/image.mbt,1385:::fn <a href="gmlewis/image#Gray16">Gray16</a>::new_empty() -> <a href="gmlewis/image#Gray16">Gray16</a>
  ```
  > 
- #### op\_get
  ```moonbit
  :::source,gmlewis/image/image.mbt,1420:::fn <a href="gmlewis/image#Gray16">Gray16</a>::op_get(self : <a href="gmlewis/image#Gray16">Gray16</a>, p : <a href="gmlewis/image#Point">Point</a>) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
  ```
  > 
- #### op\_set
  ```moonbit
  :::source,gmlewis/image/image.mbt,1453:::fn <a href="gmlewis/image#Gray16">Gray16</a>::op_set(self : <a href="gmlewis/image#Gray16">Gray16</a>, p : <a href="gmlewis/image#Point">Point</a>, c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
  ```
  > 
- #### rgba64\_at
  ```moonbit
  :::source,gmlewis/image/image.mbt,1430:::fn <a href="gmlewis/image#Gray16">Gray16</a>::rgba64_at(self : <a href="gmlewis/image#Gray16">Gray16</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>
  ```
  > 
- #### set\_gray16
  ```moonbit
  :::source,gmlewis/image/image.mbt,1486:::fn <a href="gmlewis/image#Gray16">Gray16</a>::set_gray16(self : <a href="gmlewis/image#Gray16">Gray16</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#Gray16">@gmlewis/image/color.Gray16</a>) -> Unit
  ```
  > 
- #### set\_rgba64
  ```moonbit
  :::source,gmlewis/image/image.mbt,1469:::fn <a href="gmlewis/image#Gray16">Gray16</a>::set_rgba64(self : <a href="gmlewis/image#Gray16">Gray16</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>) -> Unit
  ```
  > 

## NRGBA

```moonbit
:::source,gmlewis/image/image.mbt,481:::pub(all) struct NRGBA {
  pix : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
  stride : Int
  rect : <a href="gmlewis/image#Rectangle">Rectangle</a>
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/image.mbt,501:::impl <a href="gmlewis/image#Image">Image</a> for <a href="gmlewis/image#NRGBA">NRGBA</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,536:::fn at(self : <a href="gmlewis/image#NRGBA">NRGBA</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,526:::fn bounds(self : <a href="gmlewis/image#NRGBA">NRGBA</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,516:::fn color_index_at(_self : <a href="gmlewis/image#NRGBA">NRGBA</a>, _x : Int, _y : Int) -> Byte
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,521:::fn color_model(_self : <a href="gmlewis/image#NRGBA">NRGBA</a>) -> <a href="gmlewis/image/color#Model">@gmlewis/image/color.Model</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,506:::fn get_bytes_per_pixel(_self : <a href="gmlewis/image#NRGBA">NRGBA</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,511:::fn get_stride(self : <a href="gmlewis/image#NRGBA">NRGBA</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,639:::fn opaque(self : <a href="gmlewis/image#NRGBA">NRGBA</a>) -> Bool
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,563:::fn pix_offset(self : <a href="gmlewis/image#NRGBA">NRGBA</a>, x : Int, y : Int) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,501:::fn raw_data(self : <a href="gmlewis/image#NRGBA">NRGBA</a>) -> <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,573:::fn set(self : <a href="gmlewis/image#NRGBA">NRGBA</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,625:::fn sub_image(self : <a href="gmlewis/image#NRGBA">NRGBA</a>, r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Image">Image</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### new
  ```moonbit
  :::source,gmlewis/image/image.mbt,659:::fn <a href="gmlewis/image#NRGBA">NRGBA</a>::new(r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#NRGBA">NRGBA</a>!<a href="gmlewis/image#SizeError">SizeError</a>
  ```
  > 
- #### new\_empty
  ```moonbit
  :::source,gmlewis/image/image.mbt,496:::fn <a href="gmlewis/image#NRGBA">NRGBA</a>::new_empty() -> <a href="gmlewis/image#NRGBA">NRGBA</a>
  ```
  > 
- #### nrgba\_at
  ```moonbit
  :::source,gmlewis/image/image.mbt,547:::fn <a href="gmlewis/image#NRGBA">NRGBA</a>::nrgba_at(self : <a href="gmlewis/image#NRGBA">NRGBA</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#NRGBA">@gmlewis/image/color.NRGBA</a>
  ```
  > 
- #### op\_get
  ```moonbit
  :::source,gmlewis/image/image.mbt,531:::fn <a href="gmlewis/image#NRGBA">NRGBA</a>::op_get(self : <a href="gmlewis/image#NRGBA">NRGBA</a>, p : <a href="gmlewis/image#Point">Point</a>) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
  ```
  > 
- #### op\_set
  ```moonbit
  :::source,gmlewis/image/image.mbt,568:::fn <a href="gmlewis/image#NRGBA">NRGBA</a>::op_set(self : <a href="gmlewis/image#NRGBA">NRGBA</a>, p : <a href="gmlewis/image#Point">Point</a>, c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
  ```
  > 
- #### rgba64\_at
  ```moonbit
  :::source,gmlewis/image/image.mbt,541:::fn <a href="gmlewis/image#NRGBA">NRGBA</a>::rgba64_at(self : <a href="gmlewis/image#NRGBA">NRGBA</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>
  ```
  > 
- #### set\_nrgba
  ```moonbit
  :::source,gmlewis/image/image.mbt,611:::fn <a href="gmlewis/image#NRGBA">NRGBA</a>::set_nrgba(self : <a href="gmlewis/image#NRGBA">NRGBA</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#NRGBA">@gmlewis/image/color.NRGBA</a>) -> Unit
  ```
  > 
- #### set\_rgba64
  ```moonbit
  :::source,gmlewis/image/image.mbt,586:::fn <a href="gmlewis/image#NRGBA">NRGBA</a>::set_rgba64(self : <a href="gmlewis/image#NRGBA">NRGBA</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>) -> Unit
  ```
  > 

## NRGBA64

```moonbit
:::source,gmlewis/image/image.mbt,669:::pub(all) struct NRGBA64 {
  pix : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
  stride : Int
  rect : <a href="gmlewis/image#Rectangle">Rectangle</a>
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/image.mbt,689:::impl <a href="gmlewis/image#Image">Image</a> for <a href="gmlewis/image#NRGBA64">NRGBA64</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,724:::fn at(self : <a href="gmlewis/image#NRGBA64">NRGBA64</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,714:::fn bounds(self : <a href="gmlewis/image#NRGBA64">NRGBA64</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,704:::fn color_index_at(_self : <a href="gmlewis/image#NRGBA64">NRGBA64</a>, _x : Int, _y : Int) -> Byte
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,709:::fn color_model(_self : <a href="gmlewis/image#NRGBA64">NRGBA64</a>) -> <a href="gmlewis/image/color#Model">@gmlewis/image/color.Model</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,694:::fn get_bytes_per_pixel(_self : <a href="gmlewis/image#NRGBA64">NRGBA64</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,699:::fn get_stride(self : <a href="gmlewis/image#NRGBA64">NRGBA64</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,843:::fn opaque(self : <a href="gmlewis/image#NRGBA64">NRGBA64</a>) -> Bool
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,750:::fn pix_offset(self : <a href="gmlewis/image#NRGBA64">NRGBA64</a>, x : Int, y : Int) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,689:::fn raw_data(self : <a href="gmlewis/image#NRGBA64">NRGBA64</a>) -> <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,760:::fn set(self : <a href="gmlewis/image#NRGBA64">NRGBA64</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,829:::fn sub_image(self : <a href="gmlewis/image#NRGBA64">NRGBA64</a>, r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Image">Image</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### new
  ```moonbit
  :::source,gmlewis/image/image.mbt,863:::fn <a href="gmlewis/image#NRGBA64">NRGBA64</a>::new(r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#NRGBA64">NRGBA64</a>!<a href="gmlewis/image#SizeError">SizeError</a>
  ```
  > 
- #### new\_empty
  ```moonbit
  :::source,gmlewis/image/image.mbt,684:::fn <a href="gmlewis/image#NRGBA64">NRGBA64</a>::new_empty() -> <a href="gmlewis/image#NRGBA64">NRGBA64</a>
  ```
  > 
- #### nrgba64\_at
  ```moonbit
  :::source,gmlewis/image/image.mbt,735:::fn <a href="gmlewis/image#NRGBA64">NRGBA64</a>::nrgba64_at(self : <a href="gmlewis/image#NRGBA64">NRGBA64</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#NRGBA64">@gmlewis/image/color.NRGBA64</a>
  ```
  > 
- #### op\_get
  ```moonbit
  :::source,gmlewis/image/image.mbt,719:::fn <a href="gmlewis/image#NRGBA64">NRGBA64</a>::op_get(self : <a href="gmlewis/image#NRGBA64">NRGBA64</a>, p : <a href="gmlewis/image#Point">Point</a>) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
  ```
  > 
- #### op\_set
  ```moonbit
  :::source,gmlewis/image/image.mbt,755:::fn <a href="gmlewis/image#NRGBA64">NRGBA64</a>::op_set(self : <a href="gmlewis/image#NRGBA64">NRGBA64</a>, p : <a href="gmlewis/image#Point">Point</a>, c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
  ```
  > 
- #### rgba64\_at
  ```moonbit
  :::source,gmlewis/image/image.mbt,729:::fn <a href="gmlewis/image#NRGBA64">NRGBA64</a>::rgba64_at(self : <a href="gmlewis/image#NRGBA64">NRGBA64</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>
  ```
  > 
- #### set\_nrgba64
  ```moonbit
  :::source,gmlewis/image/image.mbt,806:::fn <a href="gmlewis/image#NRGBA64">NRGBA64</a>::set_nrgba64(self : <a href="gmlewis/image#NRGBA64">NRGBA64</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#NRGBA64">@gmlewis/image/color.NRGBA64</a>) -> Unit
  ```
  > 
- #### set\_rgba64
  ```moonbit
  :::source,gmlewis/image/image.mbt,777:::fn <a href="gmlewis/image#NRGBA64">NRGBA64</a>::set_rgba64(self : <a href="gmlewis/image#NRGBA64">NRGBA64</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>) -> Unit
  ```
  > 

## Paletted

```moonbit
:::source,gmlewis/image/image.mbt,1694:::pub(all) struct Paletted {
  pix : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
  stride : Int
  rect : <a href="gmlewis/image#Rectangle">Rectangle</a>
  palette : <a href="gmlewis/image/color#Palette">@gmlewis/image/color.Palette</a>
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/image.mbt,1711:::impl <a href="gmlewis/image#Image">Image</a> for <a href="gmlewis/image#Paletted">Paletted</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1741:::fn at(self : <a href="gmlewis/image#Paletted">Paletted</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1731:::fn bounds(self : <a href="gmlewis/image#Paletted">Paletted</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1804:::fn color_index_at(self : <a href="gmlewis/image#Paletted">Paletted</a>, x : Int, y : Int) -> Byte
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1726:::fn color_model(self : <a href="gmlewis/image#Paletted">Paletted</a>) -> <a href="gmlewis/image/color#Model">@gmlewis/image/color.Model</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1716:::fn get_bytes_per_pixel(_self : <a href="gmlewis/image#Paletted">Paletted</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1721:::fn get_stride(self : <a href="gmlewis/image#Paletted">Paletted</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1848:::fn opaque(self : <a href="gmlewis/image#Paletted">Paletted</a>) -> Bool
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1771:::fn pix_offset(self : <a href="gmlewis/image#Paletted">Paletted</a>, x : Int, y : Int) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1711:::fn raw_data(self : <a href="gmlewis/image#Paletted">Paletted</a>) -> <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1781:::fn set(self : <a href="gmlewis/image#Paletted">Paletted</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,1824:::fn sub_image(self : <a href="gmlewis/image#Paletted">Paletted</a>, r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Image">Image</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### new
  ```moonbit
  :::source,gmlewis/image/image.mbt,1874:::fn <a href="gmlewis/image#Paletted">Paletted</a>::new(r : <a href="gmlewis/image#Rectangle">Rectangle</a>, p : <a href="gmlewis/image/color#Palette">@gmlewis/image/color.Palette</a>) -> <a href="gmlewis/image#Paletted">Paletted</a>!<a href="gmlewis/image#SizeError">SizeError</a>
  ```
  > 
- #### new\_empty
  ```moonbit
  :::source,gmlewis/image/image.mbt,1886:::fn <a href="gmlewis/image#Paletted">Paletted</a>::new_empty() -> <a href="gmlewis/image#Paletted">Paletted</a>
  ```
  > 
- #### op\_get
  ```moonbit
  :::source,gmlewis/image/image.mbt,1736:::fn <a href="gmlewis/image#Paletted">Paletted</a>::op_get(self : <a href="gmlewis/image#Paletted">Paletted</a>, p : <a href="gmlewis/image#Point">Point</a>) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
  ```
  > 
- #### op\_set
  ```moonbit
  :::source,gmlewis/image/image.mbt,1776:::fn <a href="gmlewis/image#Paletted">Paletted</a>::op_set(self : <a href="gmlewis/image#Paletted">Paletted</a>, p : <a href="gmlewis/image#Point">Point</a>, c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
  ```
  > 
- #### rgba64\_at
  ```moonbit
  :::source,gmlewis/image/image.mbt,1753:::fn <a href="gmlewis/image#Paletted">Paletted</a>::rgba64_at(self : <a href="gmlewis/image#Paletted">Paletted</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>
  ```
  > 
- #### set\_color\_index
  ```moonbit
  :::source,gmlewis/image/image.mbt,1813:::fn <a href="gmlewis/image#Paletted">Paletted</a>::set_color_index(self : <a href="gmlewis/image#Paletted">Paletted</a>, x : Int, y : Int, index : Byte) -> Unit
  ```
  > 
- #### set\_rgba64
  ```moonbit
  :::source,gmlewis/image/image.mbt,1790:::fn <a href="gmlewis/image#Paletted">Paletted</a>::set_rgba64(self : <a href="gmlewis/image#Paletted">Paletted</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>) -> Unit
  ```
  > 

## Point

```moonbit
:::source,gmlewis/image/geom.mbt,10:::pub(all) struct Point {
  x : Int
  y : Int
}
```

 A Point is an X, Y coordinate pair. The axes increase right and down.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/geom.mbt,13:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/image#Point">Point</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/geom.mbt,13:::fn op_equal(<a href="gmlewis/image#Point">Point</a>, <a href="gmlewis/image#Point">Point</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/image/geom.mbt,13:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/image#Point">Point</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/geom.mbt,13:::fn output(<a href="gmlewis/image#Point">Point</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### div
  ```moonbit
  :::source,gmlewis/image/geom.mbt,41:::fn <a href="gmlewis/image#Point">Point</a>::div(self : <a href="gmlewis/image#Point">Point</a>, k : Int) -> <a href="gmlewis/image#Point">Point</a>
  ```
  > 
  >  div returns the vector p/k.
- #### is\_in
  ```moonbit
  :::source,gmlewis/image/geom.mbt,47:::fn <a href="gmlewis/image#Point">Point</a>::is_in(self : <a href="gmlewis/image#Point">Point</a>, r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> Bool
  ```
  > 
  >  is\_in reports whether p is in r.
- #### mod
  ```moonbit
  :::source,gmlewis/image/geom.mbt,54:::fn <a href="gmlewis/image#Point">Point</a>::mod(self : <a href="gmlewis/image#Point">Point</a>, r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Point">Point</a>
  ```
  > 
  >  mod returns the point q in r such that p.X-q.X is a multiple of r's width
  > and p.Y-q.Y is a multiple of r's height.
- #### mul
  ```moonbit
  :::source,gmlewis/image/geom.mbt,35:::fn <a href="gmlewis/image#Point">Point</a>::mul(self : <a href="gmlewis/image#Point">Point</a>, k : Int) -> <a href="gmlewis/image#Point">Point</a>
  ```
  > 
  >  mul returns the vector p\*k.
- #### op\_add
  ```moonbit
  :::source,gmlewis/image/geom.mbt,23:::fn <a href="gmlewis/image#Point">Point</a>::op_add(self : <a href="gmlewis/image#Point">Point</a>, q : <a href="gmlewis/image#Point">Point</a>) -> <a href="gmlewis/image#Point">Point</a>
  ```
  > 
  >  op\_add (+) returns the vector p+q.
- #### op\_equal
  ```moonbit
  :::source,gmlewis/image/geom.mbt,70:::fn <a href="gmlewis/image#Point">Point</a>::op_equal(self : <a href="gmlewis/image#Point">Point</a>, q : <a href="gmlewis/image#Point">Point</a>) -> Bool
  ```
  > 
  >  op\_equal reports whether p and q are equal.
- #### op\_sub
  ```moonbit
  :::source,gmlewis/image/geom.mbt,29:::fn <a href="gmlewis/image#Point">Point</a>::op_sub(self : <a href="gmlewis/image#Point">Point</a>, q : <a href="gmlewis/image#Point">Point</a>) -> <a href="gmlewis/image#Point">Point</a>
  ```
  > 
  >  op\_sub (-) returns the vector p-q.
- #### to\_string
  ```moonbit
  :::source,gmlewis/image/geom.mbt,17:::fn <a href="gmlewis/image#Point">Point</a>::to_string(self : <a href="gmlewis/image#Point">Point</a>) -> String
  ```
  > 
  >  to\_string returns a string representation of p like "(3,4)".

## RGBA

```moonbit
:::source,gmlewis/image/image.mbt,121:::pub(all) struct RGBA {
  pix : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
  stride : Int
  rect : <a href="gmlewis/image#Rectangle">Rectangle</a>
}
```

 RGBA is an in-memory image whose At method returns \[color.RGBA\] values.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/image.mbt,141:::impl <a href="gmlewis/image#Image">Image</a> for <a href="gmlewis/image#RGBA">RGBA</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,176:::fn at(self : <a href="gmlewis/image#RGBA">RGBA</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,166:::fn bounds(self : <a href="gmlewis/image#RGBA">RGBA</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,156:::fn color_index_at(_self : <a href="gmlewis/image#RGBA">RGBA</a>, _x : Int, _y : Int) -> Byte
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,161:::fn color_model(_self : <a href="gmlewis/image#RGBA">RGBA</a>) -> <a href="gmlewis/image/color#Model">@gmlewis/image/color.Model</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,146:::fn get_bytes_per_pixel(_self : <a href="gmlewis/image#RGBA">RGBA</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,151:::fn get_stride(self : <a href="gmlewis/image#RGBA">RGBA</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,282:::fn opaque(self : <a href="gmlewis/image#RGBA">RGBA</a>) -> Bool
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,214:::fn pix_offset(self : <a href="gmlewis/image#RGBA">RGBA</a>, x : Int, y : Int) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,141:::fn raw_data(self : <a href="gmlewis/image#RGBA">RGBA</a>) -> <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,224:::fn set(self : <a href="gmlewis/image#RGBA">RGBA</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,268:::fn sub_image(self : <a href="gmlewis/image#RGBA">RGBA</a>, r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Image">Image</a>
    ```
    > 
    >  sub\_image returns an image representing the portion of the image p visible
    > through r. The returned value shares pixels with the original image.

#### mooncakes-io-method-mark-Methods
- #### new
  ```moonbit
  :::source,gmlewis/image/image.mbt,302:::fn <a href="gmlewis/image#RGBA">RGBA</a>::new(r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#RGBA">RGBA</a>!<a href="gmlewis/image#SizeError">SizeError</a>
  ```
  > 
- #### new\_empty
  ```moonbit
  :::source,gmlewis/image/image.mbt,136:::fn <a href="gmlewis/image#RGBA">RGBA</a>::new_empty() -> <a href="gmlewis/image#RGBA">RGBA</a>
  ```
  > 
- #### op\_get
  ```moonbit
  :::source,gmlewis/image/image.mbt,171:::fn <a href="gmlewis/image#RGBA">RGBA</a>::op_get(self : <a href="gmlewis/image#RGBA">RGBA</a>, p : <a href="gmlewis/image#Point">Point</a>) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
  ```
  > 
- #### op\_set
  ```moonbit
  :::source,gmlewis/image/image.mbt,219:::fn <a href="gmlewis/image#RGBA">RGBA</a>::op_set(self : <a href="gmlewis/image#RGBA">RGBA</a>, p : <a href="gmlewis/image#Point">Point</a>, c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
  ```
  > 
- #### rgba64\_at
  ```moonbit
  :::source,gmlewis/image/image.mbt,181:::fn <a href="gmlewis/image#RGBA">RGBA</a>::rgba64_at(self : <a href="gmlewis/image#RGBA">RGBA</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>
  ```
  > 
- #### rgba\_at
  ```moonbit
  :::source,gmlewis/image/image.mbt,198:::fn <a href="gmlewis/image#RGBA">RGBA</a>::rgba_at(self : <a href="gmlewis/image#RGBA">RGBA</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#RGBA">@gmlewis/image/color.RGBA</a>
  ```
  > 
- #### set\_rgba
  ```moonbit
  :::source,gmlewis/image/image.mbt,254:::fn <a href="gmlewis/image#RGBA">RGBA</a>::set_rgba(self : <a href="gmlewis/image#RGBA">RGBA</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#RGBA">@gmlewis/image/color.RGBA</a>) -> Unit
  ```
  > 
- #### set\_rgba64
  ```moonbit
  :::source,gmlewis/image/image.mbt,237:::fn <a href="gmlewis/image#RGBA">RGBA</a>::set_rgba64(self : <a href="gmlewis/image#RGBA">RGBA</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>) -> Unit
  ```
  > 

## RGBA64

```moonbit
:::source,gmlewis/image/image.mbt,312:::pub(all) struct RGBA64 {
  pix : <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
  stride : Int
  rect : <a href="gmlewis/image#Rectangle">Rectangle</a>
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/image.mbt,332:::impl <a href="gmlewis/image#Image">Image</a> for <a href="gmlewis/image#RGBA64">RGBA64</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,367:::fn at(self : <a href="gmlewis/image#RGBA64">RGBA64</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,357:::fn bounds(self : <a href="gmlewis/image#RGBA64">RGBA64</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,347:::fn color_index_at(_self : <a href="gmlewis/image#RGBA64">RGBA64</a>, _x : Int, _y : Int) -> Byte
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,352:::fn color_model(_self : <a href="gmlewis/image#RGBA64">RGBA64</a>) -> <a href="gmlewis/image/color#Model">@gmlewis/image/color.Model</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,337:::fn get_bytes_per_pixel(_self : <a href="gmlewis/image#RGBA64">RGBA64</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,342:::fn get_stride(self : <a href="gmlewis/image#RGBA64">RGBA64</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,451:::fn opaque(self : <a href="gmlewis/image#RGBA64">RGBA64</a>) -> Bool
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,387:::fn pix_offset(self : <a href="gmlewis/image#RGBA64">RGBA64</a>, x : Int, y : Int) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,332:::fn raw_data(self : <a href="gmlewis/image#RGBA64">RGBA64</a>) -> <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,397:::fn set(self : <a href="gmlewis/image#RGBA64">RGBA64</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,437:::fn sub_image(self : <a href="gmlewis/image#RGBA64">RGBA64</a>, r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Image">Image</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### new
  ```moonbit
  :::source,gmlewis/image/image.mbt,471:::fn <a href="gmlewis/image#RGBA64">RGBA64</a>::new(r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#RGBA64">RGBA64</a>!<a href="gmlewis/image#SizeError">SizeError</a>
  ```
  > 
- #### new\_empty
  ```moonbit
  :::source,gmlewis/image/image.mbt,327:::fn <a href="gmlewis/image#RGBA64">RGBA64</a>::new_empty() -> <a href="gmlewis/image#RGBA64">RGBA64</a>
  ```
  > 
- #### op\_get
  ```moonbit
  :::source,gmlewis/image/image.mbt,362:::fn <a href="gmlewis/image#RGBA64">RGBA64</a>::op_get(self : <a href="gmlewis/image#RGBA64">RGBA64</a>, p : <a href="gmlewis/image#Point">Point</a>) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
  ```
  > 
- #### op\_set
  ```moonbit
  :::source,gmlewis/image/image.mbt,392:::fn <a href="gmlewis/image#RGBA64">RGBA64</a>::op_set(self : <a href="gmlewis/image#RGBA64">RGBA64</a>, p : <a href="gmlewis/image#Point">Point</a>, c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
  ```
  > 
- #### rgba64\_at
  ```moonbit
  :::source,gmlewis/image/image.mbt,372:::fn <a href="gmlewis/image#RGBA64">RGBA64</a>::rgba64_at(self : <a href="gmlewis/image#RGBA64">RGBA64</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>
  ```
  > 
- #### set\_rgba64
  ```moonbit
  :::source,gmlewis/image/image.mbt,414:::fn <a href="gmlewis/image#RGBA64">RGBA64</a>::set_rgba64(self : <a href="gmlewis/image#RGBA64">RGBA64</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>) -> Unit
  ```
  > 

## Rectangle

```moonbit
:::source,gmlewis/image/geom.mbt,89:::pub(all) struct Rectangle {
  min : <a href="gmlewis/image#Point">Point</a>
  max : <a href="gmlewis/image#Point">Point</a>
}
```

 A Rectangle contains the points with Min.X \<= X \< Max.X, Min.Y \<= Y \< Max.Y.
It is well-formed if Min.X \<= Max.X and likewise for Y. Points are always
well-formed. A rectangle's methods always return well-formed outputs for
well-formed inputs.

 A Rectangle is also an \[Image\] whose bounds are the rectangle itself. At
returns color.Opaque for points in the rectangle and color.Transparent
otherwise.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/geom.mbt,105:::impl <a href="gmlewis/image#Image">Image</a> for <a href="gmlewis/image#Rectangle">Rectangle</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/geom.mbt,325:::fn at(self : <a href="gmlewis/image#Rectangle">Rectangle</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>
    ```
    > 
    >  at implements the \[Image\] trait.
  * ```moonbit
    :::source,gmlewis/image/geom.mbt,343:::fn bounds(self : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
    ```
    > 
    >  bounds implements the \[Image\] trait.
  * ```moonbit
    :::source,gmlewis/image/geom.mbt,135:::fn color_index_at(_self : <a href="gmlewis/image#Rectangle">Rectangle</a>, _x : Int, _y : Int) -> Byte
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/geom.mbt,349:::fn color_model(_self : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image/color#Model">@gmlewis/image/color.Model</a>
    ```
    > 
    >  color\_model implements the \[Image\] trait.
  * ```moonbit
    :::source,gmlewis/image/geom.mbt,125:::fn get_bytes_per_pixel(_self : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/geom.mbt,130:::fn get_stride(_self : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/geom.mbt,105:::fn opaque(_self : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> Bool
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/geom.mbt,140:::fn pix_offset(_self : <a href="gmlewis/image#Rectangle">Rectangle</a>, _x : Int, _y : Int) -> Int
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/geom.mbt,120:::fn raw_data(_self : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[Byte]
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/geom.mbt,110:::fn set(_self : <a href="gmlewis/image#Rectangle">Rectangle</a>, _x : Int, _y : Int, _c : <a href="gmlewis/image/color#Color">@gmlewis/image/color.Color</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/geom.mbt,115:::fn sub_image(self : <a href="gmlewis/image#Rectangle">Rectangle</a>, _o : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Image">Image</a>
    ```
    > 
- ```moonbit
  :::source,gmlewis/image/geom.mbt,92:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/image#Rectangle">Rectangle</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/geom.mbt,92:::fn op_equal(<a href="gmlewis/image#Rectangle">Rectangle</a>, <a href="gmlewis/image#Rectangle">Rectangle</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/image/geom.mbt,92:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/image#Rectangle">Rectangle</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/geom.mbt,92:::fn output(<a href="gmlewis/image#Rectangle">Rectangle</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### add
  ```moonbit
  :::source,gmlewis/image/geom.mbt,176:::fn <a href="gmlewis/image#Rectangle">Rectangle</a>::add(self : <a href="gmlewis/image#Rectangle">Rectangle</a>, p : <a href="gmlewis/image#Point">Point</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
  ```
  > 
  >  add returns the rectangle r translated by p.
- #### canon
  ```moonbit
  :::source,gmlewis/image/geom.mbt,308:::fn <a href="gmlewis/image#Rectangle">Rectangle</a>::canon(self : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
  ```
  > 
  >  canon returns the canonical version of r. The returned rectangle has minimum
  > and maximum coordinates swapped if necessary so that it is well-formed.
- #### copy
  ```moonbit
  :::source,gmlewis/image/geom.mbt,146:::fn <a href="gmlewis/image#Rectangle">Rectangle</a>::copy(self : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
  ```
  > 
  >  copy makes a copy of the provided rectangle without changing it.
- #### dx
  ```moonbit
  :::source,gmlewis/image/geom.mbt,158:::fn <a href="gmlewis/image#Rectangle">Rectangle</a>::dx(self : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> Int
  ```
  > 
  >  dx returns r's width.
- #### dy
  ```moonbit
  :::source,gmlewis/image/geom.mbt,164:::fn <a href="gmlewis/image#Rectangle">Rectangle</a>::dy(self : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> Int
  ```
  > 
  >  dy returns r's height.
- #### empty
  ```moonbit
  :::source,gmlewis/image/geom.mbt,269:::fn <a href="gmlewis/image#Rectangle">Rectangle</a>::empty(self : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> Bool
  ```
  > 
  >  empty reports whether the rectangle contains no points.
- #### inset
  ```moonbit
  :::source,gmlewis/image/geom.mbt,196:::fn <a href="gmlewis/image#Rectangle">Rectangle</a>::inset(self : <a href="gmlewis/image#Rectangle">Rectangle</a>, n : Int) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
  ```
  > 
  >  inset returns the rectangle r inset by n, which may be negative. If either
  > of r's dimensions is less than 2\*n then an empty rectangle near the center
  > of r will be returned.
- #### intersect
  ```moonbit
  :::source,gmlewis/image/geom.mbt,218:::fn <a href="gmlewis/image#Rectangle">Rectangle</a>::intersect(self : <a href="gmlewis/image#Rectangle">Rectangle</a>, s : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
  ```
  > 
  >  intersect returns the largest rectangle contained by both r and s. If the
  > two rectangles do not overlap then the zero rectangle will be returned.
- #### is\_in
  ```moonbit
  :::source,gmlewis/image/geom.mbt,293:::fn <a href="gmlewis/image#Rectangle">Rectangle</a>::is_in(self : <a href="gmlewis/image#Rectangle">Rectangle</a>, s : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> Bool
  ```
  > 
  >  is\_in reports whether every point in r is in s.
- #### new
  ```moonbit
  :::source,gmlewis/image/geom.mbt,100:::fn <a href="gmlewis/image#Rectangle">Rectangle</a>::new() -> <a href="gmlewis/image#Rectangle">Rectangle</a>
  ```
  > 
  >  Rectangle::new returns an empty (all zeros) rectangle.
- #### op\_equal
  ```moonbit
  :::source,gmlewis/image/geom.mbt,276:::fn <a href="gmlewis/image#Rectangle">Rectangle</a>::op_equal(self : <a href="gmlewis/image#Rectangle">Rectangle</a>, s : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> Bool
  ```
  > 
  >  op\_equal reports whether r and s contain the same set of points. All empty
  > rectangles are considered equal.
- #### overlaps
  ```moonbit
  :::source,gmlewis/image/geom.mbt,282:::fn <a href="gmlewis/image#Rectangle">Rectangle</a>::overlaps(self : <a href="gmlewis/image#Rectangle">Rectangle</a>, s : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> Bool
  ```
  > 
  >  overlaps reports whether r and s have a non-empty intersection.
- #### rgba64\_at
  ```moonbit
  :::source,gmlewis/image/geom.mbt,334:::fn <a href="gmlewis/image#Rectangle">Rectangle</a>::rgba64_at(self : <a href="gmlewis/image#Rectangle">Rectangle</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>
  ```
  > 
  >  rgba64\_at implements the \[RGBA64Image\] trait.
- #### size
  ```moonbit
  :::source,gmlewis/image/geom.mbt,170:::fn <a href="gmlewis/image#Rectangle">Rectangle</a>::size(self : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Point">Point</a>
  ```
  > 
  >  size returns r's width and height.
- #### sub
  ```moonbit
  :::source,gmlewis/image/geom.mbt,185:::fn <a href="gmlewis/image#Rectangle">Rectangle</a>::sub(self : <a href="gmlewis/image#Rectangle">Rectangle</a>, p : <a href="gmlewis/image#Point">Point</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
  ```
  > 
  >  sub returns the rectangle r translated by -p.
- #### to\_string
  ```moonbit
  :::source,gmlewis/image/geom.mbt,152:::fn <a href="gmlewis/image#Rectangle">Rectangle</a>::to_string(self : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> String
  ```
  > 
  >  to\_string returns a string representation of r like "(3,4)-(6,5)".
- #### union
  ```moonbit
  :::source,gmlewis/image/geom.mbt,244:::fn <a href="gmlewis/image#Rectangle">Rectangle</a>::union(self : <a href="gmlewis/image#Rectangle">Rectangle</a>, s : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
  ```
  > 
  >  union returns the smallest rectangle that contains both r and s.

## SizeError

```moonbit
:::source,gmlewis/image/image.mbt,98:::type SizeError
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/image.mbt,98:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/image#SizeError">SizeError</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,98:::fn op_equal(<a href="gmlewis/image#SizeError">SizeError</a>, <a href="gmlewis/image#SizeError">SizeError</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/image/image.mbt,98:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/image#SizeError">SizeError</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/image.mbt,98:::fn output(<a href="gmlewis/image#SizeError">SizeError</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## add

```moonbit
:::source,gmlewis/image/geom.mbt,176:::fn add(self : <a href="gmlewis/image#Rectangle">Rectangle</a>, p : <a href="gmlewis/image#Point">Point</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
```

 add returns the rectangle r translated by p.

## add2\_non\_neg

```moonbit
:::source,gmlewis/image/geom.mbt,385:::fn add2_non_neg(x : Int, y : Int) -> Int
```

 add2\_non\_neg returns (x + y), unless at least one argument is negative or if
the computation overflows the int type, in which case it returns -1.

## alpha16\_at

```moonbit
:::source,gmlewis/image/image.mbt,1106:::fn alpha16_at(self : <a href="gmlewis/image#Alpha16">Alpha16</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#Alpha16">@gmlewis/image/color.Alpha16</a>
```


## alpha\_at

```moonbit
:::source,gmlewis/image/image.mbt,940:::fn alpha_at(self : <a href="gmlewis/image#Alpha">Alpha</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#Alpha">@gmlewis/image/color.Alpha</a>
```


## canon

```moonbit
:::source,gmlewis/image/geom.mbt,308:::fn canon(self : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
```

 canon returns the canonical version of r. The returned rectangle has minimum
and maximum coordinates swapped if necessary so that it is well-formed.

## cmyk\_at

```moonbit
:::source,gmlewis/image/image.mbt,1594:::fn cmyk_at(self : <a href="gmlewis/image#CMYK">CMYK</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#CMYK">@gmlewis/image/color.CMYK</a>
```


## copy

```moonbit
:::source,gmlewis/image/geom.mbt,146:::fn copy(self : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
```

 copy makes a copy of the provided rectangle without changing it.

## div

```moonbit
:::source,gmlewis/image/geom.mbt,41:::fn div(self : <a href="gmlewis/image#Point">Point</a>, k : Int) -> <a href="gmlewis/image#Point">Point</a>
```

 div returns the vector p/k.

## dx

```moonbit
:::source,gmlewis/image/geom.mbt,158:::fn dx(self : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> Int
```

 dx returns r's width.

## dy

```moonbit
:::source,gmlewis/image/geom.mbt,164:::fn dy(self : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> Int
```

 dy returns r's height.

## empty

```moonbit
:::source,gmlewis/image/geom.mbt,269:::fn empty(self : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> Bool
```

 empty reports whether the rectangle contains no points.

## gray16\_at

```moonbit
:::source,gmlewis/image/image.mbt,1436:::fn gray16_at(self : <a href="gmlewis/image#Gray16">Gray16</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#Gray16">@gmlewis/image/color.Gray16</a>
```


## gray\_at

```moonbit
:::source,gmlewis/image/image.mbt,1282:::fn gray_at(self : <a href="gmlewis/image#Gray">Gray</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#Gray">@gmlewis/image/color.Gray</a>
```


## inset

```moonbit
:::source,gmlewis/image/geom.mbt,196:::fn inset(self : <a href="gmlewis/image#Rectangle">Rectangle</a>, n : Int) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
```

 inset returns the rectangle r inset by n, which may be negative. If either
of r's dimensions is less than 2\*n then an empty rectangle near the center
of r will be returned.

## intersect

```moonbit
:::source,gmlewis/image/geom.mbt,218:::fn intersect(self : <a href="gmlewis/image#Rectangle">Rectangle</a>, s : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
```

 intersect returns the largest rectangle contained by both r and s. If the
two rectangles do not overlap then the zero rectangle will be returned.

## is\_in

```moonbit
:::source,gmlewis/image/geom.mbt,47:::fn is_in(self : <a href="gmlewis/image#Point">Point</a>, r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> Bool
```

 is\_in reports whether p is in r.

## mod

```moonbit
:::source,gmlewis/image/geom.mbt,54:::fn mod(self : <a href="gmlewis/image#Point">Point</a>, r : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Point">Point</a>
```

 mod returns the point q in r such that p.X-q.X is a multiple of r's width
and p.Y-q.Y is a multiple of r's height.

## mul

```moonbit
:::source,gmlewis/image/geom.mbt,35:::fn mul(self : <a href="gmlewis/image#Point">Point</a>, k : Int) -> <a href="gmlewis/image#Point">Point</a>
```

 mul returns the vector p\*k.

## mul3\_non\_neg

```moonbit
:::source,gmlewis/image/geom.mbt,366:::fn mul3_non_neg(x : Int, y : Int, z : Int) -> Int
```

 mul3\_non\_neg returns (x \* y \* z), unless at least one argument is negative or
if the computation overflows the int type, in which case it returns -1.

## nrgba64\_at

```moonbit
:::source,gmlewis/image/image.mbt,735:::fn nrgba64_at(self : <a href="gmlewis/image#NRGBA64">NRGBA64</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#NRGBA64">@gmlewis/image/color.NRGBA64</a>
```


## nrgba\_at

```moonbit
:::source,gmlewis/image/image.mbt,547:::fn nrgba_at(self : <a href="gmlewis/image#NRGBA">NRGBA</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#NRGBA">@gmlewis/image/color.NRGBA</a>
```


## op\_add

```moonbit
:::source,gmlewis/image/geom.mbt,23:::fn op_add(self : <a href="gmlewis/image#Point">Point</a>, q : <a href="gmlewis/image#Point">Point</a>) -> <a href="gmlewis/image#Point">Point</a>
```

 op\_add (+) returns the vector p+q.

## op\_equal

```moonbit
:::source,gmlewis/image/geom.mbt,70:::fn op_equal(self : <a href="gmlewis/image#Point">Point</a>, q : <a href="gmlewis/image#Point">Point</a>) -> Bool
```

 op\_equal reports whether p and q are equal.

## op\_sub

```moonbit
:::source,gmlewis/image/geom.mbt,29:::fn op_sub(self : <a href="gmlewis/image#Point">Point</a>, q : <a href="gmlewis/image#Point">Point</a>) -> <a href="gmlewis/image#Point">Point</a>
```

 op\_sub (-) returns the vector p-q.

## overlaps

```moonbit
:::source,gmlewis/image/geom.mbt,282:::fn overlaps(self : <a href="gmlewis/image#Rectangle">Rectangle</a>, s : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> Bool
```

 overlaps reports whether r and s have a non-empty intersection.

## pt

```moonbit
:::source,gmlewis/image/geom.mbt,76:::fn pt(x : Int, y : Int) -> <a href="gmlewis/image#Point">Point</a>
```

 pt is shorthand for \[Point\]{X, Y}.

## rect

```moonbit
:::source,gmlewis/image/geom.mbt,357:::fn rect(x0 : Int, y0 : Int, x1 : Int, y1 : Int) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
```

 rect is shorthand for \[Rectangle\]{Pt(x0, y0), \[Pt\](x1, y1)}. The returned
rectangle has minimum and maximum coordinates swapped if necessary so that
it is well-formed.

## rgba64\_at

```moonbit
:::source,gmlewis/image/geom.mbt,334:::fn rgba64_at(self : <a href="gmlewis/image#Rectangle">Rectangle</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#RGBA64">@gmlewis/image/color.RGBA64</a>
```

 rgba64\_at implements the \[RGBA64Image\] trait.

## rgba\_at

```moonbit
:::source,gmlewis/image/image.mbt,198:::fn rgba_at(self : <a href="gmlewis/image#RGBA">RGBA</a>, x : Int, y : Int) -> <a href="gmlewis/image/color#RGBA">@gmlewis/image/color.RGBA</a>
```


## set\_alpha

```moonbit
:::source,gmlewis/image/image.mbt,985:::fn set_alpha(self : <a href="gmlewis/image#Alpha">Alpha</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#Alpha">@gmlewis/image/color.Alpha</a>) -> Unit
```


## set\_alpha16

```moonbit
:::source,gmlewis/image/image.mbt,1154:::fn set_alpha16(self : <a href="gmlewis/image#Alpha16">Alpha16</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#Alpha16">@gmlewis/image/color.Alpha16</a>) -> Unit
```


## set\_cmyk

```moonbit
:::source,gmlewis/image/image.mbt,1650:::fn set_cmyk(self : <a href="gmlewis/image#CMYK">CMYK</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#CMYK">@gmlewis/image/color.CMYK</a>) -> Unit
```


## set\_color\_index

```moonbit
:::source,gmlewis/image/image.mbt,1813:::fn set_color_index(self : <a href="gmlewis/image#Paletted">Paletted</a>, x : Int, y : Int, index : Byte) -> Unit
```


## set\_gray

```moonbit
:::source,gmlewis/image/image.mbt,1329:::fn set_gray(self : <a href="gmlewis/image#Gray">Gray</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#Gray">@gmlewis/image/color.Gray</a>) -> Unit
```


## set\_gray16

```moonbit
:::source,gmlewis/image/image.mbt,1486:::fn set_gray16(self : <a href="gmlewis/image#Gray16">Gray16</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#Gray16">@gmlewis/image/color.Gray16</a>) -> Unit
```


## set\_nrgba

```moonbit
:::source,gmlewis/image/image.mbt,611:::fn set_nrgba(self : <a href="gmlewis/image#NRGBA">NRGBA</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#NRGBA">@gmlewis/image/color.NRGBA</a>) -> Unit
```


## set\_nrgba64

```moonbit
:::source,gmlewis/image/image.mbt,806:::fn set_nrgba64(self : <a href="gmlewis/image#NRGBA64">NRGBA64</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#NRGBA64">@gmlewis/image/color.NRGBA64</a>) -> Unit
```


## set\_rgba

```moonbit
:::source,gmlewis/image/image.mbt,254:::fn set_rgba(self : <a href="gmlewis/image#RGBA">RGBA</a>, x : Int, y : Int, c : <a href="gmlewis/image/color#RGBA">@gmlewis/image/color.RGBA</a>) -> Unit
```


## size

```moonbit
:::source,gmlewis/image/geom.mbt,170:::fn size(self : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Point">Point</a>
```

 size returns r's width and height.

## sub

```moonbit
:::source,gmlewis/image/geom.mbt,185:::fn sub(self : <a href="gmlewis/image#Rectangle">Rectangle</a>, p : <a href="gmlewis/image#Point">Point</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
```

 sub returns the rectangle r translated by -p.

## to\_string

```moonbit
:::source,gmlewis/image/geom.mbt,17:::fn to_string(self : <a href="gmlewis/image#Point">Point</a>) -> String
```

 to\_string returns a string representation of p like "(3,4)".

## union

```moonbit
:::source,gmlewis/image/geom.mbt,244:::fn union(self : <a href="gmlewis/image#Rectangle">Rectangle</a>, s : <a href="gmlewis/image#Rectangle">Rectangle</a>) -> <a href="gmlewis/image#Rectangle">Rectangle</a>
```

 union returns the smallest rectangle that contains both r and s.

## Image


#### mooncakes-io-method-mark-Methods
- #### empty
  ```moonbit
  :::source,gmlewis/image/image.mbt,78:::fn <a href="gmlewis/image#Image">Image</a>::empty(self : <a href="gmlewis/image#Image">Image</a>) -> Bool
  ```
  > 
- #### new\_empty
  ```moonbit
  :::source,gmlewis/image/image.mbt,73:::fn <a href="gmlewis/image#Image">Image</a>::new_empty() -> <a href="gmlewis/image#Image">Image</a>
  ```
  > 
