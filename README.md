COA (Certified OpenStack Administrator) Cheat Sheet
===================================================

This repository is a note for anyone who want to take COA (Certified OpenStack Administrator).

### Cheat Sheet

## Keystone
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
