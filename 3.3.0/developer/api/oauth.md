# OAuth

The Oauth authorization protocol allows third party applications access user information from PhoneGap Build without ever seeing the user's login information. Client Applications are pre-registered with PhoneGap Build, and users can view and manage which applications are interacting with PhoneGap Build on their behalf.

## Client Application Registration

As an application developer, you first need to [register your client application with Build](https://build.phonegap.com/people/edit):

<table class="table">
  <tr>
    <td>Name</td>
    <td>A suitable display name for your application.</td>
  </tr>
  <tr>
    <td>Main Application Url</td>
    <td>A url where a user can go to see what this application is.</td>
  </tr>
  <tr>
    <td>Callback Url</td>
    <td>The url we'll redirect to after a user allows your application to interact with your Build account. More info on this below.</td>
  </tr>
</table>

We'll generate a couple of fields for you:

<table class="table">
  <tr>
    <td>Client ID</td>
    <td>A unique identifier that you'll include in requests, identifying your application.</td>
  </tr>
  <tr>
    <td>Client Secret</td>
    <td>Don't share this, it will verify that the request is indeed from your application.</td>
  </tr>
</table>

## Web Application Flow

You've registred your application and are ready to hook it into PhoneGap Build. The first thing you'll do is redirect users to PhoneGap Build where we'll ask them if they want to allow your app to access their resources:
    
    GET https://build.phonegap.com/authorize?client_id=abcdef

If they deny, we'll redirect to your Main Application Url. If they allow, we'll redirect to the Callback Url that you indicated when you registered your application, along with a `code` parameter.

Now that the user has allowed your application to access Build, you need to request an access token from us:

    POST https://build.phonegap.com/authorize/token?client_id=abcdef&client_secret=123456&code=a1b2c3

If all those params check out, we'll respond with a json object containing your access token:

    { "access_token": "xyz123" }

Save it.

Now, you can make requests to PhoneGap Build on behalf of this user:

    GET https://build.phonegap.com/api/v1/me?access_token=xyz123x

## Non Web Application Flow

Its possible that you're creating an application that doesn't include a web server that we can interact with. Don't fret, you can also use basic authentication to obtain authorization to access the API. Of course, you'll still need to register your application with Build as above.

    POST https://build.phonegap.com/authorize?client_id=abcdef&client_secret=123456

For example, via curl:
	
    curl -u steve@goat-simulator.com -X POST https://build.phonegap.com/authorize?client_id=abcdef&client_secret=123456

If those params check out, we'll respond with a json object containing your access token:

    { "access_token": "xyz123" }

And make your requests on behalf of Steve.

    GET https://build.phonegap.com/api/v1/me?access_token=xyz123x

Head [back to the API Docs](developer_api_api.md.html) for the full API spec.
