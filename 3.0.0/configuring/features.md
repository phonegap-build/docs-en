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

The `<feature>` element can be used to specify which features your application is using. If you specify features of the PhoneGap API, those will be expanded to the appropriate permissions for you application. 

<i class="glyphicon glyphicon-check"></i> PhoneGap Build uses feature tags slightly differently then local Cordova/PhoneGap apps. Here is what we support:

<a name="debug"></a>
## Custom Debug Server

The `debug-server` feature allows you to use a custom Weinre instance for your application. By default PhoneGap Build uses `http://debug.build.phonegap.com` however this can be changed by adding the following to your `config.xml`.

    <feature name="debug-server" required="true">
       <param name="domain" value="http://debug.custom.com"/>
       <param name="key" value="some_unique_key"/>
    </feature>

<i class="glyphicon glyphicon-check"></i> Don't forget to change the domain and key to the appropriate values.
      
## API Features

Currently supported through this interface are the following feature names:

<table class="table">
  <tr>
  <td><code>http://api.phonegap.com/1.0/battery</code></td>
  <td>maps to <code>android:BROADCAST_STICKY</code> permission</td>
  </tr>
  <tr>
    <td><code>http://api.phonegap.com/1.0/camera</code></td>
    <td>
      maps to <code>android:CAMERA</code>, <code>winphone:ID_CAP_ISV_CAMERA</code>,
      and <code>winphone:ID_HW_FRONTCAMERA</code> permissions
    </td>
  </tr>
  <tr>
    <td><code>http://api.phonegap.com/1.0/contacts</code></td>
    <td>
      maps to <code>android:READ_CONTACTS</code>, <code>android:WRITE_CONTACTS</code>,
      <code>android:GET_ACCOUNTS</code>, and <code>winphone:ID_CAP_CONTACTS</code> permissions
    </td>
  </tr>
  <tr>
    <td><code>http://api.phonegap.com/1.0/file</code></td>
    <td>maps to <code>WRITE_EXTERNAL_STORAGE</code> permission</td>
  </tr>
  <tr>
    <td><code>http://api.phonegap.com/1.0/geolocation</code></td>
    <td>
      maps to <code>android:ACCESS_COARSE_LOCATION</code>, <code>android:ACCESS_FINE_LOCATION</code>, 
      <code>android:ACCESS_LOCATION_EXTRA_COMMANDS</code>, and <code>winphone:ID_CAP_LOCATION</code>
      permissions
    </td>
  </tr>
  <tr>
    <td><code>http://api.phonegap.com/1.0/media</code></td>
    <td>
      maps to <code>android:RECORD_AUDIO</code>, <code>android:RECORD_VIDEO</code>,
      <code>android:MODIFY_AUDIO_SETTINGS</code>, and <code>winphone:ID_CAP_MICROPHONE</code>
      permissions
    </td>
  </tr>
  <tr>
    <td><code>http://api.phonegap.com/1.0/network</code></td>
    <td>
      maps to <code>android:ACCESS_NETWORK_STATE</code>, and <code>winphone:ID_CAP_NETWORKING</code>
      permissions
    </td>
  </tr>
  <tr>
    <td><code>http://api.phonegap.com/1.0/notification</code></td>
    <td>maps to <code>VIBRATE</code> permission</td>
  </tr>
  <tr>
    <td><code>http://api.phonegap.com/1.0/device</code></td>
    <td>maps to <code>winphone:ID_CAP_IDENTITY_DEVICE</code> permission</td>
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
