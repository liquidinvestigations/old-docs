# Testing Discovery for Liquid Investigations


## About the VMs

The zeroconf and DNS test harness uses Vagrant to create a suitable testing
environment, consisting of multiple machines in a single, private network.

The
[Vagrantfile](https://github.com/liquidinvestigations/setup/blob/master/test/zeroconf/Vagrantfile)
provisions three VMs, named "one", "two" and "three", starting from an x64
Ubuntu 16.04 image.

The Liquid Investigations software gets installed on each one of those VMs.
The only differences between these machines are:

- ip address on the shared network
- `liquid_domain` configuration string given to the [ansible
  scripts](https://github.com/liquidinvestigations/setup/tree/avahi-daemon).
  Also, it's being set in `/etc/hosts` to `127.0.0.1` and in `/etc/hostname` by
  the provisioning script in the Vagrantfile. Thus, the `liquid_domain`
  configuration also sets the machine hostname.
- `.local` address used to publish the service, because using non-`.local`
  domains with zeroconf is unstable and largely undocumented. This address is
  chosen automatically by `avahi-daemon`, being derived from the hostname.


## Provisioning multiple Vagrant VMs with the Liquid Investigations software

When using [Vagrant in multi-machine mode](link), the VMs are started and
provisioned one at a time, starting from a Vagrant `.box` pre-loaded with the
Liquid Investigations software hosted at [our
website](liquidinvestigations.org/images).


## Network architecture for testing

_Note_: When implementing the tests, the host machine used Vagrant 1.9.5 and
VirtualBox 5.1.12.

On each node, we set the following:
- ip address
- `liquid_domain`

The topology of the network is described in the following diagram, along with
the configuration values for the thigs listed above:

![network architecture diagram](testing-diagram.png)

The test harness connects to each VM through `vagrant ssh one`, `vagrant ssh
two` and so on. It tries to connect to the JSON endpoint at the current
hostname and to the DNS server that is running on the VM itself. The expected
value sets for node "one" are displayed below.

The current testing configuration only connects nodes through a single
interface. At the time of writing, connecting nodes through multiple interfaces
is not supported.


### Testing the `/nodes` endpoint on each node

    Running as the `vagrant` user, on VM "one", through ssh:

        GET http://localhost:13777/nodes

    Response:

    ```json
    {
      "eth0": {
        "li-vagrant-box-one-example._liquid._tcp.local.": {
          "address": "10.0.0.20",
          "discovered_at": "2017-07-24T11:52:37.454125",
          "hostname": "vagrant-box-one.example",
          "is_local": true
        },
        "li-vagrant-box-two-example._liquid._tcp.local.": {
          "address": "10.0.0.27",
          "discovered_at": "2017-07-24T11:52:37.413575",
          "hostname": "vagrant-box-two.example",
          "is_local": false
        }
        "li-vagrant-box-three-example._liquid._tcp.local.": {
          "address": "10.0.0.23",
          "discovered_at": "2017-07-24T11:52:37.429687",
          "hostname": "vagrant-box-three.example",
          "is_local": false
        }
      }
    }
    ```


### Testing the DNS server on each node

The DNS server on all nodes must have the following records:

    vagrant-box-one.example    A   10.0.0.20
    vagrant-box-two.example    A   10.0.0.27
    vagrant-box-three.example  A   10.0.0.23
