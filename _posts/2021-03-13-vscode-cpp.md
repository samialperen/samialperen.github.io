---
layout: post
title:  "Configure Virtual Studio Code for C++17 (Linux)"
author: Alperen
date:   2021-03-13
categories:
  - Software
---

In this post, I will explain how to configure VS Code for C++17 on Linux. As a compiler, we will use **g++/GCC**, and as a debugger, we will use **GDB**. I tested these steps on Ubuntu 16.04, but they should work in all Linux systems.


For configuration of VS code for c++11, you can follow [official documentation](https://code.visualstudio.com/docs/cpp/config-linux).

* As an initial step, I will assume that you have already followed [the official documentation](https://code.visualstudio.com/docs/cpp/config-linux),  
* Next, make sure that you are using **g++** version 7 or higher since some of the functionalities comes with c++17 are not available until GCC version 7.
* Check your **GCC/g++** version:
```
$ g++ --version
```
* If the version is less than 7, then follow the steps in [this link](https://tuxamito.com/wiki/index.php/Installing_newer_GCC_versions_in_Ubuntu). If you already have a version 7 or higher, then you can jump into modifying **.json** files.

* **c_cpp_properties.json** file should have cpp standard as c++17. If you don't have this file under ```.vscode/``` folder, then you can create it by viewing the C/C++ configuration UI by running the command C/C++: Edit Configurations (UI) from the Command Palette (Ctrl+Shift+P).
```
{
    "configurations": [
        {
            "name": "Linux",
            "includePath": [
                "${workspaceFolder}/**"
            ],
            "defines": [],
            "compilerPath": "/usr/bin/gcc",
            "cStandard": "c11",
            "cppStandard": "c++17",
            "intelliSenseMode": "clang-x64"
        }
    ],
    "version": 4
}
```

* **tasks.json** file should have ```-std=c++17``` as an argument:
```
{
    "version": "2.0.0",
    "tasks": [
        {
            "type": "shell",
            "label": "g++ build active file",
            "command": "/usr/bin/g++",
            "args": [
                "-g",
                "-std=c++17",
                "${fileDirname}/*.cpp", // to allow compilation of all cpp files in the same folder
                "-o",
                "${fileDirname}/${fileBasenameNoExtension}"
            ],
            "options": {
                "cwd": "/usr/bin"
            },
            "problemMatcher": [
                "$gcc"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            }
        }
    ]
}
```

* **settings.json** does not require any change, but here it is as a reference:
```
{
    "files.associations": {
        "iostream": "cpp",
        "type_traits": "cpp"
    }
}
```

* **launch.json** does not require any change either:
```
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "g++ - Build and debug active file",
            "type": "cppdbg",
            "request": "launch",
            "program": "${fileDirname}/${fileBasenameNoExtension}",
            "args": [],
            "stopAtEntry": true,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ],
            "preLaunchTask": "g++ build active file",
            "miDebuggerPath": "/usr/bin/gdb"
        }
    ]
}
```






