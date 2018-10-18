# libstdc-.-
Xcode 10 (iOS 12) does not contain libstdc++.* 
 
 
libstdc++ was deprecated 5 years ago. Apple’s more recent platforms (tvOS and watchOS) don’t support it.

Support was removed from the iOS 12.0 Simulator runtime, but it remains in the iOS 12.0 (device) runtime for binary compatibility with shipping apps.

You should update your project to use libc++ rather than libstdc++ by setting the CLANG_CXX_LIBRARY build setting (“C++ Standard Library”) to libc++.

If you have any static libraries that depend on libstdc++.tbd, you can workaround it for now by copying the file from the SDKs in Xcode 9.4 (and libstdc++.*.dylib in the iOS simulator runtime), but that is not a long term solution. You should contact the provider of those libraries and request versions built using libc++.

Workaround:

If Xcode 9 is not installed .
```shell
 cd /workspace
 git clone https://github.com/johnsken-jerry/libstdc-.-.git
 cp /workspace/libstdc-.-/libstdc++.* /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS.sdk/usr/lib/

cp /workspace/libstdc-.-/libstdc++.*  /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneSimulator.platform/Developer/SDKs/iPhoneSimulator.sdk/usr/lib/
```
or

You may copy it from old Xcode(9.4). It should work.

```shell
cp /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS.sdk/usr/lib/libstdc++.* /Applications/Xcode-beta.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS.sdk/usr/lib/

cp /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneSimulator.platform/Developer/SDKs/iPhoneSimulator.sdk/usr/lib/libstdc++.* /Applications/Xcode-beta.app/Contents/Developer/Platforms/iPhoneSimulator.platform/Developer/SDKs/iPhoneSimulator.sdk/usr/lib/
```
