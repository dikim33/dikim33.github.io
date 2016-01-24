---
layout: blog-article
title: Where is ldd on OS X?
meta: LDD (List Dynamic Dependencies) is a *nix utility that prints the shared libraries required by each program or shared library specified on the command line. 
source:
category: apple
folder: apple
---

I have tried to look for ldd in my DarwinPort but it is not there. Instead, I found that OS X uses "otool -L" which is doing the exactly same thing as ldd does.

For more infomation, try to do "man otool"

