## oai-ansible

Experimental Ansible playbooks for OpenAirInterface

## using the playbooks.

Assumes a CentOS 7 host with minimal or cloud iso install.

Modify the `./inventory/vms.inventory` (or create your own) and install the real-time kernel using this playbook:

```
ansible-playbook -i inventory/vms.inventory realtime.yml
```


