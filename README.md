# SETUP
1. [VIPER 4 ANDROID](https://github.com/AxionAOSP/android_packages_apps_ViPER4AndroidFX)
2. [OIS FIX](https://github.com/Chaitanyakm/device_xiaomi_marble/blob/16.0/properties/system.prop)
3. [MIUI Camera Marble](https://github.com/Chaitanyakm/device_xiaomi_marble/commit/f873761bbb3167a3ff9e4235fd29949f0ab97d9e)
4. [MIUI Camera Garnet](https://github.com/Evolution-X-Devices/device_xiaomi_garnet/commit/8727e2b04e007876604d6e44b22acf8d37e3cd79)
5. [AOSP Surfaceflinger](https://github.com/Evolution-X-Devices/device_xiaomi_garnet/commit/f4a5a26fd2c9b10a852c07968929a4f704a8c464)
6. [Refresh Rate Switch](https://github.com/kleidione/device_xiaomi_garnet/commit/f8edcab091f9d4d1cfca518678845ef376017d40)
7. [KSU Next Installation](https://kernelsu-next.github.io/webpage/pages/installation.html)
8. [FW Navigation Bar](https://github.com/crdroidandroid/android_frameworks_base/commit/b72c91dfd8142632763a8058e8f05b3d6377b2fa)
9. [Settings Navigation Bar](https://github.com/crdroidandroid/android_packages_apps_Settings/commit/94a94f250789ce3189a046bc838837fb31c2bca1)


## VENDOR PROP CHANGES(REPLACE/ADD/REMOVE)
```make
debug.sf.disable_client_composition_cache=0
debug.sf.enable_gl_backpressure=0
debug.sf.frame_rate_multiple_threshold=120
debug.sf.latch_unsignaled=0
debug.sf.enable_adpf_cpu_hint=true
vendor.perf.framepacing.enable=1


# hwui
ro.hwui.render_ahead=5
debug.hwui.use_hint_manager=true
debug.hwui.target_cpu_time_percent=30


REMOVE
vendor.display.override_doze_mode=1
```

## SIGN KEYS
```make
Matrixx - https://github.com/ProjectMatrixx/android_vendor_lineage-priv_keys-template.git
CrDroid - https://github.com/306bobby-android/crDroid-build-signed-script.git

# Sign Keys (device.mk)
-include vendor/lineage-priv/keys/keys.mk

```

## CHANGE DISPLAY DENSITY
```make
400
```

## FLAGS
```make
TARGET_DISABLE_EPPE := true
TARGET_ENABLE_BLUR := true
PRODUCT_NO_CAMERA := true
TARGET_EXCLUDES_AUDIOFX := true
PERF_ANIM_OVERRIDE := true
WITH_GMS := false
TARGET_DISABLE_MATLOG := true
```

## SYSTEM PROP CHANGES(REPLACE/ADD/REMOVE)
```make
# Animation override
persist.sys.activity_anim_perf_override=true
```

## OTHER

**initialize the repo:**
```make
--depth 1 --no-repo-verify -g default,-mips,-darwin,-notdefault
```

**sync repo:**
```make
repo sync -c --no-clone-bundle --no-tags --optimized-fetch --prune --force-sync -j$(nproc --all)
```

**environment setup:**
```make
. build/envsetup.sh
```

**Lunch BP2A**
```make
lunch lineage_marble-bp2a-user
lunch lineage_garnet-bp2a-user
lunch lineage_vayu-bp2a-user
```

**Lunch BP1A**
```make
lunch lineage_marble-bp1a-user
lunch lineage_garnet-bp1a-user
lunch lineage_vayu-bp1a-user
```

**DISABLE RBE**
```make
USE_RBE=false mka bacon -j96
```
