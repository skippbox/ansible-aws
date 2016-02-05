Ansible playbook to install a development Kubernetes (k8s) cluster on ec2
=========================================================================

Basic recipes using the ansible cloudstack module to create ssh keys, sec group etc and deploy [Kubernetes](http://kubernetes.io) on [CoreOS](http://coreos.com).
This setup is to be used for development purposes only, as there are no HA features in place.

Prerequisites
-------------

You will need Ansible >= 2.0, sshpubkeys and boto 

    $ sudo apt-get install -y python-pip
    $ pip install ansible sshpubkeys boto

Setup ec2
---------

Specify your ec2 credentials with:

    $ export AWS_ACCESS_KEY_ID='AK123'
    $ export AWS_SECRET_ACCESS_KEY='abc123'

We need to use the http POST method to pass the userdata to the coreOS instances.

Create a Kubernetes cluster
---------------------------

    $ ansible-playbook k8s-ec2.yml

Some variables can be edited in the `k8s-ec2.yml` file.
This will start a Kubernetes master node and a number of compute nodes.

Test your cluster
-----------------

First spawn a tunnel to your master node with:

    $ ssh -nNT -L 8080:127.0.0.1:8080 -i ~/.ssh/id_rsa_k8s core@<master-node-ip>

Check the tasks and templates in `roles/k8s`



