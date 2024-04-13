# M3 Interface & Usage
Along with Slurm, M3 provides an interface with a set of tools, software packages, commands and a way of working with and using it's directory structure. We provide a brief overview of this interface below. To get more info visit their [documentation website](https://docs.massive.org.au).

## M3 Specific Commands

| Command | Function |
| --- | --- |
| `module load <module_name>` | load a module |
| `module unload <module_name>` | unload a module |
| `module avail` | list available modules |
| `module list` | list loaded modules |
| `module spider <module_name>` | search for a module |
| `module help <module_name>` | get help for a module |
| `module show <module_name>` | show details about a module |
| `module purge` | unload all modules |
| `module swap <module_name> <module_name>` | swap two modules |

## M3's Shared Filesystem

When we talk about a shared filesystem, what we mean is that the filesystem that M3 uses allows multiple users or systems to access, manage, and share files and directories over a network, concurrently. It enables users to collaborate on projects, share resources, and maintain a unified file structure across different machines and platforms. In addition to this, it enables the many different compute nodes in M3 to access data from a single source which users also have access to, simplifying the process of running jobs on M3.

Very simply, the way it works is that the home, project and scratch directories are mounted on every node in the cluster, so they are accessible from any node.

M3 has a unique filesystem consisting of three main important parts (for you).

### Home Directory

There is each user's personal directory, which only they have access to. This has a ~10GB allocation, and should store any hidden files, configuration files, or other files that you don't want to share with others. This is backed up nightly.

### Project Directory

This is the shared project directory, for all users in MDN to use. This has a ~1TB allocation, and should be used only for project specific files, scripts, and data. This is also backed up nightly, so in the case that you accidentally delete something important, it can be recovered.

### Scratch Directory

This is also shared with all users in MDN, and has more allocation (~3TB). You may use this for personal projects, but keep your usage low. In general it is used for temporary files, larger datasets, and should be used for any files that you don't need to keep for a long time. This is not backed up, so if you delete something, it's gone forever.

### General Rules

- Keep data usage to a minimum. If you have a large amount of data, consider moving it to the scratch directory. If it is not necessary to keep it, consider deleting it.
- Keep your home directory clean.
- In general, it is good practice to make a directory in the shared directory for yourself. Name this your username or name, to make it easily identifiable. This is where you should store your files for small projects or personal use.
- The project directory is not for personal use. Do not store files in the project directory that are not related to MDN. Use the scratch directory instead.

### Copying files to and from M3

Copying files to and from M3 can be done in a few different ways. We will go over the basics of scp, as well as setting up FileZilla. 

A key thing to remember when copying files to and from M3 is that you shouldn't be using the regular ssh url. Instead, they have a dedicated SFTP url to use for file transfers. This is `m3-dtn.massive.org.au`. This is the url you will use when setting up FileZilla, and when using scp.

#### Using scp

You can copy files to M3 using the `scp` command. This is a command line tool that is built into most linux distributions. If you are using Windows, you will need to install a tool like [Git Bash](https://gitforwindows.org/) to use this command.

##### Linux / Mac

To copy a file to M3, use the following command:

```bash
scp <file> <username>@m3-dtn.massive.org.au:<destination>
```

For example, if I wanted to copy a file called `test.txt` to my home directory on M3, I would use the following command:

```bash
scp test.txt jasparm@m3-dtn.massive.org.au:~
```

To copy a file from M3 to your local machine, use the following command:

```bash
scp <username>@m3-dtn.massive.org.au:<file> <destination>
```

So, to bring that same file back to my local machine, I would use the following command:

```bash
scp jasparm@m3-dtn.massive.org.au:~/test.txt .
```

#### FileZilla

FileZilla is a SFTP client that the M3 staff recommend using. You can download it [here](https://filezilla-project.org/download.php?show_all=1).

Once installed, run the program and click on File -> Site Manager or `Ctrl-S`. This will open the site manager. Click on New Site, and enter the following details:

- Protocol: SFTP
- Host: `m3-dtn.massive.org.au`
- Logon Type: Ask for password
- User: `<your username>`

Don't change anything else. Leave password blank for now.

It should look something like this:
![Add M3 as a site](./imgs/filezilla_connect_m3.png)
Click on Connect, and enter your password when prompted. You should now be connected to M3. You can now drag and drop files to and from M3.

