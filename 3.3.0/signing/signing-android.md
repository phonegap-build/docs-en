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

[Generating a private key](#_generating_a_private_key)
[Submitting your key to build](#_submitting_your_key_to_build)
[Unlocking your key](#_unlocking_your_key)

## Generating a private key

1. [Download and install Java](http://www.java.com/en/download/index.jsp).

2. Set Java_Home directory (http://docs.oracle.com/cd/E19182-01/820-7851/inst_cli_jdk_javahome_t/index.html).

3. Open the command prompt (cmd.exe) as an Administrator, then Run the following command: `$ keytool -genkey -v -keystore [keystore_name].keystore -alias [alias_name] -keyalg RSA -keysize 2048 -validity 10000`

4. Keytool will ask for keystore password. Enter password and confirm:
![Keystore Password](https://lh6.googleusercontent.com/-dTrBt9fr6XY/UQoYlRA-5AI/AAAAAAAAACA/HQfQ0dEeORE/s800/android_keystore_pass.png)

5. Next, keytool will ask for additional information. Supply appropriately:
![Keystore Password 2](https://lh3.googleusercontent.com/-tHJyFTz4Jgg/UQoZcBfALpI/AAAAAAAAACM/RadHnubtmzQ/s800/additional_info.png)

6. Next, keytool will ask password for Alias. Return if it's the same as keystore password. Othewise enter password and confirm:
![Alias password](https://lh4.googleusercontent.com/-rDuGcZs9D1o/UQobXI9BeqI/AAAAAAAAACk/Hzq0MRVysV4/s800/alias_password.png)

7. Your signing key is now ready to submit:
![Submit signing key](https://lh3.googleusercontent.com/-HITXvrjJ_Ts/UQoefEAAnfI/AAAAAAAAADM/4uurmV0t1eM/s800/keystore_ready.png)

## Submitting your key to Build

Go to your Account > Edit Setting > Signing Key's tab. 
![Edit signing keys](https://lh4.googleusercontent.com/-8yYhqgfxFd8/UQogUPNxBaI/AAAAAAAAADc/kS6zVSBT30U/s800/edit_account_settings.png)

Click 'add a key...', ensuring you use the same alias used when you generated your key.
![Add info](https://lh5.googleusercontent.com/-SlgtUAUu0yg/UQojGv88wyI/AAAAAAAAADs/feiaimA9TDA/s800/add_key.png)

## Unlocking your key

Go to your Account > Edit Setting > Signing Key's tab: 
![Signing Keys](https://lh4.googleusercontent.com/-8yYhqgfxFd8/UQogUPNxBaI/AAAAAAAAADc/kS6zVSBT30U/s800/edit_account_settings.png)

Click unlock button and supply the the certificate password (from step #6 above) and the keystore password (from step #4 above)
![Unlocking](https://lh5.googleusercontent.com/-_0NDzwogI34/UQonEx9z8jI/AAAAAAAAAD8/S3AfFDrQHyA/s800/unlock_key.png)

***

[More info](http://developer.android.com/tools/publishing/app-signing.html#cert)
