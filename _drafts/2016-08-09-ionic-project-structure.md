---
layout: post
title:  "Ionic project structure"
date:   2016-02-15 20:30:00 +0800
categories: ionic2 
---

Within a standard Ionic app, the project structure is that of a typical Cordova app.

**./www/index.html**

The main entry point for an app, purpose is to set up script and CSS includes, and start running ("bootstrap") the app. But other than this, not much to do in here. Is a standard HTML page, scripts and stylesheets included as you would on any other HTML page.

**./app/app.ts**

Pre-compiled code, where the bulk of the app will be. Running `ionic serve` transpiles the Typescript (or ES6) code in here to regular Javascript.

Every app has a root component, which controls the rest of the application. In the standard v2 project, it looks like:

```
@Component({
  templateUrl: 'build/app.html'
})
class MyApp {
  constructor() {
  }
}

ionicBootstrap(MyApp)
```

while the one included in the cutePuppyPics app looks like:

```
@Component({
  template: '<ion-nav [root]="rootPage"></ion-nav>'
})
export class MyApp {

  private rootPage: any;

  constructor(private platform: Platform) {
    this.rootPage = TabsPage;

    platform.ready().then(() => {
      // Okay, so the platform is ready and our plugins are available.
      // Here you can do any higher level native things you might need.
      StatusBar.styleDefault();
    });
  }
}

ionicBootstrap(MyApp);
```

we can see in both the template for the app being set. In the default, the template is set explicitly. In the puppies app, the root is set via a property which is in turn set in the constructor. Finally, the app itself being bootstrapped.

**./app/app.html** or **./app/pages/tabs/tabs.html** or **whatever you set it to be**

The main template, compiled. There is a corresponding .ts file, which almost looks like a code-behind type approach

*to do - check up similarity with WinForms...*

 