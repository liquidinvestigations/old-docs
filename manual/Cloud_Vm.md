# Running a liquid node in a virtual machine


### Prepare the environment, download images

Download the [latest cloud image][]:

[latest cloud image]: https://jenkins.liquiddemo.org/job/liquidinvestigations/job/setup/job/master/lastSuccessfulBuild/artifact/liquid-cloud-x86_64-raw.img.gz

```shell
wget https://jenkins.liquiddemo.org/job/liquidinvestigations/job/setup/job/master/lastSuccessfulBuild/artifact/liquid-cloud-x86_64-raw.img.xz
```

Install factory:

```shell
python3 <(curl -sL https://github.com/liquidinvestigations/factory/raw/master/install.py) factory
```

Import the image into factory (unpack the disk image and create a configuration
file):

```shell
mkdir factory/images/liquid
xzcat liquid-cloud-x86_64-raw.img.xz > factory/images/liquid/disk.img
echo '{"login": {"username": "liquid", "password": "liquid"}}' > factory/images/liquid/config.json
```

### Run the VM

```shell
factory/factory login --image liquid --smp 2 --memory 2048 --tcp 8080:80
```

This will run qemu and set up a TCP port mapping – the VM's port 80 is
accessible as port 8080 on the host.

### Access the VM's web interface

To make things easier, you can map to the host's port 80, with one of these
options:
* You can change the argument to `--tcp 80:80`, but then you must run the VM as
  root.
* Set up a reverse proxy using e.g. nginx.
* Run socat as root:
  ```shell
  sudo socat TCP4-LISTEN:80,fork,bind=127.0.0.1 TCP4:127.0.0.1:8080
  ```

You must also map the domain names of the liquid node, e.g. in `/etc/hosts`:

```
127.0.0.1 liquid.example.org
127.0.0.1 hoover.liquid.example.org
127.0.0.1 hypothesis.liquid.example.org
127.0.0.1 davros.liquid.example.org
127.0.0.1 dokuwiki.liquid.example.org
127.0.0.1 matrix.liquid.example.org
```

Then, open a web browser, and go to `http://liquid.example.org`.
