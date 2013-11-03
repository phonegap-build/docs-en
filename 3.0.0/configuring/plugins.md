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

To extend the native functionality exposed by the PhoneGap native-app container, PhoneGap Build supports a white-listed selection of PhoneGap Plugins,

The list of all supported plugins is located on our
  <a href="https://build.phonegap.com/plugins" target="_blank">plugins repository.</a>

Plugins need to implemented differently for each platform, and may not be supported across all PhoneGap platforms. If you're deploying across multiple platforms, be sure that the experience degrades gracefully for users who do not have the plugin available.

If you would like to contribute a plugin to PhoneGap Build, please see the relevant documentation.

## Including a plugin in your project

There are two steps to including a plugin in your project: 

  - <a href="#importing-config">Importing the native code using the config.xml</a>
  - <a href="#importing-native">Referencing the JavaScript code for the plugin</a>

<a id="importing-config"></a>
### Importing the native code

To import the native code into your PhoneGap Build project, you will need to add the correct `<gap:plugin>` tag to your config.xml file.

<table class="table">
  <tr>
    <td><code>&lt;gap:plugin&gt;</code></td>
    <td>
        <p>
          <code>name</code>: Plugins should be referenced by the plugin ID which is
          normally in a reverse domain format (ex: com.example.www).
        </p>
        <hr>
        <p>
          <code>version</code> (optional): You can specify an optional version of a
          plugin to run with the version attribute. If no version is specified
          then the latest available version of the plugin is used. <a href="#plugin-versions">Click here, for a detailed guide on
          using versions.</a>
        </p>
        <hr>
        <p>
          <code>params</code>: Plugins may require parameters for configuration
          properties. <a href="#plugin-params">Here is a detailed explanation.</a>
        </p>
    </td>
  </tr>
</table>

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

As with `phonegap.js`, the JavaScript code for a plugin is inserted into your project by PhoneGap Build at build time. Plugins will usually depend on PhoneGap being loaded already, so insert a script tag after the phonegap.js tag.

For example, if you're using the [Barcode Scanner plugin](https://build.phonegap.com/plugins/140) it would look like the following:

    <script src="phonegap.js"></script>
    <script src="barcodescanner.js"></script>

Do not include the plugin javascript files or other plugin files in your app. These will be injected by PhoneGap Build, and including them may cause problems.

Using the Barcode Sanner example above, you should omit uploading the `barcodescanner.js` file when uploading the project to PhoneGap Build. (Also  remember not to include the `phonegap.js`!)

