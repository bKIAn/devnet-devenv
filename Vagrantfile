Vagrant.configure("2") do |config|
# Installing Ubuntu 18.04
  config.vm.box = "ubuntu/bionic64"
  config.vm.provider "virtualbox" do |vb|
    vb.name = "DevNet-Development"
    vb.memory = "2048"
    vb.cpus = 1
  end
  config.vm.provision "shell", privileged: false, inline: <<-SHELL
    #
    # Initialisation
    export DEBIAN_FRONTEND=noninteractive
    sudo apt-get update
    sudo apt-get upgrade
    sudo apt-get autoremove
    #
    # Step 0: Install XFCE and VirtualBox tools
    sudo apt-get install --yes xfce4 virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11
    sudo VBoxClient --clipboard
    sudo VBoxClient --draganddrop
    sudo VBoxClient --display
    sudo VBoxClient --checkhostversion
    sudo VBoxClient --seamless
    sudo sed -i 's/allowed_users=.*$/allowed_users=anybody/' /etc/X11/Xwrapper.config
    #
    # Step 1: Install basic Development tools
    sudo apt-get install --yes curl libssl-dev build-essential
    mkdir ~/DevNet
    cd ~/DevNet
    #
    # Steps 2 & 3: Install Git and verify
    sudo apt-get install --yes git
    git --version
    git clone https://github.com/CiscoDevNet/hello_network
    ~/DevNet/hello_network/hello_network.sh
    #
    # Step 4: Install Python and Node.js
    sudo apt-get install --yes python3 python3-venv python3-pip
    python3 --version
    python3 -m venv py3-venv
    source ~/DevNet/py3-venv/bin/activate
    python --version
    pip install ansible==2.9.2 requests flask pyotp==2.3.0 pysqlite3==0.4.1 PyYAML
    pip freeze
    deactivate
    sudo apt-get install --yes nodejs npm
    nodejs -v
    #
    # Step 5: Install IDE
    sudo apt-get install --yes snapd
    sudo snap install atom --classic
    sudo snap install code --classic
    code --install-extension tht13.python
    #
    # Step 6: Other Development Tools
    sudo snap install postman
    sudo snap install ngrok
    sudo wget --quiet https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
    sudo apt-get install --yes ./google-chrome-stable_current_amd64.deb
    sudo apt-get install --yes --fix-broken
    sudo apt-get install --yes openconnect
    #
    # Step 7: Application Container Engine (Docker)
    sudo apt-get install --yes apt-transport-https ca-certificates software-properties-common
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    sudo apt-get update
    sudo apt-get install --yes docker-ce
    sudo systemctl status docker
    sudo usermod -aG docker $USER
    newgrp docker
    #
    # Finalise
    docker run busybox
    docker ps --all
    sudo apt-get autoremove
    echo "===== Verification Summary ====="
    echo -n "* 01. Git Install:        "; git --version;
    echo -n "* 02. Git - Sample:       "; ~/DevNet/hello_network/hello_network.sh;
    echo -n "* 03. Python3 Install:    "; python3 --version;
    echo -n "* 04. Python Virtual Env: "; source ~/DevNet/py3-venv/bin/activate; python --version;
    echo -n "* 05. Python Pip Install: "; pip --version; deactivate;
    echo -n "* 06. Node.js Install:    "; nodejs --version;
    echo    "* 07. Atom Install:       "; echo "Verify yourself in GUI!";
    echo -n "* 08. VS Code Install:    "; code --version;
    echo -n "* 09. VS Code - Python:   "; code --install-extension tht13.python;
    echo    "* 10. Postman Install:    "; echo "Verify yourself in GUI!";
    echo -n "* 11. ngrok Install:      "; ngrok --version;
    echo -n "* 12. Chrome Install:     "; google-chrome --version;
    echo -n "* 13. OpenConnect Install:"; openconnect --version;
    echo -n "* 14. Docker Install:     "; docker --version;
    echo -n "* 15. Docker - Sample:    "; docker ps --format "{{.ID}}: {{.Image}} ({{.Names}})" --all;
    echo "===== Finish Verification! ====="
    echo "===== VM Ready to Start!!! ====="
    echo ""
    sudo shutdown -P now
    SHELL
  end
# Running Command:
#   $ vagrant up > Vagrantfile_`date "+%Y%m%d-%H%M"`.out
# Summary of Vagrant commands (https://www.drupal.org/node/2008794):
#   $ vagrant up: Start virtual machine.
#   $ vagrant halt: Halt virtual machine.
#   $ vagrant reload: Reload the virtual machine.
#   $ vagrant destroy: Destroy your virtual machine.
#   $ vagrant ssh: SSH into virtual machine.
