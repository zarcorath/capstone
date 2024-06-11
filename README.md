# capstone

## Ansible host requirements
pip install -r requirements.txt
ansible-galaxy install -r requirements.yml

## Cluster node requirements
- Ubuntu 22.04
- Static IP addresses in same subnet
- External DNS server

## Inventory
Development inventory file: inventory.yml
*Production* change inventory to Netbox API call

## Primary Playbook
build_environment.yml
ansible-playbook build_environment.yml -i inventory.yml -kK

## Variables
The primary playbook incorporates all variables defined in global_vars.yml
Role defaults are not used in favor of global_vars.yml