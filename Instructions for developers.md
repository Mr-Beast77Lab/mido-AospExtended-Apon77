Requirements:
1. Proper instruction about how to build your ROM as a developer
2. Proper instruction about how to install your ROM as a user.
3. Your repository must be able to understand by anyone without any extra knowledge of before.
4. Use this repository as a standard and change according to your device and ROM
5. Repository name must be like device_code_name-RomName-Builder's_Name (like mido-AospExtended-Apon77)
6. Keep license untouched.

Steps:
Make device tree of Redmi Note 4 compatible with AospExtended by bringup commit https://github.com/Apon77/aex/commit/7b64c1c6cc477ea44e50664e4e9c6739ffcd7054
Sync the AospExtended Source https://github.com/AospExtended
Clone device trees for Redmi Note 4
Change repository of AospExtended if needed by removing and reclonig them, or by using local manifest.
Run the build commands for building AospExtended
`source build/envsetup.sh`
`lunch aosp_mido-user`
`m aex -j$(nproc --all)`
