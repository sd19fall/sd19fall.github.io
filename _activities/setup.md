---
title: Set Up Your Development Environment
date: 2019-08-30 13:30:00 -04:00
---

{% include toc %}

Before we can get down to the business, we need to make sure we have the right tools for the job. If you follow these instructions (with help from our amazing NINJA team), your computer will be primed and ready to do some serious computational work.

Initially, the amount of new stuff here may seem intimidating. Please do not let this discourage you! We (NINJAs and faculty) will provide lots of help and guidance along the way to help you setup, and then gain comfort with your new toolset. The process will start at the end of the first class, and will continue with additional NINJA / faculty office hours to help you complete the process successfully. Additionally, you will gain familiarity and comfort with this toolset as the semester progresses. In other words, you should think of learning the toolset as a process and not something that you need to do all at once.

### A note about variations on the instructions

The instructions below will allow you to setup the “officially supported” environment for SoftDes. Some deviations from the setup below are okay while others are not (when in doubt please ask). That being said, it will likely be more difficult for us to help you debug problems with your setup if you have a nonstandard environment.

## Step 1: Install Ubuntu

Our officially supported OS is Ubuntu 18.04.1 64-bit.
The instructions below will help you get set up.

### Dual Boot (preferred)

The preferred method for installing Ubuntu is to use what's known as a dual boot.  In this setup, you will have Ubuntu installed alongside Windows.  Upon startup of your computer, you will be able to choose which OS to boot into.  If you are going to be using a dual boot setup, the easiest way to get up and running is to use one of the provided SoftDes thumb drives.  These thumb drives have been pre-loaded with a bootable installer for Ubuntu 18.04.1.

#### Creating Space for an Ubuntu Partition

In order to install Ubuntu on your computer, you will need to create a partition on your disk drive.  Luckily, Ubuntu's installer can do most of this for you, however, this will only work if you have unpartitioned space on your drive.  The easiest way to create unpartitioned space on your drive is to shrink the size of your Windows partition.  In this way, unused drive space that is currently allocated to Windows will now be allocated to Ubuntu.

To shrink your Windows volume, you need to open up the Windows "Disk Management" utility.  The easiest way to do this is to click the Windows button in the lower lefthand corner of the screen and enter "diskmgmt.msc" into the box and press enter.  Once you are in the Disk Management utility, check to see if you have any unallocated (or unpartitioned space).  If you do (about 50 GB is a good number), there is no need to do anything.  If you don't (which is the likely case), click on the largest partition and then click the "Shrink Volume" button.  This button will prompt you to enter how much you'd like to shrink your volume by.  We recommend choosing at least 50GB (you will enter 50,000 into the utility since it uses MB as its default units).  Once you have shrunk your volume, you will now have space to use for installation of Ubuntu.

Before beginning the Ubuntu install, you should restart your computer to make sure that Windows has a chance to scan the new partition and update its boot loader.

#### Installing from the Bootable USB Drive

Next, insert the thumb drive, reboot your computer, and hold the F12 key before your computer starts to load Windows.  Depending on your system, one of two things will happen.  If you have an Olin first-year laptop, you will be able to select which device you'd like to boot from (go ahead and select the USB drive).  If you have another type of system, you may see your computer's BIOS menu.  Use the arrow keys to select boot from "USB Storage Device".  If everything has gone properly, you will see a menu with entries such as "Install Ubuntu" and "Try Ubuntu".  Select "Install Ubuntu" and the installation process will begin.

Most of the Ubuntu installation should proceed without much intervention on your part.  Here are a few things to keep in mind.

1.  When it asks you what type of installation you'd like, make sure to select the option that says something like "install Ubuntu beside Windows".
2.  Don't worry about connecting to a network during install (you can click the box that says "Don't connect to a network").
3.  Click the option "Install 3rd Party Software"

Once you've booted into Ubuntu, the first thing you'll probably want to do is get setup with WiFi. 
These instructions assume you have an Olin network account
(cross-registered students should visit the Olin IT department in the basement of Milas Hall to get set up with an account).

1. Click the NetworkManager icon in the system tray, which is normally just to the left of the speaker icon
1. Select the OLIN wireless network.
1. Fill in your settings as shown and click "Connect"

![]({% link images/setup/wifi_settings.png %})

### Virtual Machine (not recommended)

Another option is to use a [virtual machine](https://en.wikipedia.org/wiki/Virtual_machine).  In this variant you will run Ubuntu inside of a window inside of the Windows operating system (or Mac OSX if that is what you have).  
Running Python in a virtual machine works for most cases, but is known to not work for others (e.g. audio processing), so it is not recommended for this course.
We will also have thumb drives on hand that can be used to install Ubuntu as a virtual machine.  
If you are running a VM, we recommend the freely available program [Virtual Box](https://www.virtualbox.org/).  Here are some guidelines to follow if you wind up using a VM.

1.  Make sure to allocate at least 2 CPUs (preferably 4) and at least 2 GB (preferably 4GB) of RAM to your Ubuntu VM.
2.  If you are using VirtualBox, make sure to install the VirtualBox Guest Additions once your Ubuntu is up and running.
3.  If you are using VirtualBox and are experiencing sluggish performance, [consider checking the "Use Host I/O Cache" box](https://www.electricmonk.nl/log/2016/03/14/terrible-virtualbox-disk-performance/) in the settings.

### Post Installation Configuration

To make sure your installation is up to date, you should run the following commands at the Linux terminal.  To open the terminal you can click on the "Search Your Computer" button in the top left of the Ubuntu desktop and type "terminal".  Note: that we use the convention of preceding a terminal command with the dollar sign (you don't actually need to type the dollar sign into the terminal).

```bash
$ sudo apt update
$ sudo apt upgrade
```

You may find [IT's instructions](http://wikis.olin.edu/linux/doku.php) useful for completing tasks such as setting up printers and the like (warning: these are somewhat out of date).

## Step 2: Install Python

[Adapted from _Modeling and Simulation in Python_, by Allen Downey.]

You might already have Python installed on your computer, but you might not have the latest version. To use the materials in this course, you need Python 3.7, or later. Even if you have the latest version, you probably don’t have all of the libraries we need.

You could update Python and install these libraries, but I strongly recommend that you don’t go down that road. I think you will find it easier to use **Anaconda**, which is a free Python distribution that includes many of the libraries you need in this course (and lots more).

By default, Anaconda puts all files in your home directory, so you don’t need administrator (root) permission to install it, and if you have a version of Python already, Anaconda will not remove or modify it.

To install Anaconda, visit the [Anaconda install page](http://docs.continuum.io/anaconda/install/linux/).  One quick note is that at the end of the install process you will be asked whether to prepend the path to anaconda to your `.bashrc` file.  You should select 'yes' to this prompt.  As the installer says, you will then need to open a terminal for this change to take effect.
You do not need to provide your email to get the "cheat sheet", and you don't need to install Microsoft VSCode.

## Step 3: Verify Jupyter

Run `jupyter -h` to check if Jupyter is installed.

If Jupyter was not installed automatically with Anaconda, you should run

    $ conda install jupyter

## Step 4. Install Atom

1. [Download and install](http://flight-manual.atom.io/getting-started/sections/installing-atom/) the [Atom text editor](https://atom.io) onto your computer.
2. Follow the [Atom Basics](http://flight-manual.atom.io/getting-started/sections/atom-basics/) instructions to create a text file and save it.
3. If you like you can explore the [Atom Packages](http://flight-manual.atom.io/using-atom/sections/atom-packages/) instructions to see what is available: 
`script` is useful for running Python code, and we will use `Teletype` for collaboration.

{::comment}
On Windows, if you see an error like this:

![](/images/setup/error_python-tools_480.jpg)

Then do the following:

1. In a terminal, enter `where atom`. This should report a *path* such as  `C:\Users\MYNAME\AppData\Local\Continuum\Anaconda3\python.exe`, where MYNAME is your Windows login.
2. In Atom:
  * Use <kbd>Cmd+,</kbd> to open the Settings
  * Click on Packages in the sidebar
  * Find the "python-tools" package
  * Click Settings.
  * In the “Path to python directory” setting, paste the path from 1., *without* the final `python.exe`: for example, `C:\Users\MYNAME\AppData\Local\Continuum\Anaconda3\python.exe`
{:/comment}

## Step 5: Create a GitHub Account

Git is a version control system that we will use heavily in this class. We'll talk more about git next time, but for now we'd like you to sign up for an account on [GitHub](https://github.com/) (if you don't have one already).
From Allen Downey's [online git book](https://github.com/AllenDowney/amgit/blob/master/en/02-git-basics/01-chapter2.markdown#sign-up-for-github):

> GitHub is a web-based hosting service for Git users. In general a hosting service provides storage space on remote servers, network access, and tools and applications for interacting with stored data. GitHub provides storage for Git repositories and tools for interacting with them.
>
> There are other hosting services for Git, but GitHub is one of the most popular. It is so popular that people sometimes say “GitHub” when they mean “Git”, so just to be clear:
>
> * Git is an application that runs on your computer and helps you manage repositories.
> * You can use Git to manage repos stored on your own computer or on any computer configured as a Git server.
> * Anybody can set up and run a Git server. A company that runs Git servers professionally is a Git hosting service.
> * GitHub is one of many Git hosting services.
>
> Ok, go to [https://github.com](https://github.com/). If you already have an account, log in. Otherwise, you will have to create one.
>
> You can choose any available username you like, but there are a few things you might want to think about:
>
> 1. Working on GitHub involves interacting with other people. They will see your username, so choose wisely.
> 2. Some people, like `AllenDowney`, use their full names, but the most common schema seems to be one-word lower-case usernames. For example, Scott Chacon is `schacon`.
> 3. If you want to be anonymous, you can choose a username unrelated to your real name; however,
> 4. Many software engineers use GitHub as part of their professional portfolio. If a potential employer wants to check out your skills, they might look at your GitHub repositories.
>
> It is probably a good idea to think of everything you do on GitHub as part of your public professional reputation.

