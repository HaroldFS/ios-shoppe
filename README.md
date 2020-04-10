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

#### Step 1: Adding FullStory.framework to the "Link Binary with Libraries" build phase:

1. In Xcode, select the highest level of your project in the project tree on the left hand side.
2. In the middle pane that opens, find the "Build Phases" tab and click on it.
3. In the tab, locate the line item labeled "Link Binary with Libraries" and click into it.
4. Click the + sign to add a new framework.
5. In the window that appears, click on "Add Other" then click "Add Files".
6. IF YOU INSTALLED VIA COCOAPODS:
   - Browse into your Pods directory > FullStory and select the FullStory.framework folder and click on Open.
7. IF YOU INSTALLED MANUALLY:
   - Browse to where you extracted the FullStory.framework and select it, clicking on Open.

#### Step 2: Add FSOrgId to your Info.plist

1. Click on the "Info" tab (two to the left of Build Phases tab).
2. Hover over an existing item and click on the + sign.
3. In the new blank field, type `FSOrgId` for the Key and press return
4. In the Value field, enter your FS Org Id. In this case, I'm using `PSYET` my test org.

#### Step 3: Add a build phase to ru nFullStory's asset uploading script `FullStoryCommandLine`.

1. Back in the Build Phases tab, click on the + sign in the upper left hand corner.
2. Select "New Run Script Phase", make sure this build phase is below "Copy Bundle Resources"
3. IF YOU INSTALLED VIA COCOAPODS:

   - Type the following into the shell editor:

   `"./Pods/FullStory/tools/FullStoryCommandLine" "${CONFIGURATION_BUILD_DIR}/${WRAPPER_NAME}"`

   - Note, this is a relative path and may need to change based on your pod configuration.

4. IF YOU INSTALLED MANUALLY:
   - Type above subbing out the path to your Fullstory/tools/FullStoryCommandLine file.

#### That's it! You're done :nail_care:

1. Build the app and launch it in an emulator,
2. Play around with the app and and then background it.
3. Grab a frosty beverage and wait for your session to upload to FullStory.

## Using the app

The Shoppe is a super simple e-commerce application. Build and run the app on your emulator, you can:

- Browse a list of products int the _Market_.
- Use the **Add to Cart** button to add products to your shopping cart.
- Go to your _Shopping Cart_ by clicking on the cart icon on the top right corner.

## Tips and tricks

- Checkout our [Native Mobile Privacy Rules](https://help.fullstory.com/hc/en-us/articles/360043356573-Native-Mobile-Privacy-Rules).
- For step by step guide checkout: [Getting Started Guide](https://help.fullstory.com/hc/en-us/articles/360042772333-Getting-Started-with-iOS-Recording).
