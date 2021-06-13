# Samsung Galaxy Tab S7+ (WiFi/5G) device tree for PBRP



## Compile

First download pbrp-10.0 tree:

```bash
repo init --depth=1 -u git://github.com/PitchBlackRecoveryProject/manifest_pb.git -b android-10.0
```

Then add these projects to .repo/local_manifests/roomservice.xml (If you don't have it, you can add them to .repo/manifest.xml):

```xml
  <project name="Bush-cat/android_device_samsung_gts7xl-pbrp" path="device/samsung/gts7xl" remote="github" revision="main" />
  <project name="Bush-cat/android_kernel_samsung_sm8250" path="kernel/samsung/sm8250" remote="github" revision="lineage-18.1" />
  <project path="prebuilts/clang/host/linux-x86/clang-proton" name="kdrag0n/proton-clang" remote="github" revision="master" clone-depth="1"/>
```

Now you can sync your source:

```bash
repo sync --force-sync
```

Finally execute these:

```bash
. build/envsetup.sh
export ALLOW_MISSING_DEPENDENCIES=true
export LC_ALL=C
lunch omni_gts7xl-eng 
# there will be lots of PATH errors, ignore them
mka recoveryimage 
```

Kernel Source: https://github.com/Bush-cat/android_kernel_samsung_sm8250

## Credits

Big Thanks to ianmacd and all the people who made the sources for [twrp_gts7xl](https://github.com/ianmacd/twrp_gts7xl), on which this tree is heavily based.