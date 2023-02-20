##### Chapter 3-5
##### Porting 32bit Domino applications to 64bit Domino

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
Domino is 64 bit Only.  32 Bit C applications must be ported to 64 Bit and rebuilt to run on 64 Bit Domino.   However, domino databases can be copied across 32bit and 64bit servers.<br>
<br>
The effort to port an application from 32 bits to 64 bits might range from trivial to very difficult, depending on how the applications were written and maintained. Even well-written, highly portable application like domino has subtle issues which are mentioned below. The intent of this document is not to give all the porting guide lines that need to be followed for moving an application from 32bit to 64bit. You should refer to the appropriate platforms documentation for more in-depth and detailed descriptions on issues with porting.<br>
<br>
<b><font size="5" color="#000080">Architectures &amp; Environment</font></b><br>
<br>
Same build environment (compiler and build OS) as per HCL C API and Domino system requirements<br>
<br>
<b><font size="5" color="#000080">Compiler Flags/Debuggers</font></b><br>
<br>
Please refer to appropriate platform compiler flags text file i.e., w64_cmp.txt for windows, in the sdk for compiler and link flags we use when we compile our domino code on native 64bit platforms. We use dbx on AIX64 and Microsoft Visual Studio 2005 on Windows 64 for debugging domino applications.<br>
<br>
<b><font size="5" color="#000080">32 bit to 64 bit changes</font></b><br>
<br>
There are three different popular data models on 64bit platforms  LP64, LLP64 and ILP64. Windows x64 platforms use LLP64 data model.  Since Domino is cross platform application we went with LLP64 on Windows x64 and other UNIX64 bit platforms. Only pointer and long long are 64bits while LONG is still maintained as 32 bit even though native long is 64bit on UNIX 64bit platforms. This makes the users to be aware of not to use long but to use LONG to be consistent across domino platforms.<br>
<br>
<b><font size="5" color="#000080">Lessons learned during Domino 64bit development</font></b><br>
During the migration of domino from 32bit to 64bit native we have observed the following general coding issues which are not portable. If you would like to maintain the common code like us, you should take care of these issues.<br>

<ul>Dont use native data type long as this is 32bit on 32bit and 64bit on 64bit systems. Please use LONG or ULONG which are 32bit both in 32bit and 64bit domino platform.<br>
Domino handles are 32bit on domino 32 and 64 platforms. However, windows handles are 64bit on 64bit windows. So please use DHANDLE instead of system HANDLE which is 32bit on all 32 and 64 bit platforms. Use HANDLE only when we need to use windows API but all Domino API calls should be passed with DHANDLE.<br>
Since pointer, int and long are no longer the same size on 64-bit systems, problems may arise depending on how the variables are assigned and used within an application.
<ul>
<ul>Do not use int and long interchangeably because of the possible truncation of significant digits<br>
Do not use int to store pointer. This works on 32-bit system but fails on 64-bit systems because 32-bit integer cant hold 64-bit pointer. If you need to store a pointer, use some thing like size_t instead of int.<br>
Do not use pointer to store an integer</ul>
</ul>
Numeric constants are another issue we need to worry. Hexadecimal constants are commonly used as masks or specific bit values. Hexadecimal constants without a suffix are defined as an unsigned int if it will fit into 32-bits and if the high order bit is turned on. For example, the constant 0xFFFFFFFFL is a signed long. On a 32-bit system, this sets all the bits, but on a 64-bit system, only the lower order 32-bits are set, resulting in the value of 0x00000000FFFFFFFF.
<ul>
<ul>If you want to turn all the bits on, a portable way to do this is to define a signed long constant with a value of -1. This turns all the bits on.<br>
On a 32-bit system, the constant 0x80000000 is used to turn on or mask the most significant bit. This is not a portable way. Use shift logic.</ul>
</ul>
Do not use int and size_t interchangeably. On 32-bit systems it is OK but on 64-bit system size_t is 64-bit. To make it portable always use size_t.<br>
Formatting strings are another source of problems during the porting.</ul>
<br>
Otherwise, you should also take care of some issues about make file as below.<br>

<ul>Don't use &quot;-bD:0x20000000&quot; option to set the data segment size. It Should not be used to build on AIX64.<br>
Don't use &quot;/Zp&quot; option on Win64. It dosen't work on Win64.</ul>

---
