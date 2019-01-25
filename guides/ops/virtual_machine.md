# Managing Mac OS Virtual Machines

- Virtual Machines (VM) are managed with [VMWare Fusion](https://www.vmware.com/ca/products/fusion.html).
- Virtual Machines (VM) are kept on an external hard drive.
- A clean snapshot of the Mac OS version is always maintained for the VM. e.g. `Clean 10.13.3`
- You SHOULD check if there are updates to the OS when starting the VM. If so update the OS and then save a new snapshot e.g. `Clean 10.13.6`. Remove the old snapshot afterwards, e.g. `Clean 10.13.3`
- NEVER do a major upgrade in the same VM, always create a new VM. That way we can access previous major versions. e.g. `10.3.x`, `10.4.x`.
- After you have finished with the VM, you MUST restore to a clean state, e.g. `Clean 10.13.3`, a courtesy to the next developers.
