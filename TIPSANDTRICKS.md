The goal of the theme template is to provide a comprehensive base for new and veteran themers alike. The overall design of the template's theme will match the system theme on the current version of Cyanogen. Community themers are encouraged to not only use this as a jump off point, but to actively help improve the template by submitting enhancements or new overlays that improve the coverage.

### Best Practices ###

When contributing new (or adding to) styles to the template, make sure to adhere to some basic rules:

*  <b>Whitespace</b><br>
Make sure that XML is clear of unnecessary whitespaces and does not use tab indentation. CyanogenMod standard indentation is 4 spaces.

*  <b>Proper Naming</b><br>
Make sure that assets are added with the correct names or follow our proposed naming scheme.

*  <b>Use of Common Overlay</b><br>
Cyanogen themes can make use of the common folder to reference values and styles that might be used across multiple overlays. By collecting all of this information into the common overlay, themes are easier to edit in the future and reduce size by not duplicating resources repeatedly.

*  <b>Copyright</b><br>
Make sure to include the [CyanogenMod copyright](#copyright) header in XML files.

*  <b>Overlay Coverage</b><br>
Check your overlay thoroughly and make sure that you haven't changed any values incorrectly or caused readability issues.

*  <b>Add Comments</b><br>
Add comments to style and color XMLs that explains what the values will be affecting if not immediately apparent.

### Tips & Tricks ###

*  <b>[Theme Debugger](https://www.google.com/url?q=https%3A%2F%2Fplay.google.com%2Fstore%2Fapps%2Fdetails%3Fid%3Dcom.steel89ita.themedebugger)</b> is a great tool to quickly see many of the framework assets.

*  <b>[Android SVG to VectorDrawable](http://0xd34d.github.io/svg2android/)</b> is a great resource to convert an SVG into a usable Android vector drawable XML.

### Understanding Theme Install Errors ###

When developing a new theme, you might find that your theme (or components) may fail to install. The theme engine is pretty good about providing relevant information in the log.

![Log Filter](http://cdn.cyngn.com/g/themes_template_tips/InstallTheme_LogFilter.png)

To quickly see the error messages related to a failed install, you can set up a Logcat filter. This will show you only the relevant information and skip all the other noise, allowing you to quickly see the error.

![Find DDMS](http://cdn.cyngn.com/g/themes_template_tips/InstallTheme_FindDDMS.png)

If you are using Android Studio, Android DDMS will be available directly within the IDE. You can set up the filter from the menu in the top right.

![Edit Filter](http://cdn.cyngn.com/g/themes_template_tips/InstallTheme_EditFilter.png)

If you are using a different IDE, Android DDMS can be accessed in the Android SDK. You'll find it in the /tools directory.﻿

### <a name="copyright"></a>CyanogenMod Copyright Header ###

     Copyright (C) 2015 The CyanogenMod Project

     Licensed under the Apache License, Version 2.0 (the "License");
     you may not use this file except in compliance with the License.
     You may obtain a copy of the License at

          http://www.apache.org/licenses/LICENSE-2.0

     Unless required by applicable law or agreed to in writing, software
     distributed under the License is distributed on an "AS IS" BASIS,
     WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
     See the License for the specific language governing permissions and
     limitations under the License.

---

Note: At this time, we are not accepting Google or third-party app overlays. The template should be covering frameworks and core apps only. This may change in the future.