# Basilisk

## Setting up the dependencies

The setup is made simple with the following shell code. Open the terminal and paste in the following

```bash
sudo apt install darcs flex bison make gawk  ## Installs dependency libraries
darcs get --lazy http://basilisk.fr/basilisk  ## Get Basilisk library
cd basilisk/src

echo "export BASILISK=$PWD" >> ~/.bashrc  # Export the paths so you can build from any directory
echo "export PATH=\$PATH:$BASILISK" >> ~/.bashrc

ln -s config.gcc config  # Symbolic link to the config
make -k
make
```

## Using the Makefile

When you want to start a new project, create a new folder to keep all files in. Then change into this directory and create a simple `Makefile`.

```bash
mkdir projectname
cd projectname
vim Makefile
```

Inside the Makefile, write the following:

```Makefile
CFLAGS += -O2
include $(BASILISK)/Makefile.defs
```

When you want to compile `file.c`  and run the code, all you have to do is type

```bash
make file.tst  # NOTE: We compile file.c but have told it to make file.tst
```

This will create the folder `file` in your directory.
For the simple test case included here, you can try

```bash
make test.tst
animate test/out  # here we display the animation
```

The make process takes some time because it actually generates all the outputs too and puts them in out new folder!

