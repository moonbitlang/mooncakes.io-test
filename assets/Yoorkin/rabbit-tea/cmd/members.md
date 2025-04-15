# Cmd

The `Cmd[Msg]` type represent a task that has not yet been executed. 
It's a side effect managed by the runtime. The only way to run the command 
is return it from the `update` function:

```mbt
fn update(msg : Msg, model : Model) -> (Cmd[Msg], Model) {
  match msg {
    Msg::Click(id) => {
      // create a command to tell rabbit-tea scroll to the element with the given id
      let cmd = @nav.scroll_to(id) 
      let updated_model = {...}
      (cmd, updated_model)
    }
  }
}
```

The `scroll_to` function creates a `cmd` value that is returned with the 
`updated_model`. This means the scrolling action does not occur immediately. 
Instead, it will scroll to the element with the specified `id` after the 
`updated_model` has been rendered.

# Custom Command

You can encapsulate a command to interoperate Rabbit-Tea with the external 
JavaScript world.

The `Cmd` type acts as a wrapper for a callback function that will be executed 
by the runtime at a later point:

```mbt
type Cmd[M] (Events[M]) -> Unit
```

It accepts the `Events[M]` type as a parameter, which is a collection of events 
that can be triggered by your command. The most common usage is to trigger 
another update with a message:

```mbt
fn delay[M](msg : M, ms : Int) -> Cmd[M] {
  Cmd(fn(events){
    set_timeout(fn(){ events.trigger_update(msg) }, ms)
  })
} 

extern "js" fn set_timeout(f : () -> Unit, ms : Int) = "(f,ms) => setTimeout(f, ms)"
```

The `@http` package is also implemented in a similar manner.

For a complete example, refer to `src/example/custom_command`.

# Design Considerations

Why do we wrap tasks in `Cmd` instead of running them immediately? 
Here are some reasons:

1. **Tasks Need to Run After the New Model Is Rendered**

    - As shown in the example above, the `scroll_to` function must execute after 
    the new model is rendered. If it runs immediately, the scroll action may not 
    work as expected.

    - For instance, you might need to update the UI to a loading state before 
    fetching data. If the HTTP task is executed immediately, the app could lose 
    responsiveness.

    You might ask: "Why not make the `update` function asynchronous so tasks can 
    run asynchronously, allowing the UI to update between those tasks?" Here's 
    another reason:

2. **Encourages users follows the *Single Source of Truth* Principle**

    The *single source of truth* principle ensures that the new model and view 
    are computed based on a single, consistent model.

    If the `update` function were asynchronous, updates could overlap, leading 
    to situations where one update process occurs before another is completed. 
    This could result in inconsistent states or unexpected behavior.

    ```
               +---> update(msg1, old_model) ---> new_model1
               |  
    old_model--+
               |
               +---> update(msg2, old_model) ---> new_model2
    ```

    Now you have two models, `new_model1` and `new_model2`. Which model should 
    be used in the view?

    In some other UI frameworks, this issue could occur. In rabbit-tea, it can 
    be avoided by using the `Cmd` pattern. If you doesn't use asynchronous 
    functions in update, e.g. `@cmd.attempt` and `@cmd.perform`, you will never 
    met this problem.






---
# Documentation
|Type|description|
|---|---|
|[Cmd](#Cmd)| The command type, represents a task that can be executed.|
|[Events](#Events)| Store the events that can be triggered by the command.|
|[Command](#Command)| The command type, represents a task that can be executed.|

|Value|description|
|---|---|
|[attempt](#attempt)| Create a command that runs an async function and handles errors.|
|[batch](#batch)| Create a command that runs multiple commands.|
|[map](#map)| Map the messages in the command to another type.|
|[none](#none)| Create a command that does nothing.|
|[perform](#perform)| Create a command that runs an async function.|
|[task](#task)| Create a command that trigger another update for the given message.|

## Cmd

```moonbit
:::source,Yoorkin/rabbit-tea/cmd/command.mbt,52:::pub(all) type Cmd[M] (<a href="Yoorkin/rabbit-tea/cmd#Events">Events</a>[M]) -> Unit
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

#### mooncakes-io-method-mark-Methods
- #### map
  ```moonbit
  :::source,Yoorkin/rabbit-tea/cmd/command.mbt,58:::fn <a href="Yoorkin/rabbit-tea/cmd#Cmd">Cmd</a>::map[A, B](self : <a href="Yoorkin/rabbit-tea/cmd#Cmd">Cmd</a>[A], f : (A) -> B) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">Cmd</a>[B]
  ```
  >  Map the messages in the command to another type.

## Events

```moonbit
:::source,Yoorkin/rabbit-tea/cmd/command.mbt,2:::type Events[M]
```
 Store the events that can be triggered by the command.

#### mooncakes-io-method-mark-Methods
- #### new
  ```moonbit
  :::source,Yoorkin/rabbit-tea/cmd/command.mbt,9:::fn <a href="Yoorkin/rabbit-tea/cmd#Events">Events</a>::new[M](on_url_changed : (<a href="Yoorkin/rabbit-tea/url#Url">@Yoorkin/rabbit-tea/url.Url</a>) -> Unit, on_url_request : (<a href="Yoorkin/rabbit-tea/url#UrlRequest">@Yoorkin/rabbit-tea/url.UrlRequest</a>) -> Unit, on_update : (M) -> Unit) -> <a href="Yoorkin/rabbit-tea/cmd#Events">Events</a>[M]
  ```
  >  Used by the runtime.
- #### trigger\_update
  ```moonbit
  :::source,Yoorkin/rabbit-tea/cmd/command.mbt,31:::fn <a href="Yoorkin/rabbit-tea/cmd#Events">Events</a>::trigger_update[M](self : <a href="Yoorkin/rabbit-tea/cmd#Events">Events</a>[M], msg : M) -> Unit
  ```
  >  Trigger the update function with message `msg`.
- #### trigger\_url\_changed
  ```moonbit
  :::source,Yoorkin/rabbit-tea/cmd/command.mbt,18:::fn <a href="Yoorkin/rabbit-tea/cmd#Events">Events</a>::trigger_url_changed[M](self : <a href="Yoorkin/rabbit-tea/cmd#Events">Events</a>[M], url : <a href="Yoorkin/rabbit-tea/url#Url">@Yoorkin/rabbit-tea/url.Url</a>) -> Unit
  ```
  >  Trigger the update function with `url_changed` message config by the user.
- #### trigger\_url\_request
  ```moonbit
  :::source,Yoorkin/rabbit-tea/cmd/command.mbt,23:::fn <a href="Yoorkin/rabbit-tea/cmd#Events">Events</a>::trigger_url_request[M](self : <a href="Yoorkin/rabbit-tea/cmd#Events">Events</a>[M], url : <a href="Yoorkin/rabbit-tea/url#UrlRequest">@Yoorkin/rabbit-tea/url.UrlRequest</a>) -> Unit
  ```
  >  Trigger the update function with `url_request` message config by the user.

## Command

```moonbit
:::source,Yoorkin/rabbit-tea/cmd/command.mbt,55:::type Command[M] = <a href="Yoorkin/rabbit-tea/cmd#Cmd">Cmd</a>[M]
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

## attempt

```moonbit
:::source,Yoorkin/rabbit-tea/cmd/command.mbt,97:::fn attempt[A, E : <a href="moonbitlang/core/error#Error">Error</a>, M](msg : (<a href="moonbitlang/core/result#Result">Result</a>[A, E]) -> M, f : () -> A!E) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">Cmd</a>[M]
```
 Create a command that runs an async function and handles errors.
 
 This is similar to `perform`, but it converts the returned value
or thrown error into a `Result`.

## batch

```moonbit
:::source,Yoorkin/rabbit-tea/cmd/command.mbt,76:::fn batch[M](xs : <a href="moonbitlang/core/array#Array">Array</a>[<a href="Yoorkin/rabbit-tea/cmd#Cmd">Cmd</a>[M]]) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">Cmd</a>[M]
```
 Create a command that runs multiple commands.

## map

```moonbit
:::source,Yoorkin/rabbit-tea/cmd/command.mbt,58:::fn map[A, B](self : <a href="Yoorkin/rabbit-tea/cmd#Cmd">Cmd</a>[A], f : (A) -> B) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">Cmd</a>[B]
```
 Map the messages in the command to another type.

## none

```moonbit
:::source,Yoorkin/rabbit-tea/cmd/command.mbt,71:::fn none[M]() -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">Cmd</a>[M]
```
 Create a command that does nothing.

## perform

```moonbit
:::source,Yoorkin/rabbit-tea/cmd/command.mbt,89:::fn perform[A, M](msg : (A) -> M, f : () -> A) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">Cmd</a>[M]
```
 Create a command that runs an async function.
 
 The async function `f` will be called, and the result will be wrapped in a
message `msg`, then trigger another update with this message.

## task

```moonbit
:::source,Yoorkin/rabbit-tea/cmd/command.mbt,81:::fn task[M](message : M) -> <a href="Yoorkin/rabbit-tea/cmd#Cmd">Cmd</a>[M]
```
 Create a command that trigger another update for the given message.
