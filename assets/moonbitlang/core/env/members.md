# Documentation
|Value|description|
|---|---|
|[args](#args)||
|[current\_dir](#current_dir)||
|[now](#now)||

## args

```moonbit
:::source,moonbitlang/core/env/env.mbt,17:::fn args() -> <a href="moonbitlang/core/array#Array">Array</a>[String]
```

 Get the command line arguments passed to the program.

## current\_dir

```moonbit
:::source,moonbitlang/core/env/env.mbt,29:::fn current_dir() -> String?
```

 Get the current working directory. On some platforms, this may return `None` if the current directory cannot be determined.

## now

```moonbit
:::source,moonbitlang/core/env/env.mbt,23:::fn now() -> UInt64
```

 Get the current time in milliseconds since the Unix epoch.
