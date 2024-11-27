# The Dactyl Lynx Keyboard - RMK Firmware

Keyboard firmware for [the Dactyl Lynx keyboard][] using [RMK][]. (with [Vial][] support, written in [Rust][])

[the Dactyl Lynx keyboard]: https://github.com/whitelynx/dactyl-lynx-keyboard
[RMK]: https://github.com/HaoboGu/rmk
[Vial]: https://get.vial.today
[Rust]: https://www.rust-lang.org/


## Building the Firmware

Before building for the first time, make sure `cargo-make`, `flip-link`, and the compilation target for the RP2040 are
installed, and update dependencies:
```bash
cargo install --force cargo-make
cargo install flip-link
rustup target add thumbv6m-none-eabi
cargo update
```

To build the firmware:
```bash
cargo build --release
cargo make uf2 --release
```

This will create `rmk-central.uf2` and `rmk-peripheral.uf2` in the root of the project.


## Flashing to the Keyboard

Plug in the **left** side of the keyboard while holding the `Boot` button

Double-tap the RST button on the RP2040 to enter bootloader mode. Mount the USB storage device if needed, then copy the
appropriate uf2 file to the device, for example by dragging the file to the new USB disk.

For the **left** side, copy `rmk-central.uf2`; for the **right** side, copy `rmk-peripheral.uf2`.
