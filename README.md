# capstone

## Ansible host requirements
* pip install -r requirements.txt
* ansible-galaxy install -r requirements.yml

## Cluster node requirements
* Ubuntu 22.04
* Static IP addresses in same subnet
* External DNS server

## Inventory
* Development inventory file: inventory.yml
* *Production* change inventory to Netbox API call

## Primary Playbook
* build_environment.yml
* ansible-playbook build_environment.yml -i inventory.yml -kK

## Variables
* The primary playbook incorporates all variables defined in global_vars.yml
* Role defaults are not used in favor of global_vars.yml

## Add new users
### Create a new YAML file from the following template and apply to the cluster
```
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: developers
  namespace: applicationone
subjects:
- kind: User
  name: myname # add user's name here
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role
  name: dev-writer # this must match the name of the Role
  apiGroup: rbac.authorization.k8s.io
```