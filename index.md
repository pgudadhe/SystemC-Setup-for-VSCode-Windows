# SystemC setup for Visual Studio Code Projects in Windows

## Overview
In this project we will learn how to setup SystemC on Windows to be used by a C++ project in Visual Studio Code. Our end goal here in to create a SystemC project with SC_METHOD getting triggered. From my past experiences writing a "Hello World" program in Visual Studio Code with SystemC is super easy (relatively). But things get very notorious when it comes to threads and processes in this scenario. SystemC Windows build capabilities are mainly developed around availability of Visual Studio Professional and not Visual Studio Code. After countless hours of searching, trying around I have reached a successful implementation of a project in Visual Studio Code (VSCode) with SC_METHOD/SC_THREADS. In this article I will explain the step by step process I followed to get everything set up for this project.

## Getting Started

First of all, Download the latest SystemC package: 

[Download SystemC - Accellera Systems Initiative](https://accellera.org/downloads/standards/systemc)

Extract all the files

or
```bash
git clone https://github.com/accellera-official/systemc.git
```

We will be running SystemC on Windows Subsystem for Linux (WSL). Following article looks at this process in detail. If you have already set it up, you can skip it.

[Next: WSL Setup](https://github.com/pgudadhe/SystemC-Setup-for-VSCode-Windows/wiki/Setting-up-Windows-Subsystem-for-Linux-(WSL))
