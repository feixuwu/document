# Document

This plugin help you easy integrates multiple ad networks(admob, unity(4.23only), vungle(4.23only), chartboost(4.23only)) for your game both Android and IOS same code,
All features are available in C++ and Blueprint. this plugin automatic process ads reload and other detail, so
 you can easy use just call when you need.
 Contact:feixuwu@outlook.com
 
 # AdNetworks
 Admob
 
 Unity(4.23 or new version)
 
 ChartBoost(4.23 or new version)
 
 Vungle(4.23 or new version)
 
 # Get Start(2 step)
 
 Here is a tutorial video 
 [![how to use this plugin](https://i.ytimg.com/vi/dRYf_u7S5lk/hqdefault.jpg?sqp=-oaymwEZCPYBEIoBSFXyq4qpAwsIARUAAIhCGAFwAQ==&rs=AOn4CLApWQTOHyc-FelbLr2xm8udbqkjdw)](https://youtu.be/dRYf_u7S5lk)
 
 ## 1. fill ad unit
   open Editor->Project Setting, find EasyAds fill the ad unit:
 
  ![ScreenShot](img/setting.PNG)
  
  
 ## 2. call function show ads
 in blueprint editor, when you want show show the ads, just call function "ShowBanner", "ShowInterstitial", "PlayRewardedVideo"
  ShowBanner:
  
  ![ScreenShot](img/showbanner.PNG)
  
  ShowInterstitial:
  
  ![ScreenShot](img/showinterstital.PNG)
  
  PlayRewardedVideo:
  
  ![ScreenShot](img/playvideo.PNG)
  
 Some times, you want to check if ads aviable, you can call "IsBannerReady", "IsInterstiralAdsReady", "IsRewardedVideoAdsReady"
  
  IsBannerReady:
  
  ![ScreenShot](img/checkBaner.PNG)
  
  IsInterstiralAdsReady:
  
   ![ScreenShot](img/checkInterstital.PNG)
   
  IsRewardedVideoAdsReady:
  
   ![ScreenShot](img/checkvideo.PNG)
   
   ## Read debug message to learn why ads load fail:
   
  ![ScreenShot](img/debug.PNG)
  
  the error number:
  
  ### 0 ERROR_CODE_INTERNAL_ERROR
  
  Something happened internally; for instance, an invalid response was received from the ad server.
  
  ### 1 ERROR_CODE_INVALID_REQUEST
  
  The ad request was invalid; for instance, the ad unit ID was incorrect.
  
  ### 2 ERROR_CODE_NETWORK_ERROR
  
  The ad request was unsuccessful due to network connectivity.
  
  ### 3 ERROR_CODE_NO_FILL
  
  The ad request was successful, but no ad was returned due to lack of ad inventory.
   
 # License
   free to use, and I will share 2% ads traffic. If your game earn a lot of money from ads, you may want buy the pro version, it will not share any ads traffic.
  
