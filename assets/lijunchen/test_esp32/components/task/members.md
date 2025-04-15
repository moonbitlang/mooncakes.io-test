# Documentation
|Value|description|
|---|---|
|[pdMS\_TO\_TICKS](#pdMS_TO_TICKS)||
|[vTaskDelay](#vTaskDelay)||
|[xTaskCreate](#xTaskCreate)||

## pdMS\_TO\_TICKS

```moonbit
:::source,lijunchen/test_esp32/components/task/task.mbt,28:::fn pdMS_TO_TICKS(ms : Int) -> Int
```


## vTaskDelay

```moonbit
:::source,lijunchen/test_esp32/components/task/task.mbt,23:::fn vTaskDelay(ticks : Int) -> Unit
```


## xTaskCreate

```moonbit
:::source,lijunchen/test_esp32/components/task/task.mbt,10:::fn xTaskCreate(pxTaskCode : <a href="moonbitlang/core/builtin#FuncRef">FuncRef</a>[(<a href="lijunchen/test_esp32/ctypes#Ptr">@lijunchen/test_esp32/ctypes.Ptr</a>[<a href="lijunchen/test_esp32/ctypes#Void">@lijunchen/test_esp32/ctypes.Void</a>]) -> Unit], pcName : <a href="lijunchen/test_esp32/ctypes#CString">@lijunchen/test_esp32/ctypes.CString</a>, usStackDepth : UInt, uxPriority : UInt) -> Int
```

