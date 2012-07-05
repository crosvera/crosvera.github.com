---
layout: post
title: Basic user managing
categories:
- Basic Administration
- Linux
- UBB
---

Here we go again. After several months (years?) whitout any interest in posting,
I got an assignment in a Linux class, I have to write a serie of post about
basic administration commands.

In this first post, I will write for you about basic user managing.


## The `useradd` command and others.
This is the command to designed -as the name says- to add new users to the system
It can be found in every Unix-like operating system (Linux for example).

At first look, its basis syntax is:

    useradd [options] username

If we run `useradd` without any argument, it will show a brief explanation of its
options (remember run this command as root).

![Running useradd without parameters](/basic_admin_images/01.png)

From this brief explanation, we can extract that to create an user with login name
`foobar` and its home directory at `/home/foobar` -by default, the home directory
of each user will reside in the `/home` directory- we would use the following:

    useradd -m foobar -G video,audio

Notice that we are using the `-m` option which is used to create the user directory.
Also, we use the `-G` option with `video,audio` parameters, with this we are telling
that we want create a user that belongs to the `video` and `audio` groups.

Now we have created a new user, but what is its password?, we can use the `passwd`
command to set/update the password. The basis syntax is:

    passwd [options] [LOGIN]

So, we can do `passwd foobar` to set a new password to the user `foobar`.

As a way to verify if the new user has been created, we can check the `/etc/passwd`
file. Every time `useradd` is used, an entry to the `/etc/passwd` file is added.
This file contains in one line, with seven fields delimited by colons (:), basic
information about each user account.

![The last line of a /etc/passwd  file](/basic_admin_images/02.png)

The fields shown in the above image correspond to the user's login name, password
(or just the letter x if _shaddow passwords_ are used), User Identification Number 
(UID), Group Identification Number (GID), a comment (optional), the user's home
directory and default shell (usually Bash on Linux).

But what is the _shadow password_?, Under Linux and other Unix-like operating systems,
the `/etc/shadow` file is used to stre actual passwords in encrypted format for user's
account.

Well, that's all for this post. I hope this basic informatic helps you in somehow, remember
read the [man pages][1] for further information about the use of commands.


[1]: http://linux.die.net/man/
