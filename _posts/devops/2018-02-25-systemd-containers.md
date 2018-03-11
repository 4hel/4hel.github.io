---
layout: post
title:  "systemd containers"
date:   2018-03-11 11:00:00
categories: devops
---

* TOC
{:toc}

systemd is a UNIX service manager that replaces sysvinit.

## resource bundling

### old

sysvinit meant service resources distributed all over the file system in `/usr` `/var` `/etc`.

it had no sandboxing but only usage of unprivileged users like apache.

services could leave artifacts everywhere like files/directories, system users, IPC objects


### new

#### file system

`RootDirectory=` chroot

`RootImage=` can be created with mkosi

`MountAPIVFS=` like /proc or /sys

`BindPaths=` mount hosts dir into chroot environment of service

`BindReadOnlyPaths=` s.o.

`RuntimeDirectory=foo` creates /run/foo when the service is started and deletes it when the service is stopped unless RuntimeDirectoryPreserve=true

`StateDirectory=foo` mounts /var/lib/foo when the service is started (and auto-creates it if not existing)

`CacheDirectory=foo` mounts /var/cache/foo when the service is started (and auto-creates it if not existing)

`LogsDirectory=foo` mounts /var/log/foo when the service is started (and auto-creates it if not existing)

`ConfigurationDirectory=foo` mounts /etc/foo when the service is started (and auto-creates it if not existing)

#### user table

`PrivateUsers=`

## sandboxing

### old

UNIX users

created when dep / rpm installed and remain on the system for ever

### new

#### users

`DynamicUser=true`

Creates a user when the service is started and deletes it when the service is stopped

Do not leave artifacts in the system

`RemoveIPC=true`

`PrivateTmp=true`

#### kernel and devices

`PrivateDevices=true`

The service only has access to pseudo devices like /dev/null or /dev/random but no physical devices

`PrivateNetwork=true`

service can only see loopback network / but socket activation possible if client wants to connect.

`IPAddressAllow=`  `IPAddressDeny=`

`ProtectKernelTunables=true` `ProtectKernelModules=true`

`ProtectControlGroups=true`

