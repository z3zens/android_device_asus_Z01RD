TWRP device tree for Asus Zenfone 5z

The Asus Zenfone 5z (codenamed _"Z01R"_) are high-end smartphones from Asus.
Asus Zenfone 5z was announced and released in June 2018.

## Device specifications

| Device       | Asus Zenfone 5z                                 |
| -----------: | :---------------------------------------------- |
| SoC          | Qualcomm SDM845 Snapdragon 845                  |
| CPU          | 8x Qualcomm® Kryo™ 385 up to 2.8GHz             |
| GPU          | Adreno 630                                      |
| Memory       | 4GB / 6GB / 8GB RAM (LPDDR4X)                   |
| Shipped Android version | 8.0                                  |
| Storage      | 64GB / 128GB / 256GB UFS 2.1 flash storage      |
| Battery      | Non-removable Li-Po 3300 mAh                    |
| Dimensions   | 153 x 75.7 x 7.9 mm                             |
| Display      | 1080 x 2246 pixels, (18.7:9) 6.2 inch           |
| Rear camera 1 | 12MP, f/1.8 Dual LED flash                     |
| Rear camera 2 | 8MP, f/2.0                                     |
| Front camera | 8MP, 1.12µm, f/2.0 1080p 30 fps video           |

## Device picture

![Asus Zenfone 5z](https://cdn2.gsmarena.com/vv/pics/asus/asus-zenfone-5-ze620kl-5z-zs620kl-1.jpg)


## Kernel

Prebuilt kernel source:
https://github.com/5z-devs/android_kernel_asus_sdm845

## Compile

First download omni-9.0 tree:

```
repo init -u git://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni.git -b twrp-9.0
```
Then add these string to .repo/manifests/remove.xml


Then add these projects to .repo/local_manifests/roomservice.xml (If you don't have it, you can add them to .repo/manifest.xml): 

```xml
<project name="TeamWin/android_device_asus_Z01RD" path="device/asus/Z01RD" remote="github" revision="android-9.0" />
```

Now you can sync your source:

```
repo sync
```

To auotomatic make the twrp installer, you need to import this commit in the build/make path: https://gerrit.omnirom.org/#/c/android_build/+/33182/

Finally execute these:

```
. build/envsetup.sh
export ALLOW_MISSING_DEPENDENCIES=true
export LC_ALL=C
lunch omni_Z01RD-eng
mka adbd recoveryimage 
```
