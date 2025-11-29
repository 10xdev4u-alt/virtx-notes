---
title: "Unit I: Types of Hardware Virtualization"
id: unit1-hw-types
tags: [virtualization, hardware-virtualization, full-virtualization, paravirtualization, hardware-assisted-virtualization, unit1]
aliases: [Hardware Virtualization Types, Full Virtualization, Paravirtualization, Hardware-Assisted Virtualization]
links: ["[[00_Syllabus]]", "[[01_Unit_I_Intro_and_Cloud]]", "[[02_Unit_I_Need_for_Virtualization]]", "[[03_Unit_I_Limitations_of_Virtualization]]"]
---

# Unit I: Types of Hardware Virtualization

## 1.4 Types of Hardware Virtualization

Hardware virtualization is the technique of virtualizing the underlying hardware of a computer. The way the hypervisor interacts with the hardware and the guest OS defines its type. There are three main approaches.

1.  **Full Virtualization**
    *   **Concept:** The hypervisor completely emulates or simulates the underlying hardware. The guest operating system runs on top of this emulated hardware without any modification—it does not know it is being virtualized.
    *   **How it works:** When the guest OS tries to execute a privileged instruction (an instruction that needs direct access to hardware), the hypervisor traps the instruction, translates it into a safe instruction for the host hardware, executes it, and returns the result to the guest. This trap-and-emulate process makes it compatible with any OS but introduces performance overhead.
    *   **Analogy:** A language translator who listens to a foreign speaker (Guest OS), translates every single sentence into the local language for the listener (Host Hardware), and then translates the listener's response back to the foreign speaker. It's accurate but can be slow.
    *   **Examples:** Early versions of VMware, Microsoft Virtual PC, QEMU.

2.  **Paravirtualization (PV)**
    *   **Concept:** The hypervisor does *not* try to emulate hardware. Instead, it presents an API to the guest operating system. The guest OS is **modified** to be aware of the hypervisor and makes special calls (hypercalls) to it for hardware access.
    *   **How it works:** By modifying the guest OS kernel, the need for trap-and-emulate is eliminated. The guest OS cooperates with the hypervisor, leading to much higher performance because there is no translation overhead. The downside is the need to modify the OS, which isn't always possible (e.g., with proprietary OS like Windows).
    *   **Analogy:** Two people who agree to speak a simplified, common language (the hypervisor API) to communicate, rather than relying on a translator. It's much faster and more efficient.
    *   **Examples:** Xen (in its classic mode).

3.  **Hardware-Assisted Virtualization (Partial Virtualization is an older, less relevant term)**
    *   **Concept:** This is the modern standard. CPU manufacturers (Intel and AMD) built special extensions directly into the processor hardware to support virtualization (Intel VT-x and AMD-V).
    *   **How it works:** The CPU itself provides new operating modes. The hypervisor runs in a high-privilege "root mode," while guest operating systems run in a lower-privilege "non-root mode." Privileged instructions from the guest OS are automatically trapped by the CPU hardware and redirected to the hypervisor, without the software-based overhead of traditional full virtualization. This gives the "run anything" compatibility of full virtualization with performance that is very close to paravirtualization.
    *   **Analogy:** A modern smartphone with a dedicated chip for processing photos. Instead of the main CPU doing all the work with software, the specialized hardware handles it much more efficiently.
    *   **Examples:** Modern VMware ESXi, Microsoft Hyper-V, KVM.

> [!note]
> The term **Partial Virtualization** is often used to describe systems where only *some* of the underlying hardware is virtualized, and the guest OS is aware that it's in a virtual environment but still expects to see some real hardware. This is largely a historical or academic term now, as modern systems have converged on Hardware-Assisted Virtualization, which combines the best of Full and Paravirtualization.

**Summary Table:**

| Feature            | Full Virtualization           | Paravirtualization             | Hardware-Assisted Virtualization |
|--------------------|-------------------------------|--------------------------------|----------------------------------|
| **Guest OS Mod?**  | No                            | Yes                            | No                               |
| **Performance**    | Lower (due to overhead)       | High                           | High (near-native)               |
| **Compatibility**  | Very High (any OS)            | Low (only modified OSes)       | Very High (any OS)               |
| **Key Technique**  | Binary Translation / Trap-and-Emulate | Hypercalls (API)          | CPU Extensions (Intel VT-x, AMD-V) |
| **Primary Use**    | Legacy Systems                | Niche / Early Hypervisors      | **The Modern Standard**            |

---
