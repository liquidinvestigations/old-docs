# Liquid Investigations software distribution


## Setting up a Liquid node

### Hardware requirements
The distribution works on any machine that supports Ubuntu 16.04 "Xenial", with
a minimum of 2GB of memory and 16GB of storage, and either `x86_64` or `ARM64`
processor. We provide ready-made system images for the Odroid C2, or
alternatively, you can run the installer from an existing Ubuntu Xenial system,
e.g. on a PC server or cloud VPS.

Minimal Odroid C2 shopping list:
* Odroid C2 with case and power adapter
* MicroSD card, minimum 16GB, speed class 10/UHC-1
* Compatible WiFi adapter (e.g. Asus USB-N14)

### Installing from a bootable image
Go to http://jenkins.liquiddemo.org/ and download the file
`liquid-odroid_c2-arm64-raw.img.xz`. Then write the image to an SD card, plug
it into an Odroid C2, and plug it in. Wait 2 minutes for the system to boot. If
there is a compatible WiFi adapter plugged in, the node will create a hotspot
named `Liquid-xxxx` (ending with a random word), and the password is
`investigations`.

### Installing on existing system
This advanced mode of installation assumes you have a running Ubuntu Xenial
machine. You need shell access, and it should have a working Internet
connection.

1. Clone the [setup repository](https://github.com/liquidinvestigations/setup):

    ```shell
    sudo git clone https://github.com/liquidinvestigations/setup /opt/setup
    ```

2. Run the installer:

    ```shell
    sudo /opt/setup/bin/install
    ```
