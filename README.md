# nimbus-test-vm-centos8-stream-empty

This repository contains pre-installed CentOS 8 Stream virtual machine image (OVA) that can be used as a base for installation of OPERA NIMBUS Testing Environment.

# Reconstruct (virtualbox) OVA image from multiple file:

```
cat CentOS8-Stream-For-NIMBUS.ova.part_aa CentOS8-Stream-For-NIMBUS.ova.part_ab CentOS8-Stream-For-NIMBUS.ova.part_ac > CentOS8-Stream-For-NIMBUS.ova
```

# IMPORTING VM image into VIRTUALBOX

Install VirtualBox when needed.

Make you sure that you install "virtualbox quest-additions" and "virtualbox extension-packs"
into your VirtualBox installation for smooth integration of mouse+keyboard and copy-and-paste.

You can import this VM-image **(CentOS8-Stream-For-NIMBUS.ova)** into your VirtualBox.

You can choose how much memory and how many CPU’s will your virtual machine have.

8 GB RAM, 4x CPU’s could be reasonable to start with.

After the import if the *.ova image into VirtualBox you can boot this virtual machine (VM).

Login into graphical window manager as *devtest* (#1). 
You can become *root* (#2). Use given credentials.
You have multiple desktops. 
In one desktop open a terminal and become root user (su). You need this for executing docker commands.
In the second desktop open firefox. 

Once the NIMBUS-Baltrad installation into Docker is finished you can use the [Baltrad WEB-gui](https://localhost:8443/BaltradDex).

In the Window Manager you have multiple desktops at your disposal. 
The 2nd desktop you can have Firefox with some handy bookmarks such as:

- http://git.baltrad.eu/ 
- https://localhost:8443/BaltradDex/routes.htm 
- https://localhost:8443/BaltradDex/messages_live.htm

You will probably open multiple instances (tabs) with gnome-terminal. 
You will need several terminals with root user for certain docker operations.

In Virtualbox you can store the current VM state into VM-snapshots.
You can switch between the snapshots as you wish during your tests.

### Activate network inside of the CentOS8 VM

Make sure that you **activate the (wired) network connection inside** of your brand new CentOS8 desktop VM.
You can do it after login into Window Manager and clicking on the speaker (or on/off) icons on the top menu-bar. You go to Wired Off and click *"Connect"*. 
Preferably you want to make sure that the wired network connection will be activated at every reboot of the CentOS8 VM.

```
[root@NimbusTestNode ]# 
# See which ifcfg-* nework connection configuration(s) you have and use it.
ls -al /etc/sysconfig/network-scripts/ifcfg-*
# -rw-r--r--. 1 root root 281 Mar 12  2021 /etc/sysconfig/network-scripts/ifcfg-enp0s3

# Now change ONBOOT=no  ==> ONBOOT=yes
sed -i -e 's/ONBOOT=.*/ONBOOT=yes/' /etc/sysconfig/network-scripts/ifcfg-enp0s3
grep ONBOOT /etc/sysconfig/network-scripts/ifcfg-enp0s3
# Activare wired network connection
ifup enp0s3  
```

Now you can go a internet browser and check you can access internet.
In the provided CentOS8 image there is Firefox running on the 2nd desktop.
Just reload the current page: http://git.baltrad.eu/

Reboot the VM and login again to see if the wired connection is restored.

Login into the Window Manager and pre-set gnome-terminal(s) and Firefox browser as you wish.
Consider to store the working VM state as snapshot in VirtualBox.

Name the VM snapshot something like this: **"Snapshot 1 - CentOS8 + docker: NIMBUS-ready to install"**



# NOTE: Splitting (virtualbox) OVA image from multiple file:

```
split -b 2GB CentOS8-Stream-For-NIMBUS.ova CentOS8-Stream-For-NIMBUS.ova.part_
```

