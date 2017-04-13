Using the FreeSRP with Baudline
===============================

`freesrp-io` is a command-line utility that can be used to read from a file and transmit the read samples or receive and write the raw samples to a file. It also supports output to `stdout`, so it can be used in Unix pipes. This is extremely powerful, because it will allow you to pipe the data from `freesrp-io` into any other program that accepts data on its standard input, `stdin`.

Baudline is "a time-frequency browser designed for scientific visualization of the spectral domain", as described on `its website <http://www.baudline.com/what_is_baudline.html>`_. It supports input over `stdin`, so it can be used in a pipe with `freesrp-io`.

Once you have downloaded Baudline, it is very easy to use it with the FreeSRP and start streaming samples into it. Everything can be done in this one command:

.. code-block:: bash
    
    freesrp-io -f100e6 -b10e6 -g15 -o- | baudline -stdin -channels 2 -quadrature -format le16 -samplerate 10000000



There are a couple of arguments to both `freesrp-io` and `baudline`.

* `freesrp-io`:
    * `-f`: This sets the frequency, in hertz. Setting it to `100e6` like in the example will set the FreeSRP's center frequency to 100 MHz.
    * `-b`: This sets the AD9364's sample rate, in samples per second. Setting it to `10e6` will therefore set it to 10 megasamples per second (MSps).
    * `-g`: This option sets the gain, in dB. In the example, the receiver gain is set to 15 dB.
    * `-o`: With this option, you specify the output file. In this example, the output file is `-`, which means output to `stdout`. You can also specify a regular file, which will result in the samples getting written to disk.
* `baudline`:
    * `-stdin`: Sets up baudline to get input from `stdin`.
    * `-channels`: The number of channels -- here, it's set to two: One channel represents the I-part and the other one the Q-part of the complex IQ samples the FreeSRP outputs.
    * `-quadrature`: This will tell baudline that we are using IQ (quadrature) samples.
    * `-format`: The datatype of the samples. `le16` means 16-bit signed integers that are little-endian encoded.
    * `-samplerate`: The sample rate in samples per second, which should match the setting in `freesrp-io`. Here, it's set to 10 MSps.


