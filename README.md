## oai-ansible

Experimental Ansible playbooks for OpenAirInterface

## using the playbooks.

Assumes two CentOS 7 hosts (physical or virtual) with minimal or cloud iso install.


## OpenAir-CN Host

Generally there are two steps:

* Install the GTP kernel, with `./kernel-gtp.yml`
* Build, configure & run openair-cn, with `./openair-cn.yml`

---

Modify the `./inventory/vms.inventory` (or create your own) and install the GTP kernel using this playbook:

```
$ ansible-playbook -i inventory/vms.inventory kernel-gtp.yaml
```

This playbook runs against the `openaircn` host group in the inventory.

There is a possibility this playbook will fail at the stage where it goes to validate that the GTP kernel was successfully installed. This is due to a work-around for rebooting the machine. If that happens there will probably an ssh error -- you can safely retry the playbook, or manually verify and move onto the next step.

Then run the openair-cn, to build & configure openair-cn

```
$ ansible-playbook -i inventory/vms.inventory openair-cn.yml
```


## Installing the OAI sim -- *work in progress*

We'll install a real-time kernel.

```
$ ansible-playbook -i inventory/vms.inventory realtime.yaml
```

This playbook runs against the `sim` host group in the inventory.

Then run the oaisim, to build & configure oaisim

```
ansible-playbook -i inventory/vms.inventory oaisim.yaml 
```

(This playbook is unfinished)
