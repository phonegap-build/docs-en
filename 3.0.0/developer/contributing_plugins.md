---
license: Licensed to the Apache Software Foundation (ASF) under one
         or more contributor license agreements.  See the NOTICE file
         distributed with this work for additional information
         regarding copyright ownership.  The ASF licenses this file
         to you under the Apache License, Version 2.0 (the
         "License"); you may not use this file except in compliance
         with the License.  You may obtain a copy of the License at

         http://www.apache.org/licenses/LICENSE-2.0

         Unless required by applicable law or agreed to in writing,
         software distributed under the License is distributed on an
         "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
         KIND, either express or implied.  See the License for the
         specific language governing permissions and limitations
         under the License.

---

# Contributing Plugins

We are interested in working with developers to contribute plugins for use on PhoneGap Build. Any plugins added to our system right now will be accessible to all PhoneGap Build users; there may be other mechanisms for PhoneGap Build plugin usage in the future.

PhoneGap Build supports plugins for iOS and Android. Our focus right now is on creating a great plugin experience for those two platforms.

There are two considerations when developing a plugin for PhoneGap Build:

  1. Developing the plugin code
  2. Packaging the plugin for use with our tools

The linked versions of any tools and/or specifications are the ones used by PhoneGap Build.

## Developing the plugin code

A PhoneGap Plugin consists of:

  * a JavaScript file, implementing the PhoneGap Plugin interface. Unless you have an exceptionally good excuse, the same JavaScript code should run on both supported platforms
  * a native class for each supported platform, implementing the PhoneGap Plugin interface
  * associated dependencies and assets. There may, for instance, need to be multiple native classes to implement the full plugin logic, or UI assets on the native or www side.

Plugins developed for PhoneGap Build should always be developed and tested against the latest release of PhoneGap (2.9 at the time of writing).

Up to date information about plugin development is available at [docs.phonegap.com][pgdocs]

## Packaging the plugin

PhoneGap Build uses the [plugman][pins] tool to install plugins into the native projects we generate for our users.

The correct format for plugins used by plugman is documented in [a separate spec][spec]. For an example of a plugin built according to that spec, please see [the Facebook Connect plugin][child], which is currently active on PhoneGap Build.

To check whether your plugin is packaged correctly for each supported platform:

  1. Create a new Cordova project for that platform. Edit the generated `index.html` file to reference and use your plugin
  2. Run the correct plugman command. For instance, if you're installing a plugin stored in `/Users/ramen/dev/plugin` into an iOS project stored in `/Users/ramen/dev/my_project`, run:

      `plugman -platform ios /Users/ramen/dev/my_project /Users/ramen/dev/plugin`

  3. Verify that the project can build without error, that the plugin is included, and that any JavaScript code using the plugin executes correctly.

All of the above tools and specifications are in active development. If you find a limitation or an error with plugman or the specification, please create an issue on the appropriate GitHub project.

## Submitting Your Plugin

Once your plugin is in a state that you're happy with, [submit the plugin][padd] to PhoneGap Build.

Our criteria for including the plugin on PhoneGap Build, broadly speaking, are:

  1. We believe it legitimately adds value for our users.
  2. We can build an app using your plugin, and verify that it works.
  3. We can do a quick review of the source code, and flag anything that concerns
  us (security risks, compiler warnings, that sort of thing).

If we're not satisfied with any of the above, we'll get back to you with our concerns, and hopefully we can reach a resolution. If you're worried that your plugin will not meet our standards, please get in contact while you're developing so we can help you out.

[padd]:/plugins#add
[pgdocs]:http://docs.phonegap.com/en/2.9.0/guide_plugin-development_index.md.html
[pins]:https://github.com/phonegap-build/cordova-plugman
[spec]:https://github.com/alunny/cordova-plugin-spec
[child]:https://github.com/phonegap-build/FacebookConnect
