Ansible Playbook EPICS IOC
=========================

[![BSD License](https://img.shields.io/github/license/lerwys/ansible-playbook-epics-ioc.svg?style=flat)](LICENSE)

This Ansible playbook is an example on how to use the lerwys.epics_ioc role.

## Requirements

- ansible >= 2.10

## Instructions

Install Ansible:

```bash
pip3 install --user ansible
```

Install role:

```bash
ansible-galaxy install -r lerwys.epics_ioc
```

### Optional. Install a VM to test the role

Install Vagrant and VirtualBox:

Debian 9/10:

```bash
apt install vagrant virtualbox
```

Fedora 28/29/30/31/32/33:

```bash
dnf -y install @development-tools
dnf -y install kernel-headers kernel-devel dkms elfutils-libelf-devel qt5-qtx11extras
cat <<EOF | sudo tee /etc/yum.repos.d/virtualbox.repo
[virtualbox]
[virtualbox]
name=Fedora $releasever - $basearch - VirtualBox
baseurl=http://download.virtualbox.org/virtualbox/rpm/fedora/$releasever/$basearch
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://www.virtualbox.org/download/oracle_vbox.asc
EOF
dnf update
dnf install VirtualBox-6.1
usermod -a -G vboxusers $USER
```

Bring up Debian 9 VM:

```bash
vagrant up debian.stretch
```

Setup SSH key with Ansible:

```bash
ansible-playbook -i hosts -u vagrant setup.yml
```

## Run playbook

If running against the Debian VM created above:

```bash
ansible-playbook -i hosts -l debian.stretch -u vagrant playbook.yml
```

Otherwise, use the following template:

```bash
ansible-playbook -i <hostname or IP>, -u <user_name> playbook.yml
```

## License

BSD 2-clause
