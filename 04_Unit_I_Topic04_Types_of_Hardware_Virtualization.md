---
title: "Unit I, Topic 04: Types of Hardware Virtualization"
id: unit1-topic4-hw-types-main
tags:
  - unit1
  - virtualization
  - hardware-virtualization
aliases:
  - Hardware Virtualization Techniques
links:
  - "[[00_Syllabus]]"
  - "[[03_Unit_I_Topic03_Limitations_of_Virtualization]]"
  - "[[04a_Unit_I_Topic04_SubTopic_Full_Virtualization]]"
  - "[[04b_Unit_I_Topic04_SubTopic_Paravirtualization]]"
  - "[[04c_Unit_I_Topic04_SubTopic_Hardware_Assisted_Virtualization]]"
  - "[[05_Unit_I_Topic05_Types_of_Hypervisors]]"
---

# Unit I, Topic 04: Types of Hardware Virtualization

We've established that the hypervisor's job is to create virtual machines. But *how* it does this—specifically, how it presents virtual hardware to the guest OS and handles the guest's requests to the physical hardware—is what defines the type of hardware virtualization.

The core of the challenge lies in handling **privileged instructions**. These are special, sensitive commands that an operating system uses to interact directly with hardware (e.g., managing memory, handling interrupts). In a virtualized environment, a guest OS cannot be allowed to issue these instructions directly to the physical hardware, as this would break the isolation between VMs.

The method used by the hypervisor to intercept and manage these privileged instructions determines the virtualization technique.

There are three main approaches we will study in detail:

1.  **[[04a_Unit_I_Topic04_SubTopic_Full_Virtualization|Full Virtualization]]**: The "unmodified guest" approach. The hypervisor does all the hard work to trick the guest OS into thinking it has its own hardware.
2.  **[[04b_Unit_I_Topic04_SubTopic_Paravirtualization|Paravirtualization]]**: The "cooperative guest" approach. The guest OS is modified to be aware of the hypervisor and actively collaborates with it.
3.  **[[04c_Unit_I_Topic04_SubTopic_Hardware_Assisted_Virtualization|Hardware-Assisted Virtualization]]**: The "CPU-supported" approach. The physical CPU itself provides features to make virtualization more efficient and secure. This is the modern standard.

> [!note] A Note on "Partial Virtualization"
> Your syllabus mentions **partial virtualization**. This is an older, less common term today. It typically described systems where only *some* of the hardware was virtualized (e.g., address spaces), but not all of it. The guest OS was aware it was in a virtual environment but still expected to see some real hardware. For modern practical and exam purposes, this concept has been largely superseded by and absorbed into the three main types listed above, especially Hardware-Assisted Virtualization. We will focus our study on the three primary, current techniques.

---

