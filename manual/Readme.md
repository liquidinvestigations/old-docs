# Liquid Investigations software distribution
The _Liquid Investigations_ distribution is a collection of software tools
tailored to support collaborative journalism. It provides several apps: file
upload and sharing, search, annotations, chat, and wiki.

The distribution runs on a Linux server, called a _node_, which can be a
regular PC, an ARM board (e.g. Odroid C2), or a cloud server / VPS. You can
create a user account for each collaborator and they can connect to your node
over a local network or the Internet.


## Setting up a Liquid node

### Odroid C2
The liquid distribution runs on the [Odroid C2][] microboard. There are
up-to-date system images available: [liquid-odroid_c2-arm64-raw.img.xz][].

#### Recommended hardware
* Odroid C2 board
* Plastic case for Odroid C2
* Power adapter for Odroid C2
* MicroSD card, 16GB or more, preferrably UHS-I U3 speed
* Compatible WiFi adapter (see [list of wifi adapters][])
* Ethernet CAT5 or CAT6 cable
* Personal computer with Ethernet port (or USB-to-Ethernet adapter) and
  supported web browser (Firefox, Chrome, Safari)


#### Installation instructions
1. Download the latest image: [liquid-odroid_c2-arm64-raw.img.xz][].
2. Burn the image to an SD card using [etcher][] or, if you prefer, `dd`.
3. Plug the SD card into the Odroid C2 and power it up. Optionally, plug an
   HDMI display into the Odroid, to see the boot messages.
4. Wait for 1 minute, then plug in the Ethernet cable into the Odroid and into
   your computer. Disconnect from any other networks including WiFi. Avoid
   connecting the Odroid to the network of an existing router as it will
   interfere with its operations.
5. Open a web browser and go to http://liquid.example.org. Choose a domain name
   for your node, and a password for the initial user account. After submitting
   the form, it should display a success message, with a link to the newly
   chosen domain name. Don't click on it just yet.
6. Wait for 2 minues for the system to configure itself, then click on the
   link. Log in with your newly created account. Enjoy your new liquid node.

[Odroid C2]: http://www.hardkernel.com/main/products/prdt_info.php?g_code=G145457216438
[liquid-odroid_c2-arm64-raw.img.xz]: https://jenkins.liquiddemo.org/job/setup-arm64/job/master/lastSuccessfulBuild/artifact/liquid-odroid_c2-arm64-raw.img.xz
[list of wifi adapters]: WiFi-Adapters.md
[etcher]: https://etcher.io


### Ubuntu cloud images for x86_64
The project builds cloud VM images, which are derived from ubuntu cloud images,
version 16.04, suitable for booting with qemu:
[liquid-cloud-x86_64-raw.img.gz][]. Take a look at the
[web-ui-deployment-scripts][] repo, it contains scripts for running the image.

[liquid-cloud-x86_64-raw.img.gz]: https://jenkins.liquiddemo.org/job/liquidinvestigations/job/setup/job/master/lastSuccessfulBuild/artifact/liquid-cloud-x86_64-raw.img.gz
[web-ui-deployment-scripts]: https://github.com/liquidinvestigations/web-ui-deployment-scripts

## Configuration
Log in with the initial user account, or another administrator account, and
click on the "admin" button, in the top right corner of the page. From the
admin site, you can change the following:

* *WAN* – the node's connection to the Internet. By default, the Ethernet port
  should be plugged into a router, and it will obtain configuration via DHCP
  from the router. You can specify a static configuration if needed. With a 2nd
  [WiFi adapter][], you can configure the node to connect to an existing WiFi
  network, instead of plugging in the Ethernet port.

* *LAN* – hotspot configuration. You can set the hotspot's network name and
  password. You can also change what IP addresses are given to clients.

* *User accounts* – create and change user accounts. It's not possible to
  delete accounts, but you can deactivate them.

* *Applications* – enable or disable applications bundled in the distribution.

* *SSH access* – configure SSH server, install user login keys.

[WiFi adapter]: WiFi-Adapters.md


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
