# vmware_inventory
Ansible VMware dynamic inventory with 'annotation' variable support.

Since version 6 additional information field is not supported. There is no way to get tags information.
This vesion of vmware_inventory uses annotation (notes) field  to populate tags, variables and list_variables.

* gruping by tag support
* multiple values separated by , are translated to list


example:

VCenter VM Notes:
```
ansiblemanaged
group_by_something
debian
debian9
properties_list1=true,true,false,1,2
prop=SomeProperty
alabalanica asda dasdasdas
```

ansible inventory:
```
---CUT---
    "hostvars": {
      "fusionldap.grizmin.org": {
        "name": "fusionldap.grizmin.org",
        "tags": [
          "ansiblemanaged",
          "group_by_something",
          "debian",
          "debian9"
        ],
        "properties": {
          "properties_list1": [
            "true",
            "true",
            "false",
            "1",
            "2"
          ],
          "prop": [
            "SomeProperty"
          ],
          "ldap": [
            "False"
          ]
        },
        "ansible_ssh_host": "192.168.11.24",
        "tag": [],
        "ansible_uuid": "16a4f462-eff5-4182-a74c-838937243012",

---CUT---

  "centos": {
    "hosts": [
      "kafkanode1.grizmin.org"
    ]
  },
  "debian9": {
    "hosts": [
      "fusionldap.grizmin.org",
      "ldap.grizmin.org",
      "forex.grizmin.org",
      "ansible.grizmin.org",
      "bugs.grizmin.org",
      "client.grizmin.org"
    ]
  },
  "guests": {
    "hosts": [
      "ldap.grizmin.org",
      "bugs.grizmin.org",
      "kafkanode1.grizmin.org",
      "forex.grizmin.org",
      "pfs.grizmin.org",
      "ansible.grizmin.org",
      "fusionldap.grizmin.org",
      "client.grizmin.org"
    ]
  },
  "ansiblemanaged": {
    "hosts": [
      "fusionldap.grizmin.org",
      "ldap.grizmin.org",
      "kafkanode1.grizmin.org",
      "forex.grizmin.org",
      "ansible.grizmin.org",
      "bugs.grizmin.org",
      "client.grizmin.org"
    ]
  },
  "centos64Guest": {
    "hosts": [
      "kafkanode1.grizmin.org"
    ]
  },
```


