# Blog OS (Double Faults)

[![Build Status](https://travis-ci.org/phil-opp/blog_os.svg?branch=post-07)](https://travis-ci.org/phil-opp/blog_os/branches)

This repository contains the source code for the [Double Faults][post] post of the [Writing an OS in Rust](https://os.phil-opp.com) series.

[post]: https://os.phil-opp.com/double-fault-exceptions/

**Check out the [master branch](https://github.com/phil-opp/blog_os) for more information.**

## Building

You need a nightly Rust compiler. First you need to install the `cargo-xbuild` and `bootimage` tools:

```
cargo install cargo-xbuild bootimage
```

Then you can build the project by running:

```
bootimage build
```

This creates a bootable disk image in the `target/x86_64-blog_os/debug` directory.

Please file an issue if you have any problems.

## Running

You can run the disk image in [QEMU] through:

[QEMU]: https://www.qemu.org/

```
bootimage run
```

Of course [QEMU] needs to be installed for this.

You can also write the image to an USB stick for booting it on a real machine. On Linux, the command for this is:

```
dd if=target/x86_64-blog_os/debug/bootimage-blog_os.bin of=/dev/sdX && sync
```

Where `sdX` is the device name of your USB stick. **Be careful** to choose the correct device name, because everything on that device is overwritten.

## Testing

To run the unit tests on the host system, execute `cargo test`. To run the integration tests in [QEMU], run `bootimage test`.

## License
The source code is dual-licensed under MIT or the Apache License (Version 2.0).
