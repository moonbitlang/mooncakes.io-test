# Documentation
|Type|description|
|---|---|
|[Color](#Color)||
|[Context2D](#Context2D)||
|[Model](#Model)||

|Value|description|
|---|---|
|[begin\_path](#begin_path)||
|[clear\_rect](#clear_rect)||
|[context2d](#context2d)||
|[fill\_rect](#fill_rect)||
|[fill\_text](#fill_text)||
|[line\_to](#line_to)||
|[move\_to](#move_to)||
|[new](#new)||
|[set\_fill\_style](#set_fill_style)||
|[set\_line\_width](#set_line_width)||
|[set\_stroke\_style](#set_stroke_style)||
|[stroke](#stroke)||
|[to\_html](#to_html)||
|[to\_string](#to_string)||
|[to\_unsafe\_js](#to_unsafe_js)| Get the underlying \`CanvasRenderingContext2D\` js object.|

## Color

```moonbit
:::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,37:::pub(all) enum Color {
  RGB(Int, Int, Int)
  RGBA(Int, Int, Int, Int)
  Black
  White
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,42:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="Yoorkin/rabbit-tea/html/canvas#Color">Color</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,42:::fn output(<a href="Yoorkin/rabbit-tea/html/canvas#Color">Color</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### to\_string
  ```moonbit
  :::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,45:::fn <a href="Yoorkin/rabbit-tea/html/canvas#Color">Color</a>::to_string(self : <a href="Yoorkin/rabbit-tea/html/canvas#Color">Color</a>) -> String
  ```
  > 

## Context2D

```moonbit
:::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,2:::type Context2D
```


#### mooncakes-io-method-mark-Methods
- #### begin\_path
  ```moonbit
  :::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,12:::fn <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>::begin_path(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>) -> Unit
  ```
  > 
- #### clear\_rect
  ```moonbit
  :::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,76:::fn <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>::clear_rect(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>, x : Double, y : Double, width : Double, height : Double) -> Unit
  ```
  > 
- #### fill\_rect
  ```moonbit
  :::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,65:::fn <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>::fill_rect(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>, x : Double, y : Double, width : Double, height : Double) -> Unit
  ```
  > 
- #### fill\_text
  ```moonbit
  :::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,87:::fn <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>::fill_text(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>, text : String, x : Double, y : Double) -> Unit
  ```
  > 
- #### line\_to
  ```moonbit
  :::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,22:::fn <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>::line_to(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>, x : Double, y : Double) -> Unit
  ```
  > 
- #### move\_to
  ```moonbit
  :::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,17:::fn <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>::move_to(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>, x : Double, y : Double) -> Unit
  ```
  > 
- #### set\_fill\_style
  ```moonbit
  :::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,60:::fn <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>::set_fill_style(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>, color : <a href="Yoorkin/rabbit-tea/html/canvas#Color">Color</a>) -> Unit
  ```
  > 
- #### set\_line\_width
  ```moonbit
  :::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,27:::fn <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>::set_line_width(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>, width : Double) -> Unit
  ```
  > 
- #### set\_stroke\_style
  ```moonbit
  :::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,55:::fn <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>::set_stroke_style(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>, color : <a href="Yoorkin/rabbit-tea/html/canvas#Color">Color</a>) -> Unit
  ```
  > 
- #### stroke
  ```moonbit
  :::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,32:::fn <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>::stroke(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>) -> Unit
  ```
  > 
- #### to\_unsafe\_js
  ```moonbit
  :::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,7:::fn <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>::to_unsafe_js(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>) -> <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">@Yoorkin/rabbit-tea/dom.CanvasRenderingContext2D</a>
  ```
  >  Get the underlying `CanvasRenderingContext2D` js object.
  >  
  >  This function is unsafe and should be used rarely.

## Model

```moonbit
:::source,Yoorkin/rabbit-tea/html/canvas/canvas.mbt,2:::type Model[Msg]
```


#### mooncakes-io-method-mark-Methods
- #### context2d
  ```moonbit
  :::source,Yoorkin/rabbit-tea/html/canvas/canvas.mbt,8:::fn <a href="Yoorkin/rabbit-tea/html/canvas#Model">Model</a>::context2d[Msg](self : <a href="Yoorkin/rabbit-tea/html/canvas#Model">Model</a>[Msg]) -> <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>
  ```
  > 
- #### to\_html
  ```moonbit
  :::source,Yoorkin/rabbit-tea/html/canvas/canvas.mbt,62:::fn <a href="Yoorkin/rabbit-tea/html/canvas#Model">Model</a>::to_html[Msg](self : <a href="Yoorkin/rabbit-tea/html/canvas#Model">Model</a>[Msg]) -> <a href="Yoorkin/rabbit-tea/html#T">@Yoorkin/rabbit-tea/html.T</a>[Msg]
  ```
  > 

## begin\_path

```moonbit
:::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,12:::fn begin_path(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>) -> Unit
```


## clear\_rect

```moonbit
:::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,76:::fn clear_rect(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>, x : Double, y : Double, width : Double, height : Double) -> Unit
```


## context2d

```moonbit
:::source,Yoorkin/rabbit-tea/html/canvas/canvas.mbt,8:::fn context2d[Msg](self : <a href="Yoorkin/rabbit-tea/html/canvas#Model">Model</a>[Msg]) -> <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>
```


## fill\_rect

```moonbit
:::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,65:::fn fill_rect(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>, x : Double, y : Double, width : Double, height : Double) -> Unit
```


## fill\_text

```moonbit
:::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,87:::fn fill_text(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>, text : String, x : Double, y : Double) -> Unit
```


## line\_to

```moonbit
:::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,22:::fn line_to(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>, x : Double, y : Double) -> Unit
```


## move\_to

```moonbit
:::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,17:::fn move_to(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>, x : Double, y : Double) -> Unit
```


## new

```moonbit
:::source,Yoorkin/rabbit-tea/html/canvas/canvas.mbt,13:::fn new[Msg](width~ : Double, height~ : Double, click? : (<a href="Yoorkin/rabbit-tea/html#Mouse">@Yoorkin/rabbit-tea/html.Mouse</a>) -> Msg, mousemove? : (<a href="Yoorkin/rabbit-tea/html#Mouse">@Yoorkin/rabbit-tea/html.Mouse</a>) -> Msg, mousedown? : (<a href="Yoorkin/rabbit-tea/html#Mouse">@Yoorkin/rabbit-tea/html.Mouse</a>) -> Msg, mouseup? : (<a href="Yoorkin/rabbit-tea/html#Mouse">@Yoorkin/rabbit-tea/html.Mouse</a>) -> Msg, mouseenter? : (<a href="Yoorkin/rabbit-tea/html#Mouse">@Yoorkin/rabbit-tea/html.Mouse</a>) -> Msg, mouseleave? : (<a href="Yoorkin/rabbit-tea/html#Mouse">@Yoorkin/rabbit-tea/html.Mouse</a>) -> Msg) -> <a href="Yoorkin/rabbit-tea/html/canvas#Model">Model</a>[Msg]
```


## set\_fill\_style

```moonbit
:::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,60:::fn set_fill_style(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>, color : <a href="Yoorkin/rabbit-tea/html/canvas#Color">Color</a>) -> Unit
```


## set\_line\_width

```moonbit
:::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,27:::fn set_line_width(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>, width : Double) -> Unit
```


## set\_stroke\_style

```moonbit
:::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,55:::fn set_stroke_style(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>, color : <a href="Yoorkin/rabbit-tea/html/canvas#Color">Color</a>) -> Unit
```


## stroke

```moonbit
:::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,32:::fn stroke(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>) -> Unit
```


## to\_html

```moonbit
:::source,Yoorkin/rabbit-tea/html/canvas/canvas.mbt,62:::fn to_html[Msg](self : <a href="Yoorkin/rabbit-tea/html/canvas#Model">Model</a>[Msg]) -> <a href="Yoorkin/rabbit-tea/html#T">@Yoorkin/rabbit-tea/html.T</a>[Msg]
```


## to\_string

```moonbit
:::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,45:::fn to_string(self : <a href="Yoorkin/rabbit-tea/html/canvas#Color">Color</a>) -> String
```


## to\_unsafe\_js

```moonbit
:::source,Yoorkin/rabbit-tea/html/canvas/context2d.mbt,7:::fn to_unsafe_js(self : <a href="Yoorkin/rabbit-tea/html/canvas#Context2D">Context2D</a>) -> <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">@Yoorkin/rabbit-tea/dom.CanvasRenderingContext2D</a>
```
 Get the underlying `CanvasRenderingContext2D` js object.
 
 This function is unsafe and should be used rarely.
