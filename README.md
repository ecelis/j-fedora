# The J programming language

J is a high-level, general-purpose programming language that is particularly
suited to the mathematical, statistical, and logical analysis of data. It is a
powerful tool for developing algorithms and exploring problems that are not
already well understood.

J is written in portable C and is available for Windows, Linux, Mac, iOS, Android
and Raspberry Pi. J can be installed and distributed for free. The [source](https://github.com/jsoftware/jsource)
provided under both commercial and GPL 3 licenses.

J is easy to install, has a small footprint, and has direct access to tutorials
and documentation.


## Build
```sh
git clone https://github.com/jsoftware/jsource.git
cd jsource
cp jsrc/jversion-x.h jsrc/jversion.h
sed -i 's/#define\s*jbuilder\s*"unknown"/#define jbuilder   "ecelis@sdf.org"/' \
    jsrc/jversion.h
cd make2
chmod *.sh
./build_all.sh
./clean.sh
jplatform=linux j64x=j64 ./build_jconsole.sh
jplatform=linux j64x=j64 ./build_libj.sh
jplatform=linux j64x=j64 ./build_tsdll.sh 
```

## Test

```sh
./cpbin.sh
cd ../jlibrary/bin
./jconsole ../../test/tsu.ijs
```

Within J console run
```
RUN ddall
RECHO ddall
```

# Test webassembly
```sh
cd $HOME/Projects
git clone https://github.com/emscripten-core/emsdk.git
cd emsdk
./emsdk activate latest
```

## Install


```sh
export JROOT=~/j9.6.0-beta27
mkdir $JROOT
echo "export JROOT=$JROOT" >> ~/.bashrc
echo '$JROOT:$JROOT/bin:$PATH' >> ~/.bashrc
cp -rv j_template/*
cp -rv jlibrary/* $JROOT
```
