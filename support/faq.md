# FAQ

Have a question about PhoneGap Build? Check out our FAQ below. We'll be adding to this FAQ regularly, so if you have questions that need answering, [please ask us](http://community.phonegap.com).

## What is the PhoneGap Build service and how is it different from PhoneGap?
PhoneGap is a mobile application development framework, based upon the open source [Apache Cordova](http://incubator.apache.org/cordova/) project. It allows you to write an app once with HTML, CSS and JavaScript, and then deploy it to a wide range of mobile devices without losing the features of a native app.  PhoneGap Build is a cloud-based service built on top of the PhoneGap framework. It allows you to easily build those same mobile apps in the cloud.

## How do I get started with PhoneGap Build?
Simply upload your web assets - a ZIP file of HTML, CSS and JavaScript, or a single index.html file - to PhoneGap Build, point us to your Git or SVN repository. Then we'll undertake the compilation and packaging for you. In minutes, you'll receive the download URLs for all mobile platforms.

## Do I need to install anything before I use PhoneGap Build?
No!

## What about developer accounts and SDKs? Do I need to set those up before starting with PhoneGap Build?
No! But you might want to install some of the SDK emulators if you don't own a particular device that you want to test a build for.

## What do I do with my app when I get it back from PhoneGap Build? Is it ready for app store submission?
It depends on the platform that you're targeting. For the webOS and Symbian platforms, you will get back a binary that is ready for submission and distribution. For Android, iOS, and BlackBerry, you'll need to provide the correct certificates and/or signing keys to allow distribution. See our other documentation for more details on this process.

## Can I build for iPhone?
Yes! Check out our [iOS Guide](signing_signing-ios.md.html) for information on how to get PhoneGap Build up and running with iOS.

## Can I integrate PhoneGap Build with my existing tools?
Yes! we now have an [API available](developer_api_api.md.html) you can use over HTTPS to build apps, and access data about your existing apps.

## Can I use PhoneGap Build with a private Github repository?
Yes!  As of the most recent update to PhoneGap Build, you can now point the service at a private GitHub repository. Once your Build account is connected to your GitHub account in the user settings, you simply provide your authentication information and the Build service uses it when creating new builds of your code.

## What is the difference between public and private apps?
Public apps have their source code hosted in a publicly accessible GitHub repository.

Private apps have their source code hosted in a private (non-publicly accessible) GitHub repository or are created when a developer uploads a ZIP file containing the source code and assets to the PhoneGap Build service.

## I've lost my signing key. Can Phonegap Build send it to me?
No, it is Phonegap Build's policy not to retrieve signing keys for users, for legal reasons. Hold on to them.

## Where do I go to find PhoneGap Build help?
Ask a question on our [community forum](http://community.phonegap.com), or ask us on [Twitter](http://twitter.com/PhoneGapBuild).
