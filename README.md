Welcome to the Cyanogen Theme Template! This guide will explain how to create a basic theme project, import your art, and compile an installable theme file ready for submission. We’re excited to see what you create, so let’s go!

## Things You’ll Need ##

*  <b>Android Studio</b><br>
Android Studio is a Google-distributed program that will allow us to organize and build the theme itself. Set it up on your computer by [following these instructions](http://developer.android.com/sdk/installing/studio.html).
*  <b>Image Editing Software of your choice (Illustrator, Photoshop, GIMP, etc.)</b><br>
You’ll use this to create your theme assets. Any software akin to those above will work.

*  <b>Theme Template Files</b><br>
The template includes the project we’ll use to create a theme in Android Studio and a set of example assets in each folder you can use as a base for your theme. We suggest that you grab the template files before beginning. [Download the template sample files here](https://github.com/cyngn/android_packages_themes_Template).

## Exploring the Theme Template ##

Opening the template zip file will get you two things:

The project we’ll use to create the theme in Android Studio
An /example/ resource folder with example assets to use as guides in creating your theme

Below is a visual representation of the resource folder. This is also the same structure used in the Android Studio project.

![resource tree](http://cdn.cyngn.com/g/themes_template_instructions/resource_tree.png)

#### alarms / ringtones / notifications ####

These folders contain a single sound file for each type of alert. These can be MP3 or OGG files.

#### lockscreen / wallpaper ####

These folders contain a single image file used for the lockscreen and homescreen backgrounds. These can be PNG or JPG files. Note: If a lockscreen wallpaper isn’t included, the wallpaper will show instead.

#### overlays ####

The bulk of your theme will live in folders here.

- <b>android</b> includes system assets like backgrounds for action bars, check boxes, radio buttons, switches, sliders, and more.
- <b>com.android.systemui</b> contains assets used to build the navigation bar, status bar, notification shade, and quick settings.
- <b>common</b> is a folder advanced theme builders use to share a set of assets between apps. For example, a builder could include an app drawer icon for multiple launcher apps. These assets are then connected with XML as found in launcher3’s drawable folder.
- <b>Other apps</b> on the device can be themed and are represented by their package name. The template includes folders for contacts, email, dialer, lockscreen (keyguard), messaging, and settings.

#### fonts ####

This folder contains fonts used in the theme and the XML file which tells the theme how to use them.

#### icons ####

This is where your icon pack is housed. It also contains the XML file that tells the theme which icon goes with which app. Intermediate builders can also include a backplate for unthemed apps and scale those apps’ icons to match your pack’s style.

#### bootanimation ####

This folder includes the zip file created for your boot animation. The creation of a boot animation is covered in the boot animation section.


#### res ####

While not in the assets folder, res holds your theme’s app icon which is seen when sideloading your theme and in the apps section of your device’s settings.

---

Note: While this may seem like a lot of work, keep in mind that you don’t have to theme <i>everything</i> in these folders. When you create your theme, <i>you only need to include the pieces you want to change</i>. You’re also free to include more than what the template includes as well, such as adding more apps to overlays.

### Planning Your Theme ###

After exploring the theme template, it’s best to plan what you want your theme to look like and how far you want to take the look. If this is your first theme, we recommend starting with a basic project that includes a wallpaper, changes the majority of /systemui/, and the basic controls in /android/. If you want to go a little further, create a basic icon pack and build out more of /android/.

Once you have your idea and a plan of attack, you’ll need to identify what to change. There are a few types of things you’ll encounter as you create your theme:

#### Density Buckets ####

Density buckets let devices of different screen size and resolution correctly display your theme. Folders like these:
* drawable-mdpi (~360p screens)
* drawable-hdpi (~480p screens
* drawable-xhdpi (~720p screens)
* drawable-xxhdpi (~1080p screens)

contain the same set of assets but in different sizes. More information on density buckets, DP, and PPI is available [in this designer-focused guide](http://www.google.com/url?q=http%3A%2F%2Fsebastien-gabriel.com%2Fdesigners-guide-to-dpi%2Fhome%23android&sa=D&sntz=1&usg=AFQjCNGZV6e1HsPw-Cs1F1O15-dajenAzQ). It’s important to include at least the bottom three in this list to properly support a wide variety of devices.

#### Standard Assets ####

These are basic image files like wallpapers and icons. They are typically saved in .png format.

#### 9-Patches ####

9-patches are image files that stretch to fit the space they reside in or to fit content that appears in them. They are typically used for assets like backgrounds, buttons, and shades that need to be dynamic based on context. More explanation on 9-patches can be found [in this guide](http://www.google.com/url?q=http%3A%2F%2Fsebastien-gabriel.com%2Fdesigners-guide-to-dpi%2Fhome%23strechable&sa=D&sntz=1&usg=AFQjCNGxgD0nA7bx2--Lylm6dnDaO6AbfA). You can build a 9-patch in the image editing software of your choice but there are other tools available like [Roman Nurik’s generator](http://www.google.com/url?q=http%3A%2F%2Fromannurik.github.io%2FAndroidAssetStudio%2Fnine-patches.html&sa=D&sntz=1&usg=AFQjCNEojHk293ieYSRqL1tF35S7SxttrQ) that provide a simple interface with previews and scaling support.

#### XML ####

XML files are simple text files that include specifications like colors, sizes, and fonts for objects that don’t necessarily have an image asset to represent them. For instance, the color and font of the large clock in the open notification shade is controlled by XML. As you get more comfortable with building themes, XML can provide you with a lot more control and customization than what you’d get from merely creating standard assets.

### Building Your Theme ###

Now that you know what kinds of files make up a theme, it’s time to start making some. Here are a few pointers to consider:

#### Create Your Folders ####

As you can see from the resource folder, managing an theme can be a little convoluted. We recommend creating a folder structure identical to the template that contains the areas you plan to theme. You should also plan a place for your Android Studio project. Move the template there so you have a clean area once you’re ready to compile the theme.

#### Choose a Density ####

As we discussed earlier, it’s important to support multiple density buckets so your theme can run on as many devices as possible. All these buckets are created from a source size, however, so start with one and create the others from it. If your theme’s aesthetic is simple and clean, starting at MDPI size with vector shapes and scaling up is recommended. Conversely, if your theme is highly detailed, starting at XXHDPI (or XXXHDPI for icon packs) is recommended and then scaling down for the rest.



#### Focus on a Folder ####

Many assets are used together or have different states. For this reason, you should focus on one folder at a time and under that a group of similar assets at a time. For example, if you’re working on the /systemui/ folder, focus on the status bar icons as a whole before moving onto the quick settings icons. This will help you keep them consistent between each other.

#### Mind the Specs ####

Most assets live as an object in their space; a 32x32dp icon may be a 28x28dp glyph with transparent padding around it. Unless you’re an advanced theme builder going for a specific look, make sure your themed assets fit inside the source asset’s dimensions and then fit reasonably with the size of content inside them. The same goes for constructing 9-patches.

#### Name with Care ####

Themes work by comparing the files in the system to the files in the theme. If an asset’s filename doesn’t match the system asset you intended it to replace, it won’t apply. It is therefore essential to check and recheck your assets’ filenames against the default. Use the template’s resource folder assets as a guide.

Naming for icon packs are slightly different. The app icons can be named anything. The XML file contained with them, however, must reference two things correctly to work. First, the name of each icon you create. Second, the target app’s package name (and more specifically, the app’s launcher activity if your custom icon shows up in places it shouldn’t).

![Name with Care](http://cdn.cyngn.com/g/themes_template_instructions/name_with_care.png)

### Special: Creating a Boot Animation ###

Boot animations are png sequences that play when your device is starting up. They make fun additions to themes but are built a little differently from other components. Here’s how:

#### Things You’ll Need ####

* Archive manager (Archiver, winzip, winrar, 7zip, etc.)

Boot animations are created with two pieces, the sequence itself and a text file that tells the system how to play it.

#### Step 1: Prep the folders ####

If you open the template resource folder and navigate to /bootanimation/ you will see a zip file containing a boot animation sample. Inside that is the follow structure:

![boot animation tree](http://cdn.cyngn.com/g/themes_template_instructions/bootanim_tree.png)

Each “partX” folder contains a section of the total animation sequence. For instance, the template animation has two parts: the first part (in /part0/) is the introduction and the second part (in /part1/) is the rest of the animation which loops until the device is fully booted.

The “desc.txt” file tells the device how to play the animation. Each value is separated by a single space. Below is the text file’s breakdown:

![Text File Breakdown](http://cdn.cyngn.com/g/themes_template_instructions/text_file_breakdown.png)

* Frame dimensions: These designate the width and height of the frames in the animation.
* Sequence frame rate: The frames-per-second (FPS) of the animation.
* Line markers: They tell the device how many parts there are in the animation. “p” is the default marker to use but you can also use a “c” which tells the device to finish animation before finishing boot (normally the animation cuts to the lockscreen when the device is ready). This gets you a nice complete animation on a looped part or if you want a part to play specifically at the end.
* Part loop count: This number tells the device how many times to loop a part of the animation before moving to the next one. Using a zero will make the part loop until the device is booted.
* Pause Length: This number tells the device how many seconds to wait before looping the part over (if it was so desired in the part loop count) or continuing to the next part.
* Line label: This tells the system which folder to pull frames from for a specific part. Parts should always be in consecutive order.

Once you know how you want to build your animation, create your /partX/ folders and your desc.txt file.

#### Step 2: Create your animation ####

Use whatever image creation program you have to build a sequence of images for your animation. Keep in mind the frames’ dimensions should be uniform and reflected in the “desc.txt” file. Follow the frame naming conventions shown in the template. It’s also worth noting that if your animation doesn’t require the whole screen, you can do as the template frames do and use a box area to save on file size.

#### Step 3: Pack it up ####

Once your animation is in your /partX/ folders and you’ve properly set up your “desc.txt” file, open or drag them into your archiving software to build a bootanimation.zip file. Make sure to select “STORE” or “No compression” in the options or the wizard used. When you have your compression-less zip file built, drop it in your /bootanimation/ folder.

### Packaging Your Theme ###

#### Step 1: Download and install Java Developer Kit and Android Studio ####

Android Studio requires Java 7 to run so you will need to make sure you have java installed before proceeding. [Download](http://www.google.com/url?q=http%3A%2F%2Fwww.oracle.com%2Ftechnetwork%2Fjava%2Fjavase%2Fdownloads%2Fjdk7-downloads-1880260.html&sa=D&sntz=1&usg=AFQjCNGPxpxpgEownqglhYEJoVh3Dos3RQ) and install JDK 7 and make note of its installation location. Android Studio will ask for this path once you import the theme template. Once the JDK is installed you will need to [download and install Android Studio](https://www.google.com/url?q=https%3A%2F%2Fdeveloper.android.com%2Fsdk%2Finstalling%2Fstudio.html), making sure you meet the system requirements listed on the Android Studio page prior to downloading. After installing Android Studio you will need to add an SDK by following [these instructions](https://www.google.com/url?q=http%3A%2F%2Fdeveloper.android.com%2Fsdk%2Finstalling%2Fadding-packages.html). <i>Make note of the location that the SDK is installed to as this will be needed once you import the theme template</i>.

#### Step 2: Import the theme template ####

Now that you have Android Studio installed and the theme template downloaded and extracted, you will need to import this project into Android Studio. If this is your first time running Android Studio, you should be presented with the <b><i>Welcome to Android Studio</i></b> welcome screen.

![Welcome Android Studio](http://cdn.cyngn.com/g/themes_template_instructions/welcome_android_studio.png)

If Android Studio opens up to an existing project, simply close the project from <b>File -> Close Project</b>.

From the <i>Welcome to Android Studio</i> screen, select <b><i>Import Project</i></b>. Navigate to where you extracted the theme template and once that folder is selected choose <b><i>OK</i></b>.

![Import Project](http://cdn.cyngn.com/g/themes_template_instructions/import_project.png)

Once the project is imported you may receive an error stating that it <b><i>Failed to sync Gradle project</i></b>. If you get this message, simply click on <b><i>Fix plug-in version and re-import project</i></b>.

![Fix Plugin](http://cdn.cyngn.com/g/themes_template_instructions/fix_plugin.png)

#### Step 3: Create your theme ####

Now that your project is ready to go, we’ll need to add theme details and import the assets you’ve made into the project.

Check out the project tree on the side of the window:

![Side Project Tree](http://cdn.cyngn.com/g/themes_template_instructions/side_project_tree.png)

/theme/src/main/ is the heart of the project and where we’ll be focusing our time. /assets/ is where your assets will be living. /res/ is where your theme’s app icon will go, and AndroidManifest.xml is where you will define your theme’s identity. /assets/ and /res/ are structured exactly like the example resource section, making importing simple.

Double-click on the build.gradle in the <b>theme</b> directory and you’ll see a colored text file appear in the content area of the window.

![build.gradle](http://cdn.cyngn.com/g/themes_template_instructions/theme_build_gradle.png)

The applicationId is a unique identifier for your theme, also known as the <b><i>package name</i></b>. Pick a package name and set it here, making sure to follow standard conventions [shown here](https://www.google.com/url?q=https%3A%2F%2Fdocs.oracle.com%2Fjavase%2Ftutorial%2Fjava%2Fpackage%2Fnamingpkgs.html&sa=D&sntz=1&usg=AFQjCNFWB_NXsKYz_21rdPtVcMnRMAoQMA). A simple convention could be to use <b><i>your_name.theme_name</i></b> (underscores not necessary) as the package name.

You will also want to change the package name in the AndroidManifest.xml.  Double-click on AndroidManifest and you’ll see a colored text file appear in the content area of the window.

![Manifest](http://cdn.cyngn.com/g/themes_template_instructions/manifest.png)

Moving to /res/values/, open the strings.xml file. Inside you’ll see two bits of text between chevrons. The theme_name string is where you set your theme’s name. Theme_author is your name or DBA. Be sure to check for spelling and grammar as these will be used by the system to title your theme.

Once that’s set it’s time to import your assets. Drag your created folders and files into the relevant /main/assets/ folder in the project tree. Your app icon goes in the density bucket folders in /res/. If Android Studio asks about non-project files, allow them through. You’ll now see your items in the tree. You can also check them by moving to the template on your computer and exploring the folders shown in the tree there.

#### Step 4: Build and test ####

Android Studio makes it easy to quickly build and test your theme on your device. First, make sure your device is plugged in to a USB port on your computer. Second, verify that adb is working correctly with the device that you plugged in. See this guide for more information on setting up and troubleshooting ADB.

Now that your device is plugged in and ready to go, simply press the green play button located in the toolbar.

![Play Button](http://cdn.cyngn.com/g/themes_template_instructions/play_button.png)

At this point you should be presented with a dialog box to configure how to run the APK produced by Android Studio. Make sure that you select <b><i>Do not launch Activity</i></b> under the <b>Activity</b> group and <b><i>Show chooser dialog</i></b> for <b>Target Device</b>. Finally click <b><i>Run</i></b> and then choose your device from the <b>Choose Device</b> dialog.

#### Step 5: Signing your theme APK for release ####

Once you are ready to release your theme for the public to enjoy, you will need to generate a signed APK which can then be installed on other devices. Fortunately Android Studio makes this an easy task. Follow [this guide](http://developer.android.com/tools/publishing/app-signing.html#studio) on generating a signed APK from Android Studio.

### Additional Recommendations ###

Once you have your theme installed and applied, it’s important to TEST IT. Explore your phone and make sure everything you created is working as intended. If you have access to multiple device screen resolutions, we recommend trying it on them as well to confirm each bucket of assets appear correctly.

[Theme Debugger](https://www.google.com/url?q=https%3A%2F%2Fplay.google.com%2Fstore%2Fapps%2Fdetails%3Fid%3Dcom.steel89ita.themedebugger) is a great tool to quickly see many of the framework assets.
