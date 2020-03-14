# yocto

- **PC** *$* `git clone https://git.yoctoproject.org/git/poky`
- **PC** *$* `cd poky`
- **PC** */poky$* `git checkout yocto-2.6.4`
- **PC** */poky$* `source oe-init-build-env`
- **PC** */poky/build$* `bitbake core-image-minimal`
- **PC** */poky/build$* `runqemu qemux86`
- **PC** */poky/build$* `cd ../../`
- **PC** *$* `bitbake-layers create-layer meta-live`
- **PC** *$* `bitbake-layers show-layers`
- mo file **poky/build/conf/bblayers.conf** va then duong dan meta-live vua tao, 
- vi du /home/vanson/yocto-project/meta-live

    ```
    # POKY_BBLAYERS_CONF_VERSION is increased each time build/conf/bblayers.conf
    # changes incompatibly
    POKY_BBLAYERS_CONF_VERSION = "2"

    BBPATH = "${TOPDIR}"
    BBFILES ?= ""

    BBLAYERS ?= " \
    /home/vanson/yocto-project/poky/meta \
    /home/vanson/yocto-project/poky/meta-poky \
    /home/vanson/yocto-project/poky/meta-yocto-bsp \
    /home/vanson/yocto-project/meta-live \
    "
    ```
- **PC** *$* `bitbake-layers show-layers`
- **PC** */poky/build$* `bitbake -f example`
