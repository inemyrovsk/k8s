Ansible Role: kubernetes_instance
=========

An Ansible Role to launch Amazon EC2 instances for configure Kubernetes Cluster. One of the instances will be Kubernetes Master node and other two will be Kubernetes Worker node.

Requirements
------------

Install Python library to generates inventory that Ansible can understand by making API request to AWS EC2 using the Boto library.  

```
pip3 install boto
```

The `inventory/ec2.py` script assumes Ansible is being executed where the environment variables needed for Boto have already been set:

```
export AWS_ACCESS_KEY_ID='AK123'
export AWS_SECRET_ACCESS_KEY='abc123'
``` 

**Note:** The AWS credentials can optionally be specified inside `inventory/ec2.ini` file Credentials specified here are ignored if the environment variables are set.

```
aws_access_key_id = AXXXXXXXXXXXXXX
aws_secret_access_key = XXXXXXXXXXXXXXXXXXX
```

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

```
aws_region: ap-south-1  
aws_ami: ami-08f63db601b82ff5f  
aws_instance_type: t2.micro  
subnet_id: subnet-00566450d0ea4c288  
security_group_id: sg-7a400518  
key: ansible-key  
name:  
  - K8S_Master  
  - K8S_Worker1  
  - K8S_Worker2  
access_key: AXXXXXXXXXXXXXX
secret_key: XXXXXXXXXXXXXXXXXXX
```

Dependencies
------------

None

Example Playbook
----------------

An example playbook to use this Role
    
```
- hosts: localhost
  roles:
    - kubernetes.instance
  tasks:
    - meta: refresh_inventory
```

License
-------

BSD

Author Information
------------------

This role is created in 2021 by Aditya Raj
