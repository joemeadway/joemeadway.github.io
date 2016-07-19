---
layout: post
title:  "Running .NET Core on Cloud 9 IDE"
date:   2016-07-19 11:52:00 +0800
categories: dotnet-core cloud9
---

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

6) Ta-daa!