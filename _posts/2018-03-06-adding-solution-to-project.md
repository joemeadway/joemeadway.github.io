---
layout: post
title:  "Opening CLI-created .NET project in Visual Studio"
date:   2018-03-06 11:30:00 +0800
categories: .net
---

-  With Created project

1) dotnet new sln
2) dotnet sln add <csproj file>


- In VS

1) Open .csproj in VS. The automatically creates an .sln file above this
2) Right-click on soultion, add any additional csproj files

End result of both is a file structure that doesn't necessarily follow the traditional sln > file-for-project.

