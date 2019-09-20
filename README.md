# Install Azure CLI

Ansible role to install the Azure version of Ansible. Intended for use by Packer using the standard local Ansible provisioner.

Includes a default dynamic inventory file.

Requires separate credential file or managed instance.

See the labs on <https://azurecitadel.com/automation/packeransible>.

## Installation

`ansible-galaxy install richeney.azure-ansible`

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
