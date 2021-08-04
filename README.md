# AGL_Deep_Dive
Automotive Grade Linux (https://www.automotivelinux.org/) Deep Dive Repository

<br/>

## Download AGL Source Code

The AGL source code and Yocto layers are maintained on the AGL Gerrit server. For information on how to create accounts for gerrit see [Getting Started with AGL](https://wiki.automotivelinux.org/start/getting-started).

<br/>

### Setting up the build environment

In the following, your top level directory is noted as “AGL_TOP”. For example, we will set AGL_TOP to point to a directory “$HOME/workspace_agl”:

```
export AGL_TOP=$HOME/workspace_agl
mkdir -p $AGL_TOP
```

<br/>

### Prepare Repo Tool

AGL Uses the 'repo' tool for managing repositories. You need to setup layers of AGL. You can use the commands below to prepare Repo:

```
mkdir -p ~/bin
export PATH=~/bin:$PATH
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
```

**Note**:

- More information about the tool 'repo' [Here](https://source.android.com/source/using-repo.html)

<br/>

### Download source

You can choose your source release

<br/>

### Download Latest Stable Release

To download all layers for the for the latest stable release, eel 5.0.3:

```
cd $AGL_TOP
repo init -b eel -m eel_5.1.0.xml -u https://gerrit.automotivelinux.org/gerrit/AGL/AGL-repo
repo sync
```

<br/>

### Download Master Branch

To download all code from master:

```
cd $AGL_TOP
repo init -u https://gerrit.automotivelinux.org/gerrit/AGL/AGL-repo
repo sync
```

<br/>

<br/>

<br/>

## Set up Build Environment Info

AGL has created a set up script for defining the target build and desired optional features.

To get a complete list of the options available run.

```
cd $AGL_TOP
source meta-agl/scripts/aglsetup.sh -h
```

Once you run aglsetup.sh with your desired parameters, you can build any target desired.

<br/>

<br/>

<br/>

## Features supported by aglsetup

Here is the list of features for AGL 2.1 that can be specified in the aglsetup.sh command line:

- in **meta-agl**
  - agl-all-features
  - agl-appfw-smack: enables IoT.bzh Application Framework + SMACK + Cynara
  - agl-archiver
  - agl-ci
  - agl-ci-change-features
  - agl-ci-change-features-nogfx
  - agl-ci-snapshot-features
  - agl-ci-snapshot-features-nogfx
  - agl-devel: activate development options (empty root password, debugger, strace, valgrind …)
  - agl-gplv2
  - agl-isafw
  - agl-netboot: enable network boot support through TFTP and NBD (see meta-netboot layer)
  - agl-profile-graphical
  - agl-profile-graphical-html5
  - agl-profile-graphical-qt5
  - agl-profile-hud
  - agl-profile-telematics
  - agl-ptest
  - agl-sota: enable SOTA components and dependencies (meta-sota, meta-filesystems, meta-ruby, meta-rust are added)
- in **meta-agl-demo**
  - agl-demo: enable layer meta-agl-demo and meta-qt5 - required to build * agl-demo-platform
  - agl-iotivity
  - agl-sdl
- in **meta-agl-devel**
  - agl-audio-4a-framework
  - agl-audio-soundmanager-framework
  - agl-egvirt
  - agl-hmi-framework
  - agl-oem-extra-libs
  - agl-renesas-kernel
  - agl-telemetry
- in **meta-agl-extra**
  - agl-localdev: add a local layer named “meta-localdev” in meta directory and a local.dev.inc conf file if present
  - blsched

<br/>

For newer features or to get more details on a given feature, take a look at the configuration files stored for each feature and/or each machine in `meta-agl/templates` and `meta-agl-extra/templates`.
