---
layout: post
title: Windows 10 - Second Look
sortorder: 4072
date: 2016-01-28
ignoredate: 0
disqus_comments: 1
disqus_identifier: 2016-01-28-windows10-second-look
---

**A few weeks ago I wrote about my first impressions of Windows 10 [Windows 10 - First Look]({% post_url 2015-09-12-windows-10-first-impressions %}). Now I had more time to work with it and here are my findings.**

**Updates**

In the meantime I have found a way to switch off updates - at least I thought so.

Go into the Group Policy Editor (Run _gpedit.mmc_) and switch to nnn:

![Folder Properties]({{ site.url }}/res/gpedit_update.jpg)

Going back to the Settings dialog you will see the message: "lll" and the dropdown with the options is greyed out.

![Folder Properties]({{ site.url }}/res/gpedit_update.jpg)

So far so good. Later a notification popped up to indicate that updates can be downloaded. The message is a bit strange, though: "lll". So I opened the Windows Update-dialog and saw the update for Windows Defender listed. clicking on it was a one second delay and then it said, everything updated - this could not be right. How astonished was I when the Defender update history showed me that the update was already done. So it downloaded and installed the update despite acknowledging that I should be notified _before_ the download and installation. Back to square one and back into the Group Policy Editor.

There is ...

I understand that experienced system admins may know all these subtle settings, but for me this looks odd. In 8.1 and before a similar settings worked fine, so I give Microsoft the benefit of the doubt and think this is - another - bug.

Also, I had to go into the Store application to switch of the automatic app updates.

When I try to download updates manually I more than often get an error message that the download failed.

**Search**

In my first article about Windows 10 I I complained about Search results and even weeks after the Indexer running I can't see anything useful. Cortana is switched off and searching first goes to the web. Clicking on the option _Files_ takes me to the Explorer. Most probably there is somewhere a registry entry fixing this, but I am really getting tired of all this.

**No rights to delete a folder as Administrator**

This is the most curious - and annoying - thing I have experienced on a Windows machine.
When I upgrade from 8.1 to 10, a folder Windows.Old was created. After 30 days the option to revert to 8.1 disappeared as expected. I was thinking that the backup folder will be deleted as well, but this was not the case. No problem, right click on the folder and press delete. this is what I saw:

![Folder Properties]({{ site.url }}/res/norights.jpg)

Seriously? I am the admin of this machine, who else should be able to delete a folder? I understand that this may be a way to protect the folder for the time of the revert window, but after this the folder should be freed.

I could not set access rights, because I was not allowed to do it, everything was greyed out.

There are ways to get rid of the folder, but am less than impressed by this "hand holding". ...

**Edge**

Edge is not ready - simple as that. Sometimes it is fast, sometimes slow and I have no idea why. Simple things like _Save as..._ or ... are not implemented.

**Antimalware Service Executable**

Starting with Windows 8.1 I had problems with Defender, Windows' resident antimalware program. On a computer with a harddisk it is running for about 20 minutes after starting the machine, even when nothing has changed since switching off. This behavior is especially problematic during development with Visual Studio. Lots of temporary files are created and Defender feels it necessary to scan all the time taking 100% of the disk usage. Switching off temporarily is the only solution.

In Windows 10 the situation is worse and Defender seems to be more intrusive. There is the option to turn it off, but then the rundll32 service starts and I assume it is still doing the scan for a while. Switched off does not mean off as well, because the operating system switches it back on when it thinks this is necessary.

On a machine with a SSD the impact is less and I assume most developers have a machine with SSD anyway. Still, this behavior is something I put down to bad programming. In business environments there are fewer machines with SSD, although most of them are on Windows 7 anyway with no plan to upgrade soon.

**More Issues**

End of January 2016 there are more construction sites left than I expected:
- ASP.NET VNext (=ASP.NET 5 and the name may change in future) is still on RC1. RC2 and 1.0.0 Release are TBD on the roadmap published on GitHub. The name seems so confusing that companies are already searching for developers experienced with ASP.NET 5.
- Rumors say that Windows Phone on ARM processors will be dead, instead MS will focus on Intel processors with Windows 10 and Universal Apps.
- MS's marketing is not at its best. The blog entry about Windows 10 support for Skylake processors in future stirred up journalists. Headlines like "Windows versions before 10 won't run on Skylake computers" brought up heated discussions all over the world, from tech sites to mainstream newspapers. Listening to journalists for example on the Windows Weekly podcast did not clear the confusion, in fact three people discussed this issue for an hour and after it it still was not completely clear what is meant by MS.
Sky Lake: http://www.theverge.com/2016/1/16/10780876/microsoft-windows-support-policy-new-processors-skylake
- Another marketing glitch happened with OneDrive: first users were notified that their limit was downsized, later this was reverted - at least for some users.
- Surface Book and Pro 4 seem to have a plethora of faults, including drained batteries during sleep, problems with the firmware and overheating.

**Verdict**

Windows 10 in its 29th July state is a big construction site. Compatibility is good - as it was already in 8 and 8.1. The annoying issues were promised for the big November release, which apparently was called _Threshold2_ and was a mess in itself. First it was pushed to computers, then it was withdrawn because of problems and later came back again.

As a developer I am not sure about the Windows 10-release and all the promises. I can create Universal Apps, but apart from my desktop they won't run anywhere on a consumer device. Why spend time (and money) to develop an app, if the future is less than sure.

Remember the talk about _Continuum_? "Connect your phone to the docking station and work on a big screen with mouse and keyboard - just like a PC". Now it turns out that Universal Apps can run only full-screen from the phone. The problem is: there are not many apps apart from Microsoft Office. So the whole idea comes down to run Office via the dock.

Remember the impressive Hololens presentation? Many of us had already the picture in their mind of wearing it around Christmas time and having exciting times with it? Again failed, because the presentation was partly faked. The field-of-view is much more restricted than shown and people who tried it say it is more like peeping through a letterbox without peripheral vision. You can see an image here in a Verge article: [Verge Hololens](http://www.theverge.com/2015/6/18/8809323/microsoft-hololens-field-of-view-kudo-tsunoda).
It does not matter much, that the release date for the consumer device is far in the future and that the development version for the business edition will be $3000 and delivered sometimes in 2016.

All in all, I feel a bit disappointed. In my opinion Microsoft came out with the system release and the promises way too early. Of course, they did not want to lose the US holiday business, but am not sure if a half-baked system will bring masses of consumers and masses of developers. One can make people excited for a certain time period, but there is a limit and beyond this limit people will look elsewhere for excitement.

I was due to buy a new development machine and I was writing together which technologies I use and will use in the next 3-5 years. In this list Microsoft technologies - Visual Studio, .Net - are just a percentage, other technologies and languages like Erlang/Elixir, Clojure, Akka, Xamarin for Android/iOS or Aurelia take over a chunk of my development time. So it was almost natural to look at other options like Linux or Mac.

In fact I was awaiting Surface Pro 4 and the Surface Book surprised me and others. Looking at the price of the latter and the fact it is a generation 1 release and riddled with faults, I opted for a MacPro. My old machine can handle Visual Studio 2015 development well, and if I am so inclined I can have virtual machines of Linux and Windows on the Mac. Not that I think the closed world of Apple is so much better, but at least I have the impression that I am the owner of my own machine and not just a guest.