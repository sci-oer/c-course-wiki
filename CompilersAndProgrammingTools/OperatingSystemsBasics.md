
# Operating System Basics

Operating systems are the interface between the hardware and the user. They provide the basic operations that you need for your computer to be useful. Programs use those basic operations to build more complex operations (especially shell scripts)- but you can interact with the operating system at a very basic level. Its REALLY useful to understand how that works.

![This figure shows the relationship between the devices that make up a computer (the disks, video, sound, etc), the operating system, and the programs that we use. Programs use the operating system to communicate with the devices. Everything is a program.](/img/programmingTools1.jpg)

There are many different types of operating systems, some of which are listed below. Each system is different and programs that run under one operating system likely won't run under another operating system.

- Unix and Unix-likes: BSD, GNU/Linux
   - Unix variants include BSD, IRIX, Soaris, HP-UX
- Linux is a generic name for open-source unix-like. The kernel is
    opensource
   - Linux variants include: Debian, Red Hat, Mandrake, Slackware, SuSe
   - Debian has huge popularity, including ubuntu, knoppix, linspire
   - RPM-based linux distros include fedora, red had, suse
- Personal computer operating systems started with DEC, MS-DOS and
    PC-DOS
  - windows wasn't originally an operating system, was just a visual
    interface that ran on DOS.
- Mac OS.

Operating systems come with programs pre-installed (often called commands). These programs are there to do the work that people need to do to manage files and other programs. Each operating system has a different set of default programs installed and often system administrators will choose to install (or not install) others.

Some example programs that can be run on a linux operating system include:

-  ls *shows the files in the current directory*
-  vi, pico, nedit, gedit, emacs *editors*
-  iceweasel, chrome *web browsers*
-  gcc *c compiler*




#### Man Pages

Unix and linux operating systems come with a help system called *man*. You can read man pages for most c functions and nearly every unix command to find out the syntax, flags, arguments and usage for the comment. Every man page is organized into similar sections.

-   Name
-   Synopsis
-   Description
-   Examples
-   Diagnostics
-   Environment
-   Compatibility
-   See Also

Man pages are displayed using the *less* environment. Space will show a new page, return will show a new line, up and down arrow keys work to scroll through the text. Type a q to quit. Man pages are valuable references when trying to remember the syntax for a command.