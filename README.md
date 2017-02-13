
<p align="center"><img src="http://i.imgur.com/BbD1jGBl.jpg" alt="tux"/><img src="https://blog.manjaro.org/wp-content/uploads/2012/08/logo.png" alt="manjaro"/></p>

##<p align="center">**Linux Kernel 4.9 LTS (EOL 01-2019) with custom patchset for Manjaro Linux**<br/></p>

|SOURCES FOR BUILD KERNEL PACKAGE IN MANJARO LINUX |
:---------------------------------------------------

|WARNING: PACKAGES OVERWRITES INSTALLED MANJARO `linux49` SERIES!|
:-----------------------------------------------------------------

|DESIGNED FOR HIGH END MULTICORE CPUS|           
:-------------------------------------
|**USE AT YOUR OWN RISK**            |

<hr/>

## INSTALLATION GUIDE

* Set VALID custom flags:

**/etc/makepkg.conf**

```
CFLAGS="-march=native -O2 -pipe -fstack-protector-strong"
CXXFLAGS="${CFLAGS}"
MAKEFLAGS="-j$(nproc)"
COMPRESSXZ=(xz -c -z - --threads=0)
```

* Clone repository, build packages and install:

```
git clone https://github.com/FadeMind/linux49-muqss.src.git
## main kernel packages
export LANG=C;mkdir -p /tmp/makepkg
cd linux49-muqss.src/linux49
BUILDDIR=/tmp/makepkg makepkg -srci
## bbswitch module
cd ../linux49-bbswitch
BUILDDIR=/tmp/makepkg makepkg -srci
## nvidia modules
cd ../linux49-nvidia
BUILDDIR=/tmp/makepkg makepkg -srci
## r8168 module
cd ../linux49-r8168
BUILDDIR=/tmp/makepkg makepkg -srci
```

* **SHUTDOWN AND POWER ON PC (DO NOT REBOOT!)**

<hr/>

## CUSTOMS

* **`[Patch] Con Kolivas Patchset`**
* **`[Patch] AUFS4 Support`**
* **`[Patch] Reiser4 Support`**
* **`[Patch] exFAT Support`**
* **`[Patch][Config] Native optimizations autodetected by GCC for CPU`**
* **`[Config] NUMA is disabled in default`**
* **`[Config] BFQ is default I/O scheduler`**
* **`[Config] MuQSS is default CPU scheduler`**

## LICENSE

[GPL2](https://www.gnu.org/licenses/gpl-2.0.txt)
