---
layout: post
title:  "Deploying Firebase Functions using the CLI from Windows"
date:   2018-08-05 14:44:00 +0800
categories: firebase-functions
---

Running default `firebase init`, and adding functions to the project. When the time comes to `firebase deploy`, you get an error along the lines of

```
... snip ...

i  deploying database, functions
Running command: npm --prefix "$RESOURCE_DIR" run lint
npm ERR! path C:\<redacted>\%RESOURCE_DIR%\package.json
npm ERR! code ENOENT
npm ERR! errno -4058
npm ERR! syscall open
npm ERR! enoent ENOENT: no such file or directory, open 'C:\<redacted>\%RESOURCE_DIR%\package.json'
npm ERR! enoent This is related to npm not being able to find a file.
npm ERR! enoent

npm ERR! A complete log of this run can be found in:
npm ERR!     C:\<redacted>\Roaming\npm-cache\_logs\2018-08-05T13_28_14_608Z-debug.log

Error: functions predeploy error: Command terminated with non-zero exit code4294963238
```

The fix for this was found [here](https://github.com/firebase/firebase-tools/issues/610#issuecomment-365907156)

1. Open `firebase.json` file
2. Where the file references `%RESOURCE_DIR%`, replace this with `functions`

The deployment should then run without error (though I had forgotten to [enable the App Engine Admin API](https://cloud.google.com/solutions/mobile/mobile-firebase-app-engine-flexible#creating-project)).