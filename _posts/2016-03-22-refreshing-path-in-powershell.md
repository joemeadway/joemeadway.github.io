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

This works, but it's more than a little awkward to type or copy-paste this every time. It seems like this would be ideal to wrap up into a command that could be called as and when needed - either creating a Powershell function, or perhaps a batch file that does the same thing. 

Along these lines, <http://stackoverflow.com/questions/9362692/how-to-create-ls-in-windows-command-prompt> shows quite a neat way of replicating the `ls` function in Windows, which creates a batch file with the relevant commands to list the contents of a folder. It suggests the same approach would work to create a 'refresh-path' command, but it could get complicated to figure out depending on how to do the equivalent of the Powershell command above in a batch file. 