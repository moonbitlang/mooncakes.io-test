# Todo App Example

This is a simple todo app example.
It uses the [nested-TEA pattern](https://sporto.github.io/elm-patterns/architecture/nested-tea.html) to demonstrate
how to build a complex app with multiple pages. It doesn't mean the pattern is encouraged to be used in a small app like this.

## Setup

Run the following command to start the example:

```bash
cd src/example/todoMVC
bash ./launch.sh
``` 

This command will build the project with js backend, and launch the server with node.




---
# Documentation
|Type|description|
|---|---|
|[Message](#Message)||
|[Model](#Model)||

## Message

```moonbit
:::source,Yoorkin/rabbit-tea/example/todoMVC/main.mbt,2:::type Message
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,Yoorkin/rabbit-tea/example/todoMVC/main.mbt,7:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="Yoorkin/rabbit-tea/example/todoMVC#Message">Message</a>
  ```
  > 
  * ```moonbit
    :::source,Yoorkin/rabbit-tea/example/todoMVC/main.mbt,7:::fn output(<a href="Yoorkin/rabbit-tea/example/todoMVC#Message">Message</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## Model

```moonbit
:::source,Yoorkin/rabbit-tea/example/todoMVC/main.mbt,10:::type Model
```

