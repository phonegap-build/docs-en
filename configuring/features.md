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

_The feature tag has been deprecated._

If you were using a feature tag to declare a custom debug server, you should now include the debug script directly in your application html file(s). A debug-server declaration like this:

    <feature name="debug-server" required="true">
       <param name="domain" value="http://debug.custom.com"/>
       <param name="key" value="some_unique_key"/>
    </feature>

would now be included in your application's index.html page (and / or any other pages you wish to debug) like this:

    <script type="text/javascript" src=http://debug.custom.com/target/target-script-min.js#some_unique_key"></script>

Permissions and features previously injected with the feature tag should now be added through [plugins](http://docs.build.phonegap.com/en_US/configuring_plugins.md.html). In addition application manifests can be modified directly using the [config-file element](http://docs.build.phonegap.com/en_US/configuring_config_file_element.md.html).

