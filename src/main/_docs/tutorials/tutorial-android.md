---
tags: [ "eclipse" , "che" ]
title: Android
excerpt: ""
layout: tutorials
permalink: /:categories/android/
---
{% include base.html %}

# 1. Select Android Stack and Sample  
When in User Dashboard, create a project with Android stack. There are two sample applications to get started with. Both are Maven projects.

# 2. Run Android App (Emulator)  
Android stack has everything one needs to package `.apk` (Java, Maven, Android SDK), run Android emulator and install the `.apk` in an emulator.

When in the IDE, run `build` command that will package the project as `apk`. You will also see a preview URL, which is a VNC URL to get into the environment with x-server running.

The final instructions are documented in a sample [README file in the repository](https://github.com/che-samples/mobile-android-hello-world/blob/master/README.md)

# 3. Run Android App on Device  
It is possible to connect your Android phone or tablet to your machine and use `adb` commands to install `apk` right into a connected device.

There are a few pre-requisites:

* in `che.env`:
  - `CHE_WORKSPACE_VOLUME=/dev/bus/usb:/dev/bus/usb`
  - `CHE_DOCKER_PRIVILEGED=true`

Vagrant users and those running Che natively on Windows and Mac (i.e. where Virtual Box is involved) need to make sure that the VM can see USB devices connected to the host machine.

There are two pre-reqs here:

1. Install VirtualBox Extension Pack.  
 [Instructions](http://www.htpcbeginner.com/install-virtualbox-extension-pack-on-linux-windows/) | [Download Link](http://download.virtualbox.org/virtualbox/5.0.16/Oracle_VM_VirtualBox_Extension_Pack-5.0.16.vbox-extpack)

2. Enable USB in VM settings.  

Vagrant users may either add the following to a Vagrantfile - https://github.com/codenvy/artik-ide/blob/master/Vagrantfile#L16-20 (then destroy the current box and create a new one) - or manually enable USB at Settings > USB (create an empty filter).

When a workspace starts, you may check if adb can see your phone:
`adb devices`

If the phone is there, you may install `apk` right into it:
`adb install -r /path/to/your.apk`
