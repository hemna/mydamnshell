# MyDamnShell v1
This project is a set of ansible playbooks that can be used
to pull down 'dotfiles' git repos to setup a user's shell with all
the whizbangs and super bitchen custom apps, shells, that you want.

## My Damn Shell!!



# What MDS does
- Installs some basic requirements that MDS needs (bindep)
- Loops over defined dotfiles repos and
  - Clones defined 'dotfiles' git repos
  - Installs any binary dependencies as defined in each dotfiles repo (from requirements/bindep.txt)
  - Installs any python2 and python3 packages as defined in each dotfiles repo (requirements/python-requirements.txt)
- Runs setup.sh in each dotfiles repo

# dotfiles git repo ?
A dotfiles repo is a git repository that contains all of your custom 
unix files such as .bashrc, .zshrc, .vimrc, etc.
This allows you to have 1 place for all of your common config items 
so when you create an account on a new host/vm, you can suck those
configs down into your shell have have your environment setup the
way you like it.

# dotfiles repo layout requirements
The 'dotfiles' repo has to have a few required files and directories
- a 'requirements' directory with the following
  - bindep.txt (optional)
  - python-requirements.txt (optional)
  - python3-requirements.txt (optional)
- a setup script called 'setup.sh'


# Bindep
Bindep is a tool for checking the presence of binary packages needed to use an application / library. It started life as a way to make it easier to set up a development environment for OpenStack projects. While OpenStack depends heavily on pip for installation of Python dependencies, some dependencies are not Python based, and particularly for testing, some dependencies have to be installed before pip can be used - such as virtualenv and pip itself.

https://pypi.org/project/bindep/


## Requirements

MDS requires [Ansible](https://docs.ansible.com/ansible/latest/index.html) v2.8 to run.


## Systems supported
- openSuse


### Installation


```sh
$ git clone https://github.com/hemna/mydamnshell
$ cd mydamnshell
```

## Configure

MDS requires that you create a valid ansible group_vars/all.
Just copy the example file, edit it and you are ready to go

```sh
$ cp group_vars/all.example group_vars/all
$ vi group_vars/all
```

# Run MDS
There is a wrapper for running the main ansible playbook, or you can run it
manually.

```sh
$ ./run.sh
```

or

```sh
$ ansible-playbook -i hosts site.yml
```


### Todos

 - Write Tests
 - add support for Ubuntu
 - add support for Redhat
 - add support for MacOS

License
----

Apache 2.0


**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [Ansbible] <https://docs.ansible.com/ansible/latest/index.html>
   [bindep] <https://pypi.org/project/bindep>
