# RPi-PREEMPT_RT
Latency measurements of RPi3&amp;4 with Linux versions (Raspbian Jessie, Raspbian Buster, Ubuntu mate, Arch Linux, and Debian) with and without PREEMPT_RT patch.

Software (master & slave) modules used to perform real-time performance test of the above Linux versions (in RPi3&4), in a master-slave schema. The Raspberry device under test (slave) is connected to, and communicates with, another Raspberry (master) that performs the actual measurements. Measurements include the latency of response tasks in user and kernel space, the response at specific periodic rates on execution of periodic tasks in user and kernel space, the maximum sustained frequency.
