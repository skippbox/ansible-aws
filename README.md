Ansible Recipes to Install Kubernetes
=====================================

Basic recipes using the ansible cloudstack module to create ssh keys, sec group etc and deploy [Kubernetes](http://kubernetes.io) on [CoreOS](http://coreos.com).

You will need Ansible and [cs](https://github.com/exoscale/cs) :)

    $ sudo apt-get install -y python-pip
    $ sudo pip install ansible
    $ sudo pip install cs

Setup cs
--------

Create a `~/.cloudstack.ini` file with your creds and cloudstack endpoint:

    [cloudstack]
    endpoint = <your cloudstack api endpoint>
    key = <your api access key> 
    secret = <your api secret key> 
    method = post

We need to use the http POST method to pass the userdata to the coreOS instances.

Clone recursive
---------------

    $ git clone --recursive https://github.com/runseb/ansible-kubernetes.git
    $ cd ansible-kubernetes

There is the [ansible-cloudstack](https://github.com/resmo/ansible-cloudstack) submodule in there.

Create a Kubernetes cluster
---------------------------

    $ ansible-playbook k8s.yml

Some variables can be edited in the `k8s.yml` file.
This will start a Kubernetes master node and a number of compute nodes.
This is all setup via coreOS instances and passing userdata.

Check the tasks and templates in `roles/k8s`

Create etcd cluster
-------------------

That's a bonus to this work, there is a playbook to create an independent etcd cluster.

    $ ansible-playbook etcd.yml

Edit some of the variables in the `etcd.yml` file directly.

Dependencies
------------

This depends on the Ansible cloudstack [module](https://github.com/resmo/ansible-cloudstack). It is loaded in this repo as a git submodule.

This module depends on [cs](https://github.com/exoscale/cs), this module will look for the `CLOUDSTACK_ENDPOINT`, `CLOUDSTACK_KEY`, `CLOUDSTACK_SECRET` and `CLOUDSTACK_METHOD` environment variables.

