Terminal output.

In the future, this may include functions for querying the terminal
size, being notified of terminal size changes, querying supported
features, and so on.
---
# Documentation
|Type|description|
|---|---|
|[TerminalOutput](#TerminalOutput)||

## TerminalOutput

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/cli/terminalOutput/top.mbt,5:::pub(all) type TerminalOutput Int
```

 The output side of a terminal.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/cli/terminalOutput/top.mbt,5:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/cli/terminalOutput#TerminalOutput">TerminalOutput</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/cli/terminalOutput/top.mbt,5:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/cli/terminalOutput#TerminalOutput">TerminalOutput</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/cli/terminalOutput#TerminalOutput">TerminalOutput</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/cli/terminalOutput/top.mbt,5:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/cli/terminalOutput#TerminalOutput">TerminalOutput</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/cli/terminalOutput/top.mbt,5:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/cli/terminalOutput#TerminalOutput">TerminalOutput</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### drop
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/cli/terminalOutput/top.mbt,11:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/cli/terminalOutput#TerminalOutput">TerminalOutput</a>::drop(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/cli/terminalOutput#TerminalOutput">TerminalOutput</a>) -> Unit
  ```
  > 
