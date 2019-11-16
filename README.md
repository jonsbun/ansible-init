# Prepare Server(s) for Ansible (ansible-init)

Everyone of us have situation when new servers come in place. If these servers management are based on IT automation tool Ansible, SSH connectivity is required. In the most cases SSH keys are what we really need and Ansible expects the same. However, Ansible does not cares how to help us achieve this first step.

If you are looking for the fast and reliable way how to copy your Ansible master server public SSH key to the newly deployed server(s), you came to the right place. This simple ansible-init playbook just takes <i>id_rsa.pub</i> SSH public key from default location and distribute it to the new server(s) based on described inventory information.

## Preparation

If you want to use ansible-init playbook, inventory file with the following format is required:
```
server1-hostname ansible_user='server1-user' ansible_password='server1-password'
<...>
server15-hostname ansible_user='server15-user' ansible_password='server15-password'
```
<b>Note:</b> inventory file can keep one or more servers default connection information.

## Usage

For playbook execution need to use the following command:
```
ansible-playbook -i inventory ansible-init.yml
```

After successful playbook execution you are ready to include new server(s) into main inventory file because authentication from now goes via SSH key.
