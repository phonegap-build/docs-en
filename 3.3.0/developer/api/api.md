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

# PhoneGap Build Developer API

The PhoneGap Build API allows applications to use the PhoneGap Build web service to create, build, update, and download PhoneGap apps. It integrates easily into IDEs, shell scripts, app builders, and elsewhere.

The core sections discussed in this documentation article are:

* [Authentication Methods](developer_api_authentication.md.html)
* [The Read API](developer_api_read.md.html)
* [The Write API](developer_api_write.md.html)

Here are some additional notes on using the API.

## JSON

All successful requests return either a JSON-encoded string or a binary file. All requests that fail return a JSON-encoded string in the following form, with an appropriate status code:

    {
        "error":"some error message"
    }

When using the API, check each returned status code; if it's not 200, check the error field on the parsed response, for example:

    if (res.status != 200)
        console.log(JSON.parse(res.body).error)

As is standard in HTTP, a _4xx_ status indicates an error with the request, while a _5xx_ status indicates an server error. Contact
  <a href="http://community.phonegap.com" target="_blank">PhoneGap's support forums</a>
if you get a 500 error, or an unexpected 400 error.

## JSONP

JSONP access is available for PhoneGap Build developers: just add a `callback` parameter to your requests, and the JSONP response body is wrapped in that function:

    $ curl https://build.phonegap.com/api/v1/me?auth_token=ASTRINGTOKEN&callback=exec
    exec({
        "username":"alunny",
        "email":"andrew.lunny@nitobi.com"
    })

This allows you to access the PhoneGap Build API using `<script>` tags.

## HATEOAS

Wherever possible, the PhoneGap Build API v1 uses _Hypermedia as the Engine of Application State_ (
  <a href="http://en.wikipedia.org/wiki/HATEOAS" target="_blank">HATEOAS</a>
).  This means you can access the source of the api (`/api/v1`), then follow nested resources' `link` attributes to navigate the application, with no knowledge of the other routes within your application.

The home resource for the API v1 is the same as the `/me` resource, which represents the current user.
