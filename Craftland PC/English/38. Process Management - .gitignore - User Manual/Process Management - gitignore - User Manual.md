# Gitignore Process Management

# Introduction

Git is an open source distributed version control system that can efficiently and quickly handle version management of projects ranging from very small to very large. This article is mainly for users who are already using git for version management, and introduces the gitignore function and the official gitignore configuration for these users.

## What is gitignore

Not all files in the project directory need to be synchronized to the remote repository, such as personal preference configurations and temporary files. Using gitignore, you can mark files that do not need to be tracked by Git, avoid excessive synchronization and overwriting of collaborators' personal settings, thereby improving the efficiency of version management of the project.

# .gitignore file

.gitignore is a special plain text configuration file that contains all the files or folders in the project that need to be ignored. Files or folders configured in the .gitignore file will be ignored and not tracked by Git.

We create this file by default in each project and have already configured recommended ignored files and folders.

You can find the file in the project:

![image-20240724153902332](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/38-Gitignore/image-20240724153902332.png)

If you are using a Linux system, you need to use the -a flag of the ls command to display hidden files:

```defalut
ls -a
```

The default configuration of this file is:

```default
.vscode/
Cache/
Libraries/
Temp/
*.lock
```

Where:

folder name + “/” means to hide all files in that folder, and “*” + file name suffix means to hide all files with that suffix.

.vscode/: This is the VS Code configuration folder.

Cache/: This is the cache folder.

Libraries/: This is the official library folder, which cannot be edited.

Temp/: This is the temporary folder, which contains run logs and other content.

*.lock: This is all locked files.

The above are the files that Git recommends ignoring.

# Editing rules for the .gitignore file

Normally, you do not need to edit the .gitignore file. However, if you have additional files that you want to ignore or files that you want to add as concerns, you can check this description. However, it should be noted that the .gitignore file itself needs to be synchronized to the remote repository, and all collaborators in the corresponding repository will be affected by changes to the configuration of this file.

## Comments

Lines beginning with # are comments.

![image-20240724160110626](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/38-Gitignore/image-20240724160110626.png)

## Ignore files and directories

A string entered on its own will hide directories and files with the same name:

![image-20240724160343666](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/38-Gitignore/image-20240724160343666.png)

> However, files generally have extensions that distinguish them from directory names.

## Ignore only directories

![image-20240724160709884](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/38-Gitignore/image-20240724160709884.png)

Ignore all files in the directory with this name. This includes directories with the same name in multiple levels, e.g. */foldername/

## Using wildcards

1. The asterisk “*” matches multiple characters. *.test means to block all files ending in .test.
2. The question mark “?” matches any character except “/”. t?st means to block all files or directories with a name of four characters and the first, third and fourth characters being t, s or t.

3. Square brackets “[]” match every character inside the brackets. *.[abc] means that all files ending in .a, .b or .c will be ignored.

The use of a dash within square brackets means to match any character within the range of two characters. [0-9] means to match any digit from 0 to 9 in sequence.

## Reverse operation

The use of “!” can add back to the list of files that have previously been ignored.

![image-20240724161929601](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/38-Gitignore/image-20240724161929601.png)

> The filename file in foldername will be retracked.

## Other rules

1. Each line in the .gitignore file is a matching pattern, and empty lines do not match any files.
2. Git tracks files, not directories.
3. If a file is already tracked by Git, it will not be ignored even if it is added to the .gitignore file.



If you have further needs, you can refer to gitignore and the Git user guide on your own.
