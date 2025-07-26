# Installing SystemC in WSL

Open an Ubuntu shell and go to the directory where SystemC package has been extracted.

```bash
cd systemc-3.0.1
```

Create a directory where SystemC installation scripts and Makefile would be generated.

```bash
mkdir objdir
cd objdir
```
Now, We need to enable PTHREADS and DEBUG options in SystemC installation.

```bash
../configure --enable-pthreads --enable-debug
```

This would check for all available C++ compilers, automake tools etc and generate a Makefile suitable for your environment.
Run the Makefile.

```bash
make
```

Check if the build was successful. This step would take about 10 minutes to finish.

```bash
make check
```

Now we will install the SystemC

```bash
make install
```

This would create an include directory where all headers are placed and a lib-linux64 directory where SystemC libraries are placed.

Setup the environment variables required by SystemC

```bash
export SYSTEMC_HOME=/mnt/e/Documents/Code/systemc-3.0.1
export LD_LIBRARY_PATH=$SYSTEMC_HOME/lib-linux64:$LD_LIBRARY_PATH
```

Congratulations! Your SystemC installation in WSL is complete. Next we would work on creating our first sc_main "Hello World" program which links VS Code to WSL and SystemC library.

