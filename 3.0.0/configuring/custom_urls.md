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

# Custom URL Schemes

iOS allows registration of [custom URL schemes](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/AdvancedAppTricks/AdvancedAppTricks.html#//apple_ref/doc/uid/TP40007072-CH7-SW50).

  <table class="table">
    <tr>
      <td>`<gap:url-scheme>`</td>
      <td>
        <p>
          Your app can have many `url-scheme` elements present.
        </p>
        <hr>
        <p>
          `name` (optional): defaults to the application bundle id. This has to be unique. If a duplicate is found the build will fail.
        </p>
        <p>
          `role`: must be `Editor`, `Viewer`, `Shell` or `None`, optional, defaults to `None`.
        </p>
        <p>
          <i class="glyphicon glyphicon-check"></i> At least one `scheme` must be present.
        </p>
      </td>
    </tr>
  </table>


## Example Usage

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

        <gap:url-scheme name="com.acme.myscheme" role="None">
          <scheme>pgbr</scheme>
          <scheme>pgbw</scheme>
        </gap:url-scheme>
    </widget>
