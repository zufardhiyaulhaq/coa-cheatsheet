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






