# LOCAL COOKBOOK DEVELOPMENT BADGE TOPICS
_A study guide to help prepare for the Chef Local Cookbook Development Badge, derived from the Linux Academy Local Cookbook Development course. ost of the information found on this page is taken from docs.chef.io._

The Local Cookbook Development badge is awarded when someone proves that they understand the process of developing cookbooks locally. 
This guide gives **an understanding of setting up the local environment.

# Installing the ChefDk
### Download all the tools for ChefDK: 
- curl -s https://omnitruck.chef.io/install.sh | sudo bash -s -- -P chefdk
### Set up environment
#### Configure the bash profile to initialize the bash shell with chef to ensure default ruby interpreter is the chef interpreter 
- echo 'eval "$(chef shell-init bash)"' >> ~/.bash_profile
- source ~/.bash_profile
- sudo yum install vim
### Ensure chef binary is installed in /opt/chefdk/bin/chef
- which chef 
### Ensure chef default ruby environment is set in opt/chefdk/embedded/bin/ruby
- which ruby

# Configure the Workstation
### Install Git and Yum utils
- sudo yum install -y git yum-utils
### Configure git
- git config --global user.name "Chad Lei"
- git config --global user.email "cblei@uci.edu"
- git config --global core.editor vim
### Install docker (add docker repository and install packages)
#### Use yum config manager to add repository for download.docker.com with repository info for centos to get repository in place in order to install packages
- sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo  
- sudo yum makecache fast
- sudo yum -y install docker-ce
### Enable and start the service
- sudo systemctl enable docker
- sudo systemctl start docker
### Add docker to a specific group so that user can interact with it
- sudo usermod -aG docker $USER
### Disable services to ensure no issues
- sudo systemctl stop getty@tty1.service
- sudo systemctl mask getty@tty1.service
### Logout and login in order to complete the configuration
- logout
### Create a network within docker
- docker network create --subnet=10.1.1.0/24 test
### Install the gem for kitchen docker so test kitchen has the driver available
- gem install kitchen-docker




