WASI Monotonic Clock is a clock API intended to let users measure elapsed
time.

It is intended to be portable at least between Unix-family platforms and
Windows.

A monotonic clock is a clock which has an unspecified initial value, and
successive reads of the clock will produce non-decreasing values.

It is intended for measuring elapsed time.
---
# Documentation
|Value|description|
|---|---|
|[now](#now)||
|[resolution](#resolution)||
|[subscribe\_duration](#subscribe_duration)||
|[subscribe\_instant](#subscribe_instant)||

## now

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/clocks/monotonicClock/top.mbt,8:::fn now() -> UInt64
```

 Read the current value of the clock.

 The clock is monotonic, therefore calling this function repeatedly will
produce a sequence of non-decreasing values.

## resolution

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/clocks/monotonicClock/top.mbt,16:::fn resolution() -> UInt64
```

 Query the resolution of the clock. Returns the duration of time
corresponding to a clock tick.

## subscribe\_duration

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/clocks/monotonicClock/top.mbt,33:::fn subscribe_duration(when : UInt64) -> <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll#Pollable">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll.Pollable</a>
```

 Create a `pollable` which will resolve once the given duration has
elapsed, starting at the time at which this function was called.
occured.

## subscribe\_instant

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/clocks/monotonicClock/top.mbt,24:::fn subscribe_instant(when : UInt64) -> <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll#Pollable">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll.Pollable</a>
```

 Create a `pollable` which will resolve once the specified instant
occured.
