# Azure SONiC DC Topology
Exploring the use of Ansible script to build a SONiC DC topology, demonstrated in this [blog post](https://plvision.eu/blog/sdn/sonic-network-os-configuration)
Whilst there are Ansible collections aimed at configuring SONiC devices, this example uses a telnet connection.

Ideally, we'd boot strap the devices. Making them accessible to a management network, allowing the use of [dellemc.enterprise_sonic](https://galaxy.ansible.com/dellemc/enterprise_sonic).
Utilising the collections greatly simplifies the deployment. `dellemc.enterprise_sonic` wasn't avaliable in 2020, when the deployment script was created.

## Requirements

### PIP Packages
  * [ansible](https://pypi.org/project/ansible/)
  * [gns3fy](https://pypi.org/project/gns3fy/)


### Ansible Collections
  * [ansible.netcommon](https://galaxy.ansible.com/ui/repo/published/ansible/netcommon/docs/)
  * [ansible.utils](https://galaxy.ansible.com/ui/repo/published/ansible/utils/docs/)
  * [davidban77.gns3](https://galaxy.ansible.com/ui/repo/published/davidban77/gns3/docs/)

These can be installed by running the following commands
```
python3 -m pip install -r requirements.txt
ansible-galaxy install -r requirements.yml
sed -i -e 's/#!\/usr\/bin\/env python/#!\/usr\/bin\/python/g' ~/.ansible/collections/ansible_collections/davidban77/gns3/plugins/modules/*.py

```

## Deploying
### Template(s)
Before the topology can be deployed, GNS3 needs to have the SONiC template imported.
`ansible-playbook setup-sonic-gns3-template.yml`

### DC Topology
Deploying the topology is as simple as running this command
`ansible-playbook deploy-sonic-dc-topology.yml`
