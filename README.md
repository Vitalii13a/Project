# Sample three tier app

This repo contains code for a Node.js multi-tier application.


The application overview is as follows.

```
web <=> api <=> db
```

# Exchange- app

A brief description of what this project does and who it's foAIM To create a custom AWS AMI using Packer.

Packer AMI consist of the following features: 
1. Fully patched Docker and Docker-Compose will be already Installed 
2. Git Installation Source code 
3. Node-JS application Running Docker containers with three different containers: 
    - frontend 
    - backend 
    - postgres.

Steps to Reproduce Run packer file with the following command:


- packer validate packer.json
- packer build packer.json



##### Terraform script will Provision 
- EC2
- SG
- Application LoadBalancer and other required resources.

Run terraform script

# Variables: 
##### In Packer File:
- Aws access_key,
- Secret_key,
- region,
- ami_name,
- source_ami,
- instance_type,
- ssh_username,

#### In Terraform File:

- Aws access_key
- Secret_key
- region
- key_name
- instance_type
- security_group