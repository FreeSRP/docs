Source code and design files
============================

All of the design files for hardware and source code for software are being posted online. Here, you will find an outline of the different software/hardware components and learn where to get their source code:

Software
--------

* **libfreesrp**: This is a C++ library you can use to interface with the FreeSRP. The source code is on `GitHub <https://github.com/FreeSRP/libfreesrp>`_.
* **cfreesrp**: This is a C library that wraps libfreesrp. It is not production ready yet. Its main goal is allowing access to the FreeSRP from other languages that have foreign function interfaces that work well with C but not with C++. The source code is on `GitHub <https://github.com/FreeSRP/cfreesrp>`_.
* **gr-osmosdr**: This library provides blocks for using various software-defined radios in GNU Radio. The upstream gr-osmosdr project does not yet support the FreeSRP, but a fork that does provide support is available on the `FreeSRP GitHub <https://github.com/FreeSRP/gr-osmosdr>`_.
* **SoapyOsmo**: Support for SoapySDR and the Pothos SDR framework are provided through a custom fork of SoapyOsmo, which incorporates the changes from the custom gr-osmosdr from above. `Get it on GitHub <https://github.com/FreeSRP/SoapyOsmo>`_.

Firmware
--------

* **USB microcontroller software**: This is the firmware running on the Cypress EZ-USB FX3 microcontroller. Currently, it mostly handles streaming data between a PC and the FPGA, but will also be running the driver for the AD9364 (which is currently running on a MicroBlaze soft core processor on the FPGA) in the future. The `source code is available on GitHub <https://github.com/FreeSRP/usb-firmware>`_.
* **FPGA design**: This is the design for the Artix 7 FPGA on the FreeSRP which handles interfacing with the AD9364 and FX3. It currently also includes a MicroBlaze processor that runs a driver for the AD9364, but this will be moved to the USB microcontroller soon. `Get the source code on GitHub <https://github.com/FreeSRP/fpga>`_.
    
Hardware
--------

* **FreeSRP software-defined radio hardware**
    * **Full designs in the CircuitMaker repository**: Coming soon!
    * **PDF schematics**: `Download <http://freesrp.org/schematics/freesrp_alpha.pdf>`_.
