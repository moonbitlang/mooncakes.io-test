# Documentation
|Type|description|
|---|---|
|[IniFile](#IniFile)||
|[IniParseError](#IniParseError)||
|[IniParseState](#IniParseState)||

|Value|description|
|---|---|
|[parse](#parse)||

## IniFile

```moonbit
:::source,ShellWen/sw_ini/ini_file.mbt,14:::type IniFile
```


#### mooncakes-io-method-mark-Methods
- #### get
  ```moonbit
  :::source,ShellWen/sw_ini/ini_file.mbt,43:::fn <a href="ShellWen/sw_ini#IniFile">IniFile</a>::get(self : <a href="ShellWen/sw_ini#IniFile">IniFile</a>, section~ : String = .., key : String) -> String?
  ```
  >  get is a alias for get\_string
- #### get\_bool
  ```moonbit
  :::source,ShellWen/sw_ini/ini_file.mbt,74:::fn <a href="ShellWen/sw_ini#IniFile">IniFile</a>::get_bool(self : <a href="ShellWen/sw_ini#IniFile">IniFile</a>, section~ : String = .., key : String) -> Bool?
  ```
  > 
- #### get\_string
  ```moonbit
  :::source,ShellWen/sw_ini/ini_file.mbt,52:::fn <a href="ShellWen/sw_ini#IniFile">IniFile</a>::get_string(self : <a href="ShellWen/sw_ini#IniFile">IniFile</a>, section~ : String = .., key : String) -> String?
  ```
  > 
- #### new
  ```moonbit
  :::source,ShellWen/sw_ini/ini_file.mbt,21:::fn <a href="ShellWen/sw_ini#IniFile">IniFile</a>::new(is_case_sensitive~ : Bool = ..) -> <a href="ShellWen/sw_ini#IniFile">IniFile</a>
  ```
  > 
- #### set
  ```moonbit
  :::source,ShellWen/sw_ini/ini_file.mbt,121:::fn <a href="ShellWen/sw_ini#IniFile">IniFile</a>::set(self : <a href="ShellWen/sw_ini#IniFile">IniFile</a>, section~ : String = .., key : String, value : String) -> Unit
  ```
  > 

## IniParseError

```moonbit
:::source,ShellWen/sw_ini/parser.mbt,2:::pub enum IniParseError {
  UnexpectedEqualSign(Int, Int)
  EmptySection(Int, Int)
  UnclosedSection(Int, Int)
  ValueWithoutSection(Int, Int)
  QuoteMismatch(Int, Int)
  QuoteNotClosed(Int, Int)
}
```


## IniParseState

```moonbit
:::source,ShellWen/sw_ini/parser.mbt,38:::type IniParseState
```


#### mooncakes-io-method-mark-Methods
- #### finish
  ```moonbit
  :::source,ShellWen/sw_ini/parser.mbt,90:::fn <a href="ShellWen/sw_ini#IniParseState">IniParseState</a>::finish(self : <a href="ShellWen/sw_ini#IniParseState">IniParseState</a>) -> <a href="ShellWen/sw_ini#IniFile">IniFile</a>!<a href="ShellWen/sw_ini#IniParseError">IniParseError</a>
  ```
  > 
- #### new
  ```moonbit
  :::source,ShellWen/sw_ini/parser.mbt,54:::fn <a href="ShellWen/sw_ini#IniParseState">IniParseState</a>::new(is_case_sensitive~ : Bool = ..) -> <a href="ShellWen/sw_ini#IniParseState">IniParseState</a>
  ```
  > 
- #### parse
  ```moonbit
  :::source,ShellWen/sw_ini/parser.mbt,78:::fn <a href="ShellWen/sw_ini#IniParseState">IniParseState</a>::parse(self : <a href="ShellWen/sw_ini#IniParseState">IniParseState</a>, chunk : String) -> <a href="ShellWen/sw_ini#IniParseState">IniParseState</a>!<a href="ShellWen/sw_ini#IniParseError">IniParseError</a>
  ```
  > 

## parse

```moonbit
:::source,ShellWen/sw_ini/parser.mbt,70:::fn parse(str : String, is_case_sensitive~ : Bool = ..) -> <a href="ShellWen/sw_ini#IniFile">IniFile</a>!<a href="ShellWen/sw_ini#IniParseError">IniParseError</a>
```

