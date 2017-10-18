# Liquid Investigations software distribution
The Liquid Investigations distribution is a collection of software tools,
bundled together and preconfigured, to support collaborative investigation
work. It provides several apps: file upload and sharing, search in uploaded
files, annotations, chat, and a shared wiki.

The distribution runs on a Linux server, called a _node_, which can be a
regular PC, an ARM board (e.g. Odroid C2), or a cloud server / VPS. The node
has a user database which is shared across the bundled apps.


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


## Working with documents
With Liquid Investigations, you can upload documents, search them with the
[Hoover][] search engine, and make annotations using [Hypothesis][]. All users
in the system will be able to see each other's uploaded documents and
annotations.

[Hoover]: https://hoover.github.io
[Hypothesis]: https://hypothes.is

### Upload and sharing - Davros
Go to the file upload application, by opening the home page, and clicking on
_Davros_. Upload files by drag and drop. Click on files and folders to browse
and download.

Any files uploaded will be automatically indexed by Hoover. It may take up to
30 seconds for Hoover to notice the new files.

### Search - Hoover
Go to the homepage and click on _Hoover_. Files uploaded in _Davros_ show up in
the named "Davros-Sync" collection. Enter a search query to find matching
documents.

### Annotations - Hypothesis
After finding a document in _Hoover_, you can select text, and click on the
button that appears next to the selection. Alternatively, click the
_Hypothesis_ sidebar on the right side of the page, to see all annotations.


## Collaboration tools
Working in a team requires communication and coordination. The Liquid
distribution comes with a chat app – _Matrix_ – and a wiki – _DokuWiki_. Users
can share notes and exchange messages in a private and secure environment.

### Chat – matrix.org
Go to the homepage and click on _Matrix_. Log in with your credentials on the
liquid node. Here you can create and join chat rooms, and start private
conversations.

### Wiki - DokuWiki
Go to the homepage and click on _DokuWiki_. Log in with your credentials on the
liquid node. Go to _sitemap_ (upper right) to see a list of all wiki pages. See
DokuWiki's manual for details on creating pages and the wiki syntax.
