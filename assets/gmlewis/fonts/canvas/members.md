# Documentation
|Type|description|
|---|---|
|[CanvasCtx](#CanvasCtx)||

|Value|description|
|---|---|
|[from\_graphic](#from_graphic)||
|[get\_input\_bytes](#get_input_bytes)||

## CanvasCtx

```moonbit
:::source,gmlewis/fonts/canvas/ffi.mbt,21:::type CanvasCtx
```


#### mooncakes-io-method-mark-Methods
- #### from\_graphic
  ```moonbit
  :::source,gmlewis/fonts/canvas/canvas.mbt,5:::fn <a href="gmlewis/fonts/canvas#CanvasCtx">CanvasCtx</a>::from_graphic(self : <a href="gmlewis/fonts/canvas#CanvasCtx">CanvasCtx</a>, g : <a href="gmlewis/fonts/draw#Graphic">@gmlewis/fonts/draw.Graphic</a>, y_up~ : Bool = ..) -> Unit
  ```
  > 
  >  from\_graphics renders a Graphic to an HTML5 canvas using its native API.
  > Note that if the design was created with Y being "up", then it
  > must be flipped to render properly in the canvas.
- #### get\_input\_bytes
  ```moonbit
  :::source,gmlewis/fonts/canvas/canvas.mbt,156:::fn <a href="gmlewis/fonts/canvas#CanvasCtx">CanvasCtx</a>::get_input_bytes(self : <a href="gmlewis/fonts/canvas#CanvasCtx">CanvasCtx</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[Byte]
  ```
  > 

## from\_graphic

```moonbit
:::source,gmlewis/fonts/canvas/canvas.mbt,5:::fn from_graphic(self : <a href="gmlewis/fonts/canvas#CanvasCtx">CanvasCtx</a>, g : <a href="gmlewis/fonts/draw#Graphic">@gmlewis/fonts/draw.Graphic</a>, y_up~ : Bool = ..) -> Unit
```

 from\_graphics renders a Graphic to an HTML5 canvas using its native API.
Note that if the design was created with Y being "up", then it
must be flipped to render properly in the canvas.

## get\_input\_bytes

```moonbit
:::source,gmlewis/fonts/canvas/canvas.mbt,156:::fn get_input_bytes(self : <a href="gmlewis/fonts/canvas#CanvasCtx">CanvasCtx</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[Byte]
```

