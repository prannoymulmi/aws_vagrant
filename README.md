# Developer setup
This project is to help provision a system which will have a uniform development environment amongst all the developers.

## Getting Started
Currently this setup is meant to simplify setting up a developer's environment in case you have a mixed setup (win/linux/osx).

### Prerequisites
* Go through the [vagrant_requirements](vagrant-run/README.md)
* Install Vagrant 
* Install Oracle Virtual Box

### Running the Project 
Follow the steps below to run your local development environment.

#### Create A config.yaml file for yourself
``` diff
- Please create a config file in vagrant-setup folder a config.yaml following the example below, if not already created. 
```
In vargrant-setup folder create a config.yaml file please fill in the the source and the destitation file of the repos that you
want to sync from your local machine to the VM. This config lets us separate the vagrantfile with personal configurations. An example 
```
configs:
  prannoy:
     project_destination_path: /repo
     project_source_path: "C://projects\\"
  use: prannoy

```

#### Install Vagrant and Oracle VM

1. Install Vagrant and a VM Provider (e.g. Virtual Box)
https://www.vagrantup.com/downloads.html (be sure to disable Hyper-V on Windows //https://ugetfix.com/ask/how-to-disable-hyper-v-in-windows-10/ and enable  VT-Technology //http://www.smartpctricks.com/2013/05/solved-how-enable-virtualization-intel-vt-x-in-bios-lenovo-idea-pad-s400-laptop.html)

2. Checkout this project, navigate into the project folder. Create ssh/config under "aws_vagrant\vagrant-setup"  and copy your privatekey under "ssh/id_rsa" for github (or copy from host if you already have one).

3. Navigate into "vagrant-run\vagrant-setup" then run ```vagrant up``` and afterwards ```vagrant ssh```

#### Run the aws-configure.sh
This must be done in the running vagrant machine. Check the Vagrant  [Vagrant Doc](vagrant-run/README.md) how to start vagrant.


After a successful login one can call the AWS API, given that the person has the corresponding access to the resources.


### What we need & what we automated:
* Terraform
* Docker


## Git
It is better if the line feeds are in linux so that there are no stupid problems.

```
git config --global core.autocrlf input
git config --global core.eol lf
```

```
#Adds know_hosts for SSH fingerprints
ssh -T git@github.com
```

### Useful Commands
```
# Updates the Virtual box If you are using a Windows machine
vagrant box update

 
# Reload and provision new changes to vagrant machine without destroying the current machine
vagrant reload --provision
```
