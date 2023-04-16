# M3's Shared Filesystem

When we talk about a shared filesystem, what we mean is that the filesystem that M3 uses allows multiple users or systems to access, manage, and share files and directories over a network, concurrently. It enables users to collaborate on projects, share resources, and maintain a unified file structure across different machines and platforms. In addition to this, it enables the many different compute nodes in M3 to access data from a single source which users also have access to, simplifying the process of running jobs on M3.

Very simply, the way it works is that the home, project and scratch directories are mounted on every node in the cluster, so they are accessible from any node.

M3 has a unique filesystem consisting of three main important parts (for you).

## Home Directory

There is each user's personal directory, which only they have access to. This has a ~10GB allocation, and should store any hidden files, configuration files, or other files that you don't want to share with others. This is backed up nightly.

## Project Directory

This is the shared project directory, for all users in MDN to use. This has a ~1TB allocation, and should be used only for project specific files, scripts, and data. This is also backed up nightly, so in the case that you accidentally delete something important, it can be recovered.

## Scratch Directory

This is also shared with all users in MDN, and has more allocation (~3TB). You may use this for personal projects, but keep your usage low. In general it is used for temporary files, larger datasets, and should be used for any files that you don't need to keep for a long time. This is not backed up, so if you delete something, it's gone forever.

## General Rules

- Keep data usage to a minimum. If you have a large amount of data, consider moving it to the scratch directory. If it is not necessary to keep it, consider deleting it.
- Keep your home directory clean.
- In general, it is good practice to make a directory in the shared directory for yourself. Name this your username or name, to make it easily identifiable. This is where you should store your files for small projects or personal use.
- The project directory is not for personal use. Do not store files in the project directory that are not related to MDN. Use the scratch directory instead.

## Copying files to and from M3

### Using scp

You can copy files to M3 using the `scp` command. This is a command line tool that is built into most linux distributions, and is available on Windows through [PuTTY](https://www.putty.org/).

#### Linux / Mac

To copy a file to M3, use the following command:

```bash
scp <file> <username>@m3.massive.org.au:<destination>
```

For example, if I wanted to copy a file called `test.txt` to my home directory on M3, I would use the following command:

```bash
scp test.txt jasparm@m3.massive.org.au:~
```

To copy a file from M3 to your local machine, use the following command:

```bash
scp <username>@m3.massive.org.au:<file> <destination>
```

So, to bring that same file back to my local machine, I would use the following command:

```bash
scp jasparm@m3.massive.org.au:~/test.txt .
```
