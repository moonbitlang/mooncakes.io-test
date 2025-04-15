
# Html 

This package provides the helper functions to build Html.

Here are two design choices:

- Guide Users with Type Definitions

  This package defines specific types for arguments instead of relying on a potentially confusing `String` type. These types serve as documentation, helping users understand how to correctly provide arguments.

- Seamless HTML EDSL

  Instead of relying on a precompiler to process JSX-like syntax, this EDSL allows users to leverage the full power of Moonbit's syntax and toolchain. 
    
  You can embed expressions in views without needing escape characters like `property={expression}` or `:property=expression`. For cases where the property name matches the variable name, you can use the convenient name-punning syntax, such as `property?` or `property~`.

  In this early stage, we need to focus on improving the functionality of Rabbit-TEA. Language extensions like JSX may be considered after the 1.0 release.
  
# Using the Html EDSL

We are trying to define wrapper functions for each HTML element. They all follow a form like this:

```mbt
pub fn div[M](
  style~ : Array[String] = [],
  id? : String,
  class? : String,
  click? : M,
  childrens : Array[Html[M]]
) -> Html[M] 
```

## The `text` element

To represent text in HTML, use the `text` function.

```mbt
let html = p([text("hello world")])
```

## The special `nothing` element

There is a special `nothing` element that does not represent an actual HTML element, it simply represents "nothing". This is particularly useful for handling multiple `Option` types in your model:

```mbt
fn bar(path : Path, tag : Option[Tag]){
  let path = foo(path)
  let tag = match tag {
    None => []
    Some(x) => [view(x)] // Yuck!
  }
  div([path] + tag) // Don't do this
}
```

```mbt
fn bar(path : Path, tag : Option[Tag]){
  let path = foo(path)
  let tag = match tag {
    None => nothing()
    Some(x) => view(x)  
  }
  div([path, tag]) // Use @html.nothing
}
```

## Advanced Usage

The wrapper functions and properties provided here may not cover all possible use cases. If you encounter missing functionality, feel free to file an issue or use the `node()` function as a workaround. The `node()` function allows you to manually specify the tag name, attributes, and children for your HTML element, offering flexibility for advanced or uncommon scenarios.

```mbt
let html = node(
  "div",
  [style("key","value"), property("id","key")],
  [child1, child2],
) 
```

Contributions to help us finish the missing wrappers or arguments are also welcome.




  








---
# Documentation
|Type|description|
|---|---|
|[Attribute](#Attribute)||
|[AutoComplete](#AutoComplete)||
|[InputType](#InputType)||
|[Mouse](#Mouse)||
|[Pos](#Pos)||
|[Scope](#Scope)||
|[T](#T)||
|[Target](#Target)||
|[Html](#Html)||

|Value|description|
|---|---|
|[a](#a)| Create \`a\` element.|
|[attribute](#attribute)||
|[b](#b)||
|[blockquote](#blockquote)||
|[br](#br)||
|[button](#button)||
|[caption](#caption)||
|[code](#code)||
|[col](#col)||
|[colgroup](#colgroup)||
|[dd](#dd)||
|[dialog](#dialog)| Dialog element. |
|[div](#div)||
|[dl](#dl)||
|[dt](#dt)||
|[em](#em)||
|[external](#external)||
|[form](#form)||
|[h1](#h1)||
|[h2](#h2)||
|[h3](#h3)||
|[h4](#h4)||
|[h5](#h5)||
|[h6](#h6)||
|[hr](#hr)||
|[href](#href)||
|[i](#i)||
|[iframe](#iframe)||
|[img](#img)||
|[input](#input)||
|[label](#label)||
|[li](#li)||
|[map](#map)| Convert msg type of Html.|
|[node](#node)| |
|[nothing](#nothing)| Represents an empty element|
|[ol](#ol)| Notice that the \`type\` attribute for \`ol\` is not important for the browser now.|
|[on\_change](#on_change)||
|[on\_click](#on_click)||
|[on\_double\_click](#on_double_click)||
|[on\_input](#on_input)||
|[on\_mouse\_down](#on_mouse_down)||
|[on\_mouse\_enter](#on_mouse_enter)||
|[on\_mouse\_leave](#on_mouse_leave)||
|[on\_mouse\_move](#on_mouse_move)||
|[on\_mouse\_out](#on_mouse_out)||
|[on\_mouse\_over](#on_mouse_over)||
|[on\_mouse\_up](#on_mouse_up)||
|[option](#option)||
|[p](#p)||
|[pre](#pre)||
|[property](#property)||
|[section](#section)||
|[select](#select)||
|[span](#span)||
|[strong](#strong)||
|[style](#style)| Specify an style|
|[sub](#sub)||
|[sup](#sup)||
|[table](#table)||
|[target](#target)||
|[tbody](#tbody)||
|[td](#td)||
|[text](#text)||
|[tfoot](#tfoot)||
|[th](#th)||
|[thead](#thead)||
|[to\_virtual\_dom](#to_virtual_dom)||
|[tr](#tr)||
|[u](#u)||
|[ul](#ul)||

## Attribute

```moonbit
:::source,Yoorkin/rabbit-tea/html/attributes.mbt,2:::type Attribute[Msg]
```


## AutoComplete

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,517:::pub(all) enum AutoComplete {
  On
  Off
}
```


## InputType

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,491:::pub(all) enum InputType {
  Button
  Checkbox
  Color
  Date
  DateTimeLocal
  Email
  File
  Hidden
  Image
  Month
  Number
  Password
  Radio
  Range
  Reset
  Search
  Submit
  Tel
  Text
  Time
  Url
  Week
}
```


## Mouse

```moonbit
:::source,Yoorkin/rabbit-tea/html/event.mbt,2:::type Mouse
```


#### mooncakes-io-method-mark-Methods
- #### client\_pos
  ```moonbit
  :::source,Yoorkin/rabbit-tea/html/event.mbt,21:::fn <a href="Yoorkin/rabbit-tea/html#Mouse">Mouse</a>::client_pos(self : <a href="Yoorkin/rabbit-tea/html#Mouse">Mouse</a>) -> <a href="Yoorkin/rabbit-tea/html#Pos">Pos</a>
  ```
  > 
- #### offset\_pos
  ```moonbit
  :::source,Yoorkin/rabbit-tea/html/event.mbt,16:::fn <a href="Yoorkin/rabbit-tea/html#Mouse">Mouse</a>::offset_pos(self : <a href="Yoorkin/rabbit-tea/html#Mouse">Mouse</a>) -> <a href="Yoorkin/rabbit-tea/html#Pos">Pos</a>
  ```
  > 
- #### screen\_pos
  ```moonbit
  :::source,Yoorkin/rabbit-tea/html/event.mbt,11:::fn <a href="Yoorkin/rabbit-tea/html#Mouse">Mouse</a>::screen_pos(self : <a href="Yoorkin/rabbit-tea/html#Mouse">Mouse</a>) -> <a href="Yoorkin/rabbit-tea/html#Pos">Pos</a>
  ```
  > 

## Pos

```moonbit
:::source,Yoorkin/rabbit-tea/html/event.mbt,5:::pub(all) struct Pos {
  x : Int
  y : Int
}
```


## Scope

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,853:::pub(all) enum Scope {
  Row
  Col
  RowGroup
  ColGroup
}
```


## T

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,2:::type T[Msg]
```


#### mooncakes-io-method-mark-Methods
- #### map
  ```moonbit
  :::source,Yoorkin/rabbit-tea/html/html.mbt,10:::fn <a href="Yoorkin/rabbit-tea/html#T">T</a>::map[A, B](self : <a href="Yoorkin/rabbit-tea/html#T">T</a>[A], f : (A) -> B) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[B]
  ```
  >  Convert msg type of Html.
  >  
  >  This is a expensive operation and should be used rarely.
- #### to\_virtual\_dom
  ```moonbit
  :::source,Yoorkin/rabbit-tea/html/html.mbt,15:::fn <a href="Yoorkin/rabbit-tea/html#T">T</a>::to_virtual_dom[Msg](self : <a href="Yoorkin/rabbit-tea/html#T">T</a>[Msg]) -> <a href="Yoorkin/rabbit-tea/internal/vdom#Node">@Yoorkin/rabbit-tea/internal/vdom.Node</a>[Msg]
  ```
  > 

## Target

```moonbit
:::source,Yoorkin/rabbit-tea/html/attributes.mbt,27:::pub(all) enum Target {
  Self
  Blank
}
```


## Html

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,5:::type Html[Msg] = <a href="Yoorkin/rabbit-tea/html#T">T</a>[Msg]
```


## a

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,218:::fn a[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, href~ : String, target~ : <a href="Yoorkin/rabbit-tea/html#Target">Target</a> = .., childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]], escape~ : Bool = ..) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```
 Create `a` element.
 
 The `escape` parameter is an optional boolean that determines whether the link
should be escaped. By default, it is set to `false`.
 
 When `escape` is set to `true`, clicking the escaped link will cause the browser
to immediately navigate to the `href` target, bypassing any interception logic.
As a result, the `UrlRequest` message will not be triggered.

## attribute

```moonbit
:::source,Yoorkin/rabbit-tea/html/attributes.mbt,10:::fn attribute[Msg](key : String, value : String) -> <a href="Yoorkin/rabbit-tea/html#Attribute">Attribute</a>[Msg]
```


## b

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,284:::fn b[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## blockquote

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,179:::fn blockquote[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## br

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,482:::fn br[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## button

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,57:::fn button[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, click? : M, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## caption

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,760:::fn caption[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## code

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,244:::fn code[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## col

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,790:::fn col[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, span? : Int, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## colgroup

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,805:::fn colgroup[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, span? : Int, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## dd

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,407:::fn dd[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## dialog

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,967:::fn dialog[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, open? : Bool, close? : (String) -> M, cancel? : M, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```
 Dialog element.
 
 Hint: You can use the `show` and `close` commands in the `@dialog` package
to manipulate the dialog.

 #### Attributes
 
 - `open`: indicates whether the dialog is open or closed by default.
 
 #### Messages
 
 - `close`: triggered when the dialog is closed.
   
   The string payload of the `close` message is the return value of the dialog.
    
 - `cancel`: triggered when the user instructs the browser that they wish to
   dismiss the current open dialog.
    
   It can be triggered when the user presses `esc` or uses the `request_close` command.
    
   If the `cancel` argument is provided, **the dialog will not close automatically**
   after this message is triggered. You can use the `@dialog.close` command
   to close it or `@cmd.none` to keep it open.
 
 #### Example
 
 ```
 typealias Model = String
 
 enum Msg {
   Open
   Closed(String)
   YesNo(Bool)
 }
 
 fn update(msg : Msg, model : Model) -> (Cmd[Msg], Model) {
   match msg {
     Open => (@dialog.show("confirm"), model)
     YesNo(answer) => (@dialog.close("confirm", return_value=answer.to_string()), model) 
     Closed(value) => (none(), value)
   }
 }
 
 fn view(model : Model) -> Html[Msg] {
   div([
     h1([text(model)]),
     button(click=Msg::Open, [text("open")]),
     dialog(id="confirm", close=Msg::Closed, [
       p([text("Are you sure?")]),
       button(click=YesNo(true), [text("Yes")]),
       button(click=YesNo(false), [text("No")]),
     ]),
   ])
 }
 ```
 

## div

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,134:::fn div[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, click? : M, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## dl

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,387:::fn dl[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## dt

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,397:::fn dt[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## em

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,254:::fn em[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## external

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,737:::fn external[Msg](node : <a href="Yoorkin/rabbit-tea/dom#Node">@Yoorkin/rabbit-tea/dom.Node</a>, attrs : <a href="moonbitlang/core/ref#Ref">Ref</a>[<a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#Attribute">Attribute</a>[Msg]]?], width~ : Int, height~ : Int) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[Msg]
```


## form

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,523:::fn form[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, action? : String, name? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## h1

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,72:::fn h1[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## h2

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,82:::fn h2[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## h3

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,92:::fn h3[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## h4

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,102:::fn h4[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## h5

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,112:::fn h5[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## h6

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,122:::fn h6[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## hr

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,159:::fn hr[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens~ : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]] = ..) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## href

```moonbit
:::source,Yoorkin/rabbit-tea/html/attributes.mbt,20:::fn href[Msg](value : String) -> <a href="Yoorkin/rabbit-tea/html#Attribute">Attribute</a>[Msg]
```


## i

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,274:::fn i[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## iframe

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,454:::fn iframe[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, src? : String, title? : String, width? : Int, height? : Int) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## img

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,419:::fn img[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, src? : String, alt? : String, title? : String, width? : Int, height? : Int, border? : Int, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## input

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,557:::fn input[M](input_type~ : <a href="Yoorkin/rabbit-tea/html#InputType">InputType</a> = .., name? : String, value? : String, checked? : Bool, read_only? : Bool, multiple? : Bool, accept? : String, placeholder? : String, auto_complete? : <a href="Yoorkin/rabbit-tea/html#AutoComplete">AutoComplete</a>, style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., max? : Int, min? : Int, step? : Int, maxlength? : Int, minlength? : Int, pattern? : String, size? : Int, width? : Int, height? : Int, id? : String, class? : String, childrens~ : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]] = .., change? : (String) -> M, input? : (String) -> M) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## label

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,542:::fn label[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, for_? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## li

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,368:::fn li[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., value? : Int, id? : String, class? : String, click? : M, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## map

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,10:::fn map[A, B](self : <a href="Yoorkin/rabbit-tea/html#T">T</a>[A], f : (A) -> B) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[B]
```
 Convert msg type of Html.
 
 This is a expensive operation and should be used rarely.

## node

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,21:::fn node[Msg](tag : String, attributes : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#Attribute">Attribute</a>[Msg]], childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[Msg]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[Msg]
```
 

## nothing

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,52:::fn nothing[M]() -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```
 Represents an empty element

## ol

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,347:::fn ol[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., reversed? : Bool, start? : Int, id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```
 Notice that the `type` attribute for `ol` is not important for the browser now.
If you want to change the type of the list, you should use the `list-style-type` property in CSS.

## on\_change

```moonbit
:::source,Yoorkin/rabbit-tea/html/event.mbt,75:::fn on_change[Msg](msg : (String) -> Msg) -> <a href="Yoorkin/rabbit-tea/html#Attribute">Attribute</a>[Msg]
```


## on\_click

```moonbit
:::source,Yoorkin/rabbit-tea/html/event.mbt,44:::fn on_click[Msg](msg : (<a href="Yoorkin/rabbit-tea/html#Mouse">Mouse</a>) -> Msg) -> <a href="Yoorkin/rabbit-tea/html#Attribute">Attribute</a>[Msg]
```


## on\_double\_click

```moonbit
:::source,Yoorkin/rabbit-tea/html/event.mbt,104:::fn on_double_click[Msg](msg : (<a href="Yoorkin/rabbit-tea/html#Mouse">Mouse</a>) -> Msg) -> <a href="Yoorkin/rabbit-tea/html#Attribute">Attribute</a>[Msg]
```


## on\_input

```moonbit
:::source,Yoorkin/rabbit-tea/html/event.mbt,49:::fn on_input[Msg](msg : (String) -> Msg) -> <a href="Yoorkin/rabbit-tea/html#Attribute">Attribute</a>[Msg]
```


## on\_mouse\_down

```moonbit
:::source,Yoorkin/rabbit-tea/html/event.mbt,109:::fn on_mouse_down[Msg](msg : (<a href="Yoorkin/rabbit-tea/html#Mouse">Mouse</a>) -> Msg) -> <a href="Yoorkin/rabbit-tea/html#Attribute">Attribute</a>[Msg]
```


## on\_mouse\_enter

```moonbit
:::source,Yoorkin/rabbit-tea/html/event.mbt,124:::fn on_mouse_enter[Msg](msg : (<a href="Yoorkin/rabbit-tea/html#Mouse">Mouse</a>) -> Msg) -> <a href="Yoorkin/rabbit-tea/html#Attribute">Attribute</a>[Msg]
```


## on\_mouse\_leave

```moonbit
:::source,Yoorkin/rabbit-tea/html/event.mbt,134:::fn on_mouse_leave[Msg](msg : (<a href="Yoorkin/rabbit-tea/html#Mouse">Mouse</a>) -> Msg) -> <a href="Yoorkin/rabbit-tea/html#Attribute">Attribute</a>[Msg]
```


## on\_mouse\_move

```moonbit
:::source,Yoorkin/rabbit-tea/html/event.mbt,119:::fn on_mouse_move[Msg](msg : (<a href="Yoorkin/rabbit-tea/html#Mouse">Mouse</a>) -> Msg) -> <a href="Yoorkin/rabbit-tea/html#Attribute">Attribute</a>[Msg]
```


## on\_mouse\_out

```moonbit
:::source,Yoorkin/rabbit-tea/html/event.mbt,139:::fn on_mouse_out[Msg](msg : (<a href="Yoorkin/rabbit-tea/html#Mouse">Mouse</a>) -> Msg) -> <a href="Yoorkin/rabbit-tea/html#Attribute">Attribute</a>[Msg]
```


## on\_mouse\_over

```moonbit
:::source,Yoorkin/rabbit-tea/html/event.mbt,129:::fn on_mouse_over[Msg](msg : (<a href="Yoorkin/rabbit-tea/html#Mouse">Mouse</a>) -> Msg) -> <a href="Yoorkin/rabbit-tea/html#Attribute">Attribute</a>[Msg]
```


## on\_mouse\_up

```moonbit
:::source,Yoorkin/rabbit-tea/html/event.mbt,114:::fn on_mouse_up[Msg](msg : (<a href="Yoorkin/rabbit-tea/html#Mouse">Mouse</a>) -> Msg) -> <a href="Yoorkin/rabbit-tea/html#Attribute">Attribute</a>[Msg]
```


## option

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,705:::fn option[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, disabled? : Bool, value? : String, selected~ : Bool = .., childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## p

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,149:::fn p[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## pre

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,169:::fn pre[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## property

```moonbit
:::source,Yoorkin/rabbit-tea/html/attributes.mbt,15:::fn property[M](key : String, value : <a href="Yoorkin/rabbit-tea/variant#Variant">@Yoorkin/rabbit-tea/variant.Variant</a>) -> <a href="Yoorkin/rabbit-tea/html#Attribute">Attribute</a>[M]
```


## section

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,189:::fn section[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## select

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,672:::fn select[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, disabled? : Bool, name? : String, change? : (String) -> M, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## span

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,201:::fn span[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## strong

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,264:::fn strong[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## style

```moonbit
:::source,Yoorkin/rabbit-tea/html/attributes.mbt,5:::fn style[Msg](key : String, value : String) -> <a href="Yoorkin/rabbit-tea/html#Attribute">Attribute</a>[Msg]
```
 Specify an style

## sub

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,304:::fn sub[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## sup

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,314:::fn sup[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## table

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,750:::fn table[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## target

```moonbit
:::source,Yoorkin/rabbit-tea/html/attributes.mbt,41:::fn target[Msg](value : <a href="Yoorkin/rabbit-tea/html#Target">Target</a>) -> <a href="Yoorkin/rabbit-tea/html#Attribute">Attribute</a>[Msg]
```


## tbody

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,780:::fn tbody[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## td

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,830:::fn td[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, colspan? : Int, rowspan? : Int, headers? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## text

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,324:::fn text[Msg](str : String) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[Msg]
```


## tfoot

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,902:::fn tfoot[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## th

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,861:::fn th[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, abbr? : String, colspan? : Int, rowspan? : Int, headers? : String, scope? : <a href="Yoorkin/rabbit-tea/html#Scope">Scope</a>, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## thead

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,770:::fn thead[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## to\_virtual\_dom

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,15:::fn to_virtual_dom[Msg](self : <a href="Yoorkin/rabbit-tea/html#T">T</a>[Msg]) -> <a href="Yoorkin/rabbit-tea/internal/vdom#Node">@Yoorkin/rabbit-tea/internal/vdom.Node</a>[Msg]
```


## tr

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,820:::fn tr[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## u

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,294:::fn u[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```


## ul

```moonbit
:::source,Yoorkin/rabbit-tea/html/html.mbt,331:::fn ul[M](style~ : <a href="moonbitlang/core/array#Array">Array</a>[String] = .., id? : String, class? : String, click? : M, childrens : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/html#T">T</a>[M]]) -> <a href="Yoorkin/rabbit-tea/html#T">T</a>[M]
```

