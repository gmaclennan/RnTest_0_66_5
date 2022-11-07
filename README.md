## `react-native-v8` bug reproduction

This repo is a minimal reproduction of an issue with `react-native-v8@1.5.2` with `react-native@0.65.5`. This app was created by:

  1. `npx react-native init RnTest_0_66_5 --version 0.66.5`
  2. Following the install steps from [kudo/react-native-v8/README.md](https://github.com/Kudo/react-native-v8/blob/4821e303cf18d745d884510740a45a449afc1ec6/README.md)

Running `npx react-native run-android` results in the following output:

```
❯ npx react-native run-android
info Running jetifier to migrate libraries to AndroidX. You can disable it using "--no-jetifier" flag.
Jetifier found 879 file(s) to forward-jetify. Using 16 workers...
info JS server already running.
info Installing the app...

> Configure project :react-native-v8
WARNING:: Mapping new ns http://schemas.android.com/repository/android/common/02 to old ns http://schemas.android.com/repository/android/common/01
Mapping new ns http://schemas.android.com/repository/android/common/02 to old ns http://schemas.android.com/repository/android/common/01
WARNING:: Mapping new ns http://schemas.android.com/repository/android/generic/02 to old ns http://schemas.android.com/repository/android/generic/01
Mapping new ns http://schemas.android.com/repository/android/generic/02 to old ns http://schemas.android.com/repository/android/generic/01
WARNING:: Mapping new ns http://schemas.android.com/sdk/android/repo/addon2/02 to old ns http://schemas.android.com/sdk/android/repo/addon2/01
Mapping new ns http://schemas.android.com/sdk/android/repo/addon2/02 to old ns http://schemas.android.com/sdk/android/repo/addon2/01
WARNING:: Mapping new ns http://schemas.android.com/sdk/android/repo/addon2/03 to old ns http://schemas.android.com/sdk/android/repo/addon2/01
Mapping new ns http://schemas.android.com/sdk/android/repo/addon2/03 to old ns http://schemas.android.com/sdk/android/repo/addon2/01
WARNING:: Mapping new ns http://schemas.android.com/sdk/android/repo/repository2/02 to old ns http://schemas.android.com/sdk/android/repo/repository2/01
Mapping new ns http://schemas.android.com/sdk/android/repo/repository2/02 to old ns http://schemas.android.com/sdk/android/repo/repository2/01
WARNING:: Mapping new ns http://schemas.android.com/sdk/android/repo/repository2/03 to old ns http://schemas.android.com/sdk/android/repo/repository2/01
Mapping new ns http://schemas.android.com/sdk/android/repo/repository2/03 to old ns http://schemas.android.com/sdk/android/repo/repository2/01
WARNING:: Mapping new ns http://schemas.android.com/sdk/android/repo/sys-img2/03 to old ns http://schemas.android.com/sdk/android/repo/sys-img2/01
Mapping new ns http://schemas.android.com/sdk/android/repo/sys-img2/03 to old ns http://schemas.android.com/sdk/android/repo/sys-img2/01
WARNING:: Mapping new ns http://schemas.android.com/sdk/android/repo/sys-img2/02 to old ns http://schemas.android.com/sdk/android/repo/sys-img2/01
Mapping new ns http://schemas.android.com/sdk/android/repo/sys-img2/02 to old ns http://schemas.android.com/sdk/android/repo/sys-img2/01
WARNING:: unexpected element (uri:"", local:"base-extension"). Expected elements are <{}codename>,<{}layoutlib>,<{}api-level>
unexpected element (uri:"", local:"base-extension"). Expected elements are <{}codename>,<{}layoutlib>,<{}api-level>

> Task :react-native-v8:downloadBoost
Download https://github.com/react-native-community/boost-for-react-native/releases/download/v1.63.0-0/boost_1_63_0.tar.gz

> Task :react-native-v8:downloadDoubleConversion
Download https://github.com/google/double-conversion/archive/v1.1.6.tar.gz

> Task :react-native-v8:downloadFolly
Download https://github.com/facebook/folly/archive/v2021.06.28.00.tar.gz

> Task :react-native-v8:downloadGlog
Download https://github.com/google/glog/archive/v0.3.5.tar.gz

> Task :react-native-v8:generateJsonModelDebug FAILED
39 actionable tasks: 31 executed, 8 up-to-date

FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':react-native-v8:generateJsonModelDebug'.
> ./node_modules/react-native-v8/android/CMakeLists.txt : C/C++ debug|armeabi-v7a : CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
  Please set them or make sure they are set and tested correctly in the CMake files:
  RUNTIMEEXECUTOR_LIB
      linked by target "v8executor" in directory ./node_modules/react-native-v8/android

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. Run with --scan to get full insights.

* Get more help at https://help.gradle.org

BUILD FAILED in 53s

error Failed to install the app. Make sure you have the Android development environment set up: https://reactnative.dev/docs/environment-setup.
Error: Command failed: ./gradlew app:installDebug -PreactNativeDevServerPort=8081

FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':react-native-v8:generateJsonModelDebug'.
> ./node_modules/react-native-v8/android/CMakeLists.txt : C/C++ debug|armeabi-v7a : CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
  Please set them or make sure they are set and tested correctly in the CMake files:
  RUNTIMEEXECUTOR_LIB
      linked by target "v8executor" in directory ./node_modules/react-native-v8/android

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. Run with --scan to get full insights.

* Get more help at https://help.gradle.org

BUILD FAILED in 53s

    at makeError (./node_modules/execa/index.js:174:9)
    at ./node_modules/execa/index.js:278:16
    at processTicksAndRejections (node:internal/process/task_queues:96:5)
    at async runOnAllDevices (./node_modules/@react-native-community/cli-platform-android/build/commands/runAndroid/runOnAllDevices.js:109:5)
    at async Command.handleAction (./node_modules/@react-native-community/cli/build/index.js:192:9)
info Run CLI with --verbose flag for more details.

```
