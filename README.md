# `gt`

`gt` for "Goto" is a custom cd for bash

# How use ?

1. Download `gt`
2. Move gt into your script directory
3. Modify your `.bashrc` :

add : 

```bash
alias cd='f(){ cd "$(echo $(gt $1))";  unset -f f; }; f'
```

> Thanks to :  
> https://stackoverflow.com/questions/7131670/make-a-bash-alias-that-takes-a-parameter

4. Restart your console.
5. Tape cd [your command].

# Why I created `gt` ?

Just for help me

# Exemple

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

---

1. You are in **/home/$USER/**  

You want to go in `/home/$USER/Documents/MyWorks/`

Without `gt` :
```sh
$ cd Documents/MyWorks/
$ pwd
/home/$USER/Documents/MyWorks/
```

With `gt` :

```sh
$ cd works
$ pwd
/home/$USER/Documents/MyWorks/
```