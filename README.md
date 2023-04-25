# Users & Permissions Lab

## Task

In this lab, we will be practicing user creation, as well as viewing and modifying permissions as we went over in the previous chapters.

## Instructions

### Creating a new user

Let's begin by creating a new user:

```bash
$ sudo adduser labuser
```

The new user setup will ask for random information; fill it out however you please.

### Modifying permissions

Make sure you're logged in to your main user; if you need to switch, use the `su` (switch user) command:

```bash
$ su <user>
```

Now, let's create a new directory to use for the purposes of this lab:

```bash
$ mkdir permissions_lab
```

Verify that the directory has been created:

```bash
$ ls
testdir
```

Let's enter the directory as well:

```bash
$ cd permissions_lab
```

Now let's start playing around with permissions!

Create three files:

```bash
$ touch file1 file2 file3
```

> **Note:** The `touch` command simply creates a file if it does not exist. If it exists, it does nothing.

Use the `ls` command with the `-a` argument to print out the permissions for the files in the directory:

```bash
-rw-rw-r-- 1 <username> <groupname> 0 <date> file1
-rw-rw-r-- 1 <username> <groupname> 0 <date> file2
-rw-rw-r-- 1 <username> <groupname> 0 <date> file3
```

If you recall the lesson before, we can infer from the permission line that the owner and group in this case both have read/write permissions, and everyone else has read permissions only. We know who the owner is by the `<username>` column.

Switch to our new user now:

```bash
$ su labuser
```

If you open any of the files in `nano` and try making a change and then saving it, you will expectedly encounter an error. Let's change the owner of `file1` and `file3` to our new `labuser`!

Before we run a command with `sudo`, we need to be logged in as a user that has the ability to run commands as root. New users by default do not have this ability, and it's good practice to keep it limited to a small set of users. Go ahead and switch back to your main user, and then run the following commands to make `labuser` own the two files:

```bash
$ sudo chown labuser file1
$ sudo chown labuser file3
```

Now if we switch to `labuser` and try editing them, since it has `rw` permissions, we can edit the files!


## Submission

Take a screenshot of the terminal after running the command `ls -l`, with the output visible:

Upload the screenshot as the submission for this assignment.