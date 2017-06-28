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
$ ansible-playbook -i inventory/vms.inventory realtime.yml
```

This playbook runs against the `openaircn` host group in the inventory.

There is a possibility this playbook will fail at the stage where it goes to validate that the real-time kernel was successfully installed. This is due to a work-around for rebooting the machine. If that happens there will probably an ssh error -- you can safely retry the playbook, or manually verify and move onto the next step.

Then run the openair-cn, to build & configure openair-cn

```
$ ansible-playbook -i inventory/vms.inventory openair-cn.yml
```

### eNodeB (eNB) Host

We'll install a kernel preparing for GTP. 

```
$ ansible-playbook -i inventory/vms.inventory kernel-411.yaml
```

This playbook runs against the `enb` host group in the inventory.

Now we'll run a playbook for the enb host...

```
ansible-playbook -i inventory/vms.inventory enb.yaml
```

This will also run the `./run_spgw` application.

