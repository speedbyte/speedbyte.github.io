---
layout: post
title: "tutorials_linuxlibrarystructure"
date: 1970-01-01
---

<html>
<h3>Introduction</h3>
Before starting to compile the compiler, it is worth to know the structure of the libraries.
<h3>Example Library</h3>
One of the important packages which assist in compiling the kernel is glibc. The name is a little misleading because first - glibc has nothing to do with gnome and second it does not only contains the libc library. Rather it is a packet of libraries that form the complete set. The contents in this packet is what you might already be familiar with - libm, libdl and so on.
<h3>Major Revision Number</h3>
So, that the contained libraries in the packet of libraries remain synchronous with each other i.e compatible, they are given a number. All the libraries contained in the glibc package are suffixed with this number. For example, the package glibc-2.23 will contain the math library named as libm-2.23 or the dynamic linker libdl-2.23. But ofcourse the development process of libm may vary from libdl. It may be possible that libm has undergone more development iteration because of bug fixing than the libdl library. Hence both the libraries are assigned a major revision number.  For example, libm.so.6 has  major revision number 6 and points to libm-2.23. This means that with the release of glibc, the major revision released along with was 6 for libm and for example 2 for libmvec ( libmvec.so.2 ).
<h3>Library Update</h3>
When a next update is delivered, ofcourse the numbers will change. The glibc package will have a new number and therefore many libraries inside the package will have a different major revision number. ( perhaps glibgc-2.24 ). However, it is not mandatory that all the libraries have been modified because may be there hasnt been any bug reports on libm for example.
<h3>Application Code Linking:</h3>
The problem with this structure is that everytime there is an update, the developers need to update their source code as well because they would like to link their application source code with these libraries. So, in the above case if there are math functions in the application source code, then the linker needs to be told the name and location of the library. Many a times, the developers want to actually link to a major revision number, because that makes sure, that any kind of update in the math library would not break their source code. But this is a special case. Generally, to avoid linking to a major revision number, another file with just the library name is created. This is actually not a library but simply a human readable file. The file itself is called a <strong>link script</strong>. The contents of the file tells the linker where to find the actual file. In case of libm.so for example, the contents of this file could be something like this:
<blockquote>libm.so

/* GNU ld script
*/
OUTPUT_FORMAT(elf64-x86-64)
GROUP ( /lib/x86_64-linux-gnu/libm.so.6  AS_NEEDED ( /usr/lib/x86_64-linux-gnu/libmvec_nonshared.a /lib/x86_64-linux-gnu/libmvec.so.1 ) )</blockquote>
<h3>Static library</h3>
The files above are shared object and that is the reason they end with a .so suffix. This means that they can be dynamically linked during the run time and not only one application many applications can do it parallely by loading the symbols at run time in their user space. However, sometimes, for the sake of security in embedded systems for example, it is important to have all the symbols before hand and do a static analysis of the code execution. The glibc package hence offers not only the shared object part ending with .so, but also a static archive ending with .a.
<h3></h3>
<h3>Summary</h3>
The libc package hence consists of four important parts:
<ol>
	<li>Actual shared library - this actually consists the code and has a huge size. Example libm.so.2.23</li>
	<li>Major Revision version symbolic link - This is a symbolic link to libm.so.2.23 and is the current stable revision of this library. Example libm.so.6</li>
	<li>Version Independent symbolic links - This is a link script that is human readable. Example libm.so</li>
	<li>Static library archive: A bloated version of shared object ( so ) for those who want to statically link the library into their code and thereby making the application code bigger in size.</li>
</ol>
</html>