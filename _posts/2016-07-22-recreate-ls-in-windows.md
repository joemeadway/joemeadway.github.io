---
layout: post
title:  "Recreating the 'ls' command in Windows (and presumably any other command you fancy too)"
date:   2016-07-22 24:10:00 +0800
categories: powershell windows
---

A neat little thing picked up from a Stack Overflow post: <http://stackoverflow.com/questions/9362692/how-to-create-ls-in-windows-command-prompt> shows a quick replicating the `ls` function in Windows. It is a simple command to create a batch file containing the relevant commands to list the contents of a folder. Once created, typing `ls` on the command line invokes the batch file. 
