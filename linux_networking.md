# Notes on Linux Networking

## Rami Rosen's Slides

<http://www.haifux.org/lectures/172/netLec.pdf>
<http://www.haifux.org/lectures/217/netLec5.pdf>

-   the linux kernel deals with layers 2 (Ethernet), 3 (IP), 4 (UDP, TCP)
-   the two most important data structures are:
-   [sk<sub>buff</sub>](http://lxr.free-electrons.com/source/include/linux/skbuff.h#L626): contains metadata and packet data
-   [netdevice](http://lxr.free-electrons.com/source/include/linux/netdevice.h#L1560): represents a network device ([field description](http://www.makelinux.net/ldd3/chp-17-sect-3))

Rosen references this [packet walkthrough](http://jsevy.com/network/Linux_network_stack_walkthrough.html) as prerequisite for his
slides.  Here is [another view](https://wiki.linuxfoundation.org/images/1/1c/Network_data_flow_through_kernel.png) from the Linux Foundation.

-   routing table and cache enable us to find the net device and address
    to which a packet will be sent
-   implemented by `struct fib_table`

### Netlink Sockets

Netlink sockets are a form of IPC that allows communication between a
user process and the kernel.  `ioctl()` communication is similar, but
it does not permit asynchronous messaging from the kernel while
netlink sockets do.
