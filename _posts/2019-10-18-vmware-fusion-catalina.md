---
layout: post
title: "VMWare Fusion 10 on macOS Catalina"
date: 2019-10-18
tags: [virtualization]
description: "Here's how to run VMWare Fusion 10 and 11 on macOS Catalina."
apps: [carbonize]
---

_This post is for those of us running an older version of VMWare Fusion on macOS Catalina. [VMWare Fusion 11.5](https://blogs.vmware.com/teamfusion/2019/09/vmware-fusion-11-5-available-now.html) supports macOS 10.15 out of the box._

I use VMWare Fusion 10 to test [my apps](https://www.dangercove.com) on previous and future versions of macOS. Since this fall, that's become problematic. The screen remains blank when I start one of my virtuals on Catalina. Oddly enough the preview in the virtual machine overview works fine.

Catalina requires apps to request permission for various tasks. Recording the screen is one of them. Apparently Fusion uses this feature, but neglects to ask for permission. Thus the screen stays black.

[Some people](https://communities.vmware.com/message/2884329#2884329) found a way to get around this by granting permission manually. Here's how that works.

⚠️ **Note that this requires running Terminal commands in Recovery Mode. Make sure you're comfortable with these steps. I don't offer any support and am not responsible if things don't go as planned.** ⚠️

### Create the script

Create a new script file where you can easily access it. I recommend `/tmp/fixfusion.sh`. Paste in the following:

```bash
#!/bin/sh  

# Change the following to fit your system
root="/Volumes/Macintosh HD"  
  
"$root/usr/bin/sqlite3" "${root}/Library/Application Support/com.apple.TCC/TCC.db" 'insert into access values ("kTCCServiceScreenCapture", "com.vmware.fusion", 0, 1, 1, "", "", "", "UNUSED", "", 0,1565595574)'  
```

### Enter Recovery Mode

Enter Recovery Mode by restarting your Mac and holding down `⌘` + `R` while it boots.

Start a Terminal window by selecting `Utilities` &rarr; `Terminal` from the menu bar when you've reached Recovery Mode.

#### Unlock your disk if necessary

If your primary drive is encrypted using FileVault (it should be), unlock it first by running the following command:

`diskutil apfs unlock "Macintosh HD"`

_(Again, adjust the command if your disk isn't called "Macintosh HD".)_

Enter your passphrase when it asks for it.

### Run the script

You can now run the script you created earlier:

`sh "/Volumes/Machintosh HD/tmp/fixfusion.sh"`

It's supposed to not show any output. If there's no error, it worked.

### Reboot

Check `System Preferences` &rarr; `Security & Privacy` &rarr; `Privacy` &rarr; `Screen Recording` and you'll notice VMWare Fusion has the permission it needs.

![A screenshot of System Preferences showing permission for VMWare Fusion to record the screen](/assets/blog/vmware-permission.png)

That's it. Your virtual machines should properly work again. 🥳
