# EasyFirebase
this is a firebase basic plugin for unreal engine 4 mobile developer, both c++ and blueprint supported.


# Get Start

 ## Initlize
 befor use this plugin, u need first initlize firebase in level begineplay
 ![ScreenShot](img/initlize.PNG)

 ## anonymously login
 for guest user, we can use anonymously login:
 ![ScreenShot](img/anonymously.PNG)

 ## email login
 register email user with password:
 ![ScreenShot](img/create_email_user.PNG)
 
 login with email and password:
 ![ScreenShot](img/loginemailuser.PNG)

 ## set value
 set value to firebase realtime database:
  ![ScreenShot](img/setvalue.PNG)

 ## get value
 get value from firebase realtime database:
  ![ScreenShot](img/readvalue.PNG)


# firebase auth tutorial:
[![how to use firebase auth](https://i.ytimg.com/vi/10d-iv9P6Jk/hqdefault.jpg?sqp=-oaymwEZCNACELwBSFXyq4qpAwsIARUAAIhCGAFwAQ==&rs=AOn4CLDV22XRSmrQsG8bx0XYITL7P83frg)](https://youtu.be/10d-iv9P6Jk)

# firebase realtime database tutorial:
[![how to use firebase realtime database](https://i.ytimg.com/vi/5aQ6J3tj3CU/hqdefault.jpg?sqp=-oaymwEZCNACELwBSFXyq4qpAwsIARUAAIhCGAFwAQ==&rs=AOn4CLApWT56tCHFuqmGY3cH3G6W9PL1Ww)](https://youtu.be/5aQ6J3tj3CU)


# Release note
## 1.10.00
 upgrade firebase cpp sdk to 10.3.0, remove WRITE_EXTERNAL_STORAGE from plugin.

## 1.9.6
  add blueprint transaction support, you can direct call RunTransaction on FirebaseDatabaseRef.
  here is an example:![ScreenShot](img/trasaction.PNG)
  
## 1.9.5
fix bug:in some case, game center login will cause crash.

## 1.9.3
support bitcode for ios.

## 1.9.2
 fix android univeral abb package problem.

## 1.9.0
 upgrade firebase cpp sdk to 8.4.0.
 
## 1.8.7
fix google play login crash.

# RoadMap

## custom crashlytics
 will add this feature in May 2021. here is the official document for android https://firebase.google.com/docs/crashlytics/customize-crash-reports?platform=android

# FAQ

## get facebook user photo?
since meta change their policy of get user photo, now, with firebase User, u can call photo_url() to get the url, but u can not get the user photo with this url, let's call
this url old url, u need combine a new url which can get the real user photo:

new url = "old url" + height=500&access_token=token, u can get the token from RequestFacebookCredential call back,

with the new url, u can request it and get the user's photo.


## apple login?
  ### for engine >=5.1 and plugin >=1.10.7()
  please first check your plugin version and engine version, if your engine is 5.1 or more newer than 5.1, and plugin is 1.10.7 or more newer, then the 
  apple login is default enabled, u don't need to do anything, the project can use apple login. please do remember the condition:(engine >=5.1 and plugin >=1.10.7).
  
  ## for other situation
  if not passed the preview condition, u need watch the apple login tutoria [video](https://youtu.be/QFqad0RZb4Q)
  and do what the video told u do,finaly u need edit the Plugins/EasyFirebasePro/Source/EasyFirebase/EasyFirebase.Build.cs, uncomment the line PublicDefinitions.Add("WITH_APPLE_LOGIN=1");
  after done all of this, the project can use applog login now.

## Realtime database GetValue sometimes get old value
  to fix it, before u call GetValue, u need first call SetKeepSynchronized(true), then u will always get latest value.
  ![ScreenShot](img/get_latest_value.png)

## I got error when try upload release symbol for Crashlytics
  here is the solution, before run "gradlew.bat app:uploadCrashlyticsSymbolFileRelease", run "gradlew.bat app:processReleaseGoogleServices" first,
  it will fix the problem.

## why I package fail with 4.26 for android
  here is the solution, login firebase console and create an realtime database, download the google-service.json,put it under Project/Content/google,
  the package should success.

## why my valueListener/ChildLister stop working after some time?
 the reason is your databaseref GC by the system, so to avoid this, u need save the databaseref node to a variable,
 after save as a variable, the databaseref node will not GC by system, then the valueListener/ChildListener will works as u expect.
 
## I bought EasyAds Pro and EasyFirebase Pro both, and use this two plugin in one project, android package success, but ios package fail, how to fix it?
 this problem is fixed, if u use latest easyads pro and easyfirebase pro.

  


