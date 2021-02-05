# manifest-kmtek-stm32mp

## Required Packages for the Build Host
Essentials: Packages needed to build an image on a headless system:

     $ sudo apt-get install gawk wget git diffstat unzip texinfo gcc-multilib \
     build-essential chrpath socat cpio python3 python3-pip python3-pexpect \
     xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev \
     pylint3 xterm
                        
Documentation: Packages needed if you are going to build out the Yocto Project documentation manuals:

     $ sudo apt-get install make xsltproc docbook-utils fop dblatex xmlto
     
## Build Yocto
- `mkdir yocto-kmtek`
- `cd yocto-kmtek`
- `repo init -u https://github.com/thanhduongvs/manifest-kmtek-stm32mp.git -b dunfell`
- `repo sync -j8`
- `DISTRO=openstlinux-weston MACHINE=kmtek source layers/meta-st/scripts/envsetup.sh build`
- `bitbake kmtek-weston --runall=fetch` (download package)
- `bitbake -k kmtek-weston` (build image)

## Generate the SDK installation
- `bitbake -c populate_sdk kmtek-weston`
- `ls tmp-glibc/deploy/sdk/`
- [How to create an SDK for OpenSTLinux distribution](https://wiki.st.com/stm32mpu/wiki/How_to_create_an_SDK_for_OpenSTLinux_distribution)
