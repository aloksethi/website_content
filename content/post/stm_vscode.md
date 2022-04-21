---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Using ST32 uC in vscode"
subtitle: ""
summary: ""
authors: []
tags: [STM32, vscode]
categories: []
date: 2021-01-18T23:15:06+02:00
lastmod: 2021-01-18T23:15:06+02:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---
Below are the steps I used to have a basic building and debugging interface for STM32 uCs in vscode. 
Ultimately I did move to STM32CubeIDE as that seemed to be more debuggin friendly.

1. Used STM32CubeMX for generating a makefile based project.
1. Installed chocolatey inorder to get 'make' [choco](https://chocolatey.org/install).  `choco install make`
1. made directory `.vscode`, created file `tasks.json`
```
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "Build",
            "type": "shell",
            "command": "make",
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "presentation": {
                "reveal": "always",
                "panel": "new"
            },
            "problemMatcher": [
                "$gcc"
            ]
        },
        {
            "label": "Build clean",
            "type": "shell",
            "command": "make clean",
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "presentation": {
                "reveal": "always",
                "panel": "new"
            },
        }
    ]
}
```    
1. can build now with `Ctrl+Shift+B`
1. make another file `launch.json` 
```
{
    "configurations": [
        {
            "cwd": "${workspaceRoot}",
            "request": "launch",
            "type": "cortex-debug",
            "servertype": "openocd",
            "name": "Debug (OpenOCD)",
            "preLaunchTask": "Build",
            "runToMain": true,
            "executable": "./build/mmcov4_controller.elf",
            "device": "STM32F429ZIT6U",
            "configFiles": [
                "interface/stlink.cfg",
                "target/stm32f4x.cfg"
            ],
            "svdFile": "${workspaceRoot}/.vscode/STM32F429.svd",
            "swoConfig": {
                "enabled": true,
                "cpuFrequency": 8000000,
                "swoFrequency": 2000000,
                "source": "probe",
                "decoders": [
                    {
                        "type": "console",
                        "label": "ITM",
                        "port": 0
                    }
                ]
            }
        }
    ]
}
```
1. Now, with `Ctrl+Shift+D` can move to debug view from where the uC can be programmed and debugged.