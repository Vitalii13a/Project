
Packer is an open source tool for creating identical machine images for multiple platforms from a single source configuration. Packer is lightweight, runs on every major operating system, and is highly performant, creating machine images for multiple platforms in parallel.

#### Install Packer on Ubuntu Workstation
- curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
- sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
- sudo apt-get update && sudo apt-get install packer
- sudo cp /usr/bin/packer /usr/local/bin/packer

#### https://github.com/btkrausen/hashicorp/tree/master/packer
#### https://learn.hashicorp.com/tutorials/packer/get-started-install-cli 

    build           build image(s) from template
    console         creates a console for testing variable interpolation
    fix             fixes templates from old versions of packer
    fmt             Rewrites HCL2 config files to canonical format
    hcl2_upgrade    transform a JSON template into an HCL2 configuration
    init            Install missing plugins or upgrade plugins
    inspect         see components of a template
    validate        check that a template is valid
    version         Prints the Packer version



#### Installing Packer - Linux 
- sudo yum install -y yum-utils
- sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
- sudo yum -y install packer 

#### Validate the Packer Install
- which packer
- /usr/local/bin/packer
- packer version
- Packer v1.7.2 

#### Enable autocompletion for Packer CLI
- packer -autocomplete-install

### Create a Source Block
Source blocks define what kind of virtualization to use for the image, how to launch the image and how to connect to the image. Sources can be used across multiple builds. We will use the amazon-ebs source configuration to launch a t2.micro AMI in the us-west-2 region.

##### The Packer AWS builder supports the ability to create an AMI in multiple AWS regions. AMIs are specific to regions so this will ensure that the same image is available in all regions within a single cloud.

### Write Packer template
A Packer template is a configuration file that defines the image you want to build and how to build it. Packer templates use the Hashicorp Configuration Language (HCL). or Json format 


### Provisioners
Provisioners use builtin and third-party software to install and configure the machine image after booting. Provisioners prepare the system for use, so common use cases for provisioners include:

installing packages
patching the kernel
creating users
downloading application code
See the provisioner block documentation to learn more about working with provisioners. For information on an individual provisioner, choose it from the sidebar.
### The manifest post-processor 
writes a JSON file with a list of all of the artifacts packer produces during a run. If your Packer template includes multiple builds, this helps you keep track of which output artifacts (files, AMI IDs, docker containers, etc.) correspond to each build.

The manifest post-processor is invoked each time a build completes and updates data in the manifest file. Builds are identified by name and type, and include their build time, artifact ID, and file list.

If packer is run with the -force flag the manifest file will be truncated automatically during each packer run. Otherwise, subsequent builds will be added to the file. You can use the timestamps to see which is the latest artifact.

You can specify manifest more than once and write each build to its own file, or write all builds to the same file. For simple builds manifest only needs to be specified once (see below) but you can also chain it together with other post-processors such as Docker and Artifice.



    
