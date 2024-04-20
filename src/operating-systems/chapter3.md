# Operating Systems

A decent chunk of HPC involves using low-level tools and techniques to find optimisations and make software run faster. The main reason we use C is that it gives us access to deeper parts of the computer that are normally hidden away and managed on your behalf by your Python or Java interpreter. 

![comp-levels](./imgs/programming-levels.jpg)

> **Note:** Not all low-level, machine (Assembly) code is faster than high-level code. The primary reason that lower level coding tends to be faster is that it avoids a lot of the overhead (eg. garbage collection) involved in executing higher level code.

If you have done FIT2100 Operating Systems, this chapter would mostly be a refresher for you. It's intended to provide you with a crash course intro to operating systems theory so that you are capable of using low-level tools and implementing things like cache optimisations.