# Cisco DevNet Development Environment (devnet-devenv)
Vagrant file to deploy a local development environment for Cisco DevNet, based on Ubuntu 18.04 LTS (Bionic Beaver) on VirtualBox provider.

## Provisioned Tools
1. Ubuntu 18.04 LTS (Bionic Beaver)
1. XFCE 4
1. VirtualBox Guest Tools
1. Basic Development Tools and Git
1. Snap and Docker
1. Python3, Python3 Virtual Environment (python3-venv), and Pip (python3-pip)
1. Node.js and npm
1. Atom and Visual Studio Code (Python for VSCode activated)
1. Postman and ngork
1. OpenConnect (for Cisco AnyConnect)
1. Google Chrome
1. and finally, a checklist of installed applications.

## Test Environment
Tested and verified on:
1. (X)Ubuntu 18.04.4 LTS (Bionic Beaver)
1. VirtualBox 5.2.34_Ubuntur133883
1. Vagrant 2.0.2

## Installation
1) Install dependencies:
* [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
* [Vagrant](https://www.vagrantup.com/downloads.html)
* [Git](https://git-scm.com/downloads)
2) Clone this project:
```
$ git clone https://github.com/bKIAn/devnet-devenv/
$ cd devnet-devenv
```
3) Run Vagrant and enjoy: Run Vagrant and grab a coffee. Then login to `DevNet-Development`. In another word:
```
$ vagrant up > Vagrantfile_`date "+%Y%m%d-%H%M"`.out
Open Virtualbox
Run the VM named as DevNet-Development
Login with username and password (both of them are "vagrant")
$ startx
```

## Toubleshooting
Whenever you run the ``vagrant up > Vagrantfile_`date "+%Y%m%d-%H%M"`.out`` command, the output of IaC procedure will be saved in a file with a naming similar to `Vagrantfile_20200719-1910.out`. This file is the output file of the IaC (Infrastructure as Code) procedure. In case of any issues, open that file with a text editor. Reach to the end of the file and you will find verifications starting with `===== Verification Summary =====`. This summary helps you to identify which installation step failed. I apprecaite to notify me and I'll try to help you.

## Contributing
1. Fork it
1. Create your feature branch (`$ git checkout -b my-new-feature`)
1. Commit your changes (`$ git commit -am 'Add some feature'`)
1. Push to the branch (`$ git push origin my-new-feature`)
1. Create new Pull Request
