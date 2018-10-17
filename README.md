## Configure

To edit values relative to AWS instances, see playbooks/host_vars/ec2-deploy.yaml

## Ansible master configuration

Do the following configuration steps on whichever machine is running the playbook.

#### Make ssh key accessible to ansible

  - $ eval ssh-agent && ssh-add ~/.ssh/<key>

#### Setup AWS keys
  - (https://docs.ansible.com/ansible/2.6/scenario_guides/guide_aws.html#authentication)
  - $ export AWS_ACCESS_KEY_ID='AK123'
  - $ export AWS_SECRET_ACCESS_KEY='abc123'

### Config env for ec2.py (dynamic inventory)

	NOTE: Dynamic inventories are not used for now, so this step is optional.

  - https://aws.amazon.com/blogs/apn/getting-started-with-ansible-and-dynamic-amazon-ec2-inventory-management/

#### Dynamic Inventory Groups
	
	NOTE: Dynamic inventories are not used for now, so this step is optional.

   - https://docs.ansible.com/ansible/2.6/user_guide/intro_dynamic_inventory.html#static-groups-of-dynamic-groups
   
#### Test ec2.py

   - $ ansible -u ec2-user -m ping tag_Name_your_tag_name


## Run

### Start Instances
To deploy 3 aws ec2 instances:

```
ansible-playbook playbooks/cluster-up.yaml -e "tag_name=<some name>"
```

Optionally, to change the number of instances, set the `num_nodes` var:

```
ansible-playbook playbooks/cluster-up.yaml -e "tag_name=<some name> num_nodes=42"
```


### Destroy Instances

To tear down all clusters with the same `Name:` tag:

```
ansible-playbook playbooks/cluster-down.yaml -e "tag_name=<some name>"
```

