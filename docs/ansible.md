# Ansible Reference

## Ansible Basics

Ansible is an IaC (Infrastructure as Code) tool that allows for the automated provisioning 
and management of servers. A computer running the Ansible program is considered the Ansible control Host. The Control Host can push commands from a YAML config file to any number of slave" servers to accomplish certain actions (installation, configuration, execution, etc.). Server to server communication is done via SSH and any slave servers do NOT need Ansible installed in order to receive and process commands from the Control Host.

## Setup for SSH

- make sure OpenSSH Server is installed on all of your servers
- manually access each server to add fingerprint to known hosts
- generate an SSH key on each server using `ssh-keygen -t ed25519 -C "Ansible connect"`
- to copy SSH public key to Control Host `ssh-copy-id -i ~/.ssh/<filename>.pub 123.123.123.123`
- d

A few details:

- in the above, we specify ed25519 because it provides a high security level while also producing a shorter key length ([more info](https://goteleport.com/blog/comparing-ssh-keys/))
- for additional security, we can set a passphrase that will be required any time the key is used (but it is optional)

## Ansible Installation

On Debain/Ubuntu systems, the installation follows the typical pattern:

```
# update distribution index
sudo apt update
# install ansible with auto-confirm
sudo apt install -y ansible
```

## Ansible Configuration

**Inventory** files are used to define the domains or IP addresses of all the servers you want to manage.  For detailed info on inventories, check out the [Ansible inventory docs](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html).

An example of an inventory file in YAML format:

```
all:
  hosts:
    123.123.123.123
  children:
    group1:
      hosts:
        111.111.111.111
        222.222.222.222
```



Ansible config files ending in **.cfg** can be created in a directory to define default data for all commands. This can be useful since many repetitive options can be omitted from your commands if the default values have been set in the config. Local configs take precedence over the global config found in `/etc/ansible/ansible.cfg`.

An example Ansible config:

```
[defaults]
inventory = inventory
private_key_file = ~/.ssh/ansible
```

##  

## Resources

[Learn Linux TV - Ansible playlist](https://www.youtube.com/playlist?list=PLT98CRl2KxKEUHie1m24-wkyHpEsa4Y70)
