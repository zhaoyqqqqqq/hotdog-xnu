# hotdog-xnu

Builds XNU (xnu-8796 / iOS 16 generation) with the ios-sweet + ios-flame patch series
on a GitHub macOS runner, for the OnePlus 7T Pro (hotdog) port.

- `xnu/patches/` : 124 patches (0001-0081 ios-sweet, 0082-0124 flame)
- `.github/workflows/xnu.yml` : builds with MACOS_VERSION=13.5, MACHINE_CONFIG=SWEET, KERNEL_CONFIG=DEVELOPMENT

## Run

Actions -> xnu -> Run workflow (defaults are fine).

Artifact `xnu-kernel` contains `kernel.development.sweet`.

## Downstream

```
tools/make-payload.sh kernel.development.sweet
tools/build-shim-linux.sh build/payload.bin build/shim-hotdog-boot.img
fastboot boot build/shim-hotdog-boot.img
```
