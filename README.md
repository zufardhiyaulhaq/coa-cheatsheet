COA (Certified OpenStack Administrator) Cheat Sheet
===================================================

This repository is a note for anyone who want to take COA (Certified OpenStack Administrator).

## Cheat Sheet

### Keystone
- Create User **johnnyc-cli**
```
openstack user create --domain default --project trade --description "Developer" --email johnnyc@example.com --password openstack johnnyc-cli
```

- Add User **johnnyc-cli** to Project **trade** with role **member**
```
openstack role add --user johnnyc-cli --project trade _member_
```

- Add **acme-corp** Domain
``` 
openstack domain create acme-corp
```

- Add user **edgarp** to domain **acme-corp**
```
openstack user create --domain acme-corp edgarp --password openstack
```

- Add Project **development** to domain **acme-corp**
```
openstack project create --domain acme-corp development
```

- Add group **interns** to domain **acme-corp**
```
openstack group create --domain acme-corp interns
```

- Add user **edgarp** into group
```
openstack group add user --group-domain acme-corp interns edgarp
```

- Add group **interns** into project **development**
```
openstack role add --project-domain acme-corp --project development --group interns _member_
```

- Add new Service with **database** type
```
openstack service create --name trove --description "OpenStack Trove" database
```

- Create Endpoint for **database** type with region
```
openstack endpoint create --region RegionOne database public http://192.168.56.56:8779/v1.0/
openstack endpoint create --region RegionOne database internal http://192.168.56.56:8779/v1.0/
openstack endpoint create --region RegionOne database admin http://192.168.56.56:8779/v1.0/
```

- Modify Quota

List all project
```
openstack project list
```
Set Quota base on project ID
```
Openstack quota set --instances 20 eb1a2580ea87490bbe206162ecf2fde5
```

### Glance
- Create image **cirros-cli** 
```
openstack image create --file cirros-0.3.5-x86_64-disk.img --disk-format qcow2 --min-disk 1 --min-ram 512 --property description='Cirros Cloud Image for COA Exam Prep' cirros-cli
```

- Download image **cirros-cli**
```
openstack image save --file /tmp/mydownloadedimage.img cirros-cli
```

- Share **cirros-cli** with **marketing** project
```
openstack image add project cirros-cli 99a06694e4444e038d632aca0cc1a89e
```
**99a06694e4444e038d632aca0cc1a89e** is marketing project ID.

### Nova
- Create Flavor **awesome-flavor-cli**
```
openstack flavor create --id 200 --vcpus 1 --ram 512 --disk 1 "awesome-flavor-cli"
```

- Launch instance **instance3-cli**
```
openstack server create --image cirros --flavor m1.tiny --key-name my-new-keypair-cli instance3-cli
```

- Create snapshot from **instance3-cli**
```
openstack server image create --name instance3-cli-snapshot instance3-cli
```
**Note** : Shutdown instance first!

- Start/Stop/Suspend/Resume Instance **instance3-cli**
```
nova stop instance3-cli
nova start instance3-cli
nova suspend instance3-cli
nova resume instance3-cli
```


