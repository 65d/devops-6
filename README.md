# Vagrant LVM Setup

This Vagrantfile sets up an Ubuntu 22.04 virtual machine with LVM (Logical Volume Management) configured on multiple disks. It's designed to demonstrate LVM setup and usage in a controlled environment.

## Prerequisites

- [Vagrant](https://www.vagrantup.com/downloads)
- [Oracle VB](https://www.virtualbox.org) 

## Usage

1. Clone this repository or copy the Vagrantfile to your local machine.
2. Open a terminal and navigate to the directory containing the Vagrantfile.
3. Run the following command to start the VM:

   ```
   vagrant up
   ```

4. To access the VM, use:

   ```
   vagrant ssh
   ```

5. To stop the VM, use:

   ```
   vagrant halt
   ```

6. To delete the VM, use:

   ```
   vagrant destroy
   ```

## Configuration Details

- **Base Box**: Ubuntu 22.04 (generic/ubuntu2204)
- **Provider**: VMware Desktop
- **Memory**: 1024 MB
- **CPUs**: 2
- **Additional Disks**: 4 x 500MB

## Provisioning Steps

The Vagrantfile includes a shell script that performs the following actions:

1. Updates the system and installs necessary packages (mc, vim, parted).
2. Creates GPT partitions on the additional disks (/dev/sdb, /dev/sdc, /dev/sdd, /dev/sde).
3. Sets up LVM:
   - Creates physical volumes
   - Creates a volume group named 'vg0'
   - Creates two logical volumes: 'vol0' and 'vol1' (800MB each)
4. Formats the logical volumes with ext4 filesystem.
5. Mounts the logical volumes and adds them to /etc/fstab for persistent mounting.

## Accessing LVM Volumes

After provisioning, you can access the LVM volumes at:
- /mnt/vol0
- /mnt/vol1
