# Documentation
|Trait|description|
|---|---|
|[@gmlewis/spin-moonbit-sdk/common.HashFunc](#@gmlewis/spin-moonbit-sdk/common.HashFunc)||

## @gmlewis/spin-moonbit-sdk/common.HashFunc

```moonbit
:::source,gmlewis/spin-moonbit-sdk/common/hash-func.mbt,3:::pub(open) trait @gmlewis/spin-moonbit-sdk/common.HashFunc {
  name(Self) -> String
  write(Self, Byte) -> Unit
  check_sum(Self) -> String
}
```

 `HashFunc` represents a hash algorithm like `@md5` or `@sha256`.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/common/hash-func.mbt,16:::impl <a href="gmlewis/spin-moonbit-sdk/common#HashFunc">HashFunc</a> for <a href="gmlewis/md5#Digest">@gmlewis/md5.Digest</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/common/hash-func.mbt,26:::fn check_sum(self : <a href="gmlewis/md5#Digest">@gmlewis/md5.Digest</a>) -> String
    ```
    > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/common/hash-func.mbt,16:::fn name(self : <a href="gmlewis/md5#Digest">@gmlewis/md5.Digest</a>) -> String
    ```
    > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/common/hash-func.mbt,21:::fn write(self : <a href="gmlewis/md5#Digest">@gmlewis/md5.Digest</a>, b : Byte) -> Unit
    ```
    > 
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/common/hash-func.mbt,31:::impl <a href="gmlewis/spin-moonbit-sdk/common#HashFunc">HashFunc</a> for <a href="gmlewis/sha256#Digest">@gmlewis/sha256.Digest</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/common/hash-func.mbt,41:::fn check_sum(self : <a href="gmlewis/sha256#Digest">@gmlewis/sha256.Digest</a>) -> String
    ```
    > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/common/hash-func.mbt,31:::fn name(self : <a href="gmlewis/sha256#Digest">@gmlewis/sha256.Digest</a>) -> String
    ```
    > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/common/hash-func.mbt,36:::fn write(self : <a href="gmlewis/sha256#Digest">@gmlewis/sha256.Digest</a>, b : Byte) -> Unit
    ```
    > 
