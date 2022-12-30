# ipxe-flatcar-k3s

This public repo is an experiment for the minimum viable iPXE, as well as the butane and  ignition configs to bootstrap a bare metal machine 

Hostnames are hardcoded as has my public key - don't use it unless you'd like to give me access to your flatcar linux nodes.

## Using

The process is as follows:

1)a usb boot iso of IPXE is run on the bare metal server.
2) using IPXE console, load the ipxe config from this repo (/ipxe/kube1.ipxe)
3)the ipxe boot kicks off an in-memory install of flatcar with an initial ignition config from the repo: (https://github.com/gmcnaught/ipxe-flatcar-k3s/blob/main/ignition/kube1/pxe.ign)
4)the in-memory install of flatcar runs install-flatcar to persist the OS to disk, and writes the /opt/ignition.json , sourcing from (https://github.com/gmcnaught/ipxe-flatcar-k3s/blob/main/ignition/kube1/boot.ign)


All of this is based on prior work from:
Installing Flatcar from IPXE:
 https://www.flatcar.org/docs/latest/installing/bare-metal/booting-with-ipxe/#booting-ipxe
Automating K3 cluster installation on flatcar linux:
https://thenewstack.io/automate-k3s-cluster-installation-on-flatcar-container-linux/
