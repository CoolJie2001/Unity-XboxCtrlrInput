![XboxControllerSVG](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/Xbox_Controller.svg/200px-Xbox_Controller.svg.png)

XboxCtrlrInput for Unity
========================

Feel free to contribute. The example project requires at least Unity 4.3 or greater. 64-bit Mac native builds require at least Unity 4.5 or greater. The wrapper itself should work in older versions.

### Decription

`XboxCtrlrInput` is a wrapper written in C# for Unity3D that handles Xbox 360 controller input. It's used in the same way as Unity's [`Input`](http://docs.unity3d.com/Documentation/ScriptReference/Input.html) class. My reasons for starting this project can be read [here](http://jibransyed.wordpress.com/2013/09/07/the-motivation-behind-xboxctrlrinput/).

[`XboxCtrlrInput.cs`](https://github.com/JISyed/Unity-XboxCtrlrInput/blob/master/XboxCtrlrInput/Assets/XboxCtrlrInputPackage/XboxCtrlrInput.cs) itself is not a Unity script and thus does not need to be attached to any GameObject, since it contains no [`MonoBehavior`](http://docs.unity3d.com/Documentation/ScriptReference/MonoBehaviour.html) derived classes in it. It should work on older versions of Unity that support joystick input.

`XboxCtrlrInput.cs` includes a C# namespace called `XboxCtrlrInput`. In that namespace there are three enumerations, [`XboxButton`](https://github.com/JISyed/Unity-XboxCtrlrInput/wiki/XboxButton), [`XboxDPad`](https://github.com/JISyed/Unity-XboxCtrlrInput/wiki/XboxDPad), and [`XboxAxis`](https://github.com/JISyed/Unity-XboxCtrlrInput/wiki/XboxAxis). Most importantly, there is a static class called [`XCI`](https://github.com/JISyed/Unity-XboxCtrlrInput/wiki/Coding-Reference#the-xci-class) that is used to get Xbox input.


### Goals

The goals of `XboxCtrlrInput` are:

1.   To be able to make simple calls to Xbox controller input that works on Mac, Windows, and Linux (Ubuntu),
2.   And to be able to handle multiple Xbox controllers that works as you expect.


### How to Use

1. Download the [XboxCtrlrInput C# file](https://raw.github.com/JISyed/Unity-XboxCtrlrInput/master/XboxCtrlrInput/Assets/XboxCtrlrInputPackage/XboxCtrlrInput.cs) (Right Click -> Save As...) and then put it into your Unity project under the [`Assets/`](https://github.com/JISyed/Unity-XboxCtrlrInput/tree/master/XboxCtrlrInput/Assets) folder. It can be anywhere in that folder.

2. Next, take the a copy of Unity's Input Manager (either as a [text asset](https://github.com/JISyed/Unity-XboxCtrlrInput/raw/master/InputManager%20Copies/InputManagerText.asset) or as a [binary asset](https://github.com/JISyed/Unity-XboxCtrlrInput/raw/master/InputManager%20Copies/InputManagerBinary.asset) ) (Right Click -> Save As...). If you're using the free version of Unity 4.1 or older, be sure to download the binary copy. Place the copy into your project's [`/ProjectSettings`](https://github.com/JISyed/Unity-XboxCtrlrInput/tree/master/XboxCtrlrInput/ProjectSettings) folder. Then rename it `InputManager.asset`, this will replace the original file that was there. 

3. Download [XInputInterface.dll](https://github.com/JISyed/Unity-XboxCtrlrInput/raw/master/XboxCtrlrInput/XInputInterface.dll) and put it in the base folder of your Unity project (the same folder that contains `/Assets` and `/ProjectSettings`).

4. Download [XInputDotNetPure.dll](https://github.com/JISyed/Unity-XboxCtrlrInput/raw/master/XboxCtrlrInput/Assets/Plugins/XInputDotNetPure.dll) and put it in `/Assets/Plugins` relative to your project. If the `Plugins` folder does not exist in your `/Assets` folder, you'll have to make one.

5. For any C# script where you want to use Xbox input, place `using XboxCtrlrInput;` at the top of the script under `using UnityEngine;`.

6. The `XboxCtrlrInput` namespace includes the class [`XCI`](https://github.com/JISyed/Unity-XboxCtrlrInput/wiki/Coding-Reference#the-xci-class), which you will use to get Xbox input, such as:
```csharp
bool didPressA = XCI.GetButton(XboxButton.A);
```

**Note for Windows users:** When making a Windows build, you must take [XInputInterface.dll](https://github.com/JISyed/Unity-XboxCtrlrInput/raw/master/XboxCtrlrInput/XInputInterface.dll) and put it in the same folder as your .exe, otherwise input won't work. This doesn't apply for web builds.

**Note for OSX users:** Be sure to install the latest version of the [Tattie Bogle drivers](http://tattiebogle.net/index.php/ProjectRoot/Xbox360Controller/OsxDriver). If you are making a native Mac build with either 64-bit or Universal binary, you need Unity 4.5 or greater. Input will not work if using older versions of Unity.

**Note for OSX Yosemite usere:** Above download to Tattie Bogle drivers don't seem to work on Yosemite. Follow [this blog post](http://www.jacobtomlinson.co.uk/2014/10/17/use-xbox-360-pad-with-yosemite/) to help get Xbox controllers to work on Yosemite.

**Note for Linux users:** All of my Linux testing was done on Ubuntu 13.04 64-bit. To test 32-bit Unity builds on a 64-bit OS, I ran `sudo apt-get install ia32-libs` in a terminal. I am using the default Xbox controller driver that came with Ubuntu, which is known as [xpad](http://lxr.free-electrons.com/source/drivers/input/joystick/xpad.c). I could not get Unity builds to cooperate with [xboxdrv](http://pingus.seul.org/~grumbel/xboxdrv/). Your milage may vary. For best results, make sure all your Xbox controllers are connected before testing anything.


### What Works?

If you want to find out what currently works (such as button mappings), refer to the [What Works](https://github.com/JISyed/Unity-XboxCtrlrInput/wiki/What-Works) page on the wiki. Compatability information can also be found there.

*Update 11/7/13:* Just so everyone knows, using the triggers with multiple controllers on a Windows web build won't probably work. Unfortunately this is a limitation of Microsoft's implementation of DirectInput. One controller will work fine though. See [Issue #10](https://github.com/JISyed/Unity-XboxCtrlrInput/issues/10).


### Documentation

For documentation, including information about the included enumerations and methods, refer to the [Coding References](https://github.com/JISyed/Unity-XboxCtrlrInput/wiki/Coding-Reference) page on the wiki. A diagram showing all the labeled Xbox inputs can also be found there.

### Issues

To see the latest bugs and limitations, refer to the repo's [Issues](https://github.com/JISyed/Unity-XboxCtrlrInput/issues) section.

### License

Everything in this repository is public domain, including the code and documentation art. I encourage everyone to use and even modify the code to your own specifications, and of course to contribute to this repo by forking the project. See [`UNLICENSE.md`](https://github.com/JISyed/Unity-XboxCtrlrInput/blob/master/UNLICENSE.md).

### About the Example Project

`XboxCtrlrInput` includes a demo Unity project that requires Unity 4.3 or above. For more information about the demo, refer to the [Example Unity Project](https://github.com/JISyed/Unity-XboxCtrlrInput/wiki/The-Example-Unity-Project) page on the wiki.

![demoScreenshot](http://jibransyed.files.wordpress.com/2013/09/screen-shot-2013-09-09-at-3-24-24-pm.png?w=600)
