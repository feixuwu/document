# Document

This plugin help you easy integrates multiple ad networks(admob, unity(4.23 or newer), vungle(4.23 or newer), chartboost(4.23 or newer)) for your game both Android and IOS same code,
All features are available in C++ and Blueprint. this plugin automatic process ads reload and other detail, so
 you can easy use just call when you need.
 
 **There's two version of this plugin in marketplace, the free version have 2% ads traffic share, the pro version have no any ads traffic share.**
 
 Contact:feixuwu@outlook.com
 
 # AdNetworks
 Admob
 
 Unity(4.23 or new version)
 
 ChartBoost(4.23 or new version)
 
 Vungle(4.23 or new version)
 
 # New Feature:Custom Load and Custom Show(Pro only)
   the EasyAds Pro allow the users to load and show ads wtih custom ad unit in code. this means you can use as many ad unit as you can,
 you are not limited can only use a single interstitial and a single rewarded video.
 here is the tutorial video:  [![tutotial video](https://i9.ytimg.com/vi/vI-uF5lHc64/mq2.jpg?sqp=CMGGuPQF&rs=AOn4CLA_luwU7Yu1ml9RuBCHTIsEQoG8QQ)](https://youtu.be/vI-uF5lHc64)
 
 # Get Start(2 step)
 
 Here is a tutorial video 
 [![how to use this plugin](https://i9.ytimg.com/vi/uoAdOpi1wCQ/mq2.jpg?sqp=COWCuPQF&rs=AOn4CLCl0FDi22YcRvuEfQVZtjW6gQjGsQ)](https://youtu.be/uoAdOpi1wCQ)
 
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
   
   in level blueprint, on event BeginPlay call this function:
   
  ![ScreenShot](img/debug.png)
  
  from the out debug message, you can find the error number, each number describle a reason:
  
  ### 0 ERROR_CODE_INTERNAL_ERROR
  
  Something happened internally; for instance, an invalid response was received from the ad server.
  
  ### 1 ERROR_CODE_INVALID_REQUEST
  
  The ad request was invalid; for instance, the ad unit ID was incorrect.
  
  ### 2 ERROR_CODE_NETWORK_ERROR
  
  The ad request was unsuccessful due to network connectivity.
  
  ### 3 ERROR_CODE_NO_FILL
  
  The ad request was successful, but no ad was returned due to lack of ad inventory.
  
# Admob Test Ads

Android: appid:ca-app-pub-3940256099942544~3347511713

banner:ca-app-pub-3940256099942544/6300978111

interstitial:ca-app-pub-3940256099942544/1033173712

rewarded video:ca-app-pub-3940256099942544/5224354917

IOS: appid:ca-app-pub-3940256099942544~1458002511

banner:ca-app-pub-3940256099942544/2934735716

interstitial:ca-app-pub-3940256099942544/4411468910

rewarded video:ca-app-pub-3940256099942544/1712485313

# FAQ
 
## I bought EasyAds Pro and EasyFirebase Pro both, and use this two plugin in one project, android package success, but ios package fail, how to fix it?
  this is a problem of plugin conflict in ios, since this two plugin use part of same framework, so to fix it, need to change UBT code.
  I build 4.24 and 4.25 UBT and upload to google drive, to fix the plugin conflict in ios, download the zip file and unzip it, put the UBT replace the UBT in engine,
### 4.24:
 1.[UBT 4.24](https://drive.google.com/file/d/1hA12ZzBzJJgKZZNspeYTZplanKomNz6_/view?usp=sharing)
 download and unzip, put the UnrealBuildTool.exe to 
 UE_4.24\Engine\Binaries\DotNET\
 
 2.package for ios again,then it will success.

### 4.25:
1.[UBT 4.25](https://drive.google.com/file/d/1wxWlS-UcAxG03EqC1vPzsjUszov8iCJY/view?usp=sharing)
download and unzip, put the UnrealBuildTool.exe to 
UE_4.25\Engine\Binaries\DotNET\

2.package for ios again,then it will success.


# License
   **free version share 2% ads traffic, pro version have no any ads traffic share.**
  
