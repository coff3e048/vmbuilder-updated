
*This repo is a continuation of francismunch's easy cloud VM script to include modern versions of distributions (while also omitting outdated versions). The majority of the script code is his making.*

# Proxmox Virtual Machine Builder with Cloud Images

You can have a virtual machine created and booted with the information you set within two minutes. Auto downloads the cloud image if you need it and once all the information is set it auto starts it for you.

This script can be used for beginners that don't know much about Proxmox yet or it can be used by advanced users to get a bunch of different VM's running in no time.  (Pro tip give it your ansible key when asked for keys and then run your playbook after creation)



# How To Run the script
  
  It is recommended to use `curl` and keep it in whatever home folder you use for easier updating. Moving into */usr/sbin* is also an option
  
  ```curl 'https://raw.githubusercontent.com/pascal48/vmbuilder-updated/main/vmbuilder.sh' >> vmbuilder && chmod +x vmbuilder```



# Features
 If you are in a cluster environment you are able to pick the Proxmox node to have it on (by the way of qm migrate)
 It will download the image for you if you don't have it
 It builds a user.yaml file and adds it as a snippet - so you can customize a lot of the cloud image VM when creating it (See Proxmox Wiki about snippets to learn more)
 It checks what storage is availabe on your Proxmox node and you are able to pick what you want to use
 It checks what snippet storage is availabe on your Proxmox node and you are able to pick what you want to use
 You can customize:
   - Hostname
   - ID number (It checks ID's in the entire cluster and also provides next number if you don't use custom numbers)
   - Username
   - Password
   - Add a SSH key file (example id_rsa.pub)
   - Asks if you want to enable SSH password authentication (Keys are safer)
   - Select storage you want to run the Virtual Machine on
   - Select the storage location of your ISO files
   - Select the storage and location of your snippet files (for user.yaml)
   - Check if you want to use DHCP or enter Static IP
   - If you want to enter a VLAN number
   - If you want to resize the cloud image storage so you can have more space
   - It lets you set the number of cores and memory for the Virtual Machine
   - Asks if you want it to install qemu-guest-agent (see Proxmox's wiki for more infomation) - Great to have out of the box from the Admin side of Proxmox
   - Added the option to start after creation or not to start
   - Asks what Proxmox node to have the VM running after all is complete
   - Makes it simple to learn some of the CLI of proxmox (by reviewing the script) and some awesome built in featues of Proxmox to get things up and running fast and easily
 
 # Cloud Images supported
   - Ubuntu Hirsute 21.04
   - Ubuntu Focal 20.04
   - Ubuntu 20.04 Minimal
   - CentOS 7
   - CentOS 8
   - AlmaLinux 8
   - Debian 10
   - Debian 11
   - Ubuntu Bionic 18.04
   - Fedora 34
   - Fedora 35

# Changelog

 Added 12/02/2021
 - Changed machine type to q35
 - Changed CPU type from generic "kvm64" to "host"
 - Disks are now added in virtio instead of scsi
 - Fedora 35 added
 - CentOS 8 switched out for AlmaLinux 8
 - Added a thing that tells the user they can use a root account
 
# Future script ideas
  
    - Add an option to use IPV6 or IPV4
    - Alpine Linux
    - FreeBSD Support
    - Fedora Cloud Image works, but doesn't transfer all user.yaml (like host name) snippet info yet...but works with username/password/sshkeys
    - CentOS 8 Cloud Image works, but doesn't transfer all user.yaml (like host name) snippet info yet...but works with username/password/sshkeys 
