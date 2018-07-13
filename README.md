[![Build Status](https://travis-ci.org/OlegGorj/ansible-on-docker.svg?branch=master)](https://travis-ci.org/OlegGorj/ansible-on-docker)
[![GitHub Issues](https://img.shields.io/github/issues/OlegGorJ/ansible-on-docker.svg)](https://github.com/OlegGorJ/ansible-on-docker/issues)
[![Average time to resolve an issue](http://isitmaintained.com/badge/resolution/OlegGorJ/ansible-on-docker.svg)](http://isitmaintained.com/project/OlegGorJ/ansible-on-docker "Average time to resolve an issue")
[![Percentage of issues still open](http://isitmaintained.com/badge/open/OlegGorJ/ansible-on-docker.svg)](http://isitmaintained.com/project/OlegGorJ/ansible-on-docker "Percentage of issues still open")
[![Docker Stars](https://img.shields.io/docker/stars/OlegGorJ/ansible.svg)](https://hub.docker.com/r/OlegGorJ/ansible/)
[![Docker Pulls](https://img.shields.io/docker/pulls/OlegGorJ/ansible.svg)](https://hub.docker.com/r/OlegGorJ/ansible/)
[![ImageLayers](https://images.microbadger.com/badges/image/OlegGorJ/ansible.svg)](https://microbadger.com/#/images/OlegGorJ/ansible)
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


## Here's how to use it

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
