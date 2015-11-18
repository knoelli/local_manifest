CM13-Y300 Local Manifest
========================

Local Manifest to build CM13 for the Huawei Y300/G510/G330

Build Instructions
-----------------------------------------------------------------------------

1. Initialize repo using the Cyanogenmod 13 manifest
    
        repo init -u git://github.com/CyanogenMod/android.git -b cm-13.0

2. Add my local manifest

        mkdir .repo/local_manifests
        Copy cm13_huawei.xml to .repo/local_manifests

3. Then sync up the repositories
 
        repo sync

4. Cherry-pick required commits from gerrit

        Use repopick to cherry-pick each commit listed in CHERRIES.md in the specified order
		./build/tools/repopick.py {COMMIT_ID}
		

5. Initialize the build environment and apply patches

        source build/envsetup.sh
    
6. Build the ROM

        For Y300:
            brunch u8833


Current Status
-----------------------------------------------------------------------------

### Working so far:

* It boots successfully, display works, touchscreen & buttons all work ok
* GPS
* Wifi
* Bluetooth
* Audio
* Video playback (software decoding)
* External SD Card - Set as primary storage by default
* Phone/Data - Needs testing! Rild & libril now built from source using custom libril based on CM13 hardware/ril-caf with a [commit][1] from @LegacyHuawei.
* Camera

All of the above need a lot more testing but basically works. Wifi is probably unstable just as in LP.

### Not Working:

* Internal SD Card - Marshmallow sdcard handling is completely different - Internal SD is not used. Mount directly in fstab?
* Video playback (hardware decoding)
* FM Radio

[1]: https://github.com/LegacyHuawei/android_device_huawei_u8860/commit/63474ebe2e33a6fb7ae39f778940b30f9efe917c