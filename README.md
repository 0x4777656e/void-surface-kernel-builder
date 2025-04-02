# void-surface-kernel-builder
Script to build XBPS packages for linux-surface kernels

### About
Due to some hardware quirks, Microsoft Surface devices often require some kernel
patches for all of their functionality to be usable. These patches are developed
in the [linux-surface](https://github.com/linux-surface/linux-surface) 
repository, but the resulting kernels are not packaged for Void. This repository 
aims to help bridge the gap and provide a simple way to use linux-surface 
kernels on Void with full XBPS integration.

> **Note**: This script works on my machine, but cannot guarantee that it will 
> work on yours. If you're having trouble, feel free to create an issue here, 
> and I'll do my best to help. This utility is not officially supported by Void 
> or linux-surface — try building the kernel manually before creating an issue 
> in the void-packages or linux-surface repositories.

### Dependencies
All dependencies of 
[void-packages](https://github.com/void-linux/void-packages), as well as 
`xtools`.

### Usage
By default, `build-kernel` will package the most recent kernel version supported 
by both Void and linux-surface, targeting the host's architecture. 

Build a specific version:

`$ ./build-kernel -v <version>`

Build for a different architecture:

`$ ./build-kernel -a <architecture>`

`build-kernel` can also be supplied with an additional kernel configuration file 
and/or any number of patches:

`$ ./build-kernel -c <configfile> -p <patchfile> -p <patchfile>`

`build-kernel` calls `void-packages/xbps-src` directly, so it will obey any 
configuration set in `void-packages/etc/conf`. Alternatively, any command line 
options after `--` will be passed to `xbps-src`:

`$ ./build-kernel -- <xbps-src option>...`

### References
[mournfully/patched-void-surface-kernel](https://github.com/mournfully/patched-void-surface-kernel) — 
Installing void-linux with linux-surface kernel on a surface laptop 2

*Shoutout to [@mournfully](https://github.com/mournfully) for their work on this 
— their repo was a HUGE help in getting this all working.*

[linux-surface/linux-surface](https://github.com/linux-surface/linux-surface) —
Linux Kernel for Surface Devices

[void-linux/void-packages](https://github.com/void-linux/void-packages) — The 
Void source packages collection
