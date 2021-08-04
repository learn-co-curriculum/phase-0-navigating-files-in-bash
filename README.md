# Navigating Files and Directories in Bash

## Learning Goals

- List directory files in the shell with `ls`
- Move or rename files and directories with `mv`
- Copy Files with `cp`
- Create empty files with `touch`
- Make new directories with `mkdir`
- Remove files with `rm`

## Introduction

In the previous lesson we learned how to "navigate" the directory structure
of our file system. But our file systems (and lives) would be so boring
without _files_. Copying files, moving files, reading the contents of
files, feeding files to the `ruby` program, cat .gifs. We looooooove files.

This lesson will show you how to work with your files. In time, you might
stop using Finder and other tools because it's so much faster (and fun!)
to use the CLI.

## List Directory Files in the Shell with `ls`

In a new terminal, which automatically puts you in your _home directory_,
try this:

```bash
$ ls
```

The command `ls` stands for "**l**i**s**t" — the first character is a lower case
letter L. After you run it, you should then see a list of all the files within
your working directory.

> **Note:** For Ubuntu/WSL users, your home directory may start out empty, so
> you might not see anything running `ls`. If this is the case, try creating a
> folder. In fact, now is a good time to create a `Development` folder where you
> can store your coursework. We'll use `mkdir` to create the folder (more on
> this in a moment):
>
> ```bash
> mkdir Development
> ```
>
> Once the folder is created, run `ls` again and you should see `Development`
> listed.

True to Unix style the `ls` command is easy to type and **_short_** (both keys
on the home row of a keyboard, one letter on one hand the other on the other
hand, it's about as fast as it can get; handy for a command we will run _all the
time_).

We can list the contents of another directory by providing an absolute or
relative path

```bash
$ ls pathname
```

### Using Flags with Commands

We can use flags on most Unix commands to give more specific instructions or to
change the output. Most programs accept flags, or options for execution.

A flag is denoted by a `-` ("dash").

```bash
$ ls -l
```

This prints out a list of all the files with "long form" output: it will tell us
details about which user account owns the file, what the permissions for users
are on that file, and the file name.

For example:

```bash
$ ls  /var/tmp
SIMToolKit
hi
pfwtfp-dice-thrower-from-a-file
sinatra-user-auth
```

becomes:

```bash
$ ls -l /var/tmp
total 0
drwxrwxrwx   3 byron.poodle  wheel   96 Jun  5  2018 SIMToolKit
drwxr-xr-x   2 byron.poodle  wheel   64 Jun  5  2018 hi
drwxr-xr-x  12 byron.poodle  wheel  384 Nov  9 15:35 pfwtfp-dice-thrower-from-a-file
drwxr-xr-x  18 byron.poodle  wheel  576 May 21  2018 sinatra-user-auth
```

You don't need to know what all those extra bits of information mean now, but
realize that flags can really enrich the output you get.

Single-character options can typically be combined with each other. For example,
in the `ls` command, `h` is an option on the `l` flag meaning "**h**uman
readable formats." They can be combined with `a` meaning "**a**ll information"
including "hidden files" (files that start with a `.`, often used for internal
operating system configuration — we'll expand on this in a moment).

Try these three together:

```bash
$ ls -lah
```

And also:

```bash
$ ls -l -a -h
```

Both are valid input options and mean the same thing, as far as `ls` is concerned.

When you entered `$ ls -lah` above, you should have a received a list of files
including some that you hadn't seen from entering just `$ ls` before:

```bash
drwxr-xr-x   6 kellyegreene  staff   204B Jun  2 11:21 .
drwxr-xr-x   5 kellyegreene  staff   170B May 28 15:52 ..
-rw-r--r--@  1 kellyegreene  staff   6.0K May 28 15:52 .DS_Store
drwxr-xr-x  13 kellyegreene  staff   442B Jun  2 11:02 .git
-rw-r--r--   1 kellyegreene  staff    66B May 28 15:49 .learn
-rw-r--r--   1 kellyegreene  staff    11K Jun  2 11:21 README.md
```

Notice that at the top of the file output there are a bunch of files that start
with a `.`, like `.DS_Store`

Files like `.DS_Store` are not listed. That's because files and directories that
start with a `.` are _hidden_ files. Shells are often configured by putting
information in these _hidden_ files. We'll not talk about these types of files
in this lesson except to say that sometimes things are hidden until you add a
flag.

**Note:** _Combining flags is only valid for single-letter options. A "long
option" such as_ `--force` _is defined with more than one character and must be
entered with its own flag._

## Move or Rename Files and Directories with `mv`

Move, or `mv` is a command that moves one or more files or directories from one
place to another. To move a file from the current directory to another location,
enter a path as the third word on the command line.

```bash
$ mv filename ./dir1
```

We can also rename a file or directory using the `mv` command. To rename a file
with `mv`, the third word on the command line must end in the new filename.

```bash
$ mv original_program.rb renamed_program.rb
```

We could combine these two usages as:

```bash
$ mv temp_download.gif ~/Desktop/cats_with_weapons/ninja_cat.gif
```

> **NOTE**: Look how we're using the `~` shortcut!

## Copy Files with `cp`

If you think about it, move is really "copy, but delete the original." Well,
`cp` does a `mv`, but doesn't delete the original. It's therefore a "copy."

It uses the same syntax as `mv`:

```bash
$ cp letter_to_mom.txt letter_to_mom-2019-02-15.txt
```

If you want to copy a directory and its file contents, you need to use the `-r`
flag.

```bash
$ cp -r february_cat_gifs ~/Desktop/vital_media_files
```

> **NOTE**: Look how we're using the `~` shortcut! This expands into
> `/Users/username/Desktop/vital_media_files`

## Create Empty Files with `touch`

We can use the `touch` command to create empty files in the current directory.
Try:

```bash
$ touch hello_world.rb
```

Now try:

```bash
$ ls
```

You should see the file you just created, `hello_world.rb`, in the working
directory. Note that this is an empty file and has nothing inside of it, because
you just created it.

## Make New Directories with `mkdir`

We can make directories with the `mkdir` command:

```bash
$ mkdir name_of_directory
```

Now if you enter `ls` you should see the empty directory you just created in the
working directory.

## Remove Files with `rm`

To delete a file, we can enter `rm` at a shell prompt. **Note:** Deleting a file
with rm is _permanent_. This action cannot be undone!

```bash
$ rm hello_world.rb
```

Much like `cp`, if you want to delete a directory, you need to provide the `-r`
flag

```bash
$ rm -r ~/Desktop/pokemon_fan_fiction
```

There are additional options to `rm`:

- `-i` (interactive): Prompts you to confirm the deletion. This option can stop
  you from deleting a file by mistake.
- `-f` (force): Overrides interactive mode and removes the file(s) without
  prompting. Use this with caution. This action cannot be undone!
- `-v` (verbose): Shows the progress of the files as they are being removed.

## Conclusion

There are a variety of commands you can use to manipulate files via the command
line. If this list seems overwhelming at first, remember that it takes all
programmers a little time to practice their CLI workflows. Refer back to these
resources as you need to, and it will get easier as you go along.

## Resources

- [Lifehacker on the Command Line](http://lifehacker.com/5633909/who-needs-a-mouse-learn-to-use-the-command-line-for-almost-anything)
- [Environment Variables](http://cbednarski.com/articles/understanding-environment-variables-and-the-unix-path/)
- [Built-in Shell Commands](https://www.gnu.org/software/bash/manual/html_node/Bash-Builtins.html) _Very useful_
- [15 Useful Bash Commands](http://www.thegeekstuff.com/2010/08/bash-shell-builtin-commands/)
- [The One True Path](http://blog.seldomatt.com/blog/2012/10/08/bash-and-the-one-true-path/)
- [More on paths - Wikipedia](<http://en.wikipedia.org/wiki/Path_(computing)>)
- [How Dot Files Became Hidden Files](https://linux-audit.com/linux-history-how-dot-files-became-hidden-files/)
