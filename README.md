# Install Azure CLI

Ansible role to install the Azure version of Ansible. Intended for use by Packer using the standard local Ansible provisioner.

Includes a default dynamic inventory file.

Requires separate credential file or managed instance.

See the labs on <https://azurecitadel.com/automation/packeransible>.

## Installation

Manual installation

`sudo ansible-galaxy install --roles-path /etc/ansible/roles git+https://github.com/richeney/ansible-role-azure-ansible`
`sudo mv /etc/ansible/roles/ansible-role-azure-ansible /etc/ansible/roles/azure_ansible`

Or add an entry to requirements.yml and refer to that:

```yaml
---
- src: https://github.com/richeney/ansible-role-azure-ansible
  name: azure_ansible
...
```

`sudo ansible-galaxy install --roles-path /etc/ansible/roles --role-file requirements.yml

## Example Playbook

```yaml
- hosts: all
  roles:
    - azure_ansible
```

## Requirements

None.

## Dependencies

None.
