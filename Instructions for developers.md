## Requirements:
##### 1. Proper instruction about how to build your ROM as a developer
##### 2. Proper instruction about how to install your ROM as a user.
##### 3. Your repository must be able to understand by anyone without any extra knowledge of before.
##### 4. Use this repository as a standard and change according to your device and ROM
##### 5. Repository name must be like device_code_name-RomName-Builder's_Name (like mido-AospExtended-Apon77)
##### 6. Keep license untouched.

## Notes:
##### 1. We will auto create a folder according to your repository name. So, no need to create folder again. ROM source will be synced at /tmp/mido/AospExtended/Apon77
##### 2. We have already setup build environment. So no need to setup build environment. 
##### 3. We also use ccache automatically. So no need to use ccache from your side.
##### 4. Just sync sources, run build commands and upload. That's it.

## Steps:
##### 1. Make device tree of Redmi Note 4 compatible with AospExtended by [bringup commit](https://github.com/Apon77/aex/commit/7b64c1c6cc477ea44e50664e4e9c6739ffcd7054)
##### 2. Initialize the AospExtended Source

`repo init --depth=1 -u git://github.com/AospExtended/manifest.git -b 11.x`

##### 3. Change repository of AospExtended if needed by removing and reclonig them, or by using [local manifest](https://forum.xda-developers.com/t/learn-about-the-repo-tool-manifests-and-local-manifests-and-5-important-tips.2329228/).

You can also clone device tree, common device tree, kernel tree, vendor tree by local manifist too.

`git clone https://github.com/Apon77Lab/android_.repo_local_manifests.git --depth 1 -b aex .repo/local_manifests`

##### 4. Sync the source.

`repo sync -c --no-clone-bundle --no-tags --optimized-fetch --prune --force-sync -j8`

##### 5. Clone device tree, common device tree (if exists), kernel tree and vendor tree for Redmi Note 4 to specific folder. Where to clone trees is told inside BoardConfig.mk file.

We need to clone device tree in device/xiaomi/mido said in [here](https://github.com/Apon77/aex/blob/aex/BoardConfig.mk#L17).

We need to clone kernel tree in kernel/xiaomi/mido said in [here](https://github.com/Apon77/aex/blob/aex/BoardConfig.mk#L48).

We need to clone vendor tree in vendor/xiaomi said in [here](https://github.com/Apon77/aex/blob/aex/BoardConfig.mk#L167).

We don't need to clone common device tree, because not said anywhere in [Boardconfig.mk](https://github.com/Apon77/aex/blob/aex/BoardConfig.mk)

```
git clone -b aex https://github.com/Apon77/aex device/xiaomi/mido --depth=1
git clone -b aex https://github.com/Apon77/aexk kernel/xiaomi/mido --depth=1
git clone -b aex https://github.com/Apon77/aexv vendor/xiaomi --depth=1
```

If you used local manifest to clone these trees, you must skip cloning these trees in this step.

##### 6. Run the build commands for building AospExtended

```
source build/envsetup.sh
lunch aosp_mido-user
m aex -j$(nproc --all)
```

##### 7. Upload the output zip file (AospExtended-8.0-mido*.zip) to a safe place
```
up(){
	curl --upload-file $1 https://transfer.sh/$(basename $1); echo
	# 14 days, 10 GB limit
}

up out/target/product/mido/*.zip
```
##### 8. All these steps should be inside build_rom.sh script like [this](https://github.com/Mr-Beast77Lab/mido-AospExtended-Apon77/blob/main/build_rom.sh).
##### 8. Share the links in your community and inside this repository (in [Instruction for users.md](https://github.com/Mr-Beast77Lab/mido-AospExtended-Apon77/blob/main/Instructions%20for%20users.md#1-download-latest-rom-zip-file) file). People should be able to download your ROM if they visit this repository.
##### 9. If you want to update you device, kernel or vendor trees and learn more how to build ROMS and modify it according to your need, please check these links and search in google for more information.
https://github.com/AliHasan7671/guides/commit/33361bb2c78af01426350ef21167d742f44481fd
https://github.com/nathanchance/Android-Tools/blob/master/Guides/Building_AOSP.txt


