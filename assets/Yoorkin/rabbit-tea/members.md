# Documentation
|Type|description|
|---|---|
|[Cmd](#Cmd)| The command type, represents a task that can be executed.|
|[Command](#Command)| The command type, represents a task that can be executed.|

|Value|description|
|---|---|
|[application](#application)| Start the application with initial URL. |
|[attempt](#attempt)| Create a command that runs an async function and handles errors.|
|[batch](#batch)| Create a command that runs multiple commands.|
|[none](#none)| Create a command that does nothing.|
|[perform](#perform)| Create a command that runs an async function.|
|[startup](#startup)| Start the application.|
|[task](#task)| Create a command that trigger another update for the given message.|

## Cmd

```moonbit
:::source,Yoorkin/rabbit-tea/top.mbt,2:::type Cmd[M] = <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 The command type, represents a task that can be executed.
 
 You can define your own command to interoperate Rabbit-Tea with the outside JS world.
 
 Before implementing your own command, check the existing commands in the `nav` and `http` packages.
 
 #### Example
 
 ```
 fn delay[M](msg : M, ms : Int) -> Cmd[M] {
   Cmd(fn(events){
     set_timeout(fn(){ events.trigger_update(msg) }, ms)
   })
 } 
 
 extern "js" fn set_timeout(f : () -> Unit, ms : Int) = "(f,ms) => setTimeout(f, ms)"
 ```

## Command

```moonbit
:::source,Yoorkin/rabbit-tea/top.mbt,2:::type Command[M] = <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 The command type, represents a task that can be executed.
 
 You can define your own command to interoperate Rabbit-Tea with the outside JS world.
 
 Before implementing your own command, check the existing commands in the `nav` and `http` packages.
 
 #### Example
 
 ```
 fn delay[M](msg : M, ms : Int) -> Cmd[M] {
   Cmd(fn(events){
     set_timeout(fn(){ events.trigger_update(msg) }, ms)
   })
 } 
 
 extern "js" fn set_timeout(f : () -> Unit, ms : Int) = "(f,ms) => setTimeout(f, ms)"
 ```

## application

```moonbit
:::source,Yoorkin/rabbit-tea/top.mbt,47:::fn application[Model, Msg](initialize~ : (<a href="Yoorkin/rabbit-tea/url#Url">@Yoorkin/rabbit-tea/url.Url</a>) -> (<a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[Msg], Model), update~ : (Msg, Model) -> (<a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[Msg], Model), view~ : (Model) -> <a href="Yoorkin/rabbit-tea/html#T">@Yoorkin/rabbit-tea/html.T</a>[Msg], url_changed? : (<a href="Yoorkin/rabbit-tea/url#Url">@Yoorkin/rabbit-tea/url.Url</a>) -> Msg, url_request? : (<a href="Yoorkin/rabbit-tea/url#UrlRequest">@Yoorkin/rabbit-tea/url.UrlRequest</a>) -> Msg, mount~ : String = ..) -> Unit
```
 Start the application with initial URL.
 
 - `url_changed` is a message that will be passed when the URL is changed by the navigation API in the `@browser` package.
 - `url_request` is a message that will be passed when an `<a>` tag is clicked.
 - `initialize` will be called when the application is started.
 

## attempt

```moonbit
:::source,Yoorkin/rabbit-tea/command.mbt,97:::fn attempt[A, E : <a href="moonbitlang/core/error#Error">Error</a>, M](msg : (<a href="moonbitlang/core/result#Result">Result</a>[A, E]) -> M, f : () -> A!E) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 Create a command that runs an async function and handles errors.
 
 This is similar to `perform`, but it converts the returned value
or thrown error into a `Result`.

## batch

```moonbit
:::source,Yoorkin/rabbit-tea/command.mbt,76:::fn batch[M](xs : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]]) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 Create a command that runs multiple commands.

## none

```moonbit
:::source,Yoorkin/rabbit-tea/command.mbt,71:::fn none[M]() -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 Create a command that does nothing.

## perform

```moonbit
:::source,Yoorkin/rabbit-tea/command.mbt,89:::fn perform[A, M](msg : (A) -> M, f : () -> A) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 Create a command that runs an async function.
 
 The async function `f` will be called, and the result will be wrapped in a
message `msg`, then trigger another update with this message.

## startup

```moonbit
:::source,Yoorkin/rabbit-tea/top.mbt,18:::fn startup[Model, Message](model~ : Model, update~ : (Message, Model) -> (<a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[Message], Model), view~ : (Model) -> <a href="Yoorkin/rabbit-tea/html#T">@Yoorkin/rabbit-tea/html.T</a>[Message], mount~ : String = ..) -> Unit
```
 Start the application.
 
 - `model` is the state of your application.
 - `view` is a way to turn your model into HTML.
 - `update` a way to update your state based on messages.
 
 These three are the core of the TEA. Rabbit-TEA is highly unstable at this time,
but it follows the same pattern as Elm. You can visit https://guide.elm-lang.org/
to get more intuition\!
 
 To start the application with router, you can use the `application` function.

## task

```moonbit
:::source,Yoorkin/rabbit-tea/command.mbt,81:::fn task[M](message : M) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">@Yoorkin/rabbit-tea/cmd.Cmd</a>[M]
```
 Create a command that trigger another update for the given message.
