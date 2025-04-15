# Documentation
|Type|description|
|---|---|
|[GPIOConfig](#GPIOConfig)||
|[GPIOIntType](#GPIOIntType)||
|[GPIOMode](#GPIOMode)||
|[GPIOPulldown](#GPIOPulldown)||
|[GPIOPullup](#GPIOPullup)||

|Value|description|
|---|---|
|[GPIO\_MODE\_DEF\_DISABLE](#GPIO_MODE_DEF_DISABLE)||
|[GPIO\_MODE\_DEF\_INPUT](#GPIO_MODE_DEF_INPUT)||
|[GPIO\_MODE\_DEF\_OD](#GPIO_MODE_DEF_OD)||
|[GPIO\_MODE\_DEF\_OUTPUT](#GPIO_MODE_DEF_OUTPUT)||
|[gpio\_config](#gpio_config)||
|[gpio\_set\_level](#gpio_set_level)||

## GPIOConfig

```moonbit
:::source,lijunchen/test_esp32/components/gpio/gpio.mbt,69:::pub(all) struct GPIOConfig {
  pin_bit_mask : UInt64
  mode : <a href="lijunchen/test_esp32/components/gpio#GPIOMode">GPIOMode</a>
  pull_up_en : <a href="lijunchen/test_esp32/components/gpio#GPIOPullup">GPIOPullup</a>
  pull_down_en : <a href="lijunchen/test_esp32/components/gpio#GPIOPulldown">GPIOPulldown</a>
  intr_type : <a href="lijunchen/test_esp32/components/gpio#GPIOIntType">GPIOIntType</a>
}
```


## GPIOIntType

```moonbit
:::source,lijunchen/test_esp32/components/gpio/gpio.mbt,55:::pub(all) enum GPIOIntType {
  GPIO_INTR_DISABLE
  GPIO_INTR_POSEDGE
  GPIO_INTR_NEGEDGE
  GPIO_INTR_ANYEDGE
  GPIO_INTR_LOW_LEVEL
  GPIO_INTR_HIGH_LEVEL
  GPIO_INTR_MAX
}
```


#### mooncakes-io-method-mark-Methods
- #### to\_int
  ```moonbit
  :::source,lijunchen/test_esp32/components/gpio/gpio.mbt,66:::fn <a href="lijunchen/test_esp32/components/gpio#GPIOIntType">GPIOIntType</a>::to_int(self : <a href="lijunchen/test_esp32/components/gpio#GPIOIntType">GPIOIntType</a>) -> Int
  ```
  > 

## GPIOMode

```moonbit
:::source,lijunchen/test_esp32/components/gpio/gpio.mbt,14:::pub(all) enum GPIOMode {
  GPIO_MODE_DISABLE
  GPIO_MODE_INPUT
  GPIO_MODE_OUTPUT
  GPIO_MODE_OUTPUT_OD
  GPIO_MODE_INPUT_OUTPUT_OD
  GPIO_MODE_INPUT_OUTPUT
}
```


#### mooncakes-io-method-mark-Methods
- #### to\_int
  ```moonbit
  :::source,lijunchen/test_esp32/components/gpio/gpio.mbt,24:::fn <a href="lijunchen/test_esp32/components/gpio#GPIOMode">GPIOMode</a>::to_int(self : <a href="lijunchen/test_esp32/components/gpio#GPIOMode">GPIOMode</a>) -> Int
  ```
  > 

## GPIOPulldown

```moonbit
:::source,lijunchen/test_esp32/components/gpio/gpio.mbt,46:::pub(all) enum GPIOPulldown {
  GPIO_PULLDOWN_DISABLE
  GPIO_PULLDOWN_ENABLE
}
```


#### mooncakes-io-method-mark-Methods
- #### to\_int
  ```moonbit
  :::source,lijunchen/test_esp32/components/gpio/gpio.mbt,52:::fn <a href="lijunchen/test_esp32/components/gpio#GPIOPulldown">GPIOPulldown</a>::to_int(self : <a href="lijunchen/test_esp32/components/gpio#GPIOPulldown">GPIOPulldown</a>) -> Int
  ```
  > 

## GPIOPullup

```moonbit
:::source,lijunchen/test_esp32/components/gpio/gpio.mbt,37:::pub(all) enum GPIOPullup {
  GPIO_PULLUP_DISABLE
  GPIO_PULLUP_ENABLE
}
```


#### mooncakes-io-method-mark-Methods
- #### to\_int
  ```moonbit
  :::source,lijunchen/test_esp32/components/gpio/gpio.mbt,43:::fn <a href="lijunchen/test_esp32/components/gpio#GPIOPullup">GPIOPullup</a>::to_int(self : <a href="lijunchen/test_esp32/components/gpio#GPIOPullup">GPIOPullup</a>) -> Int
  ```
  > 

## GPIO\_MODE\_DEF\_DISABLE

```moonbit
:::source,lijunchen/test_esp32/components/gpio/gpio.mbt,2:::let GPIO_MODE_DEF_DISABLE : Int
```


## GPIO\_MODE\_DEF\_INPUT

```moonbit
:::source,lijunchen/test_esp32/components/gpio/gpio.mbt,5:::let GPIO_MODE_DEF_INPUT : Int
```


## GPIO\_MODE\_DEF\_OD

```moonbit
:::source,lijunchen/test_esp32/components/gpio/gpio.mbt,11:::let GPIO_MODE_DEF_OD : Int
```


## GPIO\_MODE\_DEF\_OUTPUT

```moonbit
:::source,lijunchen/test_esp32/components/gpio/gpio.mbt,8:::let GPIO_MODE_DEF_OUTPUT : Int
```


## gpio\_config

```moonbit
:::source,lijunchen/test_esp32/components/gpio/gpio.mbt,87:::fn gpio_config(pin_bit_mask~ : UInt64, mode~ : <a href="lijunchen/test_esp32/components/gpio#GPIOMode">GPIOMode</a>, pull_up_en~ : <a href="lijunchen/test_esp32/components/gpio#GPIOPullup">GPIOPullup</a>, pull_down_en~ : <a href="lijunchen/test_esp32/components/gpio#GPIOPulldown">GPIOPulldown</a>, intr_type~ : <a href="lijunchen/test_esp32/components/gpio#GPIOIntType">GPIOIntType</a>) -> Unit!<a href="lijunchen/test_esp32/error#ESPError">@lijunchen/test_esp32/error.ESPError</a>
```


## gpio\_set\_level

```moonbit
:::source,lijunchen/test_esp32/components/gpio/gpio.mbt,109:::fn gpio_set_level(pin : Int, level : Int) -> Unit!<a href="lijunchen/test_esp32/error#ESPError">@lijunchen/test_esp32/error.ESPError</a>
```

