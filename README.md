# nimbus-test-vm-centos8-stream-empty

This repository contains pre-installed CentOS 8 Stream virtual machine image (OVA) that can be used as a base for installation of OPERA NIMBUS Testing Environment.

# Reconstruct (virtualbox) OVA image from multiple file:

```
cat CentOS8-Stream-For-NIMBUS.ova.part_aa CentOS8-Stream-For-NIMBUS.ova.part_ab CentOS8-Stream-For-NIMBUS.ova.part_ac > CentOS8-Stream-For-NIMBUS.ova
```

# Splitting (virtualbox) OVA image from multiple file:

```
split -b 2GB CentOS8-Stream-For-NIMBUS.ova CentOS8-Stream-For-NIMBUS.ova.part_
```

