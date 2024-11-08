Meson bug showcase

```shell
$ rm -r buildDir; meson format -i -r && meson setup --reconfigure buildDir && meson compile -j16 --verbose -C buildDir
The Meson build system
Version: 1.6.0
Source dir: /tmp/meson_preprocessor_bug
Build dir: /tmp/meson_preprocessor_bug/buildDir
Build type: native build
Project name: my_project
Project version: undefined
C compiler for the host machine: ccache cc (gcc 11.4.0 "cc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0")
C linker for the host machine: cc ld.bfd 2.38
Host machine cpu family: x86_64
Host machine cpu: x86_64
meson.build:8: WARNING: Source item '/tmp/meson_preprocessor_bug/buildDir/preprocessor_0.p/lscript.pp.ld' cannot be converted to File object, because it is a generated file. This will become a hard error in meson 2.0.
Build targets in project: 3

Found ninja-1.10.1 at /usr/bin/ninja
INFO: autodetecting backend as ninja
INFO: calculating backend command to run: /usr/bin/ninja -C /tmp/meson_preprocessor_bug/buildDir -j 16 -v
ninja: Entering directory `/tmp/meson_preprocessor_bug/buildDir'
ninja: error: '/tmp/meson_preprocessor_bug/buildDir/preprocessor_0.p/lscript.pp.ld', needed by 'lscript.pp.strip.ld', missing and no known rule to make it
```
