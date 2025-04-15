# Documentation
|Type|description|
|---|---|
|[Connection](#Connection)||

## Connection

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/mysql/top.mbt,5:::pub(all) type Connection Int
```

 A connection to a MySQL database.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/mysql/top.mbt,5:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/mysql#Connection">Connection</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/mysql/top.mbt,5:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/mysql#Connection">Connection</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/mysql#Connection">Connection</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/mysql/top.mbt,5:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/mysql#Connection">Connection</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/mysql/top.mbt,5:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/mysql#Connection">Connection</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### drop
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/mysql/top.mbt,11:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/mysql#Connection">Connection</a>::drop(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/mysql#Connection">Connection</a>) -> Unit
  ```
  > 
- #### execute
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/mysql/top.mbt,266:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/mysql#Connection">Connection</a>::execute(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/mysql#Connection">Connection</a>, statement : String, params : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#ParameterValue">@gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes.ParameterValue</a>]) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#Error_">@gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes.Error_</a>]
  ```
  > 
  >  execute command to the database: insert, update, delete
- #### open
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/mysql/top.mbt,17:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/mysql#Connection">Connection</a>::open(address : String) -> <a href="moonbitlang/core/result#Result">Result</a>[<a href="gmlewis/spin-moonbit-sdk/interface/imports/mysql#Connection">Connection</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#Error_">@gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes.Error_</a>]
  ```
  > 
  >  Open a connection to the MySQL instance at `address`.
- #### query
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/mysql/top.mbt,63:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/mysql#Connection">Connection</a>::query(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/mysql#Connection">Connection</a>, statement : String, params : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#ParameterValue">@gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes.ParameterValue</a>]) -> <a href="moonbitlang/core/result#Result">Result</a>[<a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#RowSet">@gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes.RowSet</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes#Error_">@gmlewis/spin-moonbit-sdk/interface/imports/rdbmsTypes.Error_</a>]
  ```
  > 
  >  query the database: select
