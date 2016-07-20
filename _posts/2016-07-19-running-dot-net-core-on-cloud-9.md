---
layout: post
title:  "Running .NET Core on Cloud 9 IDE"
date:   2016-07-19 11:52:00 +0800
categories: dotnet-core cloud9
---

Cloud 9 was one of these things I signed up for way-back - I think it was being touted as an online Javascript IDE. Intrigued, I signed up for a free account, poked around a bit, didn't see anything that grabbed my attention, and promptly forgot about it. The recent [announcement](https://c9.io/blog/great-news/) that it was being bought by Amazon brought it back to the top of my memory, and so I logged back in to that old account. And golly gosh, hasn't it grown. Circumstances for me at the mment are such that a browser based IDE is very compelling, and Cloud 9 offer language-specfic development environments to be spun up as needed. But the thing that really caught my attention was the offer of a plain Ubuntu machine to run under the hood. Coupled with .NET Core running cross-platform, perhaps it could run here? It took a few attempts, as there are certain packages missing by default that .NET Core setup requires, but running through the following steps will get a .NET Core environment running.

1) Create plain Ubuntu workspace. Creates a container running Ubuntu 14.04:

```
joemeadway:~/workspace $ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty
```

2) Update and install:

```
sudo apt-get update
sudo apt-get install apt-transport-https
```

3) Follow steps at <https://www.microsoft.com/net/core#ubuntu>

- Add .NET Core apt-get source

```
sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
sudo apt-key adv --keyserver apt-mo.trafficmanager.net --recv-keys 417A0893
sudo apt-get update
```

- Install .NET Core

```
sudo apt-get install dotnet-dev-1.0.0-preview2-003121
```

4) Test it - initialise a console application

```
mkdir testapp
cd testapp
dotnet new
```
5) Run the Hello World app

```
dotnet restore
dotnet run
```

6) And just because you can, play with F# too...

All in all, very cool.

```
mkdir fsharp-consoleapp
cd fsharp-consoleapp
dotnet new -l F#
dotnet restore
dotnet run
```

6) Ta-daa!
