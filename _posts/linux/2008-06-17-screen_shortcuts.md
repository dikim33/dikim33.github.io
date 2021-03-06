---
layout: blog-article
title: Screen Shortcuts
meta: Useful shortcuts of using a screen (full-screen window manager that multiplexes a physical terminal between several processes, typically interactive shells)
source:
category: linux
folder: linux
---

| Key |  Action |  Notes |
|-----|---------|--------|
|Ctrl+a c |new window || 
|Ctrl+a n |next window |I bind F12 to this |
|Ctrl+a p |previous window |I bind F11 to this |
|Ctrl+a " |select window from list |I have window list in the status line |
|Ctrl+a Ctrl+a |previous window viewed|| 	 	 
|Ctrl+a S |split terminal horizontally into regions| Ctrl+a c to create new window there|
|Ctrl+a X |Close the current region among the split regions ||
|Ctrl+a :resize| resize region ||
|Ctrl+a :fit |fit screen size to new terminal size |Ctrl+a F is the same. Do after resizing xterm |
|Ctrl+a :remove	|remove region |Ctrl+a X is the same |
|Ctrl+a tab |Move to next region ||
|Ctrl+a d |detach screen from terminal |Start screen with -r option to reattach |
|Ctrl+a A |set window title ||
|Ctrl+a x |lock session	Enter user password to unlock ||
|Ctrl+a [ |enter scrollback/copy mode |Enter to start and end copy region. Ctrl+a ] to leave this mode |
|Ctrl+a ] |paste buffer	Supports pasting between windows ||
|Ctrl+a > |write paste buffer to file |useful for copying between screens |
|Ctrl+a < |read paste buffer from file |useful for pasting between screens |
|Ctrl+a ? |show key bindings/command names |Note unbound commands only in man page |
|Ctrl+a : |goto screen command prompt |up shows last command entered |
