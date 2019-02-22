# CLI Essentials: Files and Directories in Bash 

## Learning Goals

* Demonstrate interacting with files and directories in the command line

## Introduction

## Demonstrate Interacting with Files and Directories in the Command Line

### Use `ls` to List Files in Shell

In a new terminal, try this:

```bash
$ ls
```

You should see a list of all the files within your working directory.

The command `ls` stands for "**l**i**s**t".

> We can use flags on most unix commands to give more specific instructions or
> to change the way the feedback is presented. Most programs also accept flags,
> or options for execution. A flag is denotated by a `-` ("dash"). **Note:** *In
> some programs, options are passed directly to the command and not via flags.*

A common flag that nearly all programs and commands accept is a standalone `h`,
for "**h**elp".

```bash
$ ls -h
```

Single-character options can typically be combined with each other. For example,
in the `ls` command, `h` is a suffix on the `l` flag meaning "**h**uman readable
formats." They can be combined with `a` meaning "**a**ll information including.
Try these three together:

try `ls -l` try `ls -h` try `ls -lh` (whoa...c-c-c-c-c-combo!)

**Note:** *Combining flags is only valid for single-letter options. A "long
option" such as* `--force` *is defined with more than one character and must be
entered with its own flag.* For example `--force --remote` `--forceremote` or
`--remoteforce`

### Use `cp` to Copy Files and Directories

...

### Use `mv` to Move or Rename Files and Directories

Move, or `mv` is a command that moves one or more files or directories from one
place to another.  Alternatively, think of it as a copy, followed by a delete of
the original. To move a file from the current directory to another location,
enter a path as the third word on the command line.

```bash
$ mv filename /dir1/
```

We can also rename file or directory using the `mv` command. To rename a file
with `mv`, the third word on the command line must end in the new filename.

```bash
$ mv original_program.rb renamed_program.rb
```

### Create Empty Files With `touch`

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
you just created it. Try using `cp` and `mv` to copy and rename this empty file.

### Making New Directories Using `mkdir`

We can make directories with the `mkdir` command:

```bash
$ mkdir name_of_directory
```
Now if you enter `ls` you should see the empty directory you just created in the
working directory.

### Removing Files With `rm`

<This section needs more spelling out: recursive deletion is a unix is a
chainsaw moment>

To delete a file, we can enter `rm` at a shell prompt. **Note:** Deleting a file
with rm is *permanent*. This action cannot be undone.

```bash
$ rm hello_world.rb
```

There additional options to `rm`:

* -i (interactive) — Prompts you to confirm the deletion. This option can stop
  you from deleting a file by mistake.
* -f (force) — Overrides interactive mode and removes the file(s) without
  prompting. Use this with caution. This action cannot be undone!
* -v (verbose) — Shows the progress of the files as they are being removed.
* -r (recursive) — Deletes a directory and all files and subdirectories it
  contains.

You can also delete directories using `rm` or `rmdir`.

<Also fair to show that `rm -rf /` is a Bad Idea (tm)>

## Conclusion

## Resources

- [Lifehacker on the Command Line](http://lifehacker.com/5633909/who-needs-a-mouse-learn-to-use-the-command-line-for-almost-anything)
- [Environment Variables](http://cbednarski.com/articles/understanding-environment-variables-and-the-unix-path/)
- [Built-in Shell Commands](https://www.gnu.org/software/bash/manual/html_node/Bash-Builtins.html) *Very useful*
- [15 Useful Bash Commands](http://www.thegeekstuff.com/2010/08/bash-shell-builtin-commands/)
