# buildkernel
A tool to build a secure-boot EFI stub kernel, and save it to the EFI system partition.

> 31 Oct 2020: sadly, due to legal obligations arising from a recent change in my 'real world' job, I must announce I am **standing down as maintainer of this project with immediate effect**. For the meantime, I will leave the repo up (for historical interest, and it may be of use to others); however, I plan no further updates, nor will I be accepting / actioning further pull requests or bug reports from this point. Email requests for support will also have to be politely declined, so, **please treat this as an effective EOL notice**.<br><br>For further details, please see my post [here](https://forums.gentoo.org/viewtopic-p-8522963.html#8522963).<br><br>With sincere apologies, sakaki ><

## Description
**buildkernel** is a script that builds a Gentoo Linux EFI stub kernel which is suitable for booting from a USB key using UEFI (no additional bootloader required). It makes use of the initramfs creation tools (and early userspace **init**(8) script) provided by **genkernel**(8).

Specifically, the assumed use-case for buildkernel is where you are creating a kernel for use in a dual-factor-authenticated LVM-over-LUKS system, booting from an external USB key, with secure boot enabled (using UEFI), where you may (optionally) wish to use the **plymouth**(8) splash manager, and where the target (final) init system is **systemd**(1).

> Note: as of version 1.0.11, **OpenRC**(8) init is also supported.

To facilitate this, **buildkernel** will create a statically linked version of **gpg**(1) — one which furthermore does not require pinentry — and include this in the initramfs.

It will also automatically set the necessary kernel configuration parameters, including the command line, sign the resulting kernel if possible, then update the EFI boot list if required.

The **buildkernel** utility can be invoked in non-interactive (default) or interactive mode (see the **--ask** option, in the manpage). Non-interactive mode is suitable for use in a scripted invocation.

Certain key options can be specified via the configuration file, _/etc/buildkernel.conf_: see **buildkernel.conf**(5) for details.

Although **buildkernel** is targetted primarily at the use-case where the EFI system partition is on a removable USB key (for security), it can also be used with a system partition on a fixed drive.

## Installation

**buildkernel** is best installed (on Gentoo) via its ebuild, available as part of the **sakaki-tools** [overlay](https://github.com/sakaki-/sakaki-tools).
Full instructions are provided as part of the [**Sakaki's EFI Install Guide**](https://wiki.gentoo.org/wiki/Sakaki's_EFI_Install_Guide) tutorial, on the Gentoo wiki.

In particular, see [this section](https://wiki.gentoo.org/wiki/Sakaki's_EFI_Install_Guide/Configuring_and_Building_the_Kernel#What_the_buildkernel_Script_Does_.28Background_Reading.29) for a detailed description of what **buildkernel** does, and why.
