# Setting up Windows Subsystem for Linux (WSL)

First of all download Ubuntu from Windows Store
[Download Ubuntu from Windows Store](https://apps.microsoft.com/detail/9PDXGNCFSCZV?hl=en-us&gl=US&ocid=pdpshare)

Next we need to enable WSL features on the PC.
Go to Control Panel > Porgrams > Turn Windows features on and off
In this menu, make sure to select
* Virtual Machine Platform
* Windows Subsystem for Linux

<img width="414" height="364" alt="image" src="https://github.com/user-attachments/assets/5c59de25-818c-4f94-b6b8-77a9445a2673" />

Restart the PC for the features to be enabled.

Now open the Ubuntu app. This would open the command prompt and start setting up Ubuntu.

Setup your Ubuntu username and a password (This can be different from Windows credentials)

Once at the bash prompt, now its time to install all of packages required by SystemC
You would be asked to enter the Ubuntu password to proceed each installation.

```bash
sudo apt install g++
sudo apt install gcc
sudo apt install make
sudo apt install gdb
sudo apt-get install automake
sudo apt install cmake
```

Make sure things are installed properly

```base
which g++
g++ --version

which gcc
gcc --version

which make
make --version

which gdb
gdb --version

which automake
automake --version

which cmake
cmake --version
```

Congratulations! You have successfully setup the WSL in order to be ready to install SystemC on your PC.
Next we will learn to install the SystemC.
