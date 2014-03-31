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

The following is a list of the currently supported icon and splash screens supported for this release of Cordova/Phonegap on PhoneGap Build.

Unless otherwise specified in a config.xml, each platform will try to use the default `icon.png` during compilation. To define platform specific icons please use the guide provided below.

Icon files should be the file formats specified in the examples below, other file types are not guaranteed to work across platforms.

<table class="table">
  <tr>
    <td><code>&lt;icon&gt;</code></td>
    <td>
      <p>
        You can have zero or more of these elements present in your
        <code>config.xml</code>. If you do not specify a icon then the PhoneGap logo will
        be used as your application's icon.
      </p>
      <p>
        <code>src</code>: (required) specifies the location of the image file, relative
        to your <code>www</code> directory
      </p>
      <p>
        <code>width</code>: (optional) but recommended to include, width in pixels
      </p>
      <p>
        <code>height</code>: (optional) but recommended to include, height in pixels
      </p>
    </td>
  </tr>
</table>

### Default

The default icon must be named `icon.png` and must reside in the root of your application folder.

    <icon src="icon.png" />

### iOS

We support classic, retina, iPhone 5 and iPad displays.

The names below reflect the names of the destination files when they are added to the application. During app submittal you may get feedback that has a reference to these filenames.

#### iOS 7.0+

    <!-- iPhone / iPod Touch  -->
    <icon src="icon-60.png" gap:platform="ios" width="60" height="60" />
    <icon src="icon-60@2x.png" gap:platform="ios" width="120" height="120" />

    <!-- iPad -->
    <icon src="icon-76.png" gap:platform="ios" width="76" height="76" />
    <icon src="icon-76@2x.png" gap:platform="ios" width="152" height="152" />

    <!-- Settings Icon -->
    <icon src="icon-small.png" gap:platform="ios" width="29" height="29" />
    <icon src="icon-small@2x.png" gap:platform="ios" width="58" height="58" />

    <!-- Spotlight Icon -->
    <icon src="icon-40.png" gap:platform="ios" width="40" height="40" />
    <icon src="icon-40@2x.png" gap:platform="ios" width="80" height="80" />
    
#### iOS 6.1
    
    <!-- iPhone / iPod Touch -->
    <icon src="icon.png" gap:platform="ios" width="57" height="57" />
    <icon src="icon@2x.png" gap:platform="ios" width="114" height="114" />

    <!-- iPad -->
    <icon src="icon-72.png" gap:platform="ios" width="72" height="72" />
    <icon src="icon-72@2x.png" gap:platform="ios" width="144" height="144" />

    <!-- iPhone Spotlight and Settings Icon -->
    <icon src="icon-small.png" gap:platform="ios" width="29" height="29" />
    <icon src="icon-small@2x.png" gap:platform="ios" width="58" height="58" />

    <!-- iPad Spotlight and Settings Icon -->
    <icon src="icon-50.png" gap:platform="ios" width="50" height="50" />
    <icon src="icon-50@2x.png" gap:platform="ios" width="100" height="100" />

### Android

We support ldpi, mdpi, hdpi, xhdpi and xxhdpi displays; the following will define icons for each specific screen type.

    <icon src="ldpi.png" gap:platform="android" gap:density="ldpi" />
    <icon src="mdpi.png" gap:platform="android" gap:density="mdpi" />
    <icon src="hdpi.png" gap:platform="android" gap:density="hdpi" />
    <icon src="xhdpi.png" gap:platform="android" gap:density="xhdpi" />
    <icon src="xxhdpi.png" gap:platform="android" gap:density="xxhdpi" />

### Windows Phone

We support two icons for Windows Phone, a regular icon and a tile image.

    <icon src="icon.png" gap:platform="winphone" />
    <icon src="tileicon.png" gap:platform="winphone" gap:role="background" />

<a name="splashes"></a>
## Splash Screens

You can have zero or more of these elements present in your `config.xml`. This element can have `src`, `gap:platform`, `width` and `height` attributes, just like the `<icon>` element above. Like icon files, your splash screens should be saved as `png` files.

    <gap:splash src="splash/ios/Default-568h@2x~iphone.png" gap:platform="ios" width="320" height="480" />

### Usage and Additional Information:

Unless otherwise specified in a config.xml, each platform will try to use the default `splash.png` during compilation. To define platform specific splash screens please use the guide provided below.

Splash files should be the file formats specified in the examples below. Any other file type is not guaranteed to work across platforms.

### Warning:
If you do not supply the `gap:platform` attribute, the referenced image will be copied to ALL platforms, increasing the size of their application packages.

### Default

The default splash must be named `splash.png` and must reside in the root of your application folder.

    <gap:splash src="splash.png" />

### iOS

We support classic, retina, iPhone 5 and iPad displays; the following will define splash screens for each of those. Standard iPads have two different splash screens, portrait, landscape. Retina iPads have two additional splash screens, retina  portrait and retina landscape.

The names below reflect the names of the destination files when they are added to the application. During app submittal you may get feedback that has a reference to these filenames.

    <!-- iPhone and iPod touch -->
    <gap:splash src="Default.png" gap:platform="ios" width="320" height="480" />
    <gap:splash src="Default@2x.png" gap:platform="ios" width="640" height="960" />

    <!-- iPhone 5 / iPod Touch (5th Generation) -->
    <gap:splash src="Default-568h@2x.png" gap:platform="ios" width="640" height="1136" />

    <!-- iPad -->
    <gap:splash src="Default-Portrait.png" gap:platform="ios" width="768" height="1024" />
    <gap:splash src="Default-Landscape.png" gap:platform="ios" width="1024" height="768" />

    <!-- Retina iPad -->
    <gap:splash src="Default-Portrait@2x.png" gap:platform="ios" width="1536" height="2048" />
    <gap:splash src="Default-Landscape@2x.png" gap:platform="ios" width="2048" height="1536" />

### Android

We support ldpi, mdpi, hdpi, xhdpi and xxhdpi displays; the following will define splash screens for each specific screen type.

    <gap:splash src="ldpi.png" gap:platform="android" gap:density="ldpi" />
    <gap:splash src="mdpi.png" gap:platform="android" gap:density="mdpi" />
    <gap:splash src="hdpi.png" gap:platform="android" gap:density="hdpi" />
    <gap:splash src="xhdpi.png" gap:platform="android" gap:density="xhdpi" />
    <gap:splash src="xxhdpi.png" gap:platform="android" gap:density="xxhdpi" />

Patch-9 backgrounds are supported. All patch-9 files have to have a ".9.png" suffix.

### Windows Phone

  Windows Phone supports a single splash image and can be defined as below. Unlike the other supported platforms, Windows Phone splash screen should be in `jpg` format

    <gap:splash src="splash/winphone/splash.jpg" gap:platform="winphone" />

