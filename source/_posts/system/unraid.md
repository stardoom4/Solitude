---
title: 'Unraid: Install'
categories:
  - 好物推荐
tags:
  - Unraid
ai: false
cover: 'https://s3.qjqq.cn/47/661e637726417.webp!color'
abbrlink: '88331569'
date: 2024-03-28 08:00:00
update: 2024-03-28 08:00:00
---

{% note success simple no-icon %}
[Google Drive](https://drive.google.com/file/d/16bbYzX68cFZ5G3c5kLWGoW9LhDuaNdhL/view?usp=sharing)
{% endnote %}

## Introduction

Unraid is a Linux-based operating system optimized for media file storage, streaming, and gaming. It is a paid software, but it is worth the price. It is easy to use and has a lot of features. It is a great choice for a home server.

## Features✨

* **Hard Disk Drive Pooling**: Multiple hard disk drives can be combined into a single storage pool to provide greater storage capacity.
* **Data Protection and Backup**: Unraid provides data protection and backup features including hard drive failsafe, data redundancy and automatic backup.
* **Virtualization**: Unraid supports virtualization technology that allows you to run multiple virtual machines on the same computer, each running a different operating system and application.
* **Plug-ins and applications**: Unraid supports plug-ins and applications that make it easy to add new features and extend the functionality of the system.
* **Easy to use**: Unraid's easy-to-use interface makes it easy for even inexperienced Linux users to get started.

## Installation

1. Download the top file from the link above.
2. Unzip the file.
    ![Unzio the file](https://s3.qjqq.cn/47/660a85062985b.webp!color)
3. Format a USB drive to FAT32.
4. Copy all files from `unRAIDServer-6.12.8-x86_64` to a USB flash drive.
    ![](https://s3.qjqq.cn/47/660a851539cdb.webp!color)

## Replacement of files

**New**
1. Replace `unraid_crack > unraid-new` in the config folder of the flash drive.
2. Replace the contents of the `go` file in the `config` folder:
    ```text
    #!/bin/bash
    export UNRAID_GUID=(!)HERE IS YOUR GUID
    export UNRAID_NAME=Tower
    export UNRAID_DATE=1654646400
    export UNRAID_VERSION=Pro
    /lib64/ld-linux-x86-64.so.2 /boot/config/unraider
    # Start the Management Utility
    /usr/local/sbin/emhttp & 
    ```

**Old update**
1. Replace all the files from unraid_crack > unraider-for-update into the config folder on the flash drive.

## Compiler

{% tabs Compiler %}

<!-- tab window @st-microsoft-fill -->
Run as administrator this file: `make_bootable.bat`
<!-- endtab -->

<!-- tab linux @st-linux -->
```bash
sudo bash make_bootable_linux
```
<!-- endtab -->

<!-- tab mac @st-apple-fill -->
```bash
./make_bootable_mac
```
<!-- endtab -->

{% endtabs %}

## Boot

1. Insert the USB drive into the computer.
2. Boot from the USB drive.

{% note danger simple no-icon %}
Unzip key: `efu.me`
{% endnote %}