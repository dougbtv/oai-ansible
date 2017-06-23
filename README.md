## oai-ansible

Experimental Ansible playbooks for OpenAirInterface

## using the playbooks.

Assumes a CentOS 7 host with minimal or cloud iso install.

Modify the `./inventory/vms.inventory` (or create your own) and install the real-time kernel using this playbook:

```
ansible-playbook -i inventory/vms.inventory realtime.yml
```

Then run the openair-cn, to build & configure openair-cn

```
ansible-playbook -i inventory/vms.inventory openair-cn.yml
```

"enode b"

oai sim: simulator emulates user device, base station & radio link (between those two)



