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

### Configuration
To change the default hotspot name/password, domain name, admin credentials,
and to configure applications, go to the node's home page. By default this
is http://fresh.liquid.local. Be sure to connect to the node's hotspot before
accessing the home page. Log in using the default credentials (username
`liquid`, password `investigations`) and click on `[admin]`.

From the admin site, you can change the following:

* *Domain name* – this determines the URLs of the liquid node's websites. It
  should either be a subdomain of your organization (so, if the organization is
  `example.com`, it can be `colombo.liquid.example.com`) or a private name
  (e.g. `colombo.liquid.local`).

* *WAN* – the node's connection to the Internet. By default, the Ethernet port
  should be plugged into a router, and it will obtain configuration via DHCP
  from the router. You can specify a static configuration if needed. With a 2nd
  WiFi adapter, you can configure the node to connect to an existing WiFi
  network, instead of plugging in the Ethernet port.

* *LAN* – hotspot configuration. You can set the hotspot's network name and
  password. You can also change what IP addresses are given to clients.

* *User accounts* – create and change user accounts. It's not possible to
  delete accounts, but you can deactivate them.

* *Applications* – enable or disable applications bundled in the distribution.
