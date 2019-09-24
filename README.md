# Install Azure CLI

Ansible role to install the Azure version of Ansible. Intended for use by Packer using the standard local Ansible provisioner, so that the image may be deployed to a new subscription and used as a config management host.

Includes a default dynamic inventory file. Does not clobber existing files.

Note that this role is currently configured for managed instance, and adds `export ANSIBLE_AZURE_AUTH_SOURCE=msi` to the .profile and .bashrc files in /etc/skel.  Ensure that the resulting VM image is deployed with managed instance access to the subscription.

As used by the labs on <https://azurecitadel.com/automation/packeransible>.

## Installation

Manual installation

```bash
sudo ansible-galaxy install --roles-path /etc/ansible/roles git+https://github.com/richeney/ansible-role-azure-ansible
sudo mv /etc/ansible/roles/ansible-role-azure-ansible /etc/ansible/roles/azure_ansible
```

Or add an entry to requirements.yml and refer to that:

```yaml
---
- src: https://github.com/richeney/ansible-role-azure-ansible
  name: azure_ansible
...
```

`sudo ansible-galaxy install --roles-path /etc/ansible/roles --role-file requirements.yml`

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
