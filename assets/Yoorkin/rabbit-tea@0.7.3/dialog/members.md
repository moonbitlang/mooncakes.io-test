# Documentation
|Value|description|
|---|---|
|[close](#close)| Create a command to close a dialog.|
|[request\_close](#request_close)| Create a command to request closing a dialog.|
|[show](#show)| Create a command to show a dialog.|

## close

```moonbit
:::source,Yoorkin/rabbit-tea/dialog/dialog.mbt,27:::fn close[M](id : String, return_value? : String) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 Create a command to close a dialog.
 
 The `return_value` argument is the value that will be filled in the `close` message.

## request\_close

```moonbit
:::source,Yoorkin/rabbit-tea/dialog/dialog.mbt,49:::fn request_close[M](id : String, return_value? : String) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 Create a command to request closing a dialog.
 
 This command will not close the dialog immediately; it will trigger the
`cancel` message.
 
 The `return_value` argument is the value that will be filled in the `close` message.

## show

```moonbit
:::source,Yoorkin/rabbit-tea/dialog/dialog.mbt,4:::fn show[M](id : String, modal~ : Bool = ..) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 Create a command to show a dialog.
 
 The `modal` argument determines whether the dialog is modal or not.
