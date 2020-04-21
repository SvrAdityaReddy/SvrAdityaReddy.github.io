---
title: Android Native Code MemoryLeak Detection
comments: true
# other options
---


In this post we will discuss how memory leaks in native code can be detected in Android.

The **libmemunreachable** provided by Google can be used to detect memory leak of a running process [1].

The below command will helps us to know whether leak is occuring or not [1]. If leak occurs it displays number of Bytes of leak and other memory related information of the process [1].


```sh

$ adb shell dumpsys -t 10000000000 meminfo --unreachable [process]

```

If **libmemunreachable** used along with **Malloc Debug** can help us get the backtrace of leak which can help us to figure/root cause the leak location in native library [1] [2].

The following commands helps us to do so [1].

```sh

$ adb root
# Command enables malloc debug for all zygote (app_process is a process which starts other process in Android) started process.
$ adb shell setprop libc.debug.malloc.program app_process
# To enable malloc_debug backtraces on allocations for a single app process
$ adb shell setprop wrap.[process] "\$\@"
# Set libc malloc options
$ adb shell setprop libc.debug.malloc.options backtrace=4
# Will Get memory leak information along with backtrace
$ adb shell dumpsys -t 10000000000 meminfo --unreachable [process]

```
The backtrace can be integer value of 8 or 16.

Commands to disable above are 

```sh

$ adb shell setprop libc.debug.malloc.options "''"
$ adb shell setprop libc.debug.malloc.program "''"
$ adb shell setprop wrap.[process]  "''"

```

References:

[1] [libmemunreachable](https://android.googlesource.com/platform/system/memory/libmemunreachable/+/master/README.md) <br>
[2] [Malloc Debug](https://android.googlesource.com/platform/bionic/+/master/libc/malloc_debug/README.md) <br>
