# dpack
A simple package manager for [Dictu](https://dictu-lang.com) written in Dictu!.

## Commands
The Basic pattern is `dpack.du <command> [options] <url/name>`
### install
Install a package from a Git Repository into the `dictu_modules/<package>` directory. The repository needs to have a **dpack.json**.
```sh
dictu dpack.du install https://github.com/foo/bar.git
```
Options:
* --branch/-b: checkout a specific branch
* --commit/-c: checkout a specific commit
* --allow-scripts/-a: Automatically run build-cmds
### sync
This can be used in a project which has packages to fetch them or to update existing packages.
```sh
dictu dpack.du sync
```
Options:
* --allow-scripts/-a: Automatically run build-cmds
### remove
Remove a package from the project.
```sh
dictu dpack.du remove <url/name>
```
### init
Create a dpack.json in the current directory.
```
dictu dpack.du init
```

## Preparing a Repository to be installable
This is not difficult. In the project repository create a dpack.json(see init).  
You can add a `build-cmd` shell/cmd command for building native code or the likes.

After pushing that file the repository is ready for usage!

For a few examples you can use packages i did: https://github.com/liz3/dictu-ui.git, https://github.com/liz3/dictu-pq.git

## importing packages
The `dictu_modules` folder is special as the Dictu VM will use it to search for files so you can omit the `dictu_modules` part of the import path.
Example from [dictu-mongo](https://github.com/liz3/dictu-mongo):
```
from "dictu-mongo/mod.du" import MongoDriver;
print(MongoDriver); // <FFIInstance>
```