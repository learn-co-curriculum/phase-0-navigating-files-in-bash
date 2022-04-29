# Working with Files and Directories in the CLI

## Learning Goals

- List files and directories with `ls`
- Create new files with `touch`
- Create new directories with `mkdir`
- Move or rename files and directories with `mv`
- Copy files and directories with `cp`
- Remove files or directories with `rm`

## Introduction

In the previous lesson we learned how to "navigate" the directory structure of
our file system. But our file systems (and lives) would be so boring without
_files_. Copying files, moving files, reading the contents of files, etc. We
looooooove files.

This lesson will show you how to work with your files. In time, you might stop
using Finder and other graphical tools because it's so much faster (and more
fun!) to use the CLI.

## List Files and Directories with `ls`

In a new terminal, which automatically puts you in your _home directory_,
try this:

```console
$ ls
```

The command `ls` stands for "**list**" — the first character is a lower case
letter L. After you run it, you should then see a list of the files and folders
within your working directory.

> **Note:** For Ubuntu/WSL users, your home directory may start out empty, so
> you might not see anything when you run `ls`. If this is the case, try
> creating a folder. In fact, now is a good time to create a `Development`
> folder where you can store your coursework. (You'll finish setting up the
> directory structure for your coursework in the next lesson.) We'll use `mkdir`
> to create the folder (more on this a bit later in this lesson):
>
> ```console
> $ mkdir Development
> ```
>
> Once the folder is created, run `ls` again and you should see `Development`
> listed.

True to Unix style the `ls` command is easy to type and **_short_** (both keys
on the home row of a keyboard, one letter on one hand the other on the other
hand, it's about as fast as it can get; handy for a command we will run _all the
time_).

We can list the contents of another directory by providing an absolute or
relative path:

```console
$ ls pathname
```

### Using Flags with Commands

We can use flags on most Unix commands to give more specific instructions or to
change the output. Most programs accept flags, or options for execution.

A flag is denoted by a `-` ("dash").

```console
$ ls -l
```

This prints out a list of all the files with "long form" output: it will give us
more details, including  which user account owns the file, what the permissions
for users are on the file, etc.

For example:

```console
$ ls  /var/tmp
SIMToolKit
hi
pfwtfp-dice-thrower-from-a-file
sinatra-user-auth
```

becomes:

```console
$ ls -l /var/tmp
total 0
drwxrwxrwx   3 byron.poodle  wheel   96 Jun  5  2018 SIMToolKit
drwxr-xr-x   2 byron.poodle  wheel   64 Jun  5  2018 hi
drwxr-xr-x  12 byron.poodle  wheel  384 Nov  9 15:35 pfwtfp-dice-thrower-from-a-file
drwxr-xr-x  18 byron.poodle  wheel  576 May 21  2018 sinatra-user-auth
```

You don't need to know what all those extra bits of information mean now; just
be aware that flags can really enrich the output you get.

Single-character options can typically be combined with each other. For example,
`a` is an additional flag you can use with the `ls` command to show "**a**ll"
files, including "hidden files." (Hidden files have names that start with a `.`,
and are often used for internal operating system configuration — we'll expand on
this in a moment.)

We can combine the two flags when we use `ls`:

```console
$ ls -la
```

Or, equivalently:

```console
$ ls -l -a
```

When you run either of the commands above, you should receive a list of files
that includes some you didn't see when you ran just `$ ls`, without the flags:

```console
drwxr-xr-x   6 kellyegreene  staff   204B Jun  2 11:21 .
drwxr-xr-x   5 kellyegreene  staff   170B May 28 15:52 ..
-rw-r--r--@  1 kellyegreene  staff   6.0K May 28 15:52 .DS_Store
drwxr-xr-x  13 kellyegreene  staff   442B Jun  2 11:02 .git
-rw-r--r--   1 kellyegreene  staff    66B May 28 15:49 .learn
-rw-r--r--   1 kellyegreene  staff    11K Jun  2 11:21 README.md
```

Notice that at the top of the file output that the current directory (`.`) and
its parent (`..`) are listed first, followed by several files that start with
a `.`, like `.DS_Store`.

Files like `.DS_Store` are not listed if you don't use the `a` flag. That's
because files and directories that start with a `.` are _hidden_ files. Shells
are often configured by putting information in these _hidden_ files. We'll not
talk about these types of files in this lesson except to say that you need to
use the `a` flag when you run `ls` if you want to see them.

**Note:** _Combining flags is only valid for single-letter options. A "long
option" such as_ `--force` _is defined with more than one character and cannot
be combined with other flags._

## Create New Files with `touch`

We can use the `touch` command to create a new (empty) file in the current
directory. Try:

```console
$ touch hello_world.rb
```

Now try:

```console
$ ls
```

You should see the file you just created, `hello_world.rb`, in the working
directory. Note that this is an empty file and has nothing inside of it, because
you just created it.

## Create New Directories with `mkdir`

We can make directories with the `mkdir` command:

```console
$ mkdir name_of_directory
```

Now if you enter `ls` you should see the empty directory you just created in the
working directory.

## Move or Rename Files and Directories with `mv`

`mv` is the command that is used to move files or directories from one place to
another:

```console
$ mv filename destination_path
```

We first type the `mv` command, followed by the name of the file we want to
move. After that, we provide a second argument: a path (either relative or
absolute) that points to the folder we want to move our file into.

If the file we want to move is not in the working directory (the directory we're
currently in), we can provide a (relative or absolute) path to that as well:

```console
mv path_to_file/filename destination_path
```

Or, if we wanted to move that file from its current location into the working
directory, we could do that like this:

```console
mv path_to_file/filename ./
```

Recall that `.` is a shell application shortcut for the "current" directory. The
command above tells the shell to move the file `filename` in the location
specified by `path_to_file` into the working directory.

You may also see `./` used to explicitly specify that we're starting from the
working directory. For example, to move a file into a subdirectory inside the
working directory, you could do the following:

```console
mv path_to_file/filename ./subdir
```

While the `./` is optional in this case, you will see this syntax used in other
places (and later in the curriculum), so it's good to understand what it's
doing.

In addition to **moving** files, We can also use the `mv` command to **rename**
a file or directory:

```console
$ mv original_program.rb renamed_program.rb
```

Or we could **combine** moving and renaming in one command:

```console
$ mv temp_download.gif ~/Desktop/cats_with_weapons/ninja_cat.gif
```

Here, we are moving `temp_download.gif` from the working directory into the
`cats_with_weapons` folder on our desktop and **also** renaming it to
`ninja_cat.gif`. Note that we're using the `~` shortcut here! This expands into
`/Users/username/Desktop/cats_with_weapons/ninja_cat.gif`

## Copy Files and Directories with `cp`

If you think about it, move is really "copy, but delete the original." Well,
`cp` does a `mv`, but doesn't delete the original. It's therefore a "copy."

It uses the same syntax as `mv`:

```console
$ cp letter_to_mom.txt letter_to_mom-2019-02-15.txt
```

If, instead of a single file, you want to copy a directory and its file
contents, you need to use the `-r` (**r**ecursive) flag:

```console
$ cp -r february_cat_gifs ~/Desktop/vital_media_files
```

This command tells the shell application to copy the `february_cat_gifs` folder
**and all of its contents** into the `vital_media_files` folder on the desktop.

## Remove Files or Directories with `rm`

To delete a file, we can use the `rm` command.

```console
$ rm hello_world.rb
```

**Important:** Deleting a file with `rm` is _permanent_. This action cannot be
undone!

Much like `cp`, if you want to delete a directory (and all its contents), you
need to add the `-r` flag:

```console
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
- [More on paths - Wikipedia](<http://en.wikipedia.org/wiki/Path_(computing)>)
- [How Dot Files Became Hidden Files](https://linux-audit.com/linux-history-how-dot-files-became-hidden-files/)
