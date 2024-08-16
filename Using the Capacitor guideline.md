>[!info] Please find the original documentation here https://capacitorjs.com/docs/getting-started/with-ionic


# what is capacitor 

> Capacitor is a cross-platform native runtime that makes it easy to build performant mobile applications that run natively on iOS, Android, and more using modern web tooling. Representing the next evolution of Hybrid apps, Capacitor creates **Web Native apps**, providing a modern native container approach for teams who want to build web-first without sacrificing full access to native SDKs when they need it.


At its core, Capacitor creates a "Web Native" environment, focusing on enabling modern web apps to run across platforms without compromising performance or access to native features. Developers can use HTML, CSS, and JavaScript while accessing native device features like the camera, GPS, or filesystem through plugins. Capacitor’s architecture is also backward-compatible with many existing Cordova plugins, simplifying migration for those who have been using older hybrid solutions like Cordova or PhoneGap.

# How do they [work internally](https://capacitorjs.jp/blog/how-capacitor-works) 

## Abstraction 
![[Pasted image 20240816091615.png]]

## Closer look 
![[Pasted image 20240816091758.png]]

A web view is a component used in mobile or desktop applications to display web content, such as HTML, CSS, and JavaScript, within a native application. Essentially, it functions as a browser embedded within the app, allowing developers to render web pages or full web apps directly inside the app’s interface.

## Native Bridge 

![[Pasted image 20240816092240.png]]
The **native bridge** is a key concept in hybrid and cross-platform mobile development. It refers to the layer that facilitates communication between the web-based code (HTML, CSS, JavaScript) running inside a web view and the native components of a mobile operating system (like iOS or Android). This is crucial because web technologies on their own cannot directly access native device features like the camera, GPS, or file system. The native bridge makes it possible to call native functions from JavaScript and vice versa.

### How the Native Bridge Works:

1. **Web Code to Native Code**: The native bridge listens for specific JavaScript function calls (like accessing the device’s camera). When triggered, the bridge passes this request to the native layer (written in Swift for iOS, Java for Android, etc.), where it is executed.
    
2. **Native Code to Web Code**: Native components can also send data back to the web view through the bridge. For example, after the camera captures an image, the bridge can send the image data back to the web view, where the JavaScript code can handle it.
    
3. **Plugins**: In frameworks like Capacitor or Cordova, plugins are used to manage this bridge. A plugin is a piece of code that handles both the JavaScript side and the native implementation side. Developers often rely on plugins to abstract the complexities of dealing with native code, offering a consistent API across different platforms.

# How to implement it + ionic 

>[!info] this video is a great tutorial on how to implement capacitor in you currently existent web platform https://youtu.be/IwHt_QpIa8A?si=vEw3vb3x91jYvan1 

Capacitor’s workflow is simple: build your web app, wrap it in Capacitor, and then deploy it as a native app. You can manage native projects (like Android Studio for Android or Xcode for iOS) directly alongside your web app. This setup allows for an efficient build process while leveraging existing web development skills.

For example, after building your web app, commands like `npx cap add ios` or `npx cap add android` can be used to integrate it with native platforms. From there, you can build and run the app with tools like Xcode or Android Studio. Capacitor’s flexibility also allows integration with popular web frameworks like React, Angular, or Vue.

## Requirements 

for the requirements of implementing the capacitor please view https://capacitorjs.com/docs/getting-started/environment-setup

just make sure you have something like Android studio to run your app on

>**iOS Requirements**[​](https://capacitorjs.com/docs/getting-started/environment-setup#ios-requirements "Direct link to iOS Requirements")
To build iOS apps, you will need **macOS**. While there are solutions like [Ionic Appflow](http://ionicframework.com/appflow) that can be used to perform iOS cloud builds if you don't have a Mac, it is highly recommended to have the tools available to you locally in order to properly test your Capacitor application.
## Installation 

>[!info] https://capacitorjs.com/docs/getting-started

But in short 
### Create a new Capacitor app[​](https://capacitorjs.com/docs/getting-started#create-a-new-capacitor-app "Direct link to Create a new Capacitor app")

```
npm init @capacitor/app
```

### Add Capacitor to your web app

#### Install Capacitor[​](https://capacitorjs.com/docs/getting-started#install-capacitor "Direct link to Install Capacitor")

In the root of your app, install Capacitor's main npm dependencies: the core JavaScript runtime and the command line interface (CLI).

```
npm i @capacitor/core
npm i -D @capacitor/cli
```

#### Initialize your Capacitor config[​](https://capacitorjs.com/docs/getting-started#initialize-your-capacitor-config "Direct link to Initialize your Capacitor config")

```
npx cap init
```

#### Using Ionic

This framework allows developers to develop high-quality hybrid mobile applications using web technologies such as HTML, CSS, and JavaScript
Capacitor is required to create/package and run your web (Ionic app) as a native Android/iOS app. Without Capacitor, you can only run the Ionic app in a web browser.
Capacitor is required to use native functionality in your Ionic app like the camera, push notifications, native storage, etc.

**Ionic is the toolkit that provides the UI components. Capacitor is what creates the bridge between the web and native functionality. It also provides the tooling to build the native apps.**

##### Install the Ionic CLI[​](https://ionicframework.com/docs/intro/cli#install-the-ionic-cli "Direct link to Install the Ionic CLI")

Before proceeding, make sure your computer has [Node.js](https://ionicframework.com/docs/reference/glossary#node) installed. See [these instructions](https://ionicframework.com/docs/intro/environment) to set up an environment for Ionic.

Install the Ionic CLI with npm:

```
npm install -g @ionic/cli
```

for this to work u need to add this in powershell 

```
Get-ExecutionPolicy
```
#### Create your Android and iOS projects[​](https://capacitorjs.com/docs/getting-started#create-your-android-and-ios-projects "Direct link to Create your Android and iOS projects")

Back to capacitor
you can install the Android and iOS platforms.

```
npm i @capacitor/android @capacitor/ios
```

Once the platforms have been added to your `package.json`, you can run the following commands to create your Android and iOS projects for your native application.

```
npx cap add android
npx cap add ios
```

#### Sync your web code to your native project[​](https://capacitorjs.com/docs/getting-started#sync-your-web-code-to-your-native-project "Direct link to Sync your web code to your native project")

```
npx cap sync
```

`npx cap sync` will copy your built web bundle expected to be found in `webDir` of the [Capacitor Config](https://capacitorjs.com/docs/config) file to your native project and install the native project's dependencies.

### Opening the Android Project[​](https://capacitorjs.com/docs/android#opening-the-android-project "Direct link to Opening the Android Project")

make sure to run 
 
```
ionic build 
```
 before running any commands to update the build 

To open the project in Android Studio, run:

```
npx cap open android
```

### Opening the iOS Project[​](https://capacitorjs.com/docs/ios#opening-the-ios-project "Direct link to Opening the iOS Project")

To open the project in Xcode, run:

```
npx cap open ios
```