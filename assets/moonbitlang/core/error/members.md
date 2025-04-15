# Documentation
|Type|description|
|---|---|
|[Error](#Error)||

## Error


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/error/error.mbt,35:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/error#Error">Error</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/error/error.mbt,35:::fn output(self : <a href="moonbitlang/core/error#Error">Error</a>, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
    >  Implements `Show` trait for `Error` type by converting the error into a
    > string representation.
    > 
    >  Parameters:
    > 
    >  * `self`: The error value to be converted.
    >  * `logger`: A buffer that accumulates the string representation.
    > 
    >  Example:
    > 
    >  ```moonbit
    >  test "Error::Show/output" {
    >    let error : Error = Failure("test error")
    >    inspect!(error, content="\"Failure(test error)\"")
    >  }
    >  ```
