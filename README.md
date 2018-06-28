# Surface Book 2 / Surface Pro (2017) Power and Volume Button Driver

_Note: I have not tested this on the Surface Pro (2017)._
_According to the DSDT, it should work._
_Test at your own risk, feedback is appreciated._

## Installing/Testing

You can either install it via the DKMS system or manually.
For the DKMS system you might need some additional packages, however it's also more convenient (i.e. w.r.t. kernel updates).

_Note: See [issues](#issues) before trying to load the module, as you may need to unload another module first._

### Via DKMS (Recommended)

Just run `make dkms-install` as root inside this folder.
You can then load the module via `modprobe sb2_button`.
It also should load automatically when you reboot.

### Manual

Run `make all` inside this folder.
You should then have the kernel module as `sb2_button.ko`.
This can be loaded via `insmod sb2_button.ko` or installed just like any other module.

## Issues

The `MSHW0040` is claimed by the `surfacepro3_button` driver.
While this is correct for the Surface Pro 4 (covered by this driver), the ACPI/DSDT code differs between the Surface Pro 4 and the Surface Book 2/Surface Pro (2017).
Thus the existing driver does not work and you may need to unload and/or blacklist its module before loading this one.

In reverse, I have also no idea on how this driver should detect the difference between `MSHW0040` on the Surface Book 2/Surface Pro (2017) and the Surface Pro 4.
If anyone has an idea, please open an issue or send a pull-request.

_TLDR: You might need to unload the `surfacepro3_button` module, i.e. run `sudo modprobe -r surfacepro3_button` before loading this module._
