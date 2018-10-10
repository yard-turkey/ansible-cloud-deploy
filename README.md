## Run

```
ansible-playbook -i inventories/aws playbooks/cluster-up.yaml 
```

## Parameters

To edit values relative to AWS instances, see playbooks/host_vars/ec2-deploy.yaml

At the very least, set the `tag_name` value to something other than the current value. 

## Configuration
#### Make ssh key accessible to ansible
  - $ eval ssh-agent && ssh-add ~/.ssh/<key>
#### Setup AWS keys
  - (https://docs.ansible.com/ansible/2.6/scenario_guides/guide_aws.html#authentication)
  - $ export AWS_ACCESS_KEY_ID='AK123'
	- $ export AWS_SECRET_ACCESS_KEY='abc123'
#### Config env for ec2.py (dynamic inventory)
  - https://aws.amazon.com/blogs/apn/getting-started-with-ansible-and-dynamic-amazon-ec2-inventory-management/

#### Dynamic Inventory Groups
   - https://docs.ansible.com/ansible/2.6/user_guide/intro_dynamic_inventory.html#static-groups-of-dynamic-groups
   
#### Test ec2.py
   - $ ansible -u ec2-user -m ping tag_Name_jcope_demo
