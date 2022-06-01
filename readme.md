# OpenOCD configuration for flashing the FPGA and PROM

## Prerequisites
### JTAG adapter
OpenOCD supports most FTDI-based adapters. We recommend Digilent HS2/HS3. OpenOCD does not support the Xilinx Platform Cable DLC9G.

### Software
Install [OpenOCD](http://openocd.org/). Binary is available for Linux, Mac OS, and Windows.

For Ubuntu, install from apt repository.

```
sudo apt install openocd
```

Create a udev rule for the JTAG (if you are using the Digilent JTAG). Create a file at `/etc/udev/rules.d/52-digilent-usb.rules` with the following content.

```
ATTR{idVendor}=="1443", MODE:="666"
ACTION=="add", ATTR{idVendor}=="0403", ATTR{manufacturer}=="Digilent", MODE:="666"
```

Reload the udev rules.

```
udevadm control --reload-rules
```

Now unplug and plug in your JTAG adapter.


## Usage

`cd` into the `openocd` directory. Use the `program_fpga.sh`. The working directory must be `openocd`.

```
./program_fpga.sh

```

## License
The bitstream included in the distribution `bscan_spi_xc6slx45.bit` is built from the following source under GPLv2.

https://github.com/quartiq/bscan_spi_bitstreams

```
Copyright (C) 2015-2019 Robert Jordens <rj@quartiq.de>

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 2 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.
```
