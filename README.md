## oai-ansible

Experimental Ansible playbooks for OpenAirInterface

## using the playbooks.

Assumes a CentOS 7 host (physical or virtual) with minimal or cloud iso install.


### OpenAir-CN Host

Generally there are two steps:

* Install the realtime kernel, with `./realtime.yml`
* Build, configure & run openair-cn, with `./openair-cn.yml`

---

Modify the `./inventory/vms.inventory` (or create your own) and install the real-time kernel using this playbook:

```
ansible-playbook -i inventory/vms.inventory realtime.yml
```

There is a possibility this playbook will fail at the stage where it goes to validate that the real-time kernel was successfully installed. This is due to a work-around for rebooting the machine. If that happens there will probably an ssh error -- you can safely retry the playbook, or manually verify and move onto the next step.

Then run the openair-cn, to build & configure openair-cn

```
ansible-playbook -i inventory/vms.inventory openair-cn.yml
```

### eNodeB (eNB) Host




