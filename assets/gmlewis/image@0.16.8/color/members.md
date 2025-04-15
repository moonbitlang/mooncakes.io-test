# Documentation
|Trait|description|
|---|---|
|[@gmlewis/image/color.Color](#@gmlewis/image/color.Color)||
|[@gmlewis/image/color.Model](#@gmlewis/image/color.Model)||

|Type|description|
|---|---|
|[Alpha](#Alpha)||
|[Alpha16](#Alpha16)||
|[CMYK](#CMYK)||
|[Gray](#Gray)||
|[Gray16](#Gray16)||
|[ModelFunc](#ModelFunc)||
|[NRGBA](#NRGBA)||
|[NRGBA64](#NRGBA64)||
|[NYCbCrA](#NYCbCrA)||
|[Palette](#Palette)||
|[RGBA](#RGBA)||
|[RGBA64](#RGBA64)||
|[YCbCr](#YCbCr)||
|[Color](#Color)||

|Value|description|
|---|---|
|[alpha16\_model](#alpha16_model)||
|[alpha\_model](#alpha_model)||
|[black](#black)||
|[cmyk\_model](#cmyk_model)||
|[cmyk\_to\_rgb](#cmyk_to_rgb)||
|[gray16\_model](#gray16_model)||
|[gray\_model](#gray_model)||
|[index](#index)||
|[length](#length)||
|[model\_func](#model_func)||
|[n\_y\_cb\_cr\_a\_model](#n_y_cb_cr_a_model)||
|[nrgba64\_model](#nrgba64_model)||
|[nrgba\_model](#nrgba_model)||
|[op\_as\_view](#op_as_view)||
|[op\_get](#op_get)||
|[op\_set](#op_set)||
|[opaque](#opaque)||
|[rgb\_to\_cmyk](#rgb_to_cmyk)||
|[rgb\_to\_y\_cb\_cr](#rgb_to_y_cb_cr)||
|[rgba64\_model](#rgba64_model)||
|[rgba\_model](#rgba_model)||
|[to\_string](#to_string)||
|[transparent](#transparent)||
|[white](#white)||
|[y\_cb\_cr\_model](#y_cb_cr_model)||
|[y\_cb\_cr\_to\_rgb](#y_cb_cr_to_rgb)||

## @gmlewis/image/color.Color

```moonbit
:::source,gmlewis/image/color/color.mbt,13:::pub(open) trait @gmlewis/image/color.Color {
  rgba(Self) -> (UInt, UInt, UInt, UInt)
  model(Self) -> String
  raw(Self) -> (UInt, UInt, UInt, UInt)
}
```

 Color can convert itself to alpha-premultiplied 16-bits per channel RGBA.
The conversion may be lossy.

## @gmlewis/image/color.Model

```moonbit
:::source,gmlewis/image/color/color.mbt,335:::pub(open) trait @gmlewis/image/color.Model {
  convert(Self, <a href="gmlewis/image/color#Color">Color</a>) -> <a href="gmlewis/image/color#Color">Color</a>
  name(Self) -> String
  get_palette(Self) -> <a href="gmlewis/image/color#Palette">Palette</a>?
}
```

 Model can convert any \[\&Color\] to one from its own color model. The conversion
may be lossy.

## Alpha

```moonbit
:::source,gmlewis/image/color/color.mbt,209:::pub(all) struct Alpha {
  a : Byte
}
```

 Alpha represents an 8-bit alpha color.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,223:::impl <a href="gmlewis/image/color#Color">Color</a> for <a href="gmlewis/image/color#Alpha">Alpha</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,223:::fn model(_self : <a href="gmlewis/image/color#Alpha">Alpha</a>) -> String
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,228:::fn raw(self : <a href="gmlewis/image/color#Alpha">Alpha</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,234:::fn rgba(self : <a href="gmlewis/image/color#Alpha">Alpha</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,211:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/image/color#Alpha">Alpha</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,211:::fn op_equal(<a href="gmlewis/image/color#Alpha">Alpha</a>, <a href="gmlewis/image/color#Alpha">Alpha</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,211:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/image/color#Alpha">Alpha</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,211:::fn output(<a href="gmlewis/image/color#Alpha">Alpha</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### from
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,498:::fn <a href="gmlewis/image/color#Alpha">Alpha</a>::from(c : <a href="gmlewis/image/color#Color">Color</a>) -> <a href="gmlewis/image/color#Alpha">Alpha</a>
  ```
  > 
- #### new
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,218:::fn <a href="gmlewis/image/color#Alpha">Alpha</a>::new(a : Byte) -> <a href="gmlewis/image/color#Alpha">Alpha</a>
  ```
  > 

## Alpha16

```moonbit
:::source,gmlewis/image/color/color.mbt,241:::pub(all) struct Alpha16 {
  a : UInt
}
```

 Alpha16 represents a 16-bit alpha color.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,255:::impl <a href="gmlewis/image/color#Color">Color</a> for <a href="gmlewis/image/color#Alpha16">Alpha16</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,255:::fn model(_self : <a href="gmlewis/image/color#Alpha16">Alpha16</a>) -> String
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,260:::fn raw(self : <a href="gmlewis/image/color#Alpha16">Alpha16</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,265:::fn rgba(self : <a href="gmlewis/image/color#Alpha16">Alpha16</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,243:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/image/color#Alpha16">Alpha16</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,243:::fn op_equal(<a href="gmlewis/image/color#Alpha16">Alpha16</a>, <a href="gmlewis/image/color#Alpha16">Alpha16</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,243:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/image/color#Alpha16">Alpha16</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,243:::fn output(<a href="gmlewis/image/color#Alpha16">Alpha16</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### from
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,514:::fn <a href="gmlewis/image/color#Alpha16">Alpha16</a>::from(c : <a href="gmlewis/image/color#Color">Color</a>) -> <a href="gmlewis/image/color#Alpha16">Alpha16</a>
  ```
  > 
- #### new
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,250:::fn <a href="gmlewis/image/color#Alpha16">Alpha16</a>::new(a : UInt) -> <a href="gmlewis/image/color#Alpha16">Alpha16</a>
  ```
  > 

## CMYK

```moonbit
:::source,gmlewis/image/color/ycbcr.mbt,430:::pub(all) struct CMYK {
  c : Byte
  m : Byte
  y : Byte
  k : Byte
}
```

 CMYK represents a fully opaque CMYK color, having 8 bits for each of cyan,
magenta, yellow and black.

 It is not associated with any particular color profile.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/color/ycbcr.mbt,447:::impl <a href="gmlewis/image/color#Color">Color</a> for <a href="gmlewis/image/color#CMYK">CMYK</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/ycbcr.mbt,447:::fn model(_self : <a href="gmlewis/image/color#CMYK">CMYK</a>) -> String
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/ycbcr.mbt,452:::fn raw(self : <a href="gmlewis/image/color#CMYK">CMYK</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/ycbcr.mbt,457:::fn rgba(self : <a href="gmlewis/image/color#CMYK">CMYK</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
- ```moonbit
  :::source,gmlewis/image/color/ycbcr.mbt,435:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/image/color#CMYK">CMYK</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/ycbcr.mbt,435:::fn op_equal(<a href="gmlewis/image/color#CMYK">CMYK</a>, <a href="gmlewis/image/color#CMYK">CMYK</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/image/color/ycbcr.mbt,435:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/image/color#CMYK">CMYK</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/ycbcr.mbt,435:::fn output(<a href="gmlewis/image/color#CMYK">CMYK</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### from
  ```moonbit
  :::source,gmlewis/image/color/ycbcr.mbt,478:::fn <a href="gmlewis/image/color#CMYK">CMYK</a>::from(c : <a href="gmlewis/image/color#Color">Color</a>) -> <a href="gmlewis/image/color#CMYK">CMYK</a>
  ```
  > 
- #### new
  ```moonbit
  :::source,gmlewis/image/color/ycbcr.mbt,442:::fn <a href="gmlewis/image/color#CMYK">CMYK</a>::new(c : Byte, m : Byte, y : Byte, k : Byte) -> <a href="gmlewis/image/color#CMYK">CMYK</a>
  ```
  > 

## Gray

```moonbit
:::source,gmlewis/image/color/color.mbt,271:::pub(all) struct Gray {
  y : Byte
}
```

 Gray represents an 8-bit grayscale color.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,285:::impl <a href="gmlewis/image/color#Color">Color</a> for <a href="gmlewis/image/color#Gray">Gray</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,285:::fn model(_self : <a href="gmlewis/image/color#Gray">Gray</a>) -> String
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,290:::fn raw(self : <a href="gmlewis/image/color#Gray">Gray</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,296:::fn rgba(self : <a href="gmlewis/image/color#Gray">Gray</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,273:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/image/color#Gray">Gray</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,273:::fn op_equal(<a href="gmlewis/image/color#Gray">Gray</a>, <a href="gmlewis/image/color#Gray">Gray</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,273:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/image/color#Gray">Gray</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,273:::fn output(<a href="gmlewis/image/color#Gray">Gray</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### from
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,529:::fn <a href="gmlewis/image/color#Gray">Gray</a>::from(c : <a href="gmlewis/image/color#Color">Color</a>) -> <a href="gmlewis/image/color#Gray">Gray</a>
  ```
  > 
- #### new
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,280:::fn <a href="gmlewis/image/color#Gray">Gray</a>::new(y : Byte) -> <a href="gmlewis/image/color#Gray">Gray</a>
  ```
  > 

## Gray16

```moonbit
:::source,gmlewis/image/color/color.mbt,303:::pub(all) struct Gray16 {
  y : UInt
}
```

 Gray16 represents a 16-bit grayscale color.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,317:::impl <a href="gmlewis/image/color#Color">Color</a> for <a href="gmlewis/image/color#Gray16">Gray16</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,317:::fn model(_self : <a href="gmlewis/image/color#Gray16">Gray16</a>) -> String
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,322:::fn raw(self : <a href="gmlewis/image/color#Gray16">Gray16</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,328:::fn rgba(self : <a href="gmlewis/image/color#Gray16">Gray16</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,305:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/image/color#Gray16">Gray16</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,305:::fn op_equal(<a href="gmlewis/image/color#Gray16">Gray16</a>, <a href="gmlewis/image/color#Gray16">Gray16</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,305:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/image/color#Gray16">Gray16</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,305:::fn output(<a href="gmlewis/image/color#Gray16">Gray16</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### from
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,555:::fn <a href="gmlewis/image/color#Gray16">Gray16</a>::from(c : <a href="gmlewis/image/color#Color">Color</a>) -> <a href="gmlewis/image/color#Gray16">Gray16</a>
  ```
  > 
- #### new
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,312:::fn <a href="gmlewis/image/color#Gray16">Gray16</a>::new(y : UInt) -> <a href="gmlewis/image/color#Gray16">Gray16</a>
  ```
  > 

## ModelFunc

```moonbit
:::source,gmlewis/image/color/color.mbt,358:::type ModelFunc
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,365:::impl <a href="gmlewis/image/color#Model">Model</a> for <a href="gmlewis/image/color#ModelFunc">ModelFunc</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,365:::fn convert(self : <a href="gmlewis/image/color#ModelFunc">ModelFunc</a>, c : <a href="gmlewis/image/color#Color">Color</a>) -> <a href="gmlewis/image/color#Color">Color</a>
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,375:::fn get_palette(self : <a href="gmlewis/image/color#ModelFunc">ModelFunc</a>) -> <a href="gmlewis/image/color#Palette">Palette</a>?
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,370:::fn name(self : <a href="gmlewis/image/color#ModelFunc">ModelFunc</a>) -> String
    ```
    > 

## NRGBA

```moonbit
:::source,gmlewis/image/color/color.mbt,128:::pub(all) struct NRGBA {
  r : Byte
  g : Byte
  b : Byte
  a : Byte
}
```

 NRGBA represents a non-alpha-premultiplied 32-bit color.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,145:::impl <a href="gmlewis/image/color#Color">Color</a> for <a href="gmlewis/image/color#NRGBA">NRGBA</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,145:::fn model(_self : <a href="gmlewis/image/color#NRGBA">NRGBA</a>) -> String
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,150:::fn raw(self : <a href="gmlewis/image/color#NRGBA">NRGBA</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,155:::fn rgba(self : <a href="gmlewis/image/color#NRGBA">NRGBA</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,133:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/image/color#NRGBA">NRGBA</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,133:::fn op_equal(<a href="gmlewis/image/color#NRGBA">NRGBA</a>, <a href="gmlewis/image/color#NRGBA">NRGBA</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,133:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/image/color#NRGBA">NRGBA</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,133:::fn output(<a href="gmlewis/image/color#NRGBA">NRGBA</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### from
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,444:::fn <a href="gmlewis/image/color#NRGBA">NRGBA</a>::from(c : <a href="gmlewis/image/color#Color">Color</a>) -> <a href="gmlewis/image/color#NRGBA">NRGBA</a>
  ```
  > 
- #### new
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,140:::fn <a href="gmlewis/image/color#NRGBA">NRGBA</a>::new(r : Byte, g : Byte, b : Byte, a : Byte) -> <a href="gmlewis/image/color#NRGBA">NRGBA</a>
  ```
  > 

## NRGBA64

```moonbit
:::source,gmlewis/image/color/color.mbt,173:::pub(all) struct NRGBA64 {
  r : UInt
  g : UInt
  b : UInt
  a : UInt
}
```

 NRGBA64 represents a non-alpha-premultiplied 64-bit color,
having 16 bits for each of red, green, blue and alpha.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,190:::impl <a href="gmlewis/image/color#Color">Color</a> for <a href="gmlewis/image/color#NRGBA64">NRGBA64</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,190:::fn model(_self : <a href="gmlewis/image/color#NRGBA64">NRGBA64</a>) -> String
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,195:::fn raw(self : <a href="gmlewis/image/color#NRGBA64">NRGBA64</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,200:::fn rgba(self : <a href="gmlewis/image/color#NRGBA64">NRGBA64</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,178:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/image/color#NRGBA64">NRGBA64</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,178:::fn op_equal(<a href="gmlewis/image/color#NRGBA64">NRGBA64</a>, <a href="gmlewis/image/color#NRGBA64">NRGBA64</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,178:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/image/color#NRGBA64">NRGBA64</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,178:::fn output(<a href="gmlewis/image/color#NRGBA64">NRGBA64</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### from
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,473:::fn <a href="gmlewis/image/color#NRGBA64">NRGBA64</a>::from(c : <a href="gmlewis/image/color#Color">Color</a>) -> <a href="gmlewis/image/color#NRGBA64">NRGBA64</a>
  ```
  > 
- #### new
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,185:::fn <a href="gmlewis/image/color#NRGBA64">NRGBA64</a>::new(r : UInt, g : UInt, b : UInt, a : UInt) -> <a href="gmlewis/image/color#NRGBA64">NRGBA64</a>
  ```
  > 

## NYCbCrA

```moonbit
:::source,gmlewis/image/color/ycbcr.mbt,277:::pub(all) struct NYCbCrA {
  y : Byte
  cb : Byte
  cr : Byte
  a : Byte
}
```

 NYCbCrA represents a non-alpha-premultiplied Y'CbCr-with-alpha color, having
8 bits each for one luma, two chroma and one alpha component.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/color/ycbcr.mbt,294:::impl <a href="gmlewis/image/color#Color">Color</a> for <a href="gmlewis/image/color#NYCbCrA">NYCbCrA</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/ycbcr.mbt,294:::fn model(_self : <a href="gmlewis/image/color#NYCbCrA">NYCbCrA</a>) -> String
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/ycbcr.mbt,299:::fn raw(self : <a href="gmlewis/image/color#NYCbCrA">NYCbCrA</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/ycbcr.mbt,304:::fn rgba(self : <a href="gmlewis/image/color#NYCbCrA">NYCbCrA</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
- ```moonbit
  :::source,gmlewis/image/color/ycbcr.mbt,282:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/image/color#NYCbCrA">NYCbCrA</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/ycbcr.mbt,282:::fn op_equal(<a href="gmlewis/image/color#NYCbCrA">NYCbCrA</a>, <a href="gmlewis/image/color#NYCbCrA">NYCbCrA</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/image/color/ycbcr.mbt,282:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/image/color#NYCbCrA">NYCbCrA</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/ycbcr.mbt,282:::fn output(<a href="gmlewis/image/color#NYCbCrA">NYCbCrA</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### new
  ```moonbit
  :::source,gmlewis/image/color/ycbcr.mbt,289:::fn <a href="gmlewis/image/color#NYCbCrA">NYCbCrA</a>::new(y : Byte, cb : Byte, cr : Byte, a : Byte) -> <a href="gmlewis/image/color#NYCbCrA">NYCbCrA</a>
  ```
  > 

## Palette

```moonbit
:::source,gmlewis/image/color/color.mbt,576:::pub(all) type Palette <a href="gmlewis/io#Slice">@gmlewis/io.Slice</a>[<a href="gmlewis/image/color#Color">Color</a>]
```

 Palette is a palette of colors and satisfies the Model trait.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,608:::impl <a href="gmlewis/image/color#Model">Model</a> for <a href="gmlewis/image/color#Palette">Palette</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,634:::fn convert(self : <a href="gmlewis/image/color#Palette">Palette</a>, c : <a href="gmlewis/image/color#Color">Color</a>) -> <a href="gmlewis/image/color#Color">Color</a>
    ```
    > 
    >  convert returns the palette color closest to c in Euclidean R,G,B space.
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,613:::fn get_palette(self : <a href="gmlewis/image/color#Palette">Palette</a>) -> <a href="gmlewis/image/color#Palette">Palette</a>?
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,608:::fn name(_self : <a href="gmlewis/image/color#Palette">Palette</a>) -> String
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### from
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,603:::fn <a href="gmlewis/image/color#Palette">Palette</a>::from(arr : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/image/color#Color">Color</a>]) -> <a href="gmlewis/image/color#Palette">Palette</a>
  ```
  > 
  >  Palette::from makes a new palette from the provided colors.
- #### index
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,645:::fn <a href="gmlewis/image/color#Palette">Palette</a>::index(self : <a href="gmlewis/image/color#Palette">Palette</a>, c : <a href="gmlewis/image/color#Color">Color</a>) -> Int
  ```
  > 
  >  index returns the index of the palette color closest to c in Euclidean
  > R,G,B,A space.
- #### length
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,623:::fn <a href="gmlewis/image/color#Palette">Palette</a>::length(self : <a href="gmlewis/image/color#Palette">Palette</a>) -> Int
  ```
  > 
- #### new
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,583:::fn <a href="gmlewis/image/color#Palette">Palette</a>::new(n : Int) -> <a href="gmlewis/image/color#Palette">Palette</a>
  ```
  > 
  >  Palette::new makes a new palette with `n` colors (initially all black).
- #### new\_empty
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,618:::fn <a href="gmlewis/image/color#Palette">Palette</a>::new_empty() -> <a href="gmlewis/image/color#Palette">Palette</a>
  ```
  > 
- #### op\_as\_view
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,628:::fn <a href="gmlewis/image/color#Palette">Palette</a>::op_as_view(self : <a href="gmlewis/image/color#Palette">Palette</a>, start~ : Int = .., end~ : Int) -> <a href="gmlewis/image/color#Palette">Palette</a>
  ```
  > 
- #### op\_get
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,597:::fn <a href="gmlewis/image/color#Palette">Palette</a>::op_get(self : <a href="gmlewis/image/color#Palette">Palette</a>, idx : Int) -> <a href="gmlewis/image/color#Color">Color</a>
  ```
  > 
- #### op\_set
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,592:::fn <a href="gmlewis/image/color#Palette">Palette</a>::op_set(self : <a href="gmlewis/image/color#Palette">Palette</a>, idx : Int, c : <a href="gmlewis/image/color#Color">Color</a>) -> Unit
  ```
  > 

## RGBA

```moonbit
:::source,gmlewis/image/color/color.mbt,54:::pub(all) struct RGBA {
  r : Byte
  g : Byte
  b : Byte
  a : Byte
}
```

 RGBA represents a traditional 32-bit alpha-premultiplied color, having 8
bits for each of red, green, blue and alpha.

 An alpha-premultiplied color component C has been scaled by alpha (A), so
has valid values 0 \<= C \<= A.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,71:::impl <a href="gmlewis/image/color#Color">Color</a> for <a href="gmlewis/image/color#RGBA">RGBA</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,71:::fn model(_self : <a href="gmlewis/image/color#RGBA">RGBA</a>) -> String
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,76:::fn raw(self : <a href="gmlewis/image/color#RGBA">RGBA</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,81:::fn rgba(self : <a href="gmlewis/image/color#RGBA">RGBA</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,59:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/image/color#RGBA">RGBA</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,59:::fn op_equal(<a href="gmlewis/image/color#RGBA">RGBA</a>, <a href="gmlewis/image/color#RGBA">RGBA</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,59:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/image/color#RGBA">RGBA</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,59:::fn output(<a href="gmlewis/image/color#RGBA">RGBA</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### from
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,410:::fn <a href="gmlewis/image/color#RGBA">RGBA</a>::from(c : <a href="gmlewis/image/color#Color">Color</a>) -> <a href="gmlewis/image/color#RGBA">RGBA</a>
  ```
  > 
- #### new
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,66:::fn <a href="gmlewis/image/color#RGBA">RGBA</a>::new(r : Byte, g : Byte, b : Byte, a : Byte) -> <a href="gmlewis/image/color#RGBA">RGBA</a>
  ```
  > 

## RGBA64

```moonbit
:::source,gmlewis/image/color/color.mbt,95:::pub(all) struct RGBA64 {
  r : UInt
  g : UInt
  b : UInt
  a : UInt
}
```

 RGBA64 represents a 64-bit alpha-premultiplied color, having 16 bits for
each of red, green, blue and alpha.

 An alpha-premultiplied color component C has been scaled by alpha (A), so
has valid values 0 \<= C \<= A.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,112:::impl <a href="gmlewis/image/color#Color">Color</a> for <a href="gmlewis/image/color#RGBA64">RGBA64</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,112:::fn model(_self : <a href="gmlewis/image/color#RGBA64">RGBA64</a>) -> String
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,117:::fn raw(self : <a href="gmlewis/image/color#RGBA64">RGBA64</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,122:::fn rgba(self : <a href="gmlewis/image/color#RGBA64">RGBA64</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,100:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/image/color#RGBA64">RGBA64</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,100:::fn op_equal(<a href="gmlewis/image/color#RGBA64">RGBA64</a>, <a href="gmlewis/image/color#RGBA64">RGBA64</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,100:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/image/color#RGBA64">RGBA64</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,100:::fn output(<a href="gmlewis/image/color#RGBA64">RGBA64</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### from
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,429:::fn <a href="gmlewis/image/color#RGBA64">RGBA64</a>::from(c : <a href="gmlewis/image/color#Color">Color</a>) -> <a href="gmlewis/image/color#RGBA64">RGBA64</a>
  ```
  > 
- #### new
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,107:::fn <a href="gmlewis/image/color#RGBA64">RGBA64</a>::new(r : UInt, g : UInt, b : UInt, a : UInt) -> <a href="gmlewis/image/color#RGBA64">RGBA64</a>
  ```
  > 

## YCbCr

```moonbit
:::source,gmlewis/image/color/ycbcr.mbt,173:::pub(all) struct YCbCr {
  y : Byte
  cb : Byte
  cr : Byte
}
```

 YCbCr represents a fully opaque 24-bit Y'CbCr color, having 8 bits each for
one luma and two chroma components.

 JPEG, VP8, the MPEG family and other codecs use this color model. Such
codecs often use the terms YUV and Y'CbCr interchangeably, but strictly
speaking, the term YUV applies only to analog video signals, and Y' (luma)
is Y (luminance) after applying gamma correction.

 Conversion between RGB and Y'CbCr is lossy and there are multiple, slightly
different formulae for converting between the two. This package follows
the JFIF specification at https://www.w3.org/Graphics/JPEG/jfif3.pdf.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/color/ycbcr.mbt,189:::impl <a href="gmlewis/image/color#Color">Color</a> for <a href="gmlewis/image/color#YCbCr">YCbCr</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/ycbcr.mbt,189:::fn model(_self : <a href="gmlewis/image/color#YCbCr">YCbCr</a>) -> String
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/ycbcr.mbt,194:::fn raw(self : <a href="gmlewis/image/color#YCbCr">YCbCr</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
  * ```moonbit
    :::source,gmlewis/image/color/ycbcr.mbt,199:::fn rgba(self : <a href="gmlewis/image/color#YCbCr">YCbCr</a>) -> (UInt, UInt, UInt, UInt)
    ```
    > 
- ```moonbit
  :::source,gmlewis/image/color/ycbcr.mbt,177:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/image/color#YCbCr">YCbCr</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/ycbcr.mbt,177:::fn op_equal(<a href="gmlewis/image/color#YCbCr">YCbCr</a>, <a href="gmlewis/image/color#YCbCr">YCbCr</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/image/color/ycbcr.mbt,177:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/image/color#YCbCr">YCbCr</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/ycbcr.mbt,177:::fn output(<a href="gmlewis/image/color#YCbCr">YCbCr</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### new
  ```moonbit
  :::source,gmlewis/image/color/ycbcr.mbt,184:::fn <a href="gmlewis/image/color#YCbCr">YCbCr</a>::new(y : Byte, cb : Byte, cr : Byte) -> <a href="gmlewis/image/color#YCbCr">YCbCr</a>
  ```
  > 

## alpha16\_model

```moonbit
:::source,gmlewis/image/color/color.mbt,396:::let alpha16_model : <a href="gmlewis/image/color#Model">Model</a>
```


## alpha\_model

```moonbit
:::source,gmlewis/image/color/color.mbt,393:::let alpha_model : <a href="gmlewis/image/color#Model">Model</a>
```


## black

```moonbit
:::source,gmlewis/image/color/color.mbt,702:::let black : <a href="gmlewis/image/color#Gray16">Gray16</a>
```

 Standard colors.

## cmyk\_model

```moonbit
:::source,gmlewis/image/color/ycbcr.mbt,470:::let cmyk_model : <a href="gmlewis/image/color#Model">Model</a>
```

 cmyk\_model is the \[Model\] for CMYK colors.

## cmyk\_to\_rgb

```moonbit
:::source,gmlewis/image/color/ycbcr.mbt,409:::fn cmyk_to_rgb(c : Byte, m : Byte, y : Byte, k : Byte) -> (Byte, Byte, Byte)
```

 cmyk\_to\_rgb converts a \[CMYK\] quadruple to an RGB triple.

## gray16\_model

```moonbit
:::source,gmlewis/image/color/color.mbt,402:::let gray16_model : <a href="gmlewis/image/color#Model">Model</a>
```


## gray\_model

```moonbit
:::source,gmlewis/image/color/color.mbt,399:::let gray_model : <a href="gmlewis/image/color#Model">Model</a>
```


## index

```moonbit
:::source,gmlewis/image/color/color.mbt,645:::fn index(self : <a href="gmlewis/image/color#Palette">Palette</a>, c : <a href="gmlewis/image/color#Color">Color</a>) -> Int
```

 index returns the index of the palette color closest to c in Euclidean
R,G,B,A space.

## length

```moonbit
:::source,gmlewis/image/color/color.mbt,623:::fn length(self : <a href="gmlewis/image/color#Palette">Palette</a>) -> Int
```


## model\_func

```moonbit
:::source,gmlewis/image/color/color.mbt,343:::fn model_func(f : (<a href="gmlewis/image/color#Color">Color</a>) -> <a href="gmlewis/image/color#Color">Color</a>, name : String, palette : <a href="gmlewis/image/color#Palette">Palette</a>?) -> <a href="gmlewis/image/color#Model">Model</a>
```

 model\_func returns a \[Model\] that invokes f to implement the conversion.

## n\_y\_cb\_cr\_a\_model

```moonbit
:::source,gmlewis/image/color/ycbcr.mbt,351:::let n_y_cb_cr_a_model : <a href="gmlewis/image/color#Model">Model</a>
```

 n\_y\_cb\_cr\_a\_model is the \[Model\] for non-alpha-premultiplied Y'CbCr-with-alpha
colors.

## nrgba64\_model

```moonbit
:::source,gmlewis/image/color/color.mbt,390:::let nrgba64_model : <a href="gmlewis/image/color#Model">Model</a>
```


## nrgba\_model

```moonbit
:::source,gmlewis/image/color/color.mbt,387:::let nrgba_model : <a href="gmlewis/image/color#Model">Model</a>
```


## op\_as\_view

```moonbit
:::source,gmlewis/image/color/color.mbt,628:::fn op_as_view(self : <a href="gmlewis/image/color#Palette">Palette</a>, start~ : Int = .., end~ : Int) -> <a href="gmlewis/image/color#Palette">Palette</a>
```


## op\_get

```moonbit
:::source,gmlewis/image/color/color.mbt,597:::fn op_get(self : <a href="gmlewis/image/color#Palette">Palette</a>, idx : Int) -> <a href="gmlewis/image/color#Color">Color</a>
```


## op\_set

```moonbit
:::source,gmlewis/image/color/color.mbt,592:::fn op_set(self : <a href="gmlewis/image/color#Palette">Palette</a>, idx : Int, c : <a href="gmlewis/image/color#Color">Color</a>) -> Unit
```


## opaque

```moonbit
:::source,gmlewis/image/color/color.mbt,711:::let opaque : <a href="gmlewis/image/color#Alpha16">Alpha16</a>
```


## rgb\_to\_cmyk

```moonbit
:::source,gmlewis/image/color/ycbcr.mbt,386:::fn rgb_to_cmyk(r : Byte, g : Byte, b : Byte) -> (Byte, Byte, Byte, Byte)
```

 rgb\_to\_cmyk converts an RGB triple to a CMYK quadruple.

## rgb\_to\_y\_cb\_cr

```moonbit
:::source,gmlewis/image/color/ycbcr.mbt,10:::fn rgb_to_y_cb_cr(r : Byte, g : Byte, b : Byte) -> (Byte, Byte, Byte)
```

 rgb\_to\_y\_cb\_cr converts an RGB triple to a Y'CbCr triple.

## rgba64\_model

```moonbit
:::source,gmlewis/image/color/color.mbt,384:::let rgba64_model : <a href="gmlewis/image/color#Model">Model</a>
```


## rgba\_model

```moonbit
:::source,gmlewis/image/color/color.mbt,381:::let rgba_model : <a href="gmlewis/image/color#Model">Model</a>
```

 Models for the standard color types.

## to\_string

```moonbit
:::source,gmlewis/image/color/color.mbt,36:::fn to_string(self : <a href="gmlewis/image/color#Color">Color</a>) -> String
```


## transparent

```moonbit
:::source,gmlewis/image/color/color.mbt,708:::let transparent : <a href="gmlewis/image/color#Alpha16">Alpha16</a>
```


## white

```moonbit
:::source,gmlewis/image/color/color.mbt,705:::let white : <a href="gmlewis/image/color#Gray16">Gray16</a>
```


## y\_cb\_cr\_model

```moonbit
:::source,gmlewis/image/color/ycbcr.mbt,258:::let y_cb_cr_model : <a href="gmlewis/image/color#Model">Model</a>
```

 y\_cb\_cr\_model is the \[Model\] for Y'CbCr colors.

## y\_cb\_cr\_to\_rgb

```moonbit
:::source,gmlewis/image/color/ycbcr.mbt,63:::fn y_cb_cr_to_rgb(y : Byte, cb : Byte, cr : Byte) -> (Byte, Byte, Byte)
```

 y\_cb\_cr\_to\_rgb converts a Y'CbCr triple to an RGB triple.

## Color


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,42:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/image/color#Color">Color</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,42:::fn op_equal(self : <a href="gmlewis/image/color#Color">Color</a>, o : <a href="gmlewis/image/color#Color">Color</a>) -> Bool
    ```
    > 
- ```moonbit
  :::source,gmlewis/image/color/color.mbt,31:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/image/color#Color">Color</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/image/color/color.mbt,31:::fn output(self : <a href="gmlewis/image/color#Color">Color</a>, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### to\_string
  ```moonbit
  :::source,gmlewis/image/color/color.mbt,36:::fn <a href="gmlewis/image/color#Color">Color</a>::to_string(self : <a href="gmlewis/image/color#Color">Color</a>) -> String
  ```
  > 
