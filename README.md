ansible_connector_install
=========

This role can be used to install Actifio Connector on RedHat Linux variants. The role will ensure all the required pre-requisite packages and configurations are inplace. 

The role can be used to install individual physical hosts, and add them to the Actifio Appliance or discover the new host using VMware host discovery method.  

Requirement
===========

Would require CDS/Sky 8.0 for the full functionality to complete the iSCSI testing to the host.

For CDS/SKy 7.1, Connector port might need to be updated manually, due to a bug fixed in 8.0. 


Role Variables
--------------

This role will require/accept the following variables.

| Variable Name  | Description | Required (Y/N) |
|----------------|---|---|
| act_appliance  | Actifio Appliance IP or FQDN. | Y               |
| act_user       | Actifio username. This should be a Actifio user with System Manage priviledges | Y
| act_pass       | Password for the Actifio User | Y
| act_vendorkey  | Vendor key can be obtained by the customer through opening a Support Case with the CSE. | Y
| discover_as_vm | Whether to discover the new host as a VM or add as a physical host. If Yes, then VM discovery routines are executed, if not specified, default option (no) will be assumed and define as a physical host | N


Example Playbook
----------------

Example Playbook:

### If you grab it from the Ansible Galaxy"
```
- name: install and configure actifio agent
  hosts: "{{ host_group }}"
  become: yes
  become_method: sudo
  roles:
    - Actifio.connector_install
```

### If you clone from GitHub

```
- name: install and configure actifio agent
  hosts: "{{ host_group }}"
  become: yes
  become_method: sudo
  roles:
    - ansible_connector_install
```


This will work with the following inventory:

[actifio]
local-ora-1 act_appliance=192.168.57.128 act_user=admin act_pass=password act_vendorkey=XXXX-XXXX...
local-ora-2 act_appliance=192.168.57.128 act_user=admin act_pass=password act_vendorkey=XXXX-XXXX... discover_as_vm=yes


License
-------

Copyright 2018 <Kosala Atapattu kosala.atapattu@actifio.com>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
