* **CPU** pertains to the hardware that executes instructions.
* **Processors** are physical chips that contain one or more CPUs
* **Cores** are the basic computation unit of the CPU

* Multicore processors are faster up to a point of diminishing returns as many processors compete for memory.
* **Non-Uniform Memory Access**  (NUMA) is a system where each processor / core has its own local [[Cache Memory]], and each local memory is connected via remote memory (called the **shared system interconnect**). *This makes local access fast but remote access slow*.