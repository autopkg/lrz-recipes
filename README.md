LRZ AutoPkg Recipes
===================
Our public repository of useful recipes for everyone.

SharedProcessors
================
NotifyPatchServer
-----------------
NotifyPatchServer is a [POST-Processor](https://github.com/autopkg/autopkg/wiki/PreAndPostProcessorSupport) for AutoPkg.
It takes the Package which is generated by autopkg, unpacks it (and it's payload) and tries to find an AppBundle inside.
After finding the AppBundle it extracts its Version, BundleIdentifier and sends it to your predefined [PatchServer](https://github.com/brysontyrrell/PatchServer).

Configuration:
```
defaults write com.github.autopkg PATCH_URL https://your.patchserv.er/
defaults write com.github.autopkg PATCH_TOKEN YoUrAcCeSsToKeNfOrIt
```

Usage:
```
autopkg run Firefox.jss --post de.lrz.SharedProcessors/NotifyPatchServer
autopkg run GoogleChrome.pkg --post de.lrz.SharedProcessors/NotifyPatchServer
```

You can also add ``STOP_IF_NO_JSS_UPLOAD=false`` as additional key, if you want to make sure it runs after every recipe.

Before NotifyPatchServer works you will have to add the Application using [PatchStarterScript](https://github.com/brysontyrrell/Patch-Starter-Script) (or doing this manually).

VersionFix
----------
VersionFix is a Processor you can use in pkg-recipes. It removes some of the not necessary string to have a proper package name afterwards.

UserAgentGenrator
-----------------
UserAgentGenerator generates a Fake Useragent for the use with URLDownloader or URLTextsearcher.
This has proven to trick some defective automatisms, who ban you based on your UserAgent, if you want to download Apps.