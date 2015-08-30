DKCamera
=======================

 [![Build Status](https://secure.travis-ci.org/zhangao0086/DKCamera.svg)](http://travis-ci.org/zhangao0086/DKCamera) [![Version Status](http://img.shields.io/cocoapods/v/DKCamera.png)][docsLink] [![license MIT](http://img.shields.io/badge/license-MIT-orange.png)][mitLink]
<img width="50%" height="50%" src="https://raw.githubusercontent.com/zhangao0086/DKImagePickerController/develop/Screenshot1.png" /><img width="50%" height="50%" src="https://raw.githubusercontent.com/zhangao0086/DKImagePickerController/develop/Screenshot2.png" />
---
<img width="50%" height="50%" src="https://raw.githubusercontent.com/zhangao0086/DKImagePickerController/develop/Screenshot3.png" /><img width="50%" height="50%" src="https://raw.githubusercontent.com/zhangao0086/DKImagePickerController/develop/Screenshot4.png" />
---
<img width="50%" height="50%" src="https://raw.githubusercontent.com/zhangao0086/DKImagePickerController/develop/Screenshot5.png" /><img width="50%" height="50%" src="https://raw.githubusercontent.com/zhangao0086/DKImagePickerController/develop/Screenshot6.png" />
---
<img width="50%" height="50%" src="https://raw.githubusercontent.com/zhangao0086/DKImagePickerController/develop/Screenshot7.png" /><img width="50%" height="50%" src="https://raw.githubusercontent.com/zhangao0086/DKImagePickerController/develop/Screenshot8.png" />
---


Update for Xcode 6.4 with Swift 1.2
---
## Description
New version! It's A Facebook style Image Picker Controller by Swift.  

## Requirements
* iOS 7.1+
* ARC

## Installation
#### iOS 8 and newer
DKImagePickerController is available on Cocoapods. Simply add the following line to your podfile:

```ruby
# For latest release in cocoapods
pod 'DKImagePickerController'
```

#### iOS 7.x
To use Swift libraries on apps that support iOS 7, you must manually copy the files into your application project.
[iOS 7.x](https://github.com/CocoaPods/blog.cocoapods.org/commit/6933ae5ccfc1e0b39dd23f4ec67d7a083975836d)

## Getting Started
#### Initialization and presentation
```swift

let pickerController = DKImagePickerController()

pickerController.didCancelled = { () in
    println("didCancelled")
}

pickerController.didSelectedAssets = { [unowned self] (assets: [DKAsset]) in
    println("didSelectedAssets")
    println(assets)
}

self.presentViewController(pickerController, animated: true) {}

````

#### Customizing

```swift
/// The maximum count of assets which the user will be able to select.
public var maxSelectableCount = 999

/// The type of picker interface to be displayed by the controller.
public var assetType = DKImagePickerControllerAssetType.allAssets

/// Whether allows to select photos and videos at the same time.
public var allowMultipleType = true

/// The callback block is executed when user pressed the select button.
public var didSelectedAssets: ((assets: [DKAsset]) -> Void)?

/// The callback block is executed when user pressed the cancel button.
public var didCancelled: (() -> Void)?

/// It will have selected the specific assets.
public var defaultSelectedAssets: [DKAsset]? {
    didSet {
        if let defaultSelectedAssets = self.defaultSelectedAssets {
            for (index, asset) in enumerate(defaultSelectedAssets) {
                if asset.isFromCamera {
                    self.defaultSelectedAssets!.removeAtIndex(index)
                }
            }
            
            self.selectedAssets = defaultSelectedAssets
            self.updateDoneButtonTitle()
        }
    }
}
```

## Localization
It has been supported languages so far:

* en.lproj
* zh-Hans.lproj

If you want to add new language, pull request or issue!

## Soon to do

* Simply to take a picture!
* It can hide the camera.
* Simple photo browser.

---
Any pull requests to be welcome!!!

[docsLink]:http://cocoadocs.org/docsets/DKCamera
[mitLink]:http://opensource.org/licenses/MIT
