---
layout: post
title:  "Refreshing PATH in Powershell"
date:   2016-03-20 20:44:00 +0800
categories: powershell windows
---

Since using Chocolatey a fair bit to install stuff, kind of annoying to open a new window after installing to get a command line tool available - installing Node, for example, needs a new window to refresh the PATH variable in order to execute 'node' or 'npm'...

So, is there an equivalent to 

```
source ~/.bashrc
```

doing on Linux?

According to this on Stackoverflow, it's a case of grabbing the System environment Path variable, and assigning it to the current environment Path:


```
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User")
```

<http://stackoverflow.com/questions/17794507/reload-the-path-in-powershell>

*Updated 22/7/2016 - creating the function*

This works, but it's more than a little awkward to type or copy-paste this every time. So, we can wrap this up into a Powershell function:

```
function RefreshPath
{
	$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User")
}
```

Entering this into Powershell will create a function `RefreshPath`, which when called will do just that. But this will be discarded when the console window closes. To preserve it across all instances, we can update the Powershell profile, adding the function there.

To check whether you have a profile already, run 

```
Test-path $profile
``` 

true means you do, false means you don't. If you don't, 

```
New-item –type file $profile
``` 

will create one. Then 

```
Notepad $profile
``` 

(or the name of your favourite text editor), and paste the RefreshPath function into the profile. Save and exit, and each Powershell console you open from now on will have the RefreshPath method available.
