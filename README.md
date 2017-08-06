# vmware_inventory
Ansible VMware dynamic inventory with 'annotation' variable support.

Since version 6 additional information field is not supported. There is no way to get tags information.
This vesion of vmware_inventory uses annotation (notes) field  to populate tags, variables and list_variables.

example:
my_tag
my_variable=value
my_list_variable=value1,value2,valuen

* gruping by tag support added
