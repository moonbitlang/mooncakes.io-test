# Documentation
|Type|description|
|---|---|
|[Lex](#Lex)||
|[Regex](#Regex)||
|[Rule](#Rule)||
|[VarType](#VarType)||
|[CodeBlock](#CodeBlock)||

|Value|description|
|---|---|
|[check\_legal](#check_legal)||
|[get\_capture\_names](#get_capture_names)||
|[get\_char\_vars](#get_char_vars)||

## Lex

```moonbit
:::source,moonbitlang/ulex/lib/type/type.mbt,156:::pub(all) struct Lex {
  header : String
  rules : <a href="moonbitlang/core/array#Array">Array</a>[<a href="moonbitlang/ulex/lib/type#Rule">Rule</a>]
  trailer : String
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/ulex/lib/type/type.mbt,160:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/ulex/lib/type#Lex">Lex</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/type/type.mbt,160:::fn output(<a href="moonbitlang/ulex/lib/type#Lex">Lex</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,moonbitlang/ulex/lib/type/type.mbt,160:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="moonbitlang/ulex/lib/type#Lex">Lex</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/type/type.mbt,160:::fn to_json(<a href="moonbitlang/ulex/lib/type#Lex">Lex</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > automatically derived

## Regex

```moonbit
:::source,moonbitlang/ulex/lib/type/type.mbt,2:::pub(all) enum Regex {
  EOF
  Character(<a href="moonbitlang/ulex/lib/util/eof_char_set#EofCharSet">@moonbitlang/ulex/lib/util/eof_char_set.EofCharSet</a>)
  Repetition(<a href="moonbitlang/ulex/lib/type#Regex">Regex</a>)
  Epsilon
  Alter(<a href="moonbitlang/ulex/lib/type#Regex">Regex</a>, <a href="moonbitlang/ulex/lib/type#Regex">Regex</a>)
  Concat(<a href="moonbitlang/ulex/lib/type#Regex">Regex</a>, <a href="moonbitlang/ulex/lib/type#Regex">Regex</a>)
  Capture(<a href="moonbitlang/ulex/lib/type#Regex">Regex</a>, String)
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/ulex/lib/type/type.mbt,10:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/ulex/lib/type#Regex">Regex</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/type/type.mbt,10:::fn op_equal(<a href="moonbitlang/ulex/lib/type#Regex">Regex</a>, <a href="moonbitlang/ulex/lib/type#Regex">Regex</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,moonbitlang/ulex/lib/type/type.mbt,10:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/ulex/lib/type#Regex">Regex</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/type/type.mbt,10:::fn output(<a href="moonbitlang/ulex/lib/type#Regex">Regex</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,moonbitlang/ulex/lib/type/type.mbt,10:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="moonbitlang/ulex/lib/type#Regex">Regex</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/type/type.mbt,10:::fn to_json(<a href="moonbitlang/ulex/lib/type#Regex">Regex</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### check\_legal
  ```moonbit
  :::source,moonbitlang/ulex/lib/type/type.mbt,19:::fn <a href="moonbitlang/ulex/lib/type#Regex">Regex</a>::check_legal(self : <a href="moonbitlang/ulex/lib/type#Regex">Regex</a>) -> Bool
  ```
  > 
- #### get\_capture\_names
  ```moonbit
  :::source,moonbitlang/ulex/lib/type/type.mbt,117:::fn <a href="moonbitlang/ulex/lib/type#Regex">Regex</a>::get_capture_names(self : <a href="moonbitlang/ulex/lib/type#Regex">Regex</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[(String, <a href="moonbitlang/ulex/lib/type#VarType">VarType</a>)]
  ```
  > 

## Rule

```moonbit
:::source,moonbitlang/ulex/lib/type/type.mbt,149:::pub(all) struct Rule {
  name : String
  signature : String
  patterns : <a href="moonbitlang/core/array#Array">Array</a>[(<a href="moonbitlang/ulex/lib/type#Regex">Regex</a>, String)]
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/ulex/lib/type/type.mbt,153:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/ulex/lib/type#Rule">Rule</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/type/type.mbt,153:::fn output(<a href="moonbitlang/ulex/lib/type#Rule">Rule</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,moonbitlang/ulex/lib/type/type.mbt,153:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="moonbitlang/ulex/lib/type#Rule">Rule</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/type/type.mbt,153:::fn to_json(<a href="moonbitlang/ulex/lib/type#Rule">Rule</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > automatically derived

## VarType

```moonbit
:::source,moonbitlang/ulex/lib/type/type.mbt,13:::pub(all) enum VarType {
  Char
  String
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/ulex/lib/type/type.mbt,16:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/ulex/lib/type#VarType">VarType</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/ulex/lib/type/type.mbt,16:::fn output(<a href="moonbitlang/ulex/lib/type#VarType">VarType</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## CodeBlock

```moonbit
:::source,moonbitlang/ulex/lib/type/type.mbt,146:::type CodeBlock = String
```


## check\_legal

```moonbit
:::source,moonbitlang/ulex/lib/type/type.mbt,19:::fn check_legal(self : <a href="moonbitlang/ulex/lib/type#Regex">Regex</a>) -> Bool
```


## get\_capture\_names

```moonbit
:::source,moonbitlang/ulex/lib/type/type.mbt,117:::fn get_capture_names(self : <a href="moonbitlang/ulex/lib/type#Regex">Regex</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[(String, <a href="moonbitlang/ulex/lib/type#VarType">VarType</a>)]
```


## get\_char\_vars

```moonbit
:::source,moonbitlang/ulex/lib/type/type.mbt,62:::fn get_char_vars(re : <a href="moonbitlang/ulex/lib/type#Regex">Regex</a>) -> <a href="moonbitlang/core/immut/sorted_set#T">@moonbitlang/core/immut/sorted_set.T</a>[String]
```

