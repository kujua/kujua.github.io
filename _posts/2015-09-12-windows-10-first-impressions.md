---
layout: post
title: Windows 10 - First Impressions
sortorder: 4075
date: 2015-09-12
updated: 2016-1-25
ignoredate: 0
disqus_comments: 1
disqus_identifier: 2015-09-12-windows10-impressions
---

**Windows 10 finally arrived on my developer machine. Read here about the first impressions with the "RTM" version.**

Of course, Microsoft tries to convince us that there are only update versions and no RTM version.

Following are a few impressions I got from working with Windows 10 for a couple of weeks. I am not talking about a beta version, but about the release version.

Before we start I have to emphasize that I am working (and earning money) with development products from Microsoft since the beginning 90s. Not exclusively, but most of this time. In the last 10 years the percentage changed and other operating systems and development environments came into the mix. This does not mean I am a fanboy, it just means that I would like Microsoft to succeed - for my own profit as well.

Being a developer also means to be a user of Windows since version 3.0, a journey with all highs and lows.

**Updates**

This is my biggest problem: even with the Pro-version it is not possible to schedule system updates for a convenient time. I divide my time between Europe and Africa and in Kenya I am using a satellite internet connection. This connection is in fact metered during the day, but unlimited downloads are possible during the night. There is no way - at least I have not found it - to tell Windows 10 that it should not download updates during certain hours. I can schedule the restart, but by then everything has already happened.

Also, don't forget to uncheck the download option for other Microsoft products - especially Office. Otherwise another 1 GB and more will be downloaded on a monthly basis. Why Office needs so many and big updates is beyond me, actually.

**Font Rendering**

Some applications' text renders awfully. Characters are blurry and almost unreadable. For exmple, it happened to me with Enterprise Architect. Menu text, diagram text etc. was so badly rendered that I could not work. Fortunately it is possible to fix this. In the exe-file properties dialog in the tab 'Compatibility' it is possible to uncheck 'DPI Compatibility' and after a restart of the application everything looked for me as it should be.

![Properties Dialog]({{ site.url }}/res/disabledpi.jpg)

I have not tried it myself, but there seems to be a problem with font rendering on high dpi monitors. A problem that begs belief after this long beta testing phase.

**Edge**

Microsoft is selling Edge as the new and future proof browser. We all know that some features like extensions are simply missing and it is not clear when they will be added.

The startup time of Edge reminds me of IE: sometimes it takes so long even to open a local page that I can start Chrome (which is not the fastest starter) and display the page I want before Edge renders it. I was thinking that it may have something to do with starting Edge the first time and subsequent starts will be faster, but the startup time is unpredictable and intermittent.

When I started Edge the first time, it asked me to import bookmarks from other browsers. I agreed and the result was very unexpected: All bookmarks were there, but in reversed order with the oldest on top and all the folders in reversed order as well. In Chrome 'News' is on the left side of the bookmark bar, in Edge it is in the overflow on the right, because it does not fit into Edge's bookmark bar. Is it really so difficult to get a feature like this right?

**Cortana**

As mentioned before, I am in different locations with my development laptop and this throws off all applications with location checking completely. My satellite internet connection in Kenya hits the first ground server in different places, in my case most of the time in Greece. This has funny - or not so funny - consequences. For example, my wife has a yahoo email address that she checks from time to time. Yahoo of course believes, that she is sitting in Greece and displays Greek text which we both can't read. Even deleting all cookies for the site and restarting did not help, the Yahoo website rechecked and all was in Greek again.

Cortana has a similar problem and displays news from Greece, weather from Athens and so on. Again, I did not find a switch to tell the program not to use the current location, but a defined one. This renders Cortana for me for some aspects more or less useless, because I get recommendations and information for a wrong location.

Otherwise am not really sold: searching does not really bring back my applications or files, too often Cortana goes to the internet and displays results I don't need. Probably this is a problem of me not using the program properly, but if it is not obvious then the UX is not as good as it should be.

**Default Settings**

As in previous Windows versions the default settings for Explorer etc. are geared towards normal users. It is no problem to reset some of the settings, for example to display hidden files, file extensions or empty folders. What I don't like is the change in setting the explorer views for folders. I like to have the file lists sorted by date with the latest file on top. A quick click on 'Apply to all folders' helped in Windows versions pre 10. But now it says 'Apply this setting to all folders of this type'.

![Folder Properties]({{ site.url }}/res/applytofolders.jpg)

Not only can't I see at one glance the type of the folder except seeing a different folder icon, but I have to click 'Apply' several times on different folders. If the settings are not changed again as it happened in previous versions is unknown so far.  

**For Developers**

The update on my development computer was coming late - I guess because of some applications on it that were not or still are not 100% compatible.

One of those applications is GenyMotion. This is actually an interesting example of an application that relies on a third party software or API that can't be controlled and is bitten by it. Some applications rely on APIs that are changed over night or just deprecated, like we all have seen with Twitter, Facebook and other big players.

GenyMotion needs VirtualBox to work and somehow there is a problem in the communication. The first complaints about non-compatibility with Windows 10 were raised in GenyMotion fora in April and there are still problems. VirtualBox was updated and I used the latest development version, but Oracle still says that VirtualBox is not yet compatible with Windows 10. This after months of beta testing and now two months after release. I got it to work, but from time to time GenyMotion just crashes. I am not blaming the product, it just shows not to be depending on something one can't control, as others have found out with applications based on Twitter or Facebook APIs.

Windows 10 brings the promise of universal apps and updated .Net libraries. One hyped feature is not available: the new ASP.NET version. It is a refactoring and rewrite of the current version and introduces new features. What I have seen so far it does not fill me with confidence that we get a lightweight framework. It is still in beta (which is more or less an alpha), though.

Visual Studio 2015 is RTM since July and I am using it on a regular basis. Overall it feels slower than before. For example, when opening a file I have opened several times before it sometimes stops, displays a window with a 'loading templates' message and then after a few seconds it displays the file. Starting VS 2015 also takes a while. VS was not a sprinter before, but now I wait a minute or two to see the start page. Waiting another 30 seconds to be logged in into TFS and then opening a solution with not more than 20 projects takes another 30-60 seconds. Sometimes at startup I see the 'creating MEF graph' message, almost always the 'loading components' message.

VS got better in telling the user what is going on, but there is always a slight delay in displaying or removing indicators for error etc. during editing. Fortunately compiling is working fast.

Opening an application that is taking longer to load reminds me of an unexpected 'feature': the operating system (in fact the explorer program) does not display the hourglass anymore. I click on a button in the task bar and nothing happens. The cursor stays in pointer mode and as a user I don't know if I was successful with my request or not. Photoshop is one of those programs that take time to start some background processes before they display the splash screen. VS at least displays the splash screen immediately.

I should mention that the only add-on or extension I use is NCrunch.

Universal apps are the latest Microsoft idea to get Windows 10 on many devices and also to make it easier for developers to create those applications. After a 3GB download all the SDKs and emulators were installed and I loaded one of the sample solutions. There are lots of Universal App samples on [Github](https://github.com/Microsoft/Windows-universal-samples) and I randomly tried to compile one. It did not work - more than 700 errors.

The reason is that one of the packages - actually the only package: Microsoft.NETCore.UniversalWindowsPlatform - was missing. For another solution I am working on I switched off the automatic loading of NuGet packages during build, so the needed package in the sample was missing. Clicking on the NuGet manager showed that the package is installed, so I uninstalled and tried to re-install. It did not work the first time, after a few times closing the solution and installing the package it worked. And no, the 'restore packages' option in the solution menu did not work.

Eventually I could compile and start the universal app; trying it on a device will have to wait, because Windows 10 for phones is not yet distributed.

**Verdict**

We all will see how Windows 10 will develop in the coming months. At the moment there are some quirks as described above. Apart from GenyMotion there were no crashes with the applications I used. Programs that use graphic cards heavily like Photoshop or games seem to work properly.

Some users have memory problems coming from old drivers, but I have not seen that. Monitoring Task Manager I have the feeling that more memory is used or nor freed, but it never goes beyond a certain limit. In average the operating system uses 2-2.4 GB on a 8 GB machine, so a computer with less memory might run Windows 10, but it will struggle with additional applications. I don't think anybody wants to run Visual Studio on a 4 GB machine, but it is certainly harder with Windows 10. Switching off certain features like Cortana can help.

Overall, all operating systems including OS X and Linux flavors like Ubuntu get very memory hungry and weighted down with non-necessary features, Windows 10 is not different. Privacy is another topic and all systems call 'home', more or less and more or less configurable.

For developers, Windows 10 should bring new opportunities, but at the moment it does not feel ready. We will see, if the promises will be fulfilled in future.  
