# Hypervisor-Enforced Kernel Integrity (Heki)

Heki is a proof-of-concept that implements new KVM features (extended page tracking, MBEC support, CR pinning) and defines a new API to protect guest VMs.

On common operating systems, one powerful way to bypass security policies is to exploit the kernel. Linux kernel vulnerabilities are common and exploited. Among other things, kernel self-protection mechanisms include control-register pinning and memory page protection restrictions that help harden systems. Unfortunately, none is bullet proof because they are implemented at the same level as the vulnerabilities they try to protect against. To get a more effective defense, we propose to move (or copy) some of these protection mechanisms out of the kernel thanks to virtualization. Our implementation is based on the Kernel-based Virtual Machine (KVM) hypervisor and designed to be merged with the mainline project. It is inspired from other private implementations currently in use (e.g. Windows's Virtual Secure Mode), but our approach is tailored to Linux specificities.

[Patched Linux source tree](https://github.com/heki-linux/linux/commits/heki-v1)

[LKML patches](https://lore.kernel.org/all/20230505152046.6575-1-mic@digikod.net/)

[Linux Security Summit North America 2023 talk](https://sched.co/1K7bR)
