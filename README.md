# libopus-Android.mk
Android NDK configuration to build [opus](https://github.com/xiph/opus) as shared library.

## How to
1. Clone the opus source code from github (e.g. next to you build.gradle to a folder named `libopus`), using your target opus version (e.g. 1.3.1) : `git clone --branch=v1.3.1 https://github.com/xiph/opus libopus`
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