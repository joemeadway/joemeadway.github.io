---
layout: post
title:  "Quick start getting an Ionic2 app up and running on Genymotion"
date:   2016-08-08 21:10:00+0800
categories: ionic2 android
---

Largely running through the steps here: <http://ionicframework.com/docs/v2/getting-started/installation/>

1. Install Ionic, and Cordova

```
npm install -g ionic@beta
npm install -g cordova
```

2. Create the Getting Started app

```
ionic start cutePuppyPics --v2
```

3. Check it out in the browser

```
cd cutePuppyPics
ionic serve
```

If you have a choice of which address to use, `localhost` is always a good start... The browser should open up automatically.

4. Install Genymotion. 

This is the emulator recommended by Ionic, as being quicker and more flexible than the default. It's not especially clear on the [Genymotion website](https://www.genymotion.com/download/), but you still need to make sure you have the Android SDK installed already on your machine. One way of doing this is installing Android Studio, which comes with the added benefit of being able to waste time poking around that for an hour or so... The down side with Genymotion is that it does involve some degree of hoop jumping to register etc. - it's a freemium product and they will try and persuade you to upgrade. But this seems like a decent way of finding out if the tool is worth paying for to meet your needs.

Note: all of this SDK installation may highlight the usefulness of a `RefreshPath` command, [perhaps](/2016/03/20/refreshing-path-in-powershell.html). 

5. Once SDK installed and Genymotion setup with a device image downloaded, start the device image. Then run

```
ionic run android
```

And hurrah! the app that was just running in the browser will fire up in the emulator running in Genymotion.