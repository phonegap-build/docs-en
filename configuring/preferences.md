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

# Preferences

PhoneGap utilizes the `<preference>` tag to customize your application configuration. All `<preference>` tags in your config.xml are copied to the platform-specific configuration files, which means that any preferences [supported by the PhoneGap framework](http://docs.phonegap.com/en/edge/config_ref_index.md.html#The%20config.xml%20File), or by any plugins you are using, will work on PhoneGap Build.

**Note**: make sure you select your PhoneGap version when looking at the PhoneGap docs page.

In addition, PhoneGap Build supports some of its own custom preferences, used for things like selecting the PhoneGap version, platform sdk version targeting, and others. These custom preferences are listed below.

If you want to see more detail about what exactly these custom preferences are doing, most of them are translated using the [open-source confetti library](http://github.com/phonegap-build/confetti). Check out the templates directory if you want to dig in.

## Multi-Platform

<table class="table">

  <tr>
    <td><code>phonegap-version</code></td>
    <td>
      Currently supported versions are <b>3.0.0</b>, <b>3.0.0</b>, <b>3.1.0</b>, <b>3.2.0</b>, <b>3.3.0</b>, <b>3.4.0</b>, <b>3.5.0</b>, <b>3.6.3</b> (default), and <b>3.7.0</b> -- all versions prior 
      to 3.0.0 are deprecated as of October 15, 2014. If you don't 
      specify a version in your config, it will be set
      to the current default version. Your app will not build if you specify
      an unsupported version number.
      <br/><br/>
      Example: 
      <br/>
      <code>
          &lt;preference name="phonegap-version" value="3.5.0" /&gt;
      </code>
    </td>
  </tr>

  <tr>
    <td><code>orientation</code></td>
    <td>
      Device orientation; possible values are <code>default, landscape, or
      portrait</code>. Please note that <code>default</code> means <b>both</b>
      landscape and portrait are enabled. If you want to use each platform's
      default settings (usually portrait only), remove this tag from your
      config.xml file.
      <br/><br/>
      Example:
      <br/>
      <code>&lt;preference name="orientation" value="landscape" /&gt;</code>
  </tr>

  <tr>
    <td><code>fullscreen</code></td>
    <td>
      Makes your app full screen, with values <code>true or false</code>. This
      hides the status bar at the top, and is false by default.
      <br/><br/>
      Example:
      <br/>
      <code>&lt;preference name="fullscreen" value="true" /&gt;</code>
      Note: may not be supported by newer versions of iOS, but users can use
      the <a href="http://phonegap.com/blog/2014/01/30/customizing-your-android-manifest-and-ios-property-list-on-phonegap-build/">config-file element on phonegap build</a>, and set UIViewControllerBasedStatusBarAppearance to false and UIStatusBarHidden to true.
  </tr>

</table>

## iOS Only

<table class="table">

  <tr>
    <td><code>target-device</code><br/>(ios only)</td>
    <td>
      For targeting a specific device; possible values are <code>handset,
      tablet, or universal</code>. Note that this currently only applies to iOS
      builds; by default all builds are universal.
      <br/><br/>
      Example:
      <br/>
      <code>
          &lt;preference name="target-device" value="universal" /&gt;
      </code>
    </td>
  </tr>

  <tr>
    <td><code>prerendered-icon</code><br/>(ios only)</td>
    <td>
      This will cause iOS to not apply its gloss to the app's icon on the user's
      home screen; possible values are <code>true or false</code>, default is
      false.
      <br/><br/>
      Example:
      <br/>
      <code>&lt;preference name="prerendered-icon" value="true" /&gt;</code>
    </td>
  </tr>

  <tr>
    <td><code>detect-data-types</code><br/>(ios only)</td>
    <td>
      Controls whether certain data types (such as phone numbers and dates) are
      automatically turned into links by the system. Defaults to "true" (as does
      the system web view). In preference to this, try using meta-tags:
      <meta name="format-detection" content="telephone=no">
      <meta name="format-detection" content="email=no">
      And use detect-data-types if meta tags don't work for you.
      <br/><br/>
      Example:
      <br/>
      <code>&lt;preference name="detect-data-types" value="true" /&gt;</code>
     </td>
  </tr>

  <tr>
    <td><code>exit-on-suspend</code><br/>(ios only)</td>
    <td>
      If set to true, app will terminate when suspended, for example when home
      button is pressed; default is <b>false</b>.
      <br/><br/>Example:
      <br/><code>&lt;preference name="exit-on-suspend" value="true" /&gt;</code>
    </td>
  </tr>

  <tr>
    <td><code>deployment-target</code><br/>(ios only)</td>
    <td>
      This sets the <code>IPHONEOS_DEPLOYMENT_TARGET</code> in the build, which tranlsates to the <code>MinimumOSVersion</code> in the ipa Propertly List.
      <br/><br/>Example:
      <br/><code>&lt;preference name="deployment-target" value="7.0" /&gt;</code>
    </td>
  </tr>

</table>

## Android Only

<table class="table">

  <tr>
    <td><code>android-minSdkVersion</code><br/>(android only)</td>
    <td>
       Minimum Android SDK version. Corresponds to the <code>usesSdk</code> attributes in
       the <code>AndroidManifest.xml</code> file - more details are in
       [the Android documentation](http://developer.android.com/guide/topics/manifest/uses-sdk-element.html). Defaults to 7 (Android 2.1).
      <br/><br/>
      Example:
      <br/>
      <code>&lt;preference name="android-minSdkVersion" value="10" /&gt;</code>
    </td>
  </tr>

  <tr>
    <td><code>android-maxSdkVersion</code><br/>(android only)</td>
    <td>
       Maximum Android SDK version. Corresponds to the <code>usesSdk</code> attributes
       in the <code>AndroidManifest.xml</code> file - more details are in
       [the Android documentation](http://developer.android.com/guide/topics/manifest/uses-sdk-element.html). Unset by default.
      <br/><br/>
      Example:
      <br/>
      <code>&lt;preference name="android-maxSdkVersion" value="15" /&gt;</code>
    </td>
  </tr>

  <tr>
    <td><code>android-targetSdkVersion</code><br/>(android only)</td>
    <td>
      Corresponds to the <code>usesSdk</code> attributes in the <code>AndroidManifest.xml</code>
      file -- an integer designating the API Level that the application
      targets. If not set, the default value equals that given to
      minSdkVersion. More details are in
      [the Android documentation](http://developer.android.com/guide/topics/manifest/uses-sdk-element.html#target). Unset by default.
      <br/><br/>
      Example:
      <br/>
      <code>
        &lt;preference name="android-targetSdkVersion" value="12" /&gt;
      </code>
    </td>
  </tr>

  <tr>
    <td><code>android-installLocation</code><br/>(android only)</td>
    <td>
      Where an app can be installed - defaults to <code>internalOnly</code>
      (as the Android SDK). <code>auto</code> or <code>preferExternal</code>
      allow the app to be installed on an SD card - this can lead to unexpected
      behavior. More details available in
      [the Android documentation](http://developer.android.com/guide/appendix/install-location.html).
      <br/><br/>
      Example:
      <br/>
      <code>
        &lt;preference name="android-installLocation" value="auto" /&gt;
      </code>
    </td>
  </tr>

  <tr>
    <td><code>android-windowSoftInputMode</code><br/>(android only)</td>
    <td>
      How the main window of the activity interacts with the window containing
      the on-screen soft keyboard. More details, and possible values, available
      in [the Android documentation](http://developer.android.com/guide/topics/manifest/activity-element.html#wsoft).
      <br/><br/>
      Example:
      <br/>
      <code>
        &lt;preference name="android-windowSoftInputMode" value="stateVisible|adjustResize" /&gt;
      </code>
    </td>
  </tr>

  <tr>
    <td><code>splash-screen-duration</code><br/>(android only)</td>
    <td>
      Deprecated -- use <a href="http://docs.phonegap.com/en/3.6.0/guide_platforms_android_config.md.html">SplashScreenDelay</a> instead.
    </td>
  </tr>

</table>
