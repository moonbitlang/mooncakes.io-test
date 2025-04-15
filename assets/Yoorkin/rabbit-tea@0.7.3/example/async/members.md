# Async Example

This example demonstrates how to manually wrap an async JS FFI in Moonbit. 

It's particularly useful when the functionality is not 
yet available in the rabbit-tea library. Ideally, the Core library should 
provide basic async utilities, but in this early stage, we need to implement 
the wrapping ourselves. 

If you are looking for HTTP request functionality, you can use the `rabbit-tea/http` package.

Run the example with the following command:

```bash
cd src/example/async
bash ./launch.sh
```

This command will build the project with js backend, and launch the server with node.

---
# Documentation
|Type|description|
|---|---|
|[Message](#Message)||
|[Model](#Model)||

|Value|description|
|---|---|
|[suspend](#suspend)||

## Message

```moonbit
:::source,Yoorkin/rabbit-tea/example/async/main.mbt,5:::type Message
```


## Model

```moonbit
:::source,Yoorkin/rabbit-tea/example/async/main.mbt,12:::type Model
```


## suspend

```moonbit
:::source,Yoorkin/rabbit-tea/example/async/main.mbt,17:::fn suspend[T](f : ((T) -> Unit) -> Unit) -> T
```

