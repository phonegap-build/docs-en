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
