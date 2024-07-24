# libopus-Android.mk
Android NDK configuration to build [opus](https://github.com/xiph/opus) as shared library.

## How to
1. Clone the opus source code from github (e.g. next to you build.gradle to a folder named `libopus`), using your target opus version (e.g. 1.5.2): `git clone --branch=v1.5.2 https://github.com/xiph/opus libopus`
2. Place the `convert_android_asm.sh` from this repo into the opus root folder and run it from there: `./convert_android_asm.sh`
3. Place the `Android.mk` somewhere (e.g. next to your build.gradle), edit the `LOCAL_OPUS_VERSION` to match your version number and let `LOCAL_PATH` point to the opus root folder.
4. Enable the native build instructions in gradle:
	Add this to the `android` section of your build.gradle file:
	```
	externalNativeBuild {
        ndkBuild{
            path "Android.mk"
        }
    }
	```
	Keep in mind that you may need to edit the path if you placed the `Android.mk` somewhere else in step 3.

## About the Android.mk
The `Android.mk` is based on the [`Android.bp`](https://android.googlesource.com/platform/external/libopus/+/5ba9953ee4045966d61fe4b65a307fb80679bbd8/Android.bp) from the Android OpenSource Project. Currently, opus 1.5.2 is targeted. Also, arm neon optimizations are always on, since
> [The OS has been neon-only for many years now](https://android.googlesource.com/platform/external/libopus/+/563d9f467ca9381e21ad5c432709b81ccf93b080)