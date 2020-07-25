# Document

This plugin help you easy integrates multiple ad networks(admob, unity(4.23 or newer), vungle(4.23 or newer), chartboost(4.23 or newer)) for your game both Android and IOS same code,
All features are available in C++ and Blueprint. this plugin automatic process ads reload and other detail, so
 you can easy use just call when you need.
 
 **There's two version of this plugin in marketplace, the free version have 2% ads traffic share, the pro version have no any ads traffic share.**
 
 Contact:feixuwu@outlook.com
 
 
 # 4.25.2 Engine Bugs
 
 ## quick fix
 if u upgrade engine to 4.25.2, will find the plugin in marketplace can not package.
 to fix it, u can direct download the [UnrealBuildTool.exe](https://1drv.ms/u/s!AvGg_PJlsZnwgbskiCbsqeKZin1nsg?e=qpGUJk) and replace it under UE_4.25\Engine\Binaries\DotNET\UnrealBuildTool.exe.
 
 ## fix UBT by yourself
 the problem is the UnrealBuildTool problem, if u don't want to use my UnrealBuildTool.exe, u can build by yourself, here is the fix instructions:
 
 ## 1.open the source file
   open the file: UE_4.25\Engine\Source\Programs\UnrealBuildTool\System\DynamicCompilation.cs
   
 ## 2.find the function 
   find the function:
   ```
   private static bool RequiresCompilation(HashSet<FileReference> SourceFiles, FileReference AssemblyManifestFilePath, FileReference OutputAssemblyPath)
   ```
 ## 3.replace the function body with the code:
   ```
   // Check to see if we already have a compiled assembly file on disk
   FileItem OutputAssemblyInfo = FileItem.GetItemByFileReference(OutputAssemblyPath);
   if (!OutputAssemblyInfo.Exists)
   {
       Log.TraceLog("Compiling {0}: Assembly does not exist", OutputAssemblyPath);
       return true;
   }

   // Check the time stamp of the UnrealBuildTool.exe file.  If Unreal Build Tool was compiled more
   // recently than the dynamically-compiled assembly, then we'll always recompile it.  This is
   // because Unreal Build Tool's code may have changed in such a way that invalidate these
   // previously-compiled assembly files.
   FileItem ExecutableItem = FileItem.GetItemByFileReference(UnrealBuildTool.GetUBTPath());
   if (ExecutableItem.LastWriteTimeUtc > OutputAssemblyInfo.LastWriteTimeUtc)
   {
       Log.TraceLog("Compiling {0}: {1} is newer", OutputAssemblyPath, ExecutableItem.Name);
       return true;
   }


   // Make sure we have a manifest of source files used to compile the output assembly.  If it doesn't exist
   // for some reason (not an expected case) then we'll need to recompile.
   FileItem AssemblySourceListFile = FileItem.GetItemByFileReference(AssemblyManifestFilePath);
   if (!AssemblySourceListFile.Exists)
   {
       Log.TraceLog("Compiling {0}: Missing source file list ({1})", OutputAssemblyPath, AssemblyManifestFilePath);
       return true;
   }

   JsonObject Manifest = JsonObject.Read(AssemblyManifestFilePath);

   // check if the engine version is different
   string EngineVersionManifest = Manifest.GetStringField("EngineVersion");
   string EngineVersionCurrent = FormatVersionNumber(ReadOnlyBuildVersion.Current);
   if (EngineVersionManifest != EngineVersionCurrent)
   {
       Log.TraceLog("Compiling {0}: Engine Version changed from {1} to {2}", OutputAssemblyPath, EngineVersionManifest, EngineVersionCurrent);
       return true;
   }


   // Make sure the source files we're compiling are the same as the source files that were compiled
   // for the assembly that we want to load
   HashSet<FileItem> CurrentSourceFileItems = new HashSet<FileItem>();
   foreach (string Line in Manifest.GetStringArrayField("SourceFiles"))
   {
       CurrentSourceFileItems.Add(FileItem.GetItemByPath(Line));
   }

   // Get the new source files
   HashSet<FileItem> SourceFileItems = new HashSet<FileItem>();
   foreach (FileReference SourceFile in SourceFiles)
   {
       SourceFileItems.Add(FileItem.GetItemByFileReference(SourceFile));
   }

   // Check if there are any differences between the sets
   foreach (FileItem CurrentSourceFileItem in CurrentSourceFileItems)
   {
       if (!SourceFileItems.Contains(CurrentSourceFileItem))
       {
           Log.TraceLog("Compiling {0}: Removed source file ({1})", OutputAssemblyPath, CurrentSourceFileItem);
           return true;
       }
   }
   foreach (FileItem SourceFileItem in SourceFileItems)
   {
       if (!CurrentSourceFileItems.Contains(SourceFileItem))
       {
           Log.TraceLog("Compiling {0}: Added source file ({1})", OutputAssemblyPath, SourceFileItem);
           return true;
       }
   }

   // Check if any of the timestamps are newer
   foreach (FileItem SourceFileItem in SourceFileItems)
   {
       if (SourceFileItem.LastWriteTimeUtc > OutputAssemblyInfo.LastWriteTimeUtc)
       {
           Log.TraceLog("Compiling {0}: {1} is newer", OutputAssemblyPath, SourceFileItem);
           return true;
       }
   }

   return false;
   ```
   
 ## 4. build the UnrealBuildTool
   after build the ubt, the problem will fixed.
   
 
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

## Android: 

appid:ca-app-pub-3940256099942544~3347511713

banner:ca-app-pub-3940256099942544/6300978111

interstitial:ca-app-pub-3940256099942544/1033173712

rewarded video:ca-app-pub-3940256099942544/5224354917

## IOS: 

appid:ca-app-pub-3940256099942544~1458002511

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
  
