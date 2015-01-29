Ansible Recipes to Install Kubernetes
=====================================

Basic recipes using the ansible cloudstack module to create ssh keys, sec group etc and deploy [Kubernetes](http://kubernetes.io) on [CoreOS](http://coreos.com).

Very early work...

Clone recursive
---------------

    $ git clone --recursive https://github.com/runseb/ansible-kubernetes.git

There is a submodule in there.


Create etcd cluster
-------------------

    $ ansible-playbook etcd.yml

Dependencies
------------

This depends on the Ansible cloudstack [module](https://github.com/resmo/ansible-cloudstack). It is loaded in this repo as a git submodule.
This module depends on [cs](https://github.com/exoscale/cs), this module will look for the CLOUDSTACK_ENDPOINT, CLOUDSTACK_KEY, CLOUDSTACK_SECRET and CLOUDSTACK_METHOD environment variables.

