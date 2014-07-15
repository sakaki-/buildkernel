# buildkernel
A tool to build a secure-boot EFI stub kernel, and save it to the EFI system partition.

## Description
**buildkernel** is a script that builds a Gentoo Linux EFI stub kernel which is suitable for booting from a USB key using UEFI (no additional bootloader required). It makes use of the initramfs creation tools (and early userspace **init**(8) script) provided by **genkernel**(8).

Specifically, the assumed use-case for buildkernel is where you are creating a kernel for use in a dual-factor-authenticated LVM-over-LUKS system, booting from an external USB key, with secure boot enabled (using UEFI), where you may (optionally) wish to use the **plymouth**(8) splash manager, and where the target (final) init system is **systemd**(1).

To facilitate this, **buildkernel** will create a statically linked version of **gpg**(1) — one which furthermore does not require pinentry — and include this in the initramfs.

It will also automatically set the necessary kernel configuration parameters, including the command line, sign the resulting kernel if possible, then update the EFI boot list if required.

The **buildkernel** utility can be invoked in non-interative (default) or interactive mode (see the **--ask** option, in the manpage). Non-interactive mode is suitable for use in a scripted invocation.

Certain key options can be specified via the configuration file, _/etc/buildkernel.conf_: see **buildkernel.conf**(5) for details.

Although **buildkernel** is targetted primarily at the use-case where the EFI system partition is on a removable USB key (for security), it can also be used with a system partition on a fixed drive.

## Installation

**buildkernel** is best installed (on Gentoo) via its ebuild, available as part of the **sakaki-tools** overlay (available on GitHub).
Full instructions are provided on the [Gentoo wiki](https://wiki.gentoo.org/wiki/) (forthcoming).
