---
layout: post
title:  "Refreshing PATH in Powershell"
date:   2016-03-20 20:44:00 +0800
categories: powershell windows
---


Since using Chocolatey a fair bit to install stuff, kind of annoying to open a new window after installing to get a command line tool available - installing Node, for example, needs a new window to refresh the PATH variable in order to execute 'node' or 'npm'...

So, is there an equivalent to 

source ~/.bashrc

on Linux?

According to this on Stackoverflow, it's a case of grabbing the System environment , and assigning it to the current Path
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User")
http://stackoverflow.com/questions/17794507/reload-the-path-in-powershell

This works, but it's more than a little awkward to type or copy-paste this every time. So - create a little Powershell command to run this, and make path-refresh a command?

https://msdn.microsoft.com/en-us/library/dd878310(v=vs.85).aspx

http://stackoverflow.com/questions/9362692/how-to-create-ls-in-windows-command-prompt
