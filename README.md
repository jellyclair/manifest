blue-velvet-cupcake-den: CyanogenMod 4.0 Restoration Project 
===========================================

This branch contains a reconstructed `repo` local manifest of the only known CyanogenMod 4.0 ("Cupcake") build to be available via CyanogenMod source code.

**See the list of manifests above for the total amount of reconstructed builds.**

Preparing a Build Environment
-----------------

It is recommended to use an older Linux distribution. All builds have been tested on Ubuntu 12.04 LTS ("Precise Pangolin"), which can be downloaded from [here](https://old-releases.ubuntu.com/releases/12.04/ubuntu-12.04.5-desktop-amd64.iso). 

To prepare a build environment, you can use our own Bash script, which you can obtain [here](https://raw.githubusercontent.com/froyocomb/tools/refs/heads/main/envsetup.sh). Download it in your compiling environment and use chmod (or GUI interface) to give it executing permissions. 

After you execute the script, select the first option by typing in 1 and pressing Enter. It should automatically update the system and install required dependencies, including the repo script. After the option is done, restart the computer.

Java 5 is required for compiling CM 4.0. To install it, run the script again - select the 2nd option in the main menu and then select option 1. The script can also change the default Java version, which can be useful if compiling different CyanogenMod versions.

After the script is finished, create a folder in your home directory in which the build files will be kept in, such as "cyanogenmod", then move on to the next step.

Downloading Source
------------------
To initialize a repository tree using one of the manifests provided by this project, execute a command like this (see the list of manifests above for available `<build>`s):

    repo init -u https://github.com/jellyclair/manifest -b cm-4.0

Then add the CyanogenMod 4.0 local manifest to the folder:

    mkdir -p .repo/local_manifests
    nano .repo/local_manifests/cm.xml

Then to download the respective code, execute:

    repo sync

Compiling
---------

To initialize the build environment, execute the following command:

    source build/envsetup.sh

Then pick from one of the available build targets by executing the command:

    lunch

As appropriate device trees are not available in the source, the only targets that are possible to pick are the generic ones.

To compile CyanogenMod, type:

    make CC=gcc-4.2 CXX=g++-4.2

The CyanogenMod 4.0 build will then likely fail half way through on 12.04. Re-type the script again, although replace 4.2 with 4.4.

Running
-------

You can run the compiled build with the Android Emulator.

In the Ubuntu build environment, you may run the currently compiled build with the in-tree emulator by executing the command:

    emulator
