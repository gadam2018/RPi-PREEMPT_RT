# RPi-PREEMPT_RT
Software modules for kernels versions latency measurements with and without PREEMPT_RT patch for RPi3&amp;4 (Linux versions  for RPis: Raspbian Jessie, Raspbian Buster, Ubuntu mate, Arch Linux, and Debian) .

# Prerequisites

Two raspberryPi devices are required connected in a master-slave schema. The RPI under test is the named the slave device and the master is the RPi that performs the measurements. Connectivity: masters GPIO17 (pin 11) is configured as output connected to slaves GPIO27 (pin 13) configured as input, and vica versa the other way.
Any kernel version could be installed from release 4 (e.g., 4.4, 4.9, 4.14, 4.19) or later, and the PREEMPT_RT patch (https://wiki.linuxfoundation.org/realtime/preempt_rt_versions).

# Installation

Simply install the software source files found respectively in master and slave folders into the master and slave device respectively.

Software (master & slave) modules used to perform real-time performance test of the above Linux versions (in RPi3&4), in a master-slave schema. The Raspberry device under test (slave) is connected to, and communicates with, another Raspberry (master) that performs the actual measurements. Measurements include the latency of response tasks in user and kernel space, the response at specific periodic rates on execution of periodic tasks in user and kernel space, the maximum sustained frequency.
