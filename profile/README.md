# Linux Virtualization Based Security (LVBS)

On common operating systems, one powerful way to bypass security policies is to exploit the kernel. Linux kernel vulnerabilities are common and exploited. Among other things, kernel self-protection mechanisms include control-register pinning and memory page protection restrictions that help harden systems. Unfortunately, none is bullet proof because they are implemented at the same level as the vulnerabilities they try to protect against. To get a more effective defense, we propose to move (or copy) some of these protection mechanisms out of the kernel thanks to virtualization.

Linux Virtualization Based Security (LVBS) is an umbrella term under which we can offer various hypervisor backed kernel protection solutions.
This is a common hypervisor agnostic extendable architecture in Linux kernel that can be used by any hypervisor to implement and extend Linux kernel protections.
Different hypervisor frameworks (Hyper-V as an example of type-1 hypervisor and KVM as an example of type-2 hypervisor) can plug into the common layer to harden the Linux kernel.

## Hypervisor-Enforced Kernel Integrity (Heki)

Heki is a proof-of-concept that implements new KVM features (extended page tracking, MBEC support, CR pinning) and defines a new API to protect guest VMs.
It is designed to be merged with the mainline project. It is inspired from other private implementations currently in use (e.g. Windows's Virtual Secure Mode), but our approach is tailored to Linux specificities.

### RFC v2

[Patched Linux source tree](https://github.com/heki-linux/linux/commits/heki-v2)

[LKML patches](https://lore.kernel.org/all/20231113022326.24388-1-mic@digikod.net/)

#### [Linux Plumbers Conference 2023 talk](https://lpc.events/event/17/contributions/1486/)

* [Slides](talks/2023-11-14%20LPC%20-%20Heki.pdf)
* [Demo CR-pinning](talks/2023-11-14%20demo%20Heki%20cr-pinning.webm)
* [Demo noexec](talks/2023-11-14%20demo%20Heki%20noexec.webm)
* [Demo kernel module](talks/2023-11-14%20demo%20Heki%20kernel%20module.webm)

### RFC v1

#### [Linux Security Summit North America 2023 talk](https://sched.co/1K7bR)

* [Slides](talks/2023-05-11%20LSS%20-%20Heki.pdf)
* [Demo noexec](talks/2023-05-11%20demo%20Heki%20noexec.webm)
* [Demo CR-pinning](talks/2023-05-11%20demo%20Heki%20cr-pinning.webm)

## LVBS Hyper-V

The LVBS Hyper-V implementation leverages the existing Hyper-V's VTL mechanism.
Our implementation includes the guest kernel changes (VTL0) and the secure kernel (VTL1).

[Patched Linux source tree for VTL0 (guest)](https://github.com/heki-linux/lvbs-linux/tree/ubuntu-lvbs)

[Patched Linux source tree for VTL1 (secure kernel)](https://github.com/heki-linux/lvbs-linux/tree/secure-kernel-lvbs)

### [Linux Plumbers Conference 2023 talk](https://lpc.events/event/17/contributions/1515/)

* [Slides](talks/2023-11-15%20LPC%20-%20LVBS.pdf)
