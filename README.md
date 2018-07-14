[![Build Status](https://travis-ci.org/OlegGorj/ansible-on-docker.svg?branch=master)](https://travis-ci.org/OlegGorj/ansible-on-docker)
[![GitHub Issues](https://img.shields.io/github/issues/OlegGorJ/ansible-on-docker.svg)](https://github.com/OlegGorJ/ansible-on-docker/issues)
[![Average time to resolve an issue](http://isitmaintained.com/badge/resolution/OlegGorJ/ansible-on-docker.svg)](http://isitmaintained.com/project/OlegGorJ/ansible-on-docker "Average time to resolve an issue")
[![Percentage of issues still open](http://isitmaintained.com/badge/open/OlegGorJ/ansible-on-docker.svg)](http://isitmaintained.com/project/OlegGorJ/ansible-on-docker "Percentage of issues still open")
[![](https://images.microbadger.com/badges/image/oleggorj/ansible.svg)](https://microbadger.com/images/oleggorj/ansible "Get your own image badge on microbadger.com")
[![](https://images.microbadger.com/badges/version/oleggorj/ansible.svg)](https://microbadger.com/images/oleggorj/ansible "Get your own version badge on microbadger.com")
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2FOlegGorj%2Fansible-on-docker.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2FOlegGorj%2Fansible-on-docker?ref=badge_shield)

# Docker image of Ansible

Docker base image of Ansible configuration management server.

This repository contains Dockerized Ansible, published to the public Docker Hub via automated build mechanism.

## Summary

Repository name in Docker Hub: **[OlegGorJ/ansible](https://hub.docker.com/r/OlegGorJ/ansible/)**

This repository contains Dockerized [Ansible](https://github.com/ansible/ansible), published to the public [Docker Hub](https://hub.docker.com/) via **automated build** mechanism.



## Configuration

These are Docker images for [Ansible](https://github.com/ansible/ansible) software, installed in a selected Linux distributions.

### Base OS

Alpine (3).

### Ansible

Version provided:

  1. provides the most recent *stable* version of Ansible based on Alpine3; suitable for most people. This image is very light - less then 70Ms in total.


## Quick example to use it

  1. make sure you can access base image from Docker Hub `OlegGorJ/ansible:latest`.

  2. put the following `Dockerfile` along with your playbook directory:

  ```
  FROM OlegGorJ/ansible:latest

  # ==> Specify requirements filename;  default = "requirements.yml"
  #ENV REQUIREMENTS  requirements.yml

  # ==> Specify playbook filename;      default = "playbook.yml"
  #ENV PLAYBOOK      playbook.yml

  # ==> Specify inventory filename;     default = "/etc/ansible/hosts"
  #ENV INVENTORY     inventory.ini

  # ==> Executing Ansible (with a simple wrapper)...
  RUN your-ansible-playbook-wrapper

  ```

  3. well, run `docker build .`

---

## Usage

Used mostly as a *base image* for configuring other software stack on some specified Linux distribution(s).

To test an Ansible `playbook.yml` against a variety of Linux distributions, we may use [Vagrant](https://www.vagrantup.com/) as follows:

```ruby
# Vagrantfile

Vagrant.configure(2) do |config|

    # ==> Choose a Vagrant box to emulate Linux distribution...
    config.vm.box = "maier/alpine-3.3.1-x86_64"


    # ==> Executing Ansible...
    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "playbook.yml"
    end

end
```

Virtual machines can emulate a variety of Linux distributions with good quality, at the cost of runtime overhead.


Docker to be a rescue. Now, with these **oleggorj/ansible** series, we may test an Ansible `playbook.yml` against a variety of Linux distributions as follows:


```dockerfile
# Dockerfile

# ==> Choose a base image to emulate Linux distribution...
FROM williamyeh/ansible:alpine3

# ==> Copying Ansible playbook...
WORKDIR /tmp
COPY  .  /tmp

# ==> Creating inventory file...
RUN echo localhost > inventory

# ==> Executing Ansible...
RUN ansible-playbook -i inventory playbook.yml \
      --connection=local --sudo
```


With Docker, we can test any Ansible playbook against any version of any Linux distribution without the help of Vagrant. More lightweight, and more portable across IaaS, PaaS, and even CaaS (Container as a Service) providers!

If better OS emulation (virtualization) isn't required, the Docker approach (containerization) should give you a more efficient Ansible experience.


---

## License
+[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2FOlegGorj%2Fansible-on-docker.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2FOlegGorj%2Fansible-on-docker?ref=badge_large)
