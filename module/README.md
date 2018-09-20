# Module

_Note: This is intended only for development._
_See the patch file for kernel integration._

## Installing/Testing

You can either install it via the DKMS system or manually.
For the DKMS system you might need some additional packages, however it's also more convenient (i.e. w.r.t. kernel updates).

_Note: See [issues](#issues) before trying to load the module, as you may need to unload another module first._

### On Arch Linux

Build and install the package via the provided PKGBUILD, i.e. run `makepkg` inside this folder and then `pacman -U *.tar.xz`.

### Via DKMS (Recommended)

Just run `make dkms-install` as root inside this folder.
You can then load the module via `modprobe sb2_button`.
It also should load automatically when you reboot.

### Manual

Run `make all` inside this folder.
You should then have the kernel module as `sb2_button.ko`.
This can be loaded via `insmod sb2_button.ko` or installed just like any other module.

## Issues

The `MSHW0040` is claimed by both, the `sb2_button` and `surfacepro3_button` drivers.
While the former now only loads on the Surface Book 2 and Surface Pro (2017), the latter loads on all devices.
Thus may need to unload and/or blacklist the `surfacepro3_button` module before loading this one.

This issue should be resolved with the latest [linux-surface kernel][linux-surface].

_TLDR: You might need to unload the `surfacepro3_button` module, i.e. run `sudo modprobe -r surfacepro3_button` before loading this module._

[linux-surface]: https://github.com/jakeday/linux-surface
