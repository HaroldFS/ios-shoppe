# ios-shoppe-demo

iOS Client for the example "Shoppe" app

The iOS Shoppe Demo is a reference application that provides tips and tricks to using [FullStory](https://www.fullstory.com/) on [Native Mobile](https://www.fullstory.com/mobile-apps/) iOS.

## Getting started

To apply the FullStory iOS Plugin, you'll need [Xcode](https://developer.apple.com/xcode). You'll then download or clone this repo to your desired directory.

1. `git clone https://github.com/rcmaples/ios-shoppe.git`
2. Open Xcode and use either File > Open to open the xcode project file, or use "open another project" from the splash screen and browse to the xcode project file.
3. Test that it works by clicking the "play" button to build the app and run it on an emulator.
4. Once you've verified it works, you can quit Xcode for the time being.

## Adding FullStory to the app

### Cocoapods Installation

Some users utilize a package management system similar to NPM to manage their dependencies. This system is called [Cocoapods](https://cocoapods.org/). To install FullStory using Cocoapods, you'll first need to install it:

Open your terminal and type the following:

`$ sudo gem install cocoapods`

Now, `cd` into the directory that houses your xcodeproj file. Then:

`$ pod init`

This will initialize a Podfile that will be used to installd dependencies (think of it like package.json for NPM/yarn).

Open Podfile and make sure that the line `use_frameworks!` is uncommented and on a line by itself. This is default for a new pod init, but it doesn't hurt to double check.

In the pod file you'll see a commented line, "Pods for ios-shoppe-demo", directly under that line, add the pod specification foer the latest version of FullStory and save your file.

`pod 'FullStory', :http => 'https://ios-releases.fullstory.com/fullstory-1.1.0.tar.gz'`

(1.1.0 at time of writing)

Next, back in the terminal, run:

`$ pod install`

### Completing the FullStory Integration

In Xcode, open the new `.xcworkspace` file. Once cocoapods is integrated into your project, you will no longer be using the xcode project file in xcode. Instead, you'll be working with the workspace file.

## Using the app

The Shoppe is a super simple e-commerce application. Build and run the app on your emulator, you can:

- Browse a list of products int the _Market_.
- Use the **Add to Cart** button to add products to your shopping cart.
- Go to your _Shopping Cart_ by clicking on the cart icon on the top right corner.

## Tips and tricks

- Checkout our [Native Mobile Privacy Rules](https://help.fullstory.com/hc/en-us/articles/360043356573-Native-Mobile-Privacy-Rules).
- For step by step guide checkout: [Getting Started Guide](https://help.fullstory.com/hc/en-us/articles/360042772333-Getting-Started-with-iOS-Recording).
