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

## 1.9.2
 fix android univeral abb package problem.

## 1.9.0
 upgrade firebase cpp sdk to 8.4.0.

# RoadMap

## custom crashlytics
 will add this feature in May 2021. here is the official document for android https://firebase.google.com/docs/crashlytics/customize-crash-reports?platform=android

# FAQ

## why I package fail with 4.26 for android
  here is the solution, login firebase console and create an realtime database, download the google-service.json,put it under Project/Content/google,
  the package should success.

## why my valueListener/ChildLister stop working after some time?
 the reason is your databaseref GC by the system, so to avoid this, u need save the databaseref node to a variable,
 after save as a variable, the databaseref node will not GC by system, then the valueListener/ChildListener will works as u expect.
 
## I bought EasyAds Pro and EasyFirebase Pro both, and use this two plugin in one project, android package success, but ios package fail, how to fix it?
 this problem is fixed, if u use latest easyads pro and easyfirebase pro.

  


