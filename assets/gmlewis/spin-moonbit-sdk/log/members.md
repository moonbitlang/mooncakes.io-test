# Documentation
|Value|description|
|---|---|
|[debug](#debug)||
|[error](#error)||
|[info](#info)||
|[warn](#warn)||

## debug

```moonbit
:::source,gmlewis/spin-moonbit-sdk/log/logger.mbt,14:::fn debug(s : String, leading_blank_line~ : Bool = ..) -> Unit
```

 `debug` prints a string prefixed with "DEBUG: " to wasi stderr with a newline.

## error

```moonbit
:::source,gmlewis/spin-moonbit-sdk/log/logger.mbt,36:::fn error(s : String, leading_blank_line~ : Bool = ..) -> Unit
```

 `error` prints a string prefixed with "ERROR: " to wasi stderr with a newline.

## info

```moonbit
:::source,gmlewis/spin-moonbit-sdk/log/logger.mbt,3:::fn info(s : String, leading_blank_line~ : Bool = ..) -> Unit
```

 `info` prints a string prefixed with "INFO: " to wasi stderr with a newline.

## warn

```moonbit
:::source,gmlewis/spin-moonbit-sdk/log/logger.mbt,25:::fn warn(s : String, leading_blank_line~ : Bool = ..) -> Unit
```

 `warn` prints a string prefixed with "WARNING: " to wasi stderr with a newline.
