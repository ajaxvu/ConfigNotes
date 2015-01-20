### Installing VMWARE on CentOS

VMWare version: **VMware Workstation 11.0.0 build-2305329**

OS version: **CentOS 6.6**

### 1. Download install package from VMWare site to local

VMware-Workstation-Full-11.0.0-2305329.x86_64.bundle

### 2. Change permisstion of install package
``chmod a+x VMware-Workstation-Full-11.0.0-2305329.x86_64.bundle ``

### 3. Run install package
if you are logged in CentOS X Windows, run:

``./VMware-Workstation-Full-11.0.0-2305329.x86_64.bundle``

If you are in console, run:

``./VMware-Workstation-Full-11.0.0-2305329.x86_64.bundle --console``

Follow the installation wizard until done.

### 4. Start VMWARE

In the console, type: ``vmware``

After running above command, you may see the message that notify you to install **gcc compiler** and some components. Just press ‘Cancel’ to continue.

Return to the terminal, then lets install “Development tools”:

``yum group install "Development tools"``

Try to start vmware again. Another issue may be be appear, its talk about **kernel-headers**. In this case, we need to install proper kernel header by typing:

``install kernel-headers-$(uname -r) ``

Reference: [http://www.tecmint.com/install-vmware-workstation-11-in-linux/](http://www.tecmint.com/install-vmware-workstation-11-in-linux/)

---
# Uninstall VMWare
``vmware-installer -u vmware-workstation``

---
# Config VMWare
By default, VMWare server listens on port *443* (service: *vmware-workstation-server*) and shared machines is at */var/lib/vmware/Shared VMs*. You can change these parameters by VMWare GUI or in config files if need...

To access and start shared VMs from, you must allow following ports:

*  VMWare server port (default 443)
* Port 902 (heartbeat UDP for serve)
