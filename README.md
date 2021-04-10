# RPis, Linux and PREEMPT_RT
Software (master & slave) modules for Linux kernels versions latency measurements with and without PREEMPT_RT patch for RPi3&amp;4 (Linux distributions  for RPis: Raspbian Jessie, Raspbian Buster, Ubuntu mate, Arch Linux, and Debian).
Software modules used to perform real-time performance mesurements of the Linux kernel versions (in RPi3&4), in a master-slave schema. The Raspberry device under test (slave) is connected to, and communicates with, another Raspberry (master) that performs the actual measurements. Measurements include the latency of response tasks in user and kernel space, the response at specific periodic rates on execution of periodic tasks in user and kernel space, the maximum sustained frequency, min, max, std.deviation and variance.

# Prerequisites

Two raspberryPi devices are required connected in a master-slave schema. The RPI under test is the named the slave device and the master is the RPi that performs the measurements. Connectivity: masters GPIO17 (pin 11) is configured as output connected to slaves GPIO27 (pin 13) configured as input, and vica versa the other way.
Any kernel version could be installed from release 4 (e.g., 4.4, 4.9, 4.14, 4.19) or later, and the PREEMPT_RT patch (https://wiki.linuxfoundation.org/realtime/preempt_rt_versions).

# Installation

Simply install the software source files found respectively in master and slave folders into the master and slave device respectively.

For user and kernel space response task measurements:
in the master COMPILE: gcc gpio_master.c -o gpio_master -lm -lrt  -lpthread
in the slave COMPILE: gcc gpio_slave.c -o gpio_slave -lrt  -lpthread

For user space periodic task measurements:
in the master COMPILE: gcc gpiop_master.c -o gpiop_master -lm -lrt
in the slave COMPILE: gcc gpiop_slave.c -o gpiop_slave -lrt 

For kernel space periodic task measurements:
in the master COMPILE: gcc kgpiop_master.c -o kgpiop_master -lm -lrt 

# Usage

Response task measurements at user space
Run the slave first, then the master to perform the measurements.
in the slave device run: sudo ./gpio_master <number-of-loops>
in the master device run: RUN: sudo ./gpio_slave <number-of-loops>
  
Response task measurements at kernel space:
Run the slave first, then the master to perform the measurements.
in the slave device run: make and sudo insmod kgpio4_slave.ko
in the master device run: RUN: sudo ./gpio_slave <number-of-loops>

Periodic task measurements at user space:
in the slave device run: sudo chrt -f 99 ./gpiop_slave <number-of-loops> <semi-period in nsecs>
in the master device run: sudo chrt -f 99 ./gpiop1_master <number-of-loops>

Periodic task measurements at kernel space:
in the slave device run: make and sudo insmod kgpiop2.ko
in the master device run: sudo chrt -f 99 ./kgpiop_master <number-of-loops>
