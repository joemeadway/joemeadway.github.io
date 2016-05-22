---
layout: post
title:  "Beginning to look at ASP.NET Core and VS Code tutorial"
date:   2016-03-21 08:24:28 +0800
categories: asp.net asp.net-core yeoman
---

Running through the tutorial steps here: [https://code.visualstudio.com/docs/runtimes/ASPnet5](https://code.visualstudio.com/docs/runtimes/ASPnet5)

Couple of things to note

1) As of 21/3/2016, there is a bug in Node meaning Yeoman doesn't pick up keypresses (latest bug report [https://github.com/nodejs/node/issues/5384](https://github.com/nodejs/node/issues/5384)). Or more accurately in my case, the second time I ran Yeoman, on the first modal screen, keypresses were not picked up. So, running

```
yo aspnet
```

becomes impossible, since you cannot select the type of solution to scaffold. Instead, you need to run

```
yo
```

and hope that aspnet is the first option on the list. The other issue with this method is that I haven't worked out how to pass parameters to the aspnet generator - so for example, the default aspnet site uses gulp as default build agent, and unable to switch to grunt.

**Update** This bug was fixed in version Node version 6.2.0, and updating allow you to select options in the first screen of Yeoman, which in turn allows the passing of parameters (such as --grunt) into the command

2) The .Net Version Manager (DNVM) toolset is not included by default in Visual Studio Code. In short, the DNVM is designed to make it easier to switch between builds of DNX (the .Net Execution Environment). dnu is a particular tool within it to make package management within a solution easier. Installing the full version of Visual Studio will install this toolset, but I'm currently just running Code. So, following the main ASP.NET Core repo instructions here: https://github.com/aspnet/home/

```
&{$Branch='dev';$wc=New-Object System.Net.WebClient;$wc.Proxy=[System.Net.WebRequest]::DefaultWebProxy;$wc.Proxy.Credentials=[System.Net.CredentialCache]::DefaultNetworkCredentials;Invoke-Expression ($wc.DownloadString('https://raw.githubusercontent.com/aspnet/Home/dev/dnvminstall.ps1'))}
Powershell command installs the toolset.
```

Refresh the PATH, and off you go...

Running `dnvm` brought up a setup input offering to install a DNX runtime environment. Saying yes, whirred a bit, after which `dnvm list` showed

```
Active Version           Runtime Architecture OperatingSystem Alias
------ -------           ------- ------------ --------------- -----
  *    1.0.0-rc1-update1 clr     x86          win             default
```

Hurrah!

After all that, `dnu restore` started downloading packages and everything was gravy.
