

(PS, My play ground for macaw libraries.)

### From a fresh Ubuntu:
```
  $ sudo add-apt-repository ppa:hvr/ghc
  $ sudo apt-get update
  $ sudo apt-get install ghc-8.2.2
```
### Build steps:
```
  $ git submodule update --init --recursive
  $ stack build
```
### Execution:
```
  $ stack exec avta-demo /dir/to/elf.exe
```
#### Note for MacOS users:
  The input language of macaw is Elf, which is not a format of object file format supported by OS X (Mach-O).

  To generate Elf file on MacOS, we cross-compile to a linux target.
  1. set gcc target to be a linux machine:
```
  $ gcc -fno-stack-protector -foptimize-sibling-calls -target x86_64-unknown-linux-gnu -c -o foo.o foo.c
```
  2. use a linker configured for that target-triple. Follow the instructions on
  https://stackoverflow.com/questions/39059597/how-to-create-an-elf-executable-on-mac-os-x before running: 
```
  $ ~/.local/binutils/x86_64-unknown-linux-gnu/bin/ld -static -o foo.exe foo.o
```


