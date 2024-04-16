# Introduction to Linux

Linux is a freely available open-source operating system built by Linux Torvalds back in 1991. It's based off of Bell Lab's development of Unix in the 1970s which also forms the basis of Android and MacOS. It's an extremely popular operating system, especially for servers (nearly all nodes in M3 use Linux). We will be learning about it and using it to gain both  low-level programming skills and an understanding of Operating Systems theory.

There are various implementations (distributions) of Linux. We won't go into detail on them but here's a comparison of some of the popular ones.

![linux-distros](./imgs/linux-distros.png)

You can think of Linux as having 3 layers or components. Here they are from the highest to the lowest level (how removed they are from the hardware):
- **System Libraries:** System libraries are special functions or programs using which application programs or system utilities access the Kernel’s features. This is the topmost layer of the operating system and you can think of it as the operating system's API. It allows access to the deeper parts of the machine without exposing them to direct user access.
- **Kernel:** The kernel is the core part of Linux. It is responsible for all major activities of this operating system. It consists of various modules which are all hidden and protected from the user. The only way that a user can access the kernel is through the system library.
- **

![linux-struct](./imgs/Structure-Of-Linux-Operating-System.png)