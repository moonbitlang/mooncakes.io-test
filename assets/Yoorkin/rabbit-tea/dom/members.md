# Documentation
|Type|description|
|---|---|
|[CanvasGradient](#CanvasGradient)||
|[CanvasLineCap](#CanvasLineCap)||
|[CanvasLineJoin](#CanvasLineJoin)||
|[CanvasPattern](#CanvasPattern)||
|[CanvasRenderingContext2D](#CanvasRenderingContext2D)||
|[ClipboardEvent](#ClipboardEvent)||
|[DOMMatrix2DInit](#DOMMatrix2DInit)||
|[DOMRect](#DOMRect)||
|[DataTransfer](#DataTransfer)||
|[DataTransferItemList](#DataTransferItemList)||
|[Document](#Document)||
|[DocumentFragment](#DocumentFragment)||
|[Element](#Element)||
|[Event](#Event)||
|[EventTarget](#EventTarget)||
|[FocusEvent](#FocusEvent)||
|[GPUCanvasContext](#GPUCanvasContext)||
|[HTMLCanvasElement](#HTMLCanvasElement)||
|[HTMLDialogElement](#HTMLDialogElement)||
|[HTMLElement](#HTMLElement)||
|[HTMLInputElement](#HTMLInputElement)||
|[HTMLSelectElement](#HTMLSelectElement)||
|[ImageBitmapRenderingContext](#ImageBitmapRenderingContext)||
|[ImageData](#ImageData)||
|[ImageDataSettings](#ImageDataSettings)||
|[InputEvent](#InputEvent)||
|[KeyboardEvent](#KeyboardEvent)||
|[MouseEvent](#MouseEvent)||
|[Node](#Node)||
|[Path2D](#Path2D)||
|[Text](#Text)||
|[UIEvent](#UIEvent)||
|[Uint8ClampedArray](#Uint8ClampedArray)||
|[WebGL2RenderingContext](#WebGL2RenderingContext)||
|[WebGLRenderingContext](#WebGLRenderingContext)||
|[Window](#Window)||
|[Listener](#Listener)||
|[PredefinedColorSpace](#PredefinedColorSpace)| Possible values are "srgb" and "display-p3".|

|Value|description|
|---|---|
|[DOM\_KEY\_LOCATION\_LEFT](#DOM_KEY_LOCATION_LEFT)||
|[DOM\_KEY\_LOCATION\_NUMPAD](#DOM_KEY_LOCATION_NUMPAD)||
|[DOM\_KEY\_LOCATION\_RIGHT](#DOM_KEY_LOCATION_RIGHT)||
|[DOM\_KEY\_LOCATION\_STANDARD](#DOM_KEY_LOCATION_STANDARD)||
|[add\_event\_listener](#add_event_listener)||
|[append\_child](#append_child)||
|[count\_child](#count_child)||
|[create\_document\_fragment](#create_document_fragment)||
|[create\_element](#create_element)||
|[create\_text\_node](#create_text_node)||
|[current\_url](#current_url)||
|[dispatch\_event](#dispatch_event)||
|[document](#document)||
|[first\_child](#first_child)||
|[get\_element\_by\_id](#get_element_by_id)||
|[history\_go\_back](#history_go_back)||
|[history\_go\_forward](#history_go_forward)||
|[insert\_before](#insert_before)||
|[last\_child](#last_child)||
|[load\_url](#load_url)||
|[next\_sibling](#next_sibling)||
|[node\_name](#node_name)||
|[node\_type](#node_type)||
|[node\_value](#node_value)||
|[nth\_child](#nth_child)| |
|[parent\_node](#parent_node)||
|[previous\_sibling](#previous_sibling)||
|[push\_url](#push_url)||
|[reload\_url](#reload_url)||
|[remove\_child](#remove_child)||
|[remove\_event\_listener](#remove_event_listener)||
|[replace\_child](#replace_child)||
|[replace\_url](#replace_url)||
|[request\_animination\_frame](#request_animination_frame)||
|[scroll\_by](#scroll_by)||
|[scroll\_to](#scroll_to)||
|[scroll\_to\_bottom](#scroll_to_bottom)||
|[scroll\_to\_top](#scroll_to_top)||
|[to\_document](#to_document)||
|[to\_document\_fragment](#to_document_fragment)||
|[to\_element](#to_element)||
|[to\_event\_target](#to_event_target)||
|[to\_node](#to_node)||
|[to\_text](#to_text)||
|[window](#window)||

## CanvasGradient

```moonbit
:::source,Yoorkin/rabbit-tea/dom/canvas.mbt,564:::type CanvasGradient
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,154:::impl <a href="rami3l/js-ffi/js#Cast">@rami3l/js-ffi/js.Cast</a> for <a href="Yoorkin/rabbit-tea/dom#CanvasGradient">CanvasGradient</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,159:::fn from(value : <a href="Yoorkin/rabbit-tea/dom#CanvasGradient">CanvasGradient</a>) -> <a href="rami3l/js-ffi/js#Value">@rami3l/js-ffi/js.Value</a>
    ```
    > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,154:::fn into(value : <a href="rami3l/js-ffi/js#Value">@rami3l/js-ffi/js.Value</a>) -> <a href="Yoorkin/rabbit-tea/dom#CanvasGradient">CanvasGradient</a>?
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### add\_color\_stop
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,567:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasGradient">CanvasGradient</a>::add_color_stop(self : <a href="Yoorkin/rabbit-tea/dom#CanvasGradient">CanvasGradient</a>, offset : Double, color : String) -> Unit
  ```
  > 

## CanvasLineCap

```moonbit
:::source,Yoorkin/rabbit-tea/dom/canvas.mbt,440:::type CanvasLineCap
```


## CanvasLineJoin

```moonbit
:::source,Yoorkin/rabbit-tea/dom/canvas.mbt,443:::type CanvasLineJoin
```


## CanvasPattern

```moonbit
:::source,Yoorkin/rabbit-tea/dom/canvas.mbt,574:::type CanvasPattern
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,170:::impl <a href="rami3l/js-ffi/js#Cast">@rami3l/js-ffi/js.Cast</a> for <a href="Yoorkin/rabbit-tea/dom#CanvasPattern">CanvasPattern</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,175:::fn from(value : <a href="Yoorkin/rabbit-tea/dom#CanvasPattern">CanvasPattern</a>) -> <a href="rami3l/js-ffi/js#Value">@rami3l/js-ffi/js.Value</a>
    ```
    > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,170:::fn into(value : <a href="rami3l/js-ffi/js#Value">@rami3l/js-ffi/js.Value</a>) -> <a href="Yoorkin/rabbit-tea/dom#CanvasPattern">CanvasPattern</a>?
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### set\_transform
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,577:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasPattern">CanvasPattern</a>::set_transform(self : <a href="Yoorkin/rabbit-tea/dom#CanvasPattern">CanvasPattern</a>, transform : <a href="rami3l/js-ffi/js#Optional">@rami3l/js-ffi/js.Optional</a>[<a href="Yoorkin/rabbit-tea/dom#DOMMatrix2DInit">DOMMatrix2DInit</a>]) -> Unit
  ```
  > 

## CanvasRenderingContext2D

```moonbit
:::source,Yoorkin/rabbit-tea/dom/canvas.mbt,33:::type CanvasRenderingContext2D
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,42:::impl <a href="rami3l/js-ffi/js#Cast">@rami3l/js-ffi/js.Cast</a> for <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,47:::fn from(value : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>) -> <a href="rami3l/js-ffi/js#Value">@rami3l/js-ffi/js.Value</a>
    ```
    > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,42:::fn into(value : <a href="rami3l/js-ffi/js#Value">@rami3l/js-ffi/js.Value</a>) -> <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>?
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### arc
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,540:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::arc(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, x : Double, y : Double, radius : Double, start_angle : Double, end_angle : Double, anticlockwise~ : Bool = ..) -> Unit
  ```
  > 
- #### arc\_to
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,510:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::arc_to(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, x1 : Double, y1 : Double, x2 : Double, y2 : Double, radius : Double) -> Unit
  ```
  > 
- #### begin\_path
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,258:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::begin_path(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>) -> Unit
  ```
  > 
- #### bezier\_curve\_to
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,499:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::bezier_curve_to(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, cp1x : Double, cp1y : Double, cp2x : Double, cp2y : Double, x : Double, y : Double) -> Unit
  ```
  > 
- #### clear\_rect
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,229:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::clear_rect(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, x : Double, y : Double, w : Double, h : Double) -> Unit
  ```
  > 
- #### clip
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,287:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::clip(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, fill_rule~ : String = ..) -> Unit
  ```
  > 
- #### clip\_with\_path
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,293:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::clip_with_path(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, path : <a href="Yoorkin/rabbit-tea/dom#Path2D">Path2D</a>, fill_rule~ : String = ..) -> Unit
  ```
  > 
- #### close\_path
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,471:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::close_path(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>) -> Unit
  ```
  > 
- #### create\_image\_data
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,383:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::create_image_data(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, sw : Double, sh : Double, settings~ : <a href="rami3l/js-ffi/js#Optional">@rami3l/js-ffi/js.Optional</a>[<a href="Yoorkin/rabbit-tea/dom#ImageDataSettings">ImageDataSettings</a>] = ..) -> <a href="Yoorkin/rabbit-tea/dom#ImageData">ImageData</a>
  ```
  > 
- #### create\_image\_data\_with\_data
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,391:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::create_image_data_with_data(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, data : <a href="Yoorkin/rabbit-tea/dom#ImageData">ImageData</a>) -> <a href="Yoorkin/rabbit-tea/dom#ImageData">ImageData</a>
  ```
  > 
- #### create\_linear\_gradient
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,206:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::create_linear_gradient(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, x0 : Double, y0 : Double, x1 : Double, y1 : Double) -> <a href="Yoorkin/rabbit-tea/dom#CanvasGradient">CanvasGradient</a>
  ```
  > 
- #### create\_radial\_gradient
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,215:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::create_radial_gradient(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, x0 : Double, y0 : Double, r0 : Double, x1 : Double, y1 : Double, r1 : Double) -> <a href="Yoorkin/rabbit-tea/dom#CanvasGradient">CanvasGradient</a>
  ```
  > 
- #### draw\_image
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,354:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::draw_image(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, dx : Double, dy : Double) -> Unit
  ```
  > 
- #### draw\_image\_with\_size
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,361:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::draw_image_with_size(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, dx : Double, dy : Double, dw : Double, dh : Double) -> Unit
  ```
  > 
- #### draw\_image\_with\_src\_and\_dst\_size
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,370:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::draw_image_with_src_and_dst_size(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, sx : Double, sy : Double, sw : Double, sh : Double, dx : Double, dy : Double, dw : Double, dh : Double) -> Unit
  ```
  > 
- #### ellipse
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,551:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::ellipse(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, x : Double, y : Double, radius_x : Double, radius_y : Double, rotation : Double, start_angle : Double, end_angle : Double, anticlockwise~ : Bool = ..) -> Unit
  ```
  > 
- #### fill
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,263:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::fill(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, fill_rule~ : String = ..) -> Unit
  ```
  > 
- #### fill\_path
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,269:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::fill_path(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, path : <a href="Yoorkin/rabbit-tea/dom#Path2D">Path2D</a>, fill_rule~ : String = ..) -> Unit
  ```
  > 
- #### fill\_rect
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,238:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::fill_rect(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, x : Double, y : Double, w : Double, h : Double) -> Unit
  ```
  > 
- #### fill\_text
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,334:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::fill_text(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, text : String, x : Double, y : Double, max_width~ : <a href="rami3l/js-ffi/js#Optional">@rami3l/js-ffi/js.Optional</a>[Double] = ..) -> Unit
  ```
  > 
- #### get\_fill\_style
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,193:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::get_fill_style(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>) -> <a href="rami3l/js-ffi/js#Union3">@rami3l/js-ffi/js.Union3</a>[String, <a href="Yoorkin/rabbit-tea/dom#CanvasGradient">CanvasGradient</a>, <a href="Yoorkin/rabbit-tea/dom#CanvasPattern">CanvasPattern</a>]
  ```
  > 
- #### get\_image\_data
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,397:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::get_image_data(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, sx : Double, sy : Double, sw : Double, sh : Double, settings~ : <a href="rami3l/js-ffi/js#Optional">@rami3l/js-ffi/js.Optional</a>[<a href="Yoorkin/rabbit-tea/dom#ImageDataSettings">ImageDataSettings</a>] = ..) -> <a href="Yoorkin/rabbit-tea/dom#ImageData">ImageData</a>
  ```
  > 
- #### get\_image\_smoothing\_quality
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,137:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::get_image_smoothing_quality(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>) -> String
  ```
  > 
- #### get\_line\_cap
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,446:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::get_line_cap(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>) -> <a href="Yoorkin/rabbit-tea/dom#CanvasLineCap">CanvasLineCap</a>
  ```
  > 
- #### get\_line\_join
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,457:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::get_line_join(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>) -> <a href="Yoorkin/rabbit-tea/dom#CanvasLineJoin">CanvasLineJoin</a>
  ```
  > 
- #### get\_line\_with
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,429:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::get_line_with(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>) -> Double
  ```
  > 
- #### get\_stroke\_style
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,180:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::get_stroke_style(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>) -> <a href="rami3l/js-ffi/js#Union3">@rami3l/js-ffi/js.Union3</a>[String, <a href="Yoorkin/rabbit-tea/dom#CanvasGradient">CanvasGradient</a>, <a href="Yoorkin/rabbit-tea/dom#CanvasPattern">CanvasPattern</a>]
  ```
  > 
- #### image\_smoothing\_enabled
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,132:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::image_smoothing_enabled(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>) -> Bool
  ```
  > 
- #### is\_context\_lost
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,79:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::is_context_lost(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>) -> Bool
  ```
  > 
- #### is\_point\_in\_path
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,300:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::is_point_in_path(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, x : Double, y : Double, fill_rule~ : String = ..) -> Bool
  ```
  > 
- #### is\_point\_in\_path\_with\_path
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,308:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::is_point_in_path_with_path(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, path : <a href="Yoorkin/rabbit-tea/dom#Path2D">Path2D</a>, x : Double, y : Double, fill_rule~ : String = ..) -> Bool
  ```
  > 
- #### is\_point\_in\_stroke
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,317:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::is_point_in_stroke(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, x : Double, y : Double) -> Bool
  ```
  > 
- #### is\_point\_in\_stroke\_with\_path
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,324:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::is_point_in_stroke_with_path(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, path : <a href="Yoorkin/rabbit-tea/dom#Path2D">Path2D</a>, x : Double, y : Double) -> Bool
  ```
  > 
- #### line\_to
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,483:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::line_to(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, x : Double, y : Double) -> Unit
  ```
  > 
- #### move\_to
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,476:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::move_to(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, x : Double, y : Double) -> Unit
  ```
  > 
- #### put\_image\_data
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,407:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::put_image_data(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, image_data : <a href="Yoorkin/rabbit-tea/dom#ImageData">ImageData</a>, dx : Int, dy : Int) -> Unit
  ```
  > 
- #### put\_image\_data\_with\_dirty
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,415:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::put_image_data_with_dirty(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, image_data : <a href="Yoorkin/rabbit-tea/dom#ImageData">ImageData</a>, dx : Int, dy : Int, dirty_x : Int, dirty_y : Int, dirty_width : Int, dirty_height : Int) -> Unit
  ```
  > 
- #### quardratic\_curve\_to
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,490:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::quardratic_curve_to(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, cpx : Double, cpy : Double, x : Double, y : Double) -> Unit
  ```
  > 
- #### rect
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,520:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::rect(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, x : Double, y : Double, w : Double, h : Double) -> Unit
  ```
  > 
- #### reset
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,74:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::reset(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>) -> Unit
  ```
  > 
- #### reset\_transform
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,126:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::reset_transform(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>) -> Unit
  ```
  > 
- #### restore
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,69:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::restore(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>) -> Unit
  ```
  > 
- #### rotate
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,91:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::rotate(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, angle : Double) -> Unit
  ```
  > 
- #### round\_rect
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,529:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::round_rect(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, x : Double, y : Double, w : Double, h : Double, radius : Double) -> Unit
  ```
  > 
- #### save
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,64:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::save(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>) -> Unit
  ```
  > 
- #### scale
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,84:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::scale(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, x : Double, y : Double) -> Unit
  ```
  > 
- #### set\_fill\_style
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,199:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::set_fill_style(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, value : <a href="rami3l/js-ffi/js#Union3">@rami3l/js-ffi/js.Union3</a>[String, <a href="Yoorkin/rabbit-tea/dom#CanvasGradient">CanvasGradient</a>, <a href="Yoorkin/rabbit-tea/dom#CanvasPattern">CanvasPattern</a>]) -> Unit
  ```
  > 
- #### set\_image\_smoothing\_quality
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,142:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::set_image_smoothing_quality(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, value : String) -> Unit
  ```
  >  Possible values are "low", "medium", and "high".
- #### set\_line\_cap
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,451:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::set_line_cap(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, value : <a href="Yoorkin/rabbit-tea/dom#CanvasLineCap">CanvasLineCap</a>) -> Unit
  ```
  > 
- #### set\_line\_join
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,462:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::set_line_join(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, value : <a href="Yoorkin/rabbit-tea/dom#CanvasLineJoin">CanvasLineJoin</a>) -> Unit
  ```
  > 
- #### set\_line\_width
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,434:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::set_line_width(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, value : Double) -> Unit
  ```
  > 
- #### set\_stroke\_style
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,186:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::set_stroke_style(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, value : <a href="rami3l/js-ffi/js#Union3">@rami3l/js-ffi/js.Union3</a>[String, <a href="Yoorkin/rabbit-tea/dom#CanvasGradient">CanvasGradient</a>, <a href="Yoorkin/rabbit-tea/dom#CanvasPattern">CanvasPattern</a>]) -> Unit
  ```
  > 
- #### set\_transform
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,115:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::set_transform(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, a : Double, b : Double, c : Double, d : Double, e : Double, f : Double) -> Unit
  ```
  > 
- #### stroke
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,276:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::stroke(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>) -> Unit
  ```
  > 
- #### stroke\_rect
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,247:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::stroke_rect(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, x : Double, y : Double, w : Double, h : Double) -> Unit
  ```
  > 
- #### stroke\_text
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,343:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::stroke_text(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, text : String, x : Double, y : Double, max_width~ : <a href="rami3l/js-ffi/js#Optional">@rami3l/js-ffi/js.Optional</a>[Double] = ..) -> Unit
  ```
  > 
- #### stroke\_with\_path
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,281:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::stroke_with_path(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, path : <a href="Yoorkin/rabbit-tea/dom#Path2D">Path2D</a>) -> Unit
  ```
  > 
- #### transform
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,104:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::transform(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, a : Double, b : Double, c : Double, d : Double, e : Double, f : Double) -> Unit
  ```
  > 
- #### translate
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,97:::fn <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>::translate(self : <a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, x : Double, y : Double) -> Unit
  ```
  > 

## ClipboardEvent

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,145:::type ClipboardEvent
```


#### mooncakes-io-method-mark-Methods
- #### clipboard\_data
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,148:::fn <a href="Yoorkin/rabbit-tea/dom#ClipboardEvent">ClipboardEvent</a>::clipboard_data(self : <a href="Yoorkin/rabbit-tea/dom#ClipboardEvent">ClipboardEvent</a>) -> <a href="Yoorkin/rabbit-tea/dom#DataTransfer">DataTransfer</a>
  ```
  > 

## DOMMatrix2DInit

```moonbit
:::source,Yoorkin/rabbit-tea/dom/canvas.mbt,583:::type DOMMatrix2DInit
```


## DOMRect

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_rect.mbt,2:::type DOMRect
```


#### mooncakes-io-method-mark-Methods
- #### get\_bottom
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_rect.mbt,23:::fn <a href="Yoorkin/rabbit-tea/dom#DOMRect">DOMRect</a>::get_bottom(self : <a href="Yoorkin/rabbit-tea/dom#DOMRect">DOMRect</a>) -> Double
  ```
  > 
- #### get\_height
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_rect.mbt,14:::fn <a href="Yoorkin/rabbit-tea/dom#DOMRect">DOMRect</a>::get_height(self : <a href="Yoorkin/rabbit-tea/dom#DOMRect">DOMRect</a>) -> Double
  ```
  > 
- #### get\_left
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_rect.mbt,26:::fn <a href="Yoorkin/rabbit-tea/dom#DOMRect">DOMRect</a>::get_left(self : <a href="Yoorkin/rabbit-tea/dom#DOMRect">DOMRect</a>) -> Double
  ```
  > 
- #### get\_right
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_rect.mbt,20:::fn <a href="Yoorkin/rabbit-tea/dom#DOMRect">DOMRect</a>::get_right(self : <a href="Yoorkin/rabbit-tea/dom#DOMRect">DOMRect</a>) -> Double
  ```
  > 
- #### get\_top
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_rect.mbt,17:::fn <a href="Yoorkin/rabbit-tea/dom#DOMRect">DOMRect</a>::get_top(self : <a href="Yoorkin/rabbit-tea/dom#DOMRect">DOMRect</a>) -> Double
  ```
  > 
- #### get\_width
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_rect.mbt,11:::fn <a href="Yoorkin/rabbit-tea/dom#DOMRect">DOMRect</a>::get_width(self : <a href="Yoorkin/rabbit-tea/dom#DOMRect">DOMRect</a>) -> Double
  ```
  > 
- #### get\_x
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_rect.mbt,5:::fn <a href="Yoorkin/rabbit-tea/dom#DOMRect">DOMRect</a>::get_x(self : <a href="Yoorkin/rabbit-tea/dom#DOMRect">DOMRect</a>) -> Double
  ```
  > 
- #### get\_y
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_rect.mbt,8:::fn <a href="Yoorkin/rabbit-tea/dom#DOMRect">DOMRect</a>::get_y(self : <a href="Yoorkin/rabbit-tea/dom#DOMRect">DOMRect</a>) -> Double
  ```
  > 

## DataTransfer

```moonbit
:::source,Yoorkin/rabbit-tea/dom/data_transfer.mbt,2:::type DataTransfer
```


#### mooncakes-io-method-mark-Methods
- #### drop\_effect
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/data_transfer.mbt,5:::fn <a href="Yoorkin/rabbit-tea/dom#DataTransfer">DataTransfer</a>::drop_effect(self : <a href="Yoorkin/rabbit-tea/dom#DataTransfer">DataTransfer</a>) -> String
  ```
  > 
- #### effect\_allowed
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/data_transfer.mbt,8:::fn <a href="Yoorkin/rabbit-tea/dom#DataTransfer">DataTransfer</a>::effect_allowed(self : <a href="Yoorkin/rabbit-tea/dom#DataTransfer">DataTransfer</a>) -> String
  ```
  > 
- #### items
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/data_transfer.mbt,11:::fn <a href="Yoorkin/rabbit-tea/dom#DataTransfer">DataTransfer</a>::items(self : <a href="Yoorkin/rabbit-tea/dom#DataTransfer">DataTransfer</a>) -> <a href="Yoorkin/rabbit-tea/dom#DataTransferItemList">DataTransferItemList</a>
  ```
  >  
- #### set\_drog\_image
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/data_transfer.mbt,16:::fn <a href="Yoorkin/rabbit-tea/dom#DataTransfer">DataTransfer</a>::set_drog_image(self : <a href="Yoorkin/rabbit-tea/dom#DataTransfer">DataTransfer</a>, image : <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>, x : Int, y : Int) -> Unit
  ```
  > 

## DataTransferItemList

```moonbit
:::source,Yoorkin/rabbit-tea/dom/data_transfer.mbt,24:::type DataTransferItemList
```


#### mooncakes-io-method-mark-Methods
- #### add
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/data_transfer.mbt,38:::fn <a href="Yoorkin/rabbit-tea/dom#DataTransferItemList">DataTransferItemList</a>::add(self : <a href="Yoorkin/rabbit-tea/dom#DataTransferItemList">DataTransferItemList</a>, data : String, type_ : String) -> Unit
  ```
  > 
- #### clear
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/data_transfer.mbt,51:::fn <a href="Yoorkin/rabbit-tea/dom#DataTransferItemList">DataTransferItemList</a>::clear(self : <a href="Yoorkin/rabbit-tea/dom#DataTransferItemList">DataTransferItemList</a>) -> Unit
  ```
  > 
- #### length
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/data_transfer.mbt,27:::fn <a href="Yoorkin/rabbit-tea/dom#DataTransferItemList">DataTransferItemList</a>::length(self : <a href="Yoorkin/rabbit-tea/dom#DataTransferItemList">DataTransferItemList</a>) -> Int
  ```
  > 
- #### op\_get
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/data_transfer.mbt,32:::fn <a href="Yoorkin/rabbit-tea/dom#DataTransferItemList">DataTransferItemList</a>::op_get(self : <a href="Yoorkin/rabbit-tea/dom#DataTransferItemList">DataTransferItemList</a>, index : Int) -> Unit
  ```
  > 
- #### remove
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/data_transfer.mbt,45:::fn <a href="Yoorkin/rabbit-tea/dom#DataTransferItemList">DataTransferItemList</a>::remove(self : <a href="Yoorkin/rabbit-tea/dom#DataTransferItemList">DataTransferItemList</a>, index : Int) -> Unit
  ```
  > 

## Document

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_document.mbt,2:::type Document
```


#### mooncakes-io-method-mark-Methods
- #### create\_document\_fragment
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_document.mbt,20:::fn <a href="Yoorkin/rabbit-tea/dom#Document">Document</a>::create_document_fragment(self : <a href="Yoorkin/rabbit-tea/dom#Document">Document</a>) -> <a href="Yoorkin/rabbit-tea/dom#DocumentFragment">DocumentFragment</a>
  ```
  > 
- #### create\_element
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_document.mbt,14:::fn <a href="Yoorkin/rabbit-tea/dom#Document">Document</a>::create_element(self : <a href="Yoorkin/rabbit-tea/dom#Document">Document</a>, tag : String) -> <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>
  ```
  > 
- #### create\_text\_node
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_document.mbt,17:::fn <a href="Yoorkin/rabbit-tea/dom#Document">Document</a>::create_text_node(self : <a href="Yoorkin/rabbit-tea/dom#Document">Document</a>, str : String) -> <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>
  ```
  > 
- #### get\_element\_by\_id
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_document.mbt,8:::fn <a href="Yoorkin/rabbit-tea/dom#Document">Document</a>::get_element_by_id(self : <a href="Yoorkin/rabbit-tea/dom#Document">Document</a>, id : String) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#Element">Element</a>]
  ```
  > 
- #### to\_node
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_cast.mbt,25:::fn <a href="Yoorkin/rabbit-tea/dom#Document">Document</a>::to_node(self : <a href="Yoorkin/rabbit-tea/dom#Document">Document</a>) -> <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>
  ```
  > 

## DocumentFragment

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_fragment.mbt,2:::type DocumentFragment
```


#### mooncakes-io-method-mark-Methods
- #### to\_node
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_cast.mbt,28:::fn <a href="Yoorkin/rabbit-tea/dom#DocumentFragment">DocumentFragment</a>::to_node(self : <a href="Yoorkin/rabbit-tea/dom#DocumentFragment">DocumentFragment</a>) -> <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>
  ```
  > 

## Element

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,2:::type Element
```


#### mooncakes-io-method-mark-Methods
- #### append\_children
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,15:::fn <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>::append_children(self : <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>, child : <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>) -> Unit
  ```
  > 
- #### children
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,11:::fn <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>::children(self : <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/dom#Element">Element</a>]
  ```
  > 
- #### get\_attribute
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,38:::fn <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>::get_attribute(self : <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>, attr : String) -> String
  ```
  > 
- #### get\_bounding\_client\_rect
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,79:::fn <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>::get_bounding_client_rect(self : <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>) -> <a href="Yoorkin/rabbit-tea/dom#DOMRect">DOMRect</a>
  ```
  > 
- #### get\_property
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,63:::fn <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>::get_property(self : <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>, prop : String) -> String
  ```
  > 
- #### remove\_attribute
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,44:::fn <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>::remove_attribute(self : <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>, attr : String) -> Unit
  ```
  > 
- #### remove\_children
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,21:::fn <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>::remove_children(self : <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>, child : <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>) -> Unit
  ```
  > 
- #### remove\_property
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,57:::fn <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>::remove_property(self : <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>, prop : String) -> Unit
  ```
  > 
- #### scroll\_into\_view
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,69:::fn <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>::scroll_into_view(self : <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>) -> Unit
  ```
  > 
- #### set\_attribute
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,31:::fn <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>::set_attribute(self : <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>, attr : String, value : String) -> Unit
  ```
  > 
- #### set\_inner\_html
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,73:::fn <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>::set_inner_html(self : <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>, html : String) -> Unit
  ```
  > 
- #### set\_property
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,50:::fn <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>::set_property(self : <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>, prop : String, value : <a href="rami3l/js-ffi/js#Value">@rami3l/js-ffi/js.Value</a>) -> Unit
  ```
  >  
- #### to\_html\_element
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,5:::fn <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>::to_html_element(self : <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#HTMLElement">HTMLElement</a>]
  ```
  > 
- #### to\_node
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_cast.mbt,31:::fn <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>::to_node(self : <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>) -> <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>
  ```
  > 

## Event

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,12:::type Event
```

 
 #### Hierarchy of DOM Events
 
 ```
 Event <-+-- ClipboardEvent
         +-- UIEvent <--+-- MouseEvent
                        +-- InputEvent
                        +-- FocusEvent
                        +-- KeyboardEvent
 ```

#### mooncakes-io-method-mark-Methods
- #### prevent\_default
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,28:::fn <a href="Yoorkin/rabbit-tea/dom#Event">Event</a>::prevent_default(self : <a href="Yoorkin/rabbit-tea/dom#Event">Event</a>) -> Unit
  ```
  > 
- #### stop\_propagation
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,31:::fn <a href="Yoorkin/rabbit-tea/dom#Event">Event</a>::stop_propagation(self : <a href="Yoorkin/rabbit-tea/dom#Event">Event</a>) -> Unit
  ```
  > 
- #### target
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,15:::fn <a href="Yoorkin/rabbit-tea/dom#Event">Event</a>::target(self : <a href="Yoorkin/rabbit-tea/dom#Event">Event</a>) -> <a href="Yoorkin/rabbit-tea/dom#EventTarget">EventTarget</a>
  ```
  > 
- #### to\_clipboard\_event
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,22:::fn <a href="Yoorkin/rabbit-tea/dom#Event">Event</a>::to_clipboard_event(self : <a href="Yoorkin/rabbit-tea/dom#Event">Event</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>]
  ```
  > 
- #### to\_ui\_event
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,18:::fn <a href="Yoorkin/rabbit-tea/dom#Event">Event</a>::to_ui_event(self : <a href="Yoorkin/rabbit-tea/dom#Event">Event</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#UIEvent">UIEvent</a>]
  ```
  > 

## EventTarget

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_event_target.mbt,10:::type EventTarget
```

 #### Hireharchy related to the DOM EventTarget
 
 ```
 EventTarget <-- Node <--+-- Document
                         +-- DocumentFragment
                         +-- Element <-- HTMLElement <--+-- HTMLCanvasElement
                                                        +-- HTMLInputElement
 ```

#### mooncakes-io-method-mark-Methods
- #### add\_event\_listener
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event_target.mbt,17:::fn <a href="Yoorkin/rabbit-tea/dom#EventTarget">EventTarget</a>::add_event_listener(self : <a href="Yoorkin/rabbit-tea/dom#EventTarget">EventTarget</a>, type_ : String, callback : (<a href="Yoorkin/rabbit-tea/dom#Event">Event</a>) -> Unit) -> Unit
  ```
  > 
- #### dispatch\_event
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event_target.mbt,33:::fn <a href="Yoorkin/rabbit-tea/dom#EventTarget">EventTarget</a>::dispatch_event(self : <a href="Yoorkin/rabbit-tea/dom#EventTarget">EventTarget</a>, event : <a href="Yoorkin/rabbit-tea/dom#Event">Event</a>) -> Unit
  ```
  > 
- #### remove\_event\_listener
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event_target.mbt,25:::fn <a href="Yoorkin/rabbit-tea/dom#EventTarget">EventTarget</a>::remove_event_listener(self : <a href="Yoorkin/rabbit-tea/dom#EventTarget">EventTarget</a>, type_ : String, callback : (<a href="Yoorkin/rabbit-tea/dom#Event">Event</a>) -> Unit) -> Unit
  ```
  > 
- #### to\_node
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event_target.mbt,13:::fn <a href="Yoorkin/rabbit-tea/dom#EventTarget">EventTarget</a>::to_node(self : <a href="Yoorkin/rabbit-tea/dom#EventTarget">EventTarget</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#Node">Node</a>]
  ```
  > 

## FocusEvent

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,97:::type FocusEvent
```


#### mooncakes-io-method-mark-Methods
- #### related\_target
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,100:::fn <a href="Yoorkin/rabbit-tea/dom#FocusEvent">FocusEvent</a>::related_target(self : <a href="Yoorkin/rabbit-tea/dom#FocusEvent">FocusEvent</a>) -> <a href="Yoorkin/rabbit-tea/dom#EventTarget">EventTarget</a>
  ```
  > 

## GPUCanvasContext

```moonbit
:::source,Yoorkin/rabbit-tea/dom/canvas.mbt,61:::type GPUCanvasContext
```


## HTMLCanvasElement

```moonbit
:::source,Yoorkin/rabbit-tea/dom/canvas.mbt,2:::type HTMLCanvasElement
```


#### mooncakes-io-method-mark-Methods
- #### get\_context
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,20:::fn <a href="Yoorkin/rabbit-tea/dom#HTMLCanvasElement">HTMLCanvasElement</a>::get_context(self : <a href="Yoorkin/rabbit-tea/dom#HTMLCanvasElement">HTMLCanvasElement</a>, context_id : String) -> <a href="rami3l/js-ffi/js#Union5">@rami3l/js-ffi/js.Union5</a>[<a href="Yoorkin/rabbit-tea/dom#CanvasRenderingContext2D">CanvasRenderingContext2D</a>, <a href="Yoorkin/rabbit-tea/dom#ImageBitmapRenderingContext">ImageBitmapRenderingContext</a>, <a href="Yoorkin/rabbit-tea/dom#WebGLRenderingContext">WebGLRenderingContext</a>, <a href="Yoorkin/rabbit-tea/dom#WebGL2RenderingContext">WebGL2RenderingContext</a>, <a href="Yoorkin/rabbit-tea/dom#GPUCanvasContext">GPUCanvasContext</a>]
  ```
  > 
- #### get\_height
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,15:::fn <a href="Yoorkin/rabbit-tea/dom#HTMLCanvasElement">HTMLCanvasElement</a>::get_height(self : <a href="Yoorkin/rabbit-tea/dom#HTMLCanvasElement">HTMLCanvasElement</a>) -> Int
  ```
  > 
- #### get\_width
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,10:::fn <a href="Yoorkin/rabbit-tea/dom#HTMLCanvasElement">HTMLCanvasElement</a>::get_width(self : <a href="Yoorkin/rabbit-tea/dom#HTMLCanvasElement">HTMLCanvasElement</a>) -> Int
  ```
  > 
- #### to\_html\_element
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,5:::fn <a href="Yoorkin/rabbit-tea/dom#HTMLCanvasElement">HTMLCanvasElement</a>::to_html_element(self : <a href="Yoorkin/rabbit-tea/dom#HTMLCanvasElement">HTMLCanvasElement</a>) -> <a href="Yoorkin/rabbit-tea/dom#HTMLElement">HTMLElement</a>
  ```
  > 

## HTMLDialogElement

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,137:::type HTMLDialogElement
```


#### mooncakes-io-method-mark-Methods
- #### close
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,148:::fn <a href="Yoorkin/rabbit-tea/dom#HTMLDialogElement">HTMLDialogElement</a>::close(self : <a href="Yoorkin/rabbit-tea/dom#HTMLDialogElement">HTMLDialogElement</a>, return_value~ : <a href="rami3l/js-ffi/js#Optional">@rami3l/js-ffi/js.Optional</a>[String] = ..) -> Unit
  ```
  > 
- #### open
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,140:::fn <a href="Yoorkin/rabbit-tea/dom#HTMLDialogElement">HTMLDialogElement</a>::open(self : <a href="Yoorkin/rabbit-tea/dom#HTMLDialogElement">HTMLDialogElement</a>) -> Bool
  ```
  > 
- #### request\_close
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,154:::fn <a href="Yoorkin/rabbit-tea/dom#HTMLDialogElement">HTMLDialogElement</a>::request_close(self : <a href="Yoorkin/rabbit-tea/dom#HTMLDialogElement">HTMLDialogElement</a>, return_value~ : <a href="rami3l/js-ffi/js#Optional">@rami3l/js-ffi/js.Optional</a>[String] = ..) -> Unit
  ```
  > 
- #### return\_value
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,143:::fn <a href="Yoorkin/rabbit-tea/dom#HTMLDialogElement">HTMLDialogElement</a>::return_value(self : <a href="Yoorkin/rabbit-tea/dom#HTMLDialogElement">HTMLDialogElement</a>) -> String
  ```
  > 
- #### show
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,160:::fn <a href="Yoorkin/rabbit-tea/dom#HTMLDialogElement">HTMLDialogElement</a>::show(self : <a href="Yoorkin/rabbit-tea/dom#HTMLDialogElement">HTMLDialogElement</a>) -> Unit
  ```
  > 
- #### show\_modal
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,163:::fn <a href="Yoorkin/rabbit-tea/dom#HTMLDialogElement">HTMLDialogElement</a>::show_modal(self : <a href="Yoorkin/rabbit-tea/dom#HTMLDialogElement">HTMLDialogElement</a>) -> Unit
  ```
  > 

## HTMLElement

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,83:::type HTMLElement
```


#### mooncakes-io-method-mark-Methods
- #### remove\_style
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,121:::fn <a href="Yoorkin/rabbit-tea/dom#HTMLElement">HTMLElement</a>::remove_style(self : <a href="Yoorkin/rabbit-tea/dom#HTMLElement">HTMLElement</a>, key : String) -> Unit
  ```
  > 
- #### set\_style
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,113:::fn <a href="Yoorkin/rabbit-tea/dom#HTMLElement">HTMLElement</a>::set_style(self : <a href="Yoorkin/rabbit-tea/dom#HTMLElement">HTMLElement</a>, key : String, value : String) -> Unit
  ```
  > 
- #### to\_element
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,86:::fn <a href="Yoorkin/rabbit-tea/dom#HTMLElement">HTMLElement</a>::to_element(self : <a href="Yoorkin/rabbit-tea/dom#HTMLElement">HTMLElement</a>) -> <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>
  ```
  > 
- #### to\_html\_canvas\_element
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,89:::fn <a href="Yoorkin/rabbit-tea/dom#HTMLElement">HTMLElement</a>::to_html_canvas_element(self : <a href="Yoorkin/rabbit-tea/dom#HTMLElement">HTMLElement</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#HTMLCanvasElement">HTMLCanvasElement</a>]
  ```
  > 
- #### to\_html\_dialog\_element
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,107:::fn <a href="Yoorkin/rabbit-tea/dom#HTMLElement">HTMLElement</a>::to_html_dialog_element(self : <a href="Yoorkin/rabbit-tea/dom#HTMLElement">HTMLElement</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#HTMLDialogElement">HTMLDialogElement</a>]
  ```
  > 
- #### to\_html\_input\_element
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,95:::fn <a href="Yoorkin/rabbit-tea/dom#HTMLElement">HTMLElement</a>::to_html_input_element(self : <a href="Yoorkin/rabbit-tea/dom#HTMLElement">HTMLElement</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#HTMLInputElement">HTMLInputElement</a>]
  ```
  > 
- #### to\_html\_select\_element
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,101:::fn <a href="Yoorkin/rabbit-tea/dom#HTMLElement">HTMLElement</a>::to_html_select_element(self : <a href="Yoorkin/rabbit-tea/dom#HTMLElement">HTMLElement</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#HTMLSelectElement">HTMLSelectElement</a>]
  ```
  > 

## HTMLInputElement

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,125:::type HTMLInputElement
```


#### mooncakes-io-method-mark-Methods
- #### value
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,128:::fn <a href="Yoorkin/rabbit-tea/dom#HTMLInputElement">HTMLInputElement</a>::value(self : <a href="Yoorkin/rabbit-tea/dom#HTMLInputElement">HTMLInputElement</a>) -> String
  ```
  > 

## HTMLSelectElement

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,131:::type HTMLSelectElement
```


#### mooncakes-io-method-mark-Methods
- #### value
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_element.mbt,134:::fn <a href="Yoorkin/rabbit-tea/dom#HTMLSelectElement">HTMLSelectElement</a>::value(self : <a href="Yoorkin/rabbit-tea/dom#HTMLSelectElement">HTMLSelectElement</a>) -> String
  ```
  > 

## ImageBitmapRenderingContext

```moonbit
:::source,Yoorkin/rabbit-tea/dom/canvas.mbt,52:::type ImageBitmapRenderingContext
```


## ImageData

```moonbit
:::source,Yoorkin/rabbit-tea/dom/canvas.mbt,599:::type ImageData
```


#### mooncakes-io-method-mark-Methods
- #### get\_color\_space
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,628:::fn <a href="Yoorkin/rabbit-tea/dom#ImageData">ImageData</a>::get_color_space(self : <a href="Yoorkin/rabbit-tea/dom#ImageData">ImageData</a>) -> String
  ```
  > 
- #### get\_data
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,623:::fn <a href="Yoorkin/rabbit-tea/dom#ImageData">ImageData</a>::get_data(self : <a href="Yoorkin/rabbit-tea/dom#ImageData">ImageData</a>) -> <a href="Yoorkin/rabbit-tea/dom#Uint8ClampedArray">Uint8ClampedArray</a>
  ```
  > 
- #### get\_height
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,620:::fn <a href="Yoorkin/rabbit-tea/dom#ImageData">ImageData</a>::get_height(self : <a href="Yoorkin/rabbit-tea/dom#ImageData">ImageData</a>) -> Int
  ```
  > 
- #### get\_width
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,617:::fn <a href="Yoorkin/rabbit-tea/dom#ImageData">ImageData</a>::get_width(self : <a href="Yoorkin/rabbit-tea/dom#ImageData">ImageData</a>) -> Int
  ```
  > 
- #### new
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,602:::fn <a href="Yoorkin/rabbit-tea/dom#ImageData">ImageData</a>::new(sw : Int, sh : Int, settings : <a href="rami3l/js-ffi/js#Optional">@rami3l/js-ffi/js.Optional</a>[<a href="Yoorkin/rabbit-tea/dom#ImageDataSettings">ImageDataSettings</a>]) -> <a href="Yoorkin/rabbit-tea/dom#ImageData">ImageData</a>
  ```
  > 
- #### new\_with\_data
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,609:::fn <a href="Yoorkin/rabbit-tea/dom#ImageData">ImageData</a>::new_with_data(data : <a href="Yoorkin/rabbit-tea/dom#Uint8ClampedArray">Uint8ClampedArray</a>, sw : Int, sh : Int, settings~ : <a href="rami3l/js-ffi/js#Optional">@rami3l/js-ffi/js.Optional</a>[<a href="Yoorkin/rabbit-tea/dom#ImageDataSettings">ImageDataSettings</a>] = ..) -> <a href="Yoorkin/rabbit-tea/dom#ImageData">ImageData</a>
  ```
  > 

## ImageDataSettings

```moonbit
:::source,Yoorkin/rabbit-tea/dom/canvas.mbt,588:::type ImageDataSettings
```


#### mooncakes-io-method-mark-Methods
- #### new
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,594:::fn <a href="Yoorkin/rabbit-tea/dom#ImageDataSettings">ImageDataSettings</a>::new(color_space : String) -> <a href="Yoorkin/rabbit-tea/dom#ImageDataSettings">ImageDataSettings</a>
  ```
  > 

## InputEvent

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,85:::type InputEvent
```


#### mooncakes-io-method-mark-Methods
- #### data
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,88:::fn <a href="Yoorkin/rabbit-tea/dom#InputEvent">InputEvent</a>::data(self : <a href="Yoorkin/rabbit-tea/dom#InputEvent">InputEvent</a>) -> String
  ```
  > 
- #### input\_type
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,94:::fn <a href="Yoorkin/rabbit-tea/dom#InputEvent">InputEvent</a>::input_type(self : <a href="Yoorkin/rabbit-tea/dom#InputEvent">InputEvent</a>) -> String
  ```
  > 
- #### is\_composing
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,91:::fn <a href="Yoorkin/rabbit-tea/dom#InputEvent">InputEvent</a>::is_composing(self : <a href="Yoorkin/rabbit-tea/dom#InputEvent">InputEvent</a>) -> Bool
  ```
  > 

## KeyboardEvent

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,103:::type KeyboardEvent
```


#### mooncakes-io-method-mark-Methods
- #### alt\_key
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,112:::fn <a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>::alt_key(self : <a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>) -> Bool
  ```
  > 
- #### code
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,109:::fn <a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>::code(self : <a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>) -> String
  ```
  > 
- #### ctrl\_key
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,115:::fn <a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>::ctrl_key(self : <a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>) -> Bool
  ```
  > 
- #### is\_composing
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,124:::fn <a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>::is_composing(self : <a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>) -> Bool
  ```
  > 
- #### key
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,106:::fn <a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>::key(self : <a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>) -> String
  ```
  > 
- #### location
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,130:::fn <a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>::location(self : <a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>) -> Int
  ```
  > 
- #### meta\_key
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,121:::fn <a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>::meta_key(self : <a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>) -> Bool
  ```
  > 
- #### repeat
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,127:::fn <a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>::repeat(self : <a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>) -> Bool
  ```
  > 
- #### shift\_key
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,118:::fn <a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>::shift_key(self : <a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>) -> Bool
  ```
  > 

## MouseEvent

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,64:::type MouseEvent
```


#### mooncakes-io-method-mark-Methods
- #### client\_x
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,73:::fn <a href="Yoorkin/rabbit-tea/dom#MouseEvent">MouseEvent</a>::client_x(self : <a href="Yoorkin/rabbit-tea/dom#MouseEvent">MouseEvent</a>) -> Int
  ```
  > 
- #### client\_y
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,76:::fn <a href="Yoorkin/rabbit-tea/dom#MouseEvent">MouseEvent</a>::client_y(self : <a href="Yoorkin/rabbit-tea/dom#MouseEvent">MouseEvent</a>) -> Int
  ```
  > 
- #### offset\_x
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,79:::fn <a href="Yoorkin/rabbit-tea/dom#MouseEvent">MouseEvent</a>::offset_x(self : <a href="Yoorkin/rabbit-tea/dom#MouseEvent">MouseEvent</a>) -> Int
  ```
  > 
- #### offset\_y
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,82:::fn <a href="Yoorkin/rabbit-tea/dom#MouseEvent">MouseEvent</a>::offset_y(self : <a href="Yoorkin/rabbit-tea/dom#MouseEvent">MouseEvent</a>) -> Int
  ```
  > 
- #### screen\_x
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,67:::fn <a href="Yoorkin/rabbit-tea/dom#MouseEvent">MouseEvent</a>::screen_x(self : <a href="Yoorkin/rabbit-tea/dom#MouseEvent">MouseEvent</a>) -> Int
  ```
  > 
- #### screen\_y
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,70:::fn <a href="Yoorkin/rabbit-tea/dom#MouseEvent">MouseEvent</a>::screen_y(self : <a href="Yoorkin/rabbit-tea/dom#MouseEvent">MouseEvent</a>) -> Int
  ```
  > 

## Node

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,2:::type Node
```


#### mooncakes-io-method-mark-Methods
- #### append\_child
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,30:::fn <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>::append_child(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>, child : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> Unit
  ```
  > 
- #### count\_child
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,52:::fn <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>::count_child(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> Int
  ```
  > 
- #### first\_child
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,15:::fn <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>::first_child(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>
  ```
  > 
- #### insert\_before
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,39:::fn <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>::insert_before(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>, value : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>, before : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> Unit
  ```
  > 
- #### last\_child
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,18:::fn <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>::last_child(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>
  ```
  > 
- #### next\_sibling
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,21:::fn <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>::next_sibling(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>
  ```
  > 
- #### node\_name
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,9:::fn <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>::node_name(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> String
  ```
  > 
- #### node\_type
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,6:::fn <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>::node_type(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> Int
  ```
  > 
- #### node\_value
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,12:::fn <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>::node_value(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> String
  ```
  > 
- #### nth\_child
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,44:::fn <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>::nth_child(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>, index : Int) -> <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>
  ```
  >   
- #### parent\_node
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,27:::fn <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>::parent_node(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>
  ```
  > 
- #### previous\_sibling
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,24:::fn <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>::previous_sibling(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>
  ```
  > 
- #### remove\_child
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,33:::fn <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>::remove_child(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>, child : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> Unit
  ```
  > 
- #### replace\_child
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,36:::fn <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>::replace_child(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>, new : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>, old : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> Unit
  ```
  > 
- #### to\_document
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_cast.mbt,3:::fn <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>::to_document(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#Document">Document</a>]
  ```
  > 
- #### to\_document\_fragment
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_cast.mbt,7:::fn <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>::to_document_fragment(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#DocumentFragment">DocumentFragment</a>]
  ```
  > 
- #### to\_element
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_cast.mbt,13:::fn <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>::to_element(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#Element">Element</a>]
  ```
  > 
- #### to\_event\_target
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_cast.mbt,21:::fn <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>::to_event_target(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="Yoorkin/rabbit-tea/dom#EventTarget">EventTarget</a>
  ```
  > 
- #### to\_text
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_cast.mbt,17:::fn <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>::to_text(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#Text">Text</a>]
  ```
  > 

## Path2D

```moonbit
:::source,Yoorkin/rabbit-tea/dom/canvas.mbt,633:::type Path2D
```


#### mooncakes-io-method-mark-Methods
- #### add\_path
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,641:::fn <a href="Yoorkin/rabbit-tea/dom#Path2D">Path2D</a>::add_path(self : <a href="Yoorkin/rabbit-tea/dom#Path2D">Path2D</a>, path : <a href="Yoorkin/rabbit-tea/dom#Path2D">Path2D</a>, transform~ : <a href="rami3l/js-ffi/js#Optional">@rami3l/js-ffi/js.Optional</a>[<a href="Yoorkin/rabbit-tea/dom#DOMMatrix2DInit">DOMMatrix2DInit</a>] = ..) -> Unit
  ```
  > 
- #### new
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/canvas.mbt,636:::fn <a href="Yoorkin/rabbit-tea/dom#Path2D">Path2D</a>::new(path~ : <a href="rami3l/js-ffi/js#Optional">@rami3l/js-ffi/js.Optional</a>[<a href="rami3l/js-ffi/js#Union2">@rami3l/js-ffi/js.Union2</a>[<a href="Yoorkin/rabbit-tea/dom#Path2D">Path2D</a>, String]] = ..) -> <a href="Yoorkin/rabbit-tea/dom#Path2D">Path2D</a>
  ```
  > 

## Text

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_text.mbt,2:::type Text
```


#### mooncakes-io-method-mark-Methods
- #### to\_node
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_cast.mbt,34:::fn <a href="Yoorkin/rabbit-tea/dom#Text">Text</a>::to_node(self : <a href="Yoorkin/rabbit-tea/dom#Text">Text</a>) -> <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>
  ```
  > 

## UIEvent

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,34:::type UIEvent
```


#### mooncakes-io-method-mark-Methods
- #### to\_event
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,37:::fn <a href="Yoorkin/rabbit-tea/dom#UIEvent">UIEvent</a>::to_event(self : <a href="Yoorkin/rabbit-tea/dom#UIEvent">UIEvent</a>) -> <a href="Yoorkin/rabbit-tea/dom#Event">Event</a>
  ```
  > 
- #### to\_focus\_event
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,52:::fn <a href="Yoorkin/rabbit-tea/dom#UIEvent">UIEvent</a>::to_focus_event(self : <a href="Yoorkin/rabbit-tea/dom#UIEvent">UIEvent</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#MouseEvent">MouseEvent</a>]
  ```
  > 
- #### to\_input\_event
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,46:::fn <a href="Yoorkin/rabbit-tea/dom#UIEvent">UIEvent</a>::to_input_event(self : <a href="Yoorkin/rabbit-tea/dom#UIEvent">UIEvent</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#MouseEvent">MouseEvent</a>]
  ```
  > 
- #### to\_keyboard\_event
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,58:::fn <a href="Yoorkin/rabbit-tea/dom#UIEvent">UIEvent</a>::to_keyboard_event(self : <a href="Yoorkin/rabbit-tea/dom#UIEvent">UIEvent</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#KeyboardEvent">KeyboardEvent</a>]
  ```
  > 
- #### to\_mouse\_event
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,40:::fn <a href="Yoorkin/rabbit-tea/dom#UIEvent">UIEvent</a>::to_mouse_event(self : <a href="Yoorkin/rabbit-tea/dom#UIEvent">UIEvent</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#MouseEvent">MouseEvent</a>]
  ```
  > 

## Uint8ClampedArray

```moonbit
:::source,Yoorkin/rabbit-tea/dom/canvas.mbt,648:::type Uint8ClampedArray
```


## WebGL2RenderingContext

```moonbit
:::source,Yoorkin/rabbit-tea/dom/canvas.mbt,58:::type WebGL2RenderingContext
```


## WebGLRenderingContext

```moonbit
:::source,Yoorkin/rabbit-tea/dom/canvas.mbt,55:::type WebGLRenderingContext
```


## Window

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,2:::type Window
```


#### mooncakes-io-method-mark-Methods
- #### alert
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,58:::fn <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>::alert(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>, msg : String) -> Unit
  ```
  > 
- #### confirm
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,61:::fn <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>::confirm(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>, msg : String) -> Bool
  ```
  > 
- #### current\_url
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,41:::fn <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>::current_url(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>) -> String
  ```
  > 
- #### history\_go\_back
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,21:::fn <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>::history_go_back(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>) -> Unit
  ```
  > 
- #### history\_go\_forward
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,25:::fn <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>::history_go_forward(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>) -> Unit
  ```
  > 
- #### load\_url
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,29:::fn <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>::load_url(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>, url : String) -> Unit
  ```
  > 
- #### push\_url
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,37:::fn <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>::push_url(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>, url : String) -> Unit
  ```
  > 
- #### reload\_url
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,33:::fn <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>::reload_url(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>) -> Unit
  ```
  > 
- #### replace\_url
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,45:::fn <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>::replace_url(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>, url : String) -> Unit
  ```
  > 
- #### request\_animination\_frame
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,49:::fn <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>::request_animination_frame(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>, f : () -> Unit) -> Unit
  ```
  > 
- #### scroll\_by
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,9:::fn <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>::scroll_by(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>, x : Int, y : Int) -> Unit
  ```
  > 
- #### scroll\_to
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,5:::fn <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>::scroll_to(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>, x : Int, y : Int) -> Unit
  ```
  > 
- #### scroll\_to\_bottom
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,17:::fn <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>::scroll_to_bottom(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>) -> Unit
  ```
  > 
- #### scroll\_to\_top
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,13:::fn <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>::scroll_to_top(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>) -> Unit
  ```
  > 
- #### to\_event\_target
  ```moonbit
  :::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,55:::fn <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>::to_event_target(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>) -> <a href="Yoorkin/rabbit-tea/dom#EventTarget">EventTarget</a>
  ```
  > 

## Listener

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_event_target.mbt,37:::type Listener = (<a href="Yoorkin/rabbit-tea/dom#Event">Event</a>) -> Unit
```


## PredefinedColorSpace

```moonbit
:::source,Yoorkin/rabbit-tea/dom/canvas.mbt,591:::type PredefinedColorSpace = String
```
 Possible values are "srgb" and "display-p3".

## DOM\_KEY\_LOCATION\_LEFT

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,136:::let DOM_KEY_LOCATION_LEFT : Int
```


## DOM\_KEY\_LOCATION\_NUMPAD

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,142:::let DOM_KEY_LOCATION_NUMPAD : Int
```


## DOM\_KEY\_LOCATION\_RIGHT

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,139:::let DOM_KEY_LOCATION_RIGHT : Int
```


## DOM\_KEY\_LOCATION\_STANDARD

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_event.mbt,133:::let DOM_KEY_LOCATION_STANDARD : Int
```


## add\_event\_listener

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_event_target.mbt,17:::fn add_event_listener(self : <a href="Yoorkin/rabbit-tea/dom#EventTarget">EventTarget</a>, type_ : String, callback : (<a href="Yoorkin/rabbit-tea/dom#Event">Event</a>) -> Unit) -> Unit
```


## append\_child

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,30:::fn append_child(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>, child : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> Unit
```


## count\_child

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,52:::fn count_child(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> Int
```


## create\_document\_fragment

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_document.mbt,20:::fn create_document_fragment(self : <a href="Yoorkin/rabbit-tea/dom#Document">Document</a>) -> <a href="Yoorkin/rabbit-tea/dom#DocumentFragment">DocumentFragment</a>
```


## create\_element

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_document.mbt,14:::fn create_element(self : <a href="Yoorkin/rabbit-tea/dom#Document">Document</a>, tag : String) -> <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>
```


## create\_text\_node

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_document.mbt,17:::fn create_text_node(self : <a href="Yoorkin/rabbit-tea/dom#Document">Document</a>, str : String) -> <a href="Yoorkin/rabbit-tea/dom#Element">Element</a>
```


## current\_url

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,41:::fn current_url(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>) -> String
```


## dispatch\_event

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_event_target.mbt,33:::fn dispatch_event(self : <a href="Yoorkin/rabbit-tea/dom#EventTarget">EventTarget</a>, event : <a href="Yoorkin/rabbit-tea/dom#Event">Event</a>) -> Unit
```


## document

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_document.mbt,5:::fn document() -> <a href="Yoorkin/rabbit-tea/dom#Document">Document</a>
```


## first\_child

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,15:::fn first_child(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>
```


## get\_element\_by\_id

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_document.mbt,8:::fn get_element_by_id(self : <a href="Yoorkin/rabbit-tea/dom#Document">Document</a>, id : String) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#Element">Element</a>]
```


## history\_go\_back

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,21:::fn history_go_back(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>) -> Unit
```


## history\_go\_forward

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,25:::fn history_go_forward(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>) -> Unit
```


## insert\_before

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,39:::fn insert_before(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>, value : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>, before : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> Unit
```


## last\_child

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,18:::fn last_child(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>
```


## load\_url

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,29:::fn load_url(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>, url : String) -> Unit
```


## next\_sibling

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,21:::fn next_sibling(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>
```


## node\_name

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,9:::fn node_name(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> String
```


## node\_type

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,6:::fn node_type(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> Int
```


## node\_value

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,12:::fn node_value(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> String
```


## nth\_child

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,44:::fn nth_child(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>, index : Int) -> <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>
```
  

## parent\_node

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,27:::fn parent_node(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>
```


## previous\_sibling

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,24:::fn previous_sibling(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>
```


## push\_url

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,37:::fn push_url(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>, url : String) -> Unit
```


## reload\_url

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,33:::fn reload_url(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>) -> Unit
```


## remove\_child

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,33:::fn remove_child(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>, child : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> Unit
```


## remove\_event\_listener

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_event_target.mbt,25:::fn remove_event_listener(self : <a href="Yoorkin/rabbit-tea/dom#EventTarget">EventTarget</a>, type_ : String, callback : (<a href="Yoorkin/rabbit-tea/dom#Event">Event</a>) -> Unit) -> Unit
```


## replace\_child

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_node.mbt,36:::fn replace_child(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>, new : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>, old : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> Unit
```


## replace\_url

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,45:::fn replace_url(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>, url : String) -> Unit
```


## request\_animination\_frame

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,49:::fn request_animination_frame(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>, f : () -> Unit) -> Unit
```


## scroll\_by

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,9:::fn scroll_by(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>, x : Int, y : Int) -> Unit
```


## scroll\_to

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,5:::fn scroll_to(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>, x : Int, y : Int) -> Unit
```


## scroll\_to\_bottom

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,17:::fn scroll_to_bottom(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>) -> Unit
```


## scroll\_to\_top

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,13:::fn scroll_to_top(self : <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>) -> Unit
```


## to\_document

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_cast.mbt,3:::fn to_document(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#Document">Document</a>]
```


## to\_document\_fragment

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_cast.mbt,7:::fn to_document_fragment(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#DocumentFragment">DocumentFragment</a>]
```


## to\_element

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_cast.mbt,13:::fn to_element(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#Element">Element</a>]
```


## to\_event\_target

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_cast.mbt,21:::fn to_event_target(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="Yoorkin/rabbit-tea/dom#EventTarget">EventTarget</a>
```


## to\_node

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_event_target.mbt,13:::fn to_node(self : <a href="Yoorkin/rabbit-tea/dom#EventTarget">EventTarget</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#Node">Node</a>]
```


## to\_text

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_cast.mbt,17:::fn to_text(self : <a href="Yoorkin/rabbit-tea/dom#Node">Node</a>) -> <a href="rami3l/js-ffi/js#Nullable">@rami3l/js-ffi/js.Nullable</a>[<a href="Yoorkin/rabbit-tea/dom#Text">Text</a>]
```


## window

```moonbit
:::source,Yoorkin/rabbit-tea/dom/dom_window.mbt,52:::fn window() -> <a href="Yoorkin/rabbit-tea/dom#Window">Window</a>
```

