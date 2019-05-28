% Fuchsia OS

<link id="linkStyle" rel="stylesheet" href="markdown.css"/>

# Getting Source #

[Fuchsia Source](https://fuchsia.googlesource.com/docs/+/44e394b8ce759c1f85dfa68e83af6f0fb1b0834f/getting_source.md)

## Creating a new checkout ##

The bootstrap procedure requires that you have Go 1.6 or newer and Git installed and on your PATH.

First, select the layer of the system you wish to build. (If you're unsure, select topaz, which contains the lower layers). Then, run the following command:

``` shell
curl -s "https://fuchsia.googlesource.com/scripts/+/master/bootstrap?format=TEXT" | base64 --decode | bash -s <layer>
```



-------------------------------------------------------------------------------

# Architecture #
 * Zircon 微内核，基础服务进程（设备管理器，核心设备驱动，libc，进程间通信接口fidl）
 * Garnet 设备层面的系统服务（软件安装，通信，媒体，图形，包管理，更新系统等）
 * Peridot 用户体验的基础设施层（模块，用户，存储服务等）
 * Topaz 系统的基础应用（Web，Dart，Flutter）

## vDSO ##

## Kernel State ##

### 虚拟内存和物理内存管理 ###
* vmo：virtual memory object：包含物理页

### 进程和进程管理 ###
* Handle指向内核中的各种对象

### 进程间通信 ###
* channel
  + channel是进程间通信的（唯一）机制
  + 一个channel有2个handle，
* MessagePack
* signal and wait

### 中断处理 ###
* 唤醒等待该终端的用户线程

### 没有POSIX支持 ###

## User State ##
* devmgr, devhost, svchost, fshost
* appmgr
* sysmgr
* Fuchsia定义了一套DDK接口，硬件厂商开发自己的闭源驱动的方便性大大提高了。
* 内核不提供POSIX支持，用户层可以模拟一部分POSXI接口

# Advance #

## vanila process sandbox ##

### global filesystem ###

### user ###

### create process ###

### Micro-kernel ### 
"微内核消息传递机制debug困难？"

## stable driver interface ##

## system modual ##

## Vulkan & 3D UI ##

## Flutter ##

