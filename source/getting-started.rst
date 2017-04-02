Getting Started
===============

Installing `libfreesrp`
-----------------------

`libfreesrp` is a library that provides access to the FreeSRP. It is required for using the FreeSRP in GNU Radio, as the `gr-osmosdr` needs it to provide support for the FreeSRP. Additionally, `libfreesrp` comes with useful command-line utilities.

There are packages for `libfreesrp` on Ubuntu. On other systems, you will have to build it from source.

Ubuntu
~~~~~~

On Ubuntu 14.04, 16.06 and 16.10, you can install `libfreesrp` from the `FreeSRP PPA <https://launchpad.net/~llb/+archive/ubuntu/freesrp>`_ as follows:

.. code:: bash

    sudo add-apt-repository ppa:llb/freesrp
    sudo apt update
    sudo apt install libfreesrp


Building from source
~~~~~~~~~~~~~~~~~~~~

If `libfreesrp` is not available as a prebuilt package for your system, or you want to get the latest changes present in the `libfreesrp` Git repository, you will have to build `libfreesrp` from source.

To build from source, you need to install the following dependencies first:

* GNU Make and GCC (Debian: `apt install build-essential`, Fedora: `dnf install @development-tools`)
* CMake (Debian: `apt install cmake`, Fedora: `dnf install cmake`)
* libusb 1.0 (Debian: `apt install libusb-1.0-0-dev`, Fedora: `dnf install libusb1-devel`)
* Boost (Debian: `apt install libboost-all-dev`, Fedora: `dnf install boost-devel`)

Now, get the source code:

.. code:: bash

    git clone https://github.com/FreeSRP/libfreesrp.git

And build the library:

.. code:: bash

    cd libfreesrp
    mkdir build && cd build
    cmake .. -DCMAKE_BUILD_TYPE=Release
    make

Finally, install it:

.. code:: bash

    make install  # Run this as root


Getting the firmware
--------------------

In addition to `libfreesrp`, you will have to download firmware for the FreeSRP's FX3 microcontroller and a bitstream for the FreeSRP's FPGA. This is required because the FreeSRP hardware does not come preprogrammed by default, and needs to be programmed before its first use. You will also want to repeat this process to upgrade your firmware every time improved versions are available.

On Ubuntu, the `freesrp-firmware` package provides the latest firmware and FPGA bitstream. On other systems, you will have to download it manually.

Ubuntu
~~~~~~

Assuming you already added the FreeSRP PPA as shown above (when installing `libfreesrp`), you can now also install the firmware by running:

.. code:: bash
    
    sudo apt install freesrp-firmware


Manual firmware download
~~~~~~~~~~~~~~~~~~~~~~~~

You can download the firmware here: 

.. todo::
    
    Upload FX3 firmware and FPGA bitstream and put download links here


After extracting the downloaded archive, you should create a new folder in your home directory called `.freesrp`. Place the `fx3.img` and `fpga.bin` files in there.


Testing your FreeSRP
--------------------

Now, you are ready to verify you can interface with your FreeSRP. Plug the FreeSRP into a USB 3.0 port on your computer and run:

.. code:: bash
    
    freesrp-ctl --fx3 --fpga

If everything is installed correctly, after a few seconds you will see:

.. code::

    Sucessfully uploaded FreeSRP firmware to FX3
    Found FreeSRP
    Loading FPGA with '.freesrp/fpga.bin'
    FPGA configured successfully
    Connected to FreeSRP
    Version: FX3 v0.1.0, FPGA v0.1.0

This means programming the FreeSRP was successful.


Next steps
----------

To actually do anything useful with your FreeSRP now, you will probably want to install GNU Radio. See :doc:`freesrp-gnuradio` for a guide on setting it up. You can also download Baudline and use it with `freesrp-io`, see :doc:`baudline` for that.
