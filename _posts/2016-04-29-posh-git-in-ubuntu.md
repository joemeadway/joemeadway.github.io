---
layout: post
title:  "Setting up posh-git-bash, for Posh-Git goodness on linux"
date:   2016-04-29 20:45:28 +0800
categories: linux ubuntu git posh-git
---

[Posh-Git][posh-git] for Windows Powershell is pretty nifty, and become something of an invaluable crutch for me while learning to use git. So imageine the joy to discover a port for the bash shell.

[posh-git-bash][posh-git-bash]

Install steps in the readme worked as described:

- clone the repostory
- update your `~./bashrc` file
- update the `PROMPT_COMMAND` variable

to add the posh-git style annotations to the prompt. The only part I had to do in addition to this was to add the final `PROMPT_COMMAND` update into the `~/.bashrc` file too, that way the goodness is loaded every time a terminal window is opened.
 
[posh-git-bash]: https://github.com/lyze/posh-gvit-sh/blob/master/README.md
[posh-git]: https://github.com/dahlbyk/posh-git