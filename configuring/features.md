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

# Features

<a name="debug"></a>
## Custom Debug Server

The `debug-server` feature allows you to use a custom Weinre instance for your application. By default PhoneGap Build uses `http://debug.build.phonegap.com` however this can be changed by adding the following to your `config.xml`.

    <feature name="debug-server" required="true">
       <param name="domain" value="http://debug.custom.com"/>
       <param name="key" value="some_unique_key"/>
    </feature>

Aside from the debug-server feature, the feature tag is essentially deprecated on PhoneGap Build since PhoneGap APIs were pluginized. Permissions are now generally managed by individual plugins, and application manifests and permissions can be modified directly using the [config-file element](http://docs.build.phonegap.com/en_US/configuring_config_file_element.md.html). However for backwards-compatibility, they are still supported and map to device permissions on Android and Windows Phone 8:

The `<feature>` element can be used to specify which features your application is using. If you specify features of the PhoneGap API, those will be expanded to the appropriate permissions for you application. 

    <feature name="http://api.phonegap.com/1.0/network" />

Feature tags are mapped to features and permissions in the manifest files in each platform. PhoneGap Build uses an open-source tool called [confetti](https://github.com/phonegap-build/confetti) to map each feature. Here is a full list of supported feature tags:

    <feature name="http://api.phonegap.com/1.0/network" />
    <feature name="http://api.phonegap.com/1.0/camera" />
    <feature name="http://api.phonegap.com/1.0/notification" />
    <feature name="http://api.phonegap.com/1.0/geolocation" />
    <feature name="http://api.phonegap.com/1.0/media" />
    <feature name="http://api.phonegap.com/1.0/contacts" />
    <feature name="http://api.phonegap.com/1.0/file" />
    <feature name="http://api.phonegap.com/1.0/battery" />
    <feature name="http://api.phonegap.com/1.0/device" />

To see how each feature maps to device permissions, have a look at the confetti source code for [Android](https://github.com/phonegap-build/confetti/blob/master/lib/confetti/templates/android_manifest.rb#L8) and [Windows Phone 8](https://github.com/phonegap-build/confetti/blob/master/lib/confetti/templates/windows_phone8_manifest.rb).

