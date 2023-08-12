# AppReview
this is a UE5 plugin for App review.

# Get Start
this plugin only have two function, one for android and the other for ios, user can wrapper in one blueprint function.
to open your game in apple store for review, you need your app store id.


![ScreenShot](img/app_review.png)


# Android Tips
please understand, in android, google decide if the app review dialog will popup, there's no way 100% to make sure the app review dialog popup, if this is not what you expect, please don't buy this plugin.

to make it works on android platform, there's some tips you should read first:

1. your app should in google play store.
2. test use internal app sharing, this is the [document](https://developer.android.com/guide/playcore/in-app-review/test#internal-app-sharing)
3. when you first open the app, it will display app review dialog, but after that, you will not see the app review dialog,
   to make it works again, first delete your review in google play if you already give a review for the app, then you need clear data and cache of google play store, after done all of these, start your game again,
   the app review dialog will works again.
4. don't trigger app review with a button, since google have quota of app review, the app review dialog may not popup,
   if you put a button to trigger app review, player may click the button but can not see anything happen.
   you should try popup app review when level finish, even the dialog not popup, your game logic still continue works.


# Example project
here is the [example project](https://1drv.ms/u/s!AvGg_PJlsZnwgcwi0mLQx8476A4qrg?e=lPzwls), u can build and install on your phone,
when u click the button, it will open google play and apple store to review.




  
