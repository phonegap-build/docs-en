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

# Android Signing

Adobe® PhoneGap Build™ allows you to sign your Android builds, so they are
suitable for submission to the [Android Market](http://market.android.com/).

To get a release build ready, you first need to generate a signing keystore
file. Full details are available in the [Android
documentation](http://developer.android.com/guide/publishing/app-signing.html):
please ensure that you record the **alias**, as well as the **keystore
password** and **key password** that you set for your keystore.

The next step is to go to [edit your account](/people/edit) and add the key.
Scroll down and you should see a new panel present, for signing keys and
certificates.

![Signing Keys Panel](img/phonegap-build/android-signing/signing-keys-panel.png)

Hit add a key and fill in all of your details - ensure that the **alias, key
password and keystore password** fields match those entered when you created
your key. The **title** field can be anything you want - something to help you
identify your key.

  ![Android Key Modal Form](img/phonegap-build/android-signing/android-key-modal.png)

Hit save and the list of keys at the bottom should be updated to include your
new key. Make sure you set your new key to be the default.

When a release build of an app is made with PhoneGap Build, we sign the binary
with your keystore, and also align it using the `zipalign` tool.

Now you're ready to go: all subsequent Android builds will use your default
selected key, and be release ready.
