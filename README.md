# Install Ansible for Azure use

Ansible role to install the Azure version of Ansible. Intended for use by Packer using the standard local Ansible provisioner, so that the image may be deployed to a new subscription and used as a config management host.

Includes a default dynamic inventory file. Does not clobber existing files.

Note that this role is currently configured for managed instance, and adds `export ANSIBLE_AZURE_AUTH_SOURCE=msi` to the .profile and .bashrc files in /etc/skel.  Ensure that the resulting VM image is deployed with managed instance access to the subscription.

As used by the labs on <https://azurecitadel.com/automation/packeransible>.

## Installation

Manual installation

```bash
sudo ansible-galaxy install --roles-path /etc/ansible/roles git+https://github.com/richeney/ansible-role-ansible-azure
sudo mv /etc/ansible/roles/ansible-role-ansible -azure/etc/ansible/roles/ansible_azure
```

Or add an entry to requirements.yml and refer to that:

```yaml
---
- src: https://github.com/richeney/ansible-role-ansible-azure
  name: ansible_azure
...
```

`sudo ansible-galaxy install --roles-path /etc/ansible/roles --role-file requirements.yml`

## Example Playbook

```yaml
---
# Master playbook to test custom role to install Ansible
- hosts: all
  become: yes
  roles:
      - role: ansible_azure
  vars:
    files:
      - ansible.cfg
      - example_playbook.yml
      - inventory.azure_rm.yml
    requirements:
      - src: https://github.com/richeney/ansible-role-common
        name: common
      - src: https://github.com/richeney/ansible-role-azure-cli
        name: azure_cli
      - src: geerlingguy.pip
        name: pip
      - src: geerlingguy.docker
        name: docker
      - src: darkwizard242.terraform
        name: terraform
      - src: darkwizard242.packer
        name: packer
...
```

## Requirements

None.

## Dependencies

None.
