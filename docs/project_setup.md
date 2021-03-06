# Project Setup

## Prerequisites

In order to follow this guide, you must have the following software installed on or downloaded to your system:

- iOS 7.* SDK (or newer)
- Xcode 6.*
- Print.IO SDK

For the latest versions, please visit [Apple's iOS Dev Center](http://developer.apple.com/devcenter/ios/).

You must be using the latest version of Apple's LLVM compiler. You should not have a problem if you're using a fresh install of Xcode 5.x, which uses this compiler by default. However, if you are working on an older project, or have upgraded from an older version of Xcode, make sure you're not using GCC.

The minimum iOS version supported by the SDK is iOS 6.1. The main reasons for this requirement are our use of ARC ([Automatic Reference Counting](http://developer.apple.com/library/ios/#releasenotes/ObjectiveC/RN-TransitioningToARC/Introduction/Introduction.html)) and our reliance on a number of Apple frameworks and libraries which require iOS 6.1.


# Configuration

In order to use the SDK in an existing app, you must do the following:

## 1. Add files

Copy the `PrintIO.framework` and `PrintIOBundle.bundle` files into your project (select "Create groups for any added folders" if needed). The PrintIO Framework is a universal binary for use on iOS device and simulator architectures (armv7, arm7s, arm64 and i386).

## 2. Link with frameworks

The Print.io SDK depends on some frameworks, so you'll need to add them to any target's "Link Binary With Libraries" Build Phase.  Make sure your app is being linked against all the following libraries:

- AVFoundation.framework
- AudioToolbox.framework
- CoreMedia.framework
- CoreLocation.framework
- Foundation.framework
- libxml2.dylib
- libsqlite3.dylib
- PrintIO.framework
- UIKit.framework


## 3. Copy bundle resources

Make sure `PrintIOBundle.bundle` is included in your target's "Copy Bundle Resources" build phase.

![Make sure our bundle is included in the build phase](https://github.com/printdotio/printio-ios-sdk/blob/gh-pages/images/screenshot_copy_bundle_resources.png?raw=true)


## 4. Add other linker flags

Update your target's (or project's) build settings to include the following "Other Linker Flags:"

- -ObjC
- -lstdc++
- -lc++

![Update your linker flags accordingly](https://github.com/printdotio/printio-ios-sdk/blob/gh-pages/images/screenshot_linker_flags.png?raw=true)


## 5. Import headers

Include the following line to make the SDK available to your code:

    #import <PrintIO/PrintIO.h>

To launch the PrintIO widget, create and display an instance of PrintIO, look at [Basic Usage](https://github.com/printdotio/printio-ios-sdk/blob/master/docs/quick_start_sample_code.md).
