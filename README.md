# git-melt
Merge multiple git projects in your working copy.
git-melt consists of a few bash scripts to extend git.

## Installation
Download the repository, copy the files from bin to /usr/bin and share to /usr/share. Permit the scripts to be executed.
```sh
$ git clone https://github.com/michail-peterlis/git-melt.git .
$ mkdir /usr/share/git-melt/
$ cp bin/git-melt* /usr/bin/
$ cp share/git-melt/template-script /usr/share/git-melt/
$ chmod 755 /usr/bin/git-melt*
$ chmod 755 /usr/share/git-melt/*
```

## Using git-melt
Initialize the directory.
```sh
$ git melt init
```
As most projects have some similar files, which are actually not required while using the project (e.g. README, LICENSE), you should put them into the melt ignore list. This is done by:
```sh
$ git melt init -e
# for example add:
# README.md
# LICENSE
# LICENCE
```
By doing so, you will see some files are already part of the list by default.
This will call the default editor (defined by variable VISUAL) to edit the ignore list. For more details see:
```sh
$ git melt --help
```
Mixin a project. In this examples we will use the test projects.
```sh
$ git melt mixin test1 https://github.com/git-melt/melt-test_1.git
```
Command mixin will (as you expect) mix in the repository into the melt folder. `test1` is the identifier used to run commands on this project. This will also create a script `git-test1`. To run git specific commands on this repository, use this newly created script.
```sh
$ ./git-test1 status
```
Repeat for all your required projects.

## Troubleshooting
Enable logging by:
```sh
$ DEBUG_LOG=yes git melt <command>
# or even more log by
$ DEBUG=yes git melt <command>
```
