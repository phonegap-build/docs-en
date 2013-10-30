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

# Upgrading from 2.9.0 to 3.0.0

This guide provides a gentle upgrade path for PhoneGap Build users who would
like to upgrade from `2.9.0` to `3.0.0`.

## Architecture Changes

Many things have changed from `2.9.0` to `3.0.0`. There have been significant
changes made to Cordova's architecture, these changes also apply to PhoneGap
Build.

The core api's that were once bundled with every release (ex: contacts,
camera, etc.) are now self contained plugins.

User's will now need to include features they would like to incorporate into
their app.

For example, if a user's app relies on the contacts api they will need to
include the following in their `config.xml`.

        <gap:plugin name="Contacts" value="org.apache.cordova.core.ContactManager" />

## How to Upgrade Your App

### Use a Config.xml

Add a `config.xml` to your application if you do not already have one. This
file must reside in the root of your project, generally it's
in the same directory as your `index.html`. For example:

        config.xml
        index.html
        imgs/
        js/
        css/
        res/

If you're unfamiliar with using a `config.xml` here is a simple template you can
use. Copy and paste the following example into the `config.xml` file.

        <?xml version="1.0" encoding="UTF-8" ?>
        <widget xmlns = "http://www.w3.org/ns/widgets"

            xmlns:gap   = "http://phonegap.com/ns/1.0"
            id          = "com.phonegap.example"
            version     = "1.0.0"
            versionCode = "10" >

            <!-- versionCode is optional and Android only -->

            <preference name="phonegap-version" value="3.0.0" />

            <name>Sample Config.xml</name>

            <description>
            An example for phonegap build docs. 
            </description>

            <author href="http://yoursite.com" email="you@youremail.com">
            Your Name
            </author>

        </widget>

It's recommended that you get familiar with using the config.xml. It improves
the extensability of PhoneGap Build by allowing users to configure various
aspects of the app such splash screens, icons, and plugins. You can view
the documentation here: Configure Your App.

### Include Core APIs

Once you have a config.xml you will need to include all the core APIs required
by your application.

To do so include a `<gap:plugin />` tag for each API, for example, if your
app uses the accelerometer include the following.

        <gap:plugin name="Accelerometer" value="org.apache.cordova.core.Accelerometer" />

If you fail to include an API your application may crash, we're currently working
on making the experince as smooth as possible.

### Non-Core APIs
