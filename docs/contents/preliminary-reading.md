In this introductory course, we are going to learn how to use Linux operating system through the Debian distribution. We will learn how to use the command line interface (CLI) and how to use the shell to interact with the operating system. We will also learn how to use the shell to write scripts and automate tasks.

This preliminary reading refers the genesis of Linux in ordrer to grasp the philosophy behind it and understand why it is so popular, even if you have never heard of it before. Yes, you may not know but you are already using it everyday. A definition of a shell is also provided.

# What is an operating system ?
According to Wikipedia, the free encyclopedia, an operating system (OS) is system software that manages computer hardware and software resources, and provides common services for computer programs. 

It receives requests to use the computer's resources - memory storage resources (e.g. access to RAM, hard disks), central processor computing resources, communication resources to peripherals (e.g. to request computing resources from the GPU or any other expansion card) or via the network - from application software. The operating system manages these requests and the necessary resources to avoid interference between software applications.

# What is UNIX ?
UNIX was an OS originally developed by Ken Thompson at Bell Labs, the legendary research arm of AT&T (the former U.S. telecommunications monopoly) in 1969 and was substantially improved at the University of California at Berkeley (UCB) during the 1970s and 1980s. Many variations were subsequently developed, sometimes rewritten from scratch but based on the same set of principles inspired from UNIX called POSIX. POSIX-compliant operating systems are nowadays widely regarded as the best operating systems ever created in terms of several criteria, including stability, security, flexibility, scalability and elegance.

# What is Linux and GNU/Linux ?

<img src="../../assets/img/gnulinux-logo.png" alt="" width="250"/>

Linux is a high-performance, POSIX-compliant free operating system. Linus Torvalds started Linux (a kernel) in 1991, aiming to create a free POSIX-compliant alternative due to dissatisfaction with MINIX. It rapidly became a global project, attracting developers worldwide [^1], leading to continuous performance improvements and widespread adoption by individuals, corporations, educational institutions, and governments.

Linux's superiority over other POSIX-compliant systems lies in being completely free, both monetarily and in terms of usage rights. This freedom is enabled by the GNU General Public License (GPL), associated with the GNU project started by Richard Stallman in 1983, providing critical utility programs for Linux, hence the name GNU/Linux. While it's mostly correct to call any Linux system a GNU/Linux system, today GNU tooling can be replaced by things such as [plan9](https://pastebin.com/td1YXjfH).

Compared to Microsoft Windows, the most widely used OS, Linux offers several benefits: (1) being free, (2) high stability, speed and security, (3) strong resistance to viruses and malware, (4) availability of numerous high-quality, free applications, and (5) compatibility with older computers unable to support newer Windows versions. For a more comprehensive list of advantages, the article ["25 Reasons to Convert to Linux"](http://www.linfo.org/reasons_to_convert.html) can provide further insights.

# What is a Linux distribution ?

A distribution is a complete operating system consisting of a \emph{kernel} (i.e., the core of an operating system) and utilities (some of which are also necessary for functioning of the operating system) together with a variety of application programs. 

There exists a hundred of currently available distributions of Linux. They come with various flavour from the most user friendly for complete beginners to the most advanced for experts. The most popular of these are Ubuntu, Fedora, Debian.

Most of these distributions are available (1) in most languages including English and French, (2) for Intel and AMD (x86-64/amd64) processors and (3) as free downloads from the Internet. They are also available (4) in other languages and (5) for other types of processors.

In this course we are going to start our Linux journey with Debian.

# What is Debian ?

<img src="../../assets/img/debian-logo.jpg" alt="" width="250"/>

Debian is a free operating system (OS) based on a UNIX-like kernel (Linux or FreeBSD) that can be dowloaded [here](https://www.debian.org/download). You can find more information about Debian [here](https://www.debian.org/intro/about). In order to install it on your computer, please refer to the tutorial already provided on the [moodle page of the course](https://moodle.myefrei.fr/course/view.php?id=11798).

# Key dates in the history of UNIX and Linux

- 1969: Ken Thompson develops the first version of UNIX at Bell Labs.
- 1973: UNIX is rewritten in the C programming language, greatly increasing its portability.
- 1983: Richard Stallman starts the GNU project to create a free UNIX-like operating system providing a lot of utilities.
- 1985: The Free Software Foundation is founded to support the GNU project.
- 1987: Andrew Tanenbaum develops MINIX, a free UNIX-like operating system for educational purposes.
- 1991: Linus Torvalds starts Linux as a hobby project.
- 1992: Linux is relicensed under the GNU GPL.
- 1993: The Debian project is founded to create a free POSIX-compliant operating system.

# POSIX-compliant OS today

- **GNU/Linux** Linux kernel + GNU utilities, equips most servers and supercomputers, and is increasingly used on desktops and laptops (2% to 4%).
- **Android** Linux kernel + Android utilities, equips most smartphones and tablets (80%).
- **FreeBSD** POSIX-compliant OS, equips most Apple Macintosh computers (10%), and the OS of Playstation 3 and 4.
- **iOS and MacOS** POSIX-compliant OS, equips iPhones and iPads and Macs from Apple.

# What is a shell ?

We saw that an OS manages user requests to use the computer's resources. These requests are made through a user interface. There are two types of user interfaces: (1) graphical user interfaces (GUIs) and (2) command line interfaces (CLIs).

A shell is a program that provides the traditional, text-only user interface for POSIX-compliant operating systems. Its primary function is to read commands (i.e., instructions) that are typed into a console (i.e., an all-text display mode) or terminal window (i.e., a graphical display mode), and then execute (i.e., run) them.

In this course we will use the Bash shell. Bash is the GNU Project's shell. Bash is the Bourne Again SHell. Bash is an sh-compatible shell that incorporates useful features from the Korn shell (ksh) and C shell (csh). It is intended to conform to the IEEE POSIX P1003.2/ISO 9945.2 Shell and Tools standard. It offers functional improvements over sh for both programming and interactive use. In addition, most sh scripts can be run by Bash without modification.

[^1]: Later, Linus Torvalds will invent Git in order to manage the developement of Linux Kernel as its developement has been spread worldwide.
