Ansible playbook to install a development Kubernetes (k8s) cluster
==================================================================

Basic recipes using the ansible cloudstack module to create ssh keys, sec group etc and deploy [Kubernetes](http://kubernetes.io) on [CoreOS](http://coreos.com).
This setup is to be used for development purposes only, as there are no HA features in place.

Prerequisites
-------------

You will need Ansible >= 2.0, sshpubkeys and [cs](https://github.com/exoscale/cs) :)

    $ sudo apt-get install -y python-pip
    $ sudo pip install ansible
    $ sudo pip install cs
    $ sudo pip install sshpubkeys

Setup cloudstack
----------------

Create a `~/.cloudstack.ini` file with your creds and cloudstack endpoint:

    [cloudstack]
    endpoint = https://api.exoscale.ch/compute
    key = <your api access key> 
    secret = <your api secret key> 
    method = post

We need to use the http POST method to pass the userdata to the coreOS instances.

Create a Kubernetes cluster
---------------------------

    $ ansible-playbook k8s.yml

Some variables can be edited in the `k8s.yml` file.
This will start a Kubernetes master node and a number of compute nodes.

Check the tasks and templates in `roles/k8s`




