# Documentation
|Value|description|
|---|---|
|[get\_arguments](#get_arguments)||
|[get\_environment](#get_environment)||
|[initial\_cwd](#initial_cwd)||

## get\_arguments

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/cli/environment/top.mbt,29:::fn get_arguments() -> <a href="moonbitlang/core/array#Array">Array</a>[String]
```

 Get the POSIX-style arguments to the program.

## get\_environment

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/cli/environment/top.mbt,12:::fn get_environment() -> <a href="moonbitlang/core/array#Array">Array</a>[(String, String)]
```

 Get the POSIX-style environment variables.

 Each environment variable is provided as a pair of string variable names
and string value.

 Morally, these are a value import, but until value imports are available
in the component model, this import function should return the same
values each time it is called.

## initial\_cwd

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/cli/environment/top.mbt,46:::fn initial_cwd() -> String?
```

 Return a path that programs should use as their initial current working
directory, interpreting `.` as shorthand for this.
