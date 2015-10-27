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

# Plugins

To extend the native functionality exposed by the PhoneGap native-app container, PhoneGap Build supports a white-listed selection of PhoneGap Plugins.

Plugins can either be from <a href="https://build.phonegap.com/plugins" target="_blank">our repostiory</a> or from <a href="https://www.npmjs.com/">npm</a>.

Plugins need to be implemented differently for each platform, and may not be supported across all PhoneGap platforms. If you're deploying across multiple platforms, ensure that the experience degrades gracefully for users who do not have the plugin available.

If you would like to contribute a plugin to the PhoneGap Build repository, please see the [Contributing Plugins ](developer_contributing_plugins.md.html) documentation. To submit a plugin to <a href="https://www.npmjs.com/">npm</a> please view their <a href="https://docs.npmjs.com/getting-started/publishing-npm-packages">documentation</a>.

## Including a plugin in your project

There are two steps to including a plugin in your project:

  - <a href="#importing-config">Importing the native code using the config.xml</a>
  - <a href="#importing-native">Referencing the JavaScript code for the plugin</a>

<a id="importing-config"></a>
### Importing the native code

To import the native code into your PhoneGap Build project, you will need to add the correct `<gap:plugin>` tag to your config.xml file.
<b>If you omit the version tag, your app will always be built with the latest version of the plugin. It will be updated automatically the next time you update your app code after a plugin is updated, which may cause unexpected behaviour.</b> For more info on plugin versioning, <a href="#plugin-versions">click here</a>.

<table class="table">
  <tr>
    <td><code>&lt;gap:plugin&gt;</code></td>
    <td>
        <p>
          <code>name</code>: Plugins should be referenced by the plugin ID which is
          normally in a reverse domain format (ex: com.phonegap.plugins.barcodescanner).
        </p>
        <hr>
        <p>
          <code>version</code>: Optional, but we highly recommend locking your plugin version, as mentioned above.
        </p>
        <hr>
        <p>
        <code>source</code>: Optional, can either be "pgb" or "npm".  Defaults to "pgb".
        </p>
        <hr>
        <p>
          <code>params</code>: Plugins may require parameters for configuration
          properties. <a href="#plugin-params">Here is a detailed explanation.</a>
        </p>
    </td>
  </tr>
</table>

<a id="plugin-sources"></a>
#### Plugin Source

Plugins can be included from either our repository, located <a href="https://build.phonegap.com/plugins">here</a>, or at <a href="https://www.npmjs.com/">npm</a>.

The default value for this attribute is `pgb` so for instance the plugin lines below both reference the same plugin in our repository.

    <gap:plugin name="com.phonegap.plugins.example" />
    <gap:plugin name="com.phonegap.plugins.example" source="pgb" />

To include a plugin from <a href="https://www.npmjs.com/">npm</a> specify `npm` in the source attribute.

    <gap:plugin name="example-plugin" source="npm" />

The version attribute and param fragments are handled identically regardless of the source of the plugin.

<a id="plugin-versions"></a>
#### Plugin Versions

Here is the most simplistic way of using a versioned plugin.

    <gap:plugin name="com.phonegap.plugins.example" version="2.2.1" />

PhoneGap Build also supports `fuzzy versions`.

You can use the tilde `~` operator to specify fuzzy versions, this will ensure that you have the latest version of a plugin with the same major version.

For example, you could replace the tag above with:

    <gap:plugin name="com.phonegap.plugins.example" version="~2" />

which would load the latest 2.x version, but not anything with a different major/initial version number.

The following version tag:

    <gap:plugin name="com.phonegap.plugins.example" version="~2.2" />

would load the latest 2.x version so long as x is greater or equal to 2.

And finally, this version tag:

    <gap:plugin name="com.phonegap.plugins.example" version="~2.2.3" />

would load the latest 2.2.x version so long as x is greater or equal to 3.

<a id="plugin-params"></a>
#### Plugin Parameters

Plugins may require configuration information to be present; this can be done with adding <param> children to the <gap:plugin> tag:

    <gap:plugin name="com.phonegap.plugins.example">
      <param name="APIKey" value="12345678" />
      <param name="APISecret" value="12345678" />
    </gap:plugin>

<i class="glyphicon glyphicon-check"></i> Make sure to check the documentation of the plugin to see if parameters are necessary.

#### Usage Example

Here is a config.xml that includes the Barcode Scanner plugins as an example:

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

        <!-- We'll include the Barcode plugin as an example -->
        <gap:plugin name="com.phonegap.plugins.barcodescanner" />
    </widget>

<a id="importing-native"></a>
### Referencing the JavaScript code

If a plugin utilizes the <code>js-module</code> element to direct cordova to load the plugin javascripts, then no <code>&lt;script&gt;</code> references will be necessary to load a plugin. This is the case for the core cordova plugins, but 3rd party plugins will be implementation-dependent. Refer to the plugin's documentation to determine if you'll need to manually include the javascript.

If you do need to manually include the plugin javascript, it would look like the following:

    <script src="cordova.js"></script>
    <script src="barcodescanner.js"></script>

Whether the script tag is required or not, **do not include the actual plugin files in the zip or repository which you submit to PhoneGap Build**. These files will be injected by PhoneGap Build, and including them may cause problems.
