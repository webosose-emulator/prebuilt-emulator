How to build
============

How to build virglrenderer
--------------------------
* Pre-requirement
  * sudo apt-get update
  * sudo apt-get upgrade
  * sudo apt-get -f install git libtool libdrm-dev libepoxy-dev libgbm-dev libegl1-mesa-dev libgtk-3-dev autoconf
* Build
    ```
    git clone git://anongit.freedesktop.org/virglrenderer
    cd virglrenderer
    git checkout virglrenderer-0.6.0
    ./autogen.sh
    ./configure --with-glx
    make && sudo make install
    ```

How to build qemu
-----------------
* Pre-requirement
  * Build virglrenderer package
  * sudo apt-get update
  * sudo apt-get upgrade
  * sudo apt-get -f install libsdl2-dev libpixman-1-dev flex libusb-dev libusb-1.0-0-dev
* Build
    ```
    git clone https://github.com/webosose-emulator/qemu
    cd qemu
    ./configure --target-list=x86_64-softmmu --enable-sdl --with-sdlabi=2.0 --audio-drv-list=alsa,pa
    make
    ```

Put results to prebuilt-emulator
----------------------------------
On 64bits Ubuntu,
* clone prebuilt-emulator
   * git clone http://mod.lge.com/hub/emulator/prebuilt-emulator.git
* virglrenderer
    * cp /usr/local/lib/libvirglrenderer.so* prebuilt-emulator/lib/x86_64
* qemu
    * cp x86_64-softmmu/qemu-system-x86_64 prebuilt-emulator/bin/x86_64
    * cp -rf pc-bios prebuilt-emulator/bin
