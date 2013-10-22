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

The `<feature>` element can be used to specify which features your
application is using. If you specify features of the PhoneGap API, those will
be expanded to the appropriate permissions for you application. 

<i class="glyphicon glyphicon-check"></i> PhoneGap Build uses feature tags
slightly differently then local Cordova/PhoneGap apps. Here is what we support:

<a name="debug"></a>
## Custom Debug Server

The `debug-server` feature allows you to use a custom Weinre instance for your
application. By default PhoneGap Build uses `http://debug.build.phonegap.com`
however this can be changed by adding the following to your `config.xml`.

    <feature name="debug-server" required="true">
       <param name="domain" value="http://debug.custom.com"/>
       <param name="key" value="some_unique_key"/>
    </feature>

<i class="glyphicon glyphicon-check"></i> Don't forget to change the domain and
key to the appropriate values.
      
## API Features

Currently supported through this interface are the following feature names:

  <table class="table">
    <tr>
    <td>`http://api.phonegap.com/1.0/battery`</td>
    <td>maps to `android:BROADCAST_STICKY` permission</td>
    </tr>
    <tr>
      <td>`http://api.phonegap.com/1.0/camera`</td>
      <td>
        maps to `android:CAMERA`, `winphone:ID_CAP_ISV_CAMERA`,
        and `winphone:ID_HW_FRONTCAMERA` permissions
      </td>
    </tr>
    <tr>
      <td>`http://api.phonegap.com/1.0/contacts`</td>
      <td>
        maps to `android:READ_CONTACTS`, `android:WRITE_CONTACTS`,
        `android:GET_ACCOUNTS`, and `winphone:ID_CAP_CONTACTS` permissions
      </td>
    </tr>
    <tr>
      <td>`http://api.phonegap.com/1.0/file`</td>
      <td>maps to `WRITE_EXTERNAL_STORAGE` permission</td>
    </tr>
    <tr>
      <td>`http://api.phonegap.com/1.0/geolocation`</td>
      <td>
        maps to `android:ACCESS_COARSE_LOCATION`, `android:ACCESS_FINE_LOCATION`, 
        `android:ACCESS_LOCATION_EXTRA_COMMANDS`, and `winphone:ID_CAP_LOCATION`
        permissions
      </td>
    </tr>
    <tr>
      <td>`http://api.phonegap.com/1.0/media`</td>
      <td>
        maps to `android:RECORD_AUDIO`, `android:RECORD_VIDEO`,
        `android:MODIFY_AUDIO_SETTINGS`, and `winphone:ID_CAP_MICROPHONE`
        permissions
      </td>
    </tr>
    <tr>
      <td>`http://api.phonegap.com/1.0/network`</td>
      <td>
        maps to `android:ACCESS_NETWORK_STATE`, and `winphone:ID_CAP_NETWORKING`
        permissions
      </td>
    </tr>
    <tr>
      <td>`http://api.phonegap.com/1.0/notification`</td>
      <td>maps to `VIBRATE` permission</td>
    </tr>
    <tr>
      <td>`http://api.phonegap.com/1.0/device`</td>
      <td>maps to `winphone:ID_CAP_IDENTITY_DEVICE` permission</td>
    </tr>
  </table>

### Example Usage
    
    <?xml version="1.0" encoding="UTF-8" ?>
        <widget xmlns   = "http://www.w3.org/ns/widgets"
            xmlns:gap   = "http://phonegap.com/ns/1.0"
            id          = "com.phonegap.example"
            versionCode = "10" 
            version     = "1.0.0" >
        
        <!-- versionCode is optional and Android only -->

        <name>PhoneGap Example</name>

        <description>
            An example for phonegap build docs. 
        </description>

        <author href="https://build.phonegap.com" email="support@phonegap.com">
            Hardeep Shoker 
        </author>

        <!--
          If you do not want any permissions to be added to your app, add the
          following tag to your config.xml; you will still have the INTERNET
          permission on your app, which PhoneGap requires.
        -->
        <preference name="permissions" value="none"/>

        <!-- to enable individual permissions use the following examples -->
        <feature name="http://api.phonegap.com/1.0/battery"/>
        <feature name="http://api.phonegap.com/1.0/camera"/>
        <feature name="http://api.phonegap.com/1.0/contacts"/>
        <feature name="http://api.phonegap.com/1.0/file"/>
        <feature name="http://api.phonegap.com/1.0/geolocation"/>
        <feature name="http://api.phonegap.com/1.0/media"/>
        <feature name="http://api.phonegap.com/1.0/network"/>
        <feature name="http://api.phonegap.com/1.0/notification"/>
    </widget>
