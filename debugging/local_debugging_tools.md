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

# Local Debugging Tools

PhoneGap Build allows users to use their own debug server with the Build service.

Build uses a tool called Weinre to enable remote debugging of mobile apps.

This guide provides information on setting up your own local server.

The pre-requisites for running Weinre are that you need to have `npm` installed. Once you've installed Weinre you will only be able to use the local server within your own network unless you plan to host it on a publicly accessible location. This will require additional setup that is outside the scope of this guide.

## Setting up Weinre

### Get Weinre

Once you have `npm` installed, obtaining and installing Weinre is as simple as running the following command in a terminal.

    sudo npm -g install weinre

That's it! Now you're ready to run your very own Weinre instance.

### Start Weinre

To start your new local Weinre instance run the following command:

    weinre

You will now see output like the following:

    Hardeeps-MacBook-Air:~ hardeep$ weinre
    2013-07-01T20:03:34.890Z weinre: starting server at http://localhost:8080

Weinre is now up and running! If you are running this behind a router that uses NAT you will need to find your IP address. You will use this IP when specifying your configuration with Build.

## Using a Local Weinre Instance with Build

Obtain the ip address of your machine running Weinre. This can be done on Windows by running `ipconfig` or on OSX/Linux by running `ifconfig`.

Now include a reference to the Weinre debug script on your debug server, like so:

    <script type="text/javascript" src=http://my.server.ip/target/target-script-min.js#some_unique_key"></script>

**Make sure your remove this before publishing your app!**

## Common Issues

__I can't connect to my Local Server__

First of all make sure that your server is running. Chances are if you're using the default configuration you can visit http://localhost:8080 and it should be responding.

If this works it's most likely the IP address you're providing to Build; please verify that it is correct. A google search such as `windows [version] find ip address` or `OSX [version] find ip address` will help you find articles on getting the right ip.

Assuming that you're using a router running NAT verify that you can visit it within your network by visiting http://[ip address]:8080.
