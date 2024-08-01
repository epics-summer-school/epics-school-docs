---
layout: page
title: Virtual Machine
subtitle: How to use the VM
---



   ## Introduction to Using VirtualBox

   VirtualBox is a powerful, open-source virtualization tool that allows you to run multiple operating systems simultaneously on your computer. This is particularly useful for testing, development, or running software that is only available on specific operating systems. In this guide, we will walk you through the steps to install VirtualBox, and how to upload and run a virtual machine using an `.ova` file.

   The `.ova` file used in this guide was built on VirtualBox version `6.1.50_Ubuntu r161033` on Ubuntu 22.04. The virtual machine requires at least 40GB of disk space and at least 4GB of RAM.

   ### Installing VirtualBox

   1. **Download VirtualBox**:
      - Visit the [VirtualBox official website](https://www.virtualbox.org/).
      - Click on the "Download VirtualBox" button.
      - Select the appropriate version for your operating system (Windows, macOS, Linux, or Solaris).

   2. **Install VirtualBox**:
      - **Windows**:
      - Double-click the downloaded `.exe` file.
      - Follow the on-screen instructions to complete the installation.
      - You may need to grant administrative privileges and confirm the installation of device software.
      - **macOS**:
      - Open the downloaded `.dmg` file.
      - Double-click the VirtualBox.pkg file to run the installer.
      - Follow the prompts to complete the installation. You may need to grant permission to install the software in your System Preferences.
      - **Linux**:
      - The installation process varies slightly depending on your Linux distribution. For Debian-based systems like Ubuntu, you can use the following commands:
         ```bash
         sudo apt update
         sudo apt install virtualbox
         ```
      - For other distributions, refer to the VirtualBox Linux downloads page for specific instructions.

   ### Running VirtualBox

   Once VirtualBox is installed, you can start it from your applications menu.

   ### Uploading and Running a Virtual Machine Using an `.ova` File

   An `.ova` file is an Open Virtualization Format Archive, which is a package that contains a virtual machine. The `.ova` file in this guide was built on VirtualBox version `6.1.50_Ubuntu r161033` on Ubuntu 22.04.

   1. **Launch VirtualBox**:
      - Open VirtualBox from your applications menu or desktop shortcut.

   2. **Import the `.ova` File**:
      - In the VirtualBox Manager, go to `File` > `Import Appliance`.
      - Click on the `Choose` button and navigate to the location of your `.ova` file.
      - Select the `.ova` file and click `Next`.

   3. **Review and Adjust Settings**:
      - VirtualBox will display the configuration details of the virtual machine. Review these settings and make any necessary adjustments.
      - Ensure that the virtual machine is allocated at least 40GB of disk space and at least 4GB of RAM.
      - Click `Import` to start the process. This may take a few minutes depending on the size of the `.ova` file and the speed of your computer.

   4. **Start the Virtual Machine**:
      - Once the import process is complete, the virtual machine will appear in the list of available VMs in the VirtualBox Manager.
      - Select the virtual machine and click `Start` to launch it.

   ### Basic Usage Tips

   - **Snapshots**: Use snapshots to save the state of your virtual machine at a particular point in time. This is useful for testing and development purposes.
   - **Shared Folders**: Configure shared folders to easily transfer files between your host machine and the virtual machine.
   - **Network Settings**: Adjust network settings based on your requirements, such as using NAT or bridged networking for different networking scenarios.
      