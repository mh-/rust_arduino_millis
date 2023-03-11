# rust_arduino_millis

This crate adds the `millis()` funtionality to an Arduino project.

It was copied from sample code by Rahix: https://github.com/Rahix/avr-hal/blob/4303bfeb6105ea572c3eba5626235f57483a27c6/examples/nano168/src/bin/nano168-millis.rs 
and slightly modified to make it a separate create.

Tested only on Arduino Nano.

## Use: 
Add the dependency to `Cargo.toml`:
```
[dependencies]
rust_arduino_millis = { git = "https://github.com/mh-/rust_arduino_millis" }
```

In `main()`:
```
fn main() -> ! {
    let dp = arduino_hal::Peripherals::take().unwrap();
...
    use rust_arduino_millis::arduino_millis::*;
    millis_init(dp.TC0);
```

In `loop()` for example:
```
    loop {
        // Read the timer:
        let time_ms: i32 = millis().try_into().unwrap();
...
```
There's also a `millis_reset()` function available, in case you need to reset millis to 0.
