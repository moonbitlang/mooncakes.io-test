# Navigation

This package provides a collection of functions to navigate, scroll the viewport, 
and manage the URL history in a web application. Each function returns a `Cmd[Msg]` 
type, representing an action that has yet to be executed.

For more details on how commands work, see the documentation in the 
`rabbit-tea/cmd` package.




---
# Documentation
|Value|description|
|---|---|
|[back](#back)| Create a command to go back in history. |
|[forward](#forward)| Create a command to go forward in history. |
|[load](#load)| Create a command to load a new URL. |
|[push\_url](#push_url)| Create a command to push a new URL to history but not trigger a page load.|
|[reload](#reload)| Create a command to reload the current url.|
|[replace\_url](#replace_url)| Create a command to change the URL but not trigger a page load.|
|[scroll\_by\_pos](#scroll_by_pos)| Create a command to scroll the window by a specific amount.|
|[scroll\_to](#scroll_to)| Create a command to scroll the window to a specific element.|
|[scroll\_to\_bottom](#scroll_to_bottom)| Create a command to scroll the window to the bottom.|
|[scroll\_to\_pos](#scroll_to_pos)| Create a command to scroll the window to a specific position.|
|[scroll\_to\_top](#scroll_to_top)| Create a command to scroll the window to the top.|

## back

```moonbit
:::source,Yoorkin/rabbit-tea/nav/navigation.mbt,3:::fn back[M]() -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 Create a command to go back in history.
This will cause the page to reload.

## forward

```moonbit
:::source,Yoorkin/rabbit-tea/nav/navigation.mbt,9:::fn forward[M]() -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 Create a command to go forward in history.
This will cause the page to reload.

## load

```moonbit
:::source,Yoorkin/rabbit-tea/nav/navigation.mbt,15:::fn load[M](url : String) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 Create a command to load a new URL.
This will cause the page to reload.

## push\_url

```moonbit
:::source,Yoorkin/rabbit-tea/nav/navigation.mbt,27:::fn push_url[M](url : String) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 Create a command to push a new URL to history but not trigger a page load.
 
 This will trigger the `url_changed` message.

## reload

```moonbit
:::source,Yoorkin/rabbit-tea/nav/navigation.mbt,20:::fn reload[M]() -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 Create a command to reload the current url.

## replace\_url

```moonbit
:::source,Yoorkin/rabbit-tea/nav/navigation.mbt,38:::fn replace_url[M](url : String) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 Create a command to change the URL but not trigger a page load.
 
 This will trigger the `url_changed` message.

## scroll\_by\_pos

```moonbit
:::source,Yoorkin/rabbit-tea/nav/scroll.mbt,7:::fn scroll_by_pos[M](x : Int, y : Int) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 Create a command to scroll the window by a specific amount.

## scroll\_to

```moonbit
:::source,Yoorkin/rabbit-tea/nav/scroll.mbt,13:::fn scroll_to[M](element : String) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 Create a command to scroll the window to a specific element.
The element is specified by its id.

## scroll\_to\_bottom

```moonbit
:::source,Yoorkin/rabbit-tea/nav/scroll.mbt,28:::fn scroll_to_bottom[M]() -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 Create a command to scroll the window to the bottom.

## scroll\_to\_pos

```moonbit
:::source,Yoorkin/rabbit-tea/nav/scroll.mbt,2:::fn scroll_to_pos[M](x : Int, y : Int) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 Create a command to scroll the window to a specific position.

## scroll\_to\_top

```moonbit
:::source,Yoorkin/rabbit-tea/nav/scroll.mbt,23:::fn scroll_to_top[M]() -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 Create a command to scroll the window to the top.
