---
license: licensed to the apache software foundation (asf) under one
         or more contributor license agreements.  see the notice file
         distributed with this work for additional information
         regarding copyright ownership.  the asf licenses this file
         to you under the apache license, version 2.0 (the
         "license"); you may not use this file except in compliance
         with the license.  you may obtain a copy of the license at

           http://www.apache.org/licenses/license-2.0

         unless required by applicable law or agreed to in writing,
         software distributed under the license is distributed on an
         "as is" basis, without warranties or conditions of any
         kind, either express or implied.  see the license for the
         specific language governing permissions and limitations
         under the license.

---

# Icons and Splash Screens

## Usage and Additional Information

The following is a list of the currently supported icon and splash screens
supported for this release of Cordova/Phonegap on PhoneGap Build.

Unless otherwise specified in a config.xml, each platform will try to use the
default `icon.png` during compilation. To define platform specific icons please
use the guide provided below.

Icon files should be the file formats specified in the examples below, other
file types are not guaranteed to work across platforms.

  <table class="table">
    <tr>
      <td>`<icon>`<td>
      <td>
        <p>
          You can have zero or more of these elements present in your
          `config.xml`. If you do not specify a icon then the PhoneGap logo will
          be used as your application's icon.
        </p>
        <p>
          `src`: (required) specifies the location of the image file, relative
          to your `www` directory
        </p>
        <p>
          `width`: (optional) but recommended to include, width in pixels
        </p>
        <p>
          `height`: (optional) but recommended to include, height in pixels
        </p>
      </td>
    </tr>
  </table>

### Default

  The default icon must be named `icon.png` and must reside in the root of your application folder.

    <icon src="icon.png" />

### iOS

  We support classic, retina, iPad displays (and retina iPad displays in PhoneGap 2.5.0+). The following will define icons
for each specific screen type.

    <icon src="icons/ios/icon.png" gap:platform="ios" width="57" height="57" />
    <icon src="icons/ios/icon-72.png" gap:platform="ios" width="72" height="72" />
    <icon src="icons/ios/icon_at_2x.png" gap:platform="ios" width="114" height="114" />

  <!-- retina iPad support: PhoneGap 2.5.0+ only -->
  <icon src="icons/ios/icon-72_at_2x.png" gap:platform="ios" width="144" height="144" />

### Android

  We support ldpi, mdpi, hdpi, and xhdpi displays; the following will define icons for
 each specific screen type.

    <icon src="icons/android/ldpi.png" gap:platform="android" gap:density="ldpi" />
    <icon src="icons/android/mdpi.png" gap:platform="android" gap:density="mdpi" />
    <icon src="icons/android/hdpi.png" gap:platform="android" gap:density="hdpi" />
    <icon src="icons/android/xhdpi.png" gap:platform="android" gap:density="xhdpi" />

### BlackBerry

  BlackBerry icons __must be smaller__ then 16kb. BlackBerry also defines an
optional hover state; this state allows for a separate icon to be displayed
when a user uses the trackpad to roll over your icon image. By default the
non-hover icon will be used as the hover state.

    <icon src="icons/bb/icon.png" gap:platform="blackberry" />
    <icon src="icons/bb/icon_hover.png" gap:platform="blackberry" gap:state="hover"/>

### Windows Phone

  We support two icons for Windows Phone, a regular icon and a tile image.

    <icon src="icons/winphone/icon.png" gap:platform="winphone" />
    <icon src="icons/winphone/tileicon.png" gap:platform="winphone" gap:role="background" />

### WebOS 

  WebOs supports a default icon and a mini icon which can be used for notifications.

    <icon src="icons/webos/icon.png" gap:platform="webos" />
    <icon src="icons/webos/miniicon.png" gap:platform="webos" gap:role="mini" />

<a name="splashes"></a>
## Splash Screens

You can have zero or more of these elements present in your
`config.xml`. This element can have `src`, `gap:platform`, `width` and `height`
attributes, just like the `<icon>` element above. Like icon files, your splash
screens should be saved as `png` files.

  <gap:splash src="splash/ios/Default-568h@2x~iphone.png" gap:platform="ios" width="320" height="480" />


### Usage and Additional Information:

Unless otherwise specified in a config.xml, each platform will try to use the
default `splash.png` during compilation. To define platform specific splash
screens please use the guide provided below.

Splash files should be the file formats specified in the examples below. Any
other file type is not guaranteed to work across platforms.

### Warning:
If you do not supply the `gap:platform` attribute, the referenced image will be
copied to ALL platforms, increasing the size of their application packages.

### Default

  The default splash must be named `splash.png` and must reside in the root of your application folder.

    <gap:splash src="splash.png" />

### iOS

  We support classic, retina, iPhone 5 and iPad displays; the following will
define splash screens for each of those. Standard iPads have two different splash
screens, portrait, landscape. Retina iPads have two additional splash screens, retina 
portrait and retina landscape (PhoneGap 2.5.0+ only).

    <gap:splash src="splash/ios/Default.png" gap:platform="ios" width="320" height="480" />
    <gap:splash src="splash/ios/Default_at_2x.png" gap:platform="ios" width="640" height="960" />
    <gap:splash src="splash/ios/Default_iphone5.png" gap:platform="ios" width="640" height="1136" />
    <gap:splash src="splash/ios/Default-Landscape.png" gap:platform="ios" width="1024" height="748" />
    <gap:splash src="splash/ios/Default-Portrait.png" gap:platform="ios" width="768" height="1004" />

    <!-- retina iPad support: PhoneGap 2.5.0+ only -->
    <gap:splash src="splash/ios/Default-Landscape_at_2x.png" gap:platform="ios" width="2048" height="1496" />
    <gap:splash src="splash/ios/Default-Portrait_at_2x.png" gap:platform="ios" width="1536" height="2008" />

### Android

  We support ldpi, mdpi, hdpi and xhdpi displays; the following will define splash
screens for each specific screen type.

    <gap:splash src="splash/android/ldpi.png" gap:platform="android" gap:density="ldpi" />
    <gap:splash src="splash/android/mdpi.png" gap:platform="android" gap:density="mdpi" />
    <gap:splash src="splash/android/hdpi.png" gap:platform="android" gap:density="hdpi" />
    <gap:splash src="splash/android/xhdpi.png" gap:platform="android" gap:density="xhdpi" />

### BlackBerry 

  BlackBerry supports a single splash image and can be defined as below.

    <gap:splash src="splash/bb/splash.png" gap:platform="blackberry" />

### Windows Phone

  Windows Phone supports a single splash image and can be defined as below.
Unlike the other supported platforms, Windows Phone splash screen should be in
`jpg` format

    <gap:splash src="splash/winphone/splash.jpg" gap:platform="winphone" />

