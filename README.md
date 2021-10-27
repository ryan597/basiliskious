# Basilisk

## Setting up the dependencies

The setup is made simple with the following shell code. Open the terminal and paste in the following

```bash
sudo apt install darcs flex bison make gawk  ## Installs dependency libraries
sudo apt install gnuplot imagemagick ffmpeg graphviz valgrind gifsicle pstoedit # Plotting libs
darcs get --lazy http://basilisk.fr/basilisk  ## Get Basilisk library
cd basilisk/src

echo "export BASILISK=$PWD" >> ~/.bashrc  # Export the paths so you can build from any directory
echo "export PATH=\$PATH:$BASILISK" >> ~/.bashrc
source ~/.bashrc  # Reload the rc

ln -s config.gcc config  # Symbolic link to the config
make -k
make
```

## Example

For an example, see the [Tutorial](program1/test.c), which was simply taken from the [Basilisk](http://basilisk.fr/Tutorial) website. 

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

Now you can "Do the Things" for your simulation eg. in a file called `test.c`.

When you want to compile `test.c`  and run the code, all you have to do is type

```bash
make test.tst  # NOTE: We have told it to make test.tst, in the Makefile.defs there are rules for this
```

This will create the folder `test` in your directory.
With the included files you should now be able to see the output animation.

```bash
animate test/out  # here we display the animation
```

The make process takes some time because it actually generates all the outputs too and puts them in out new folder!

