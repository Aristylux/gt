# `gt`

`gt` for "Goto" is a custom cd for bash

# How use ?

## Install

1. Download `gt`,
2. Move `gt` into your script directory,
3. Add this line in your `.bashrc` :

```bash
alias cd='f(){ cd "$(echo $(gt $1))";  unset -f f; }; f'
```

> Thanks to :  
> https://stackoverflow.com/questions/7131670/make-a-bash-alias-that-takes-a-parameter

4. Restart your console,
5. Tape `cd [your command]`.

## Remove

1. Delete or comment this line in your `.bashrc` :

```bash
alias cd='f(){ cd "$(echo $(gt $1))";  unset -f f; }; f'
```

2. Restart your console.

# Why did I create `gt` ?

Just for help me,  

And Move faster in the file system.

# Examples

1. You are in **/home/$USER/**

You want to move into documents

Without `gt` :
```sh
$ cd Documents/
$ pwd
/home/$USER/Documents
```

With `gt` :

```sh
$ cd doc
$ pwd
/home/$USER/Documents
```

2. You are in **/home/$USER/**  

You want to go in `/home/$USER/Documents/MyWorks/`

Without `gt` :
```sh
$ cd Documents/MyWorks/
$ pwd
/home/$USER/Documents/MyWorks
```

With `gt` :

```sh
$ cd works
$ pwd
/home/$USER/Documents/MyWorks
```

# Development

To validate a version, we need to pass all these tests:

## Test form `home`

| Command       | Result                                       | Version 1  |
| ------------- | -------------------------------------------- | :--------: |
| `~ $ cd .`    | `~ $`                                        | ✔️         |
| `~ $ cd ..`   | `/home/ $`                                   | ✔️         |
| `~ $ cd ./`   | `~ $`                                        | ✔️         |
| `~ $ cd [DDE]`| `bash: cd: [DDE]: No such file or directory` | ✔️         |
| `~ $ cd doc`  | `~/Documents $`                              | ✔️         |

**NOTE:** `DDE`: Directory Doesn't Exist

## Test from `root`

| Command       | Result                                       | Version 1  |
| ------------- | -------------------------------------------- | :--------: |
| `/ $ cd .`    | `/ $`                                        | ✔️         |
| `/ $ cd ./`   | `~ $`                                        | ✔️         |
| `/ $ cd [DDE]`| `bash: cd: [DDE]: No such file or directory` | ✔️         |
| `/ $ cd etc`  | `/etc/ $`                                    | ✔️         |
| `/ $ cd doc`  | `~/Documents $`                              | TEST?      |

**NOTE:** `DDE`: Directory Doesn't Exist
