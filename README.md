Role Name
=========

A helper ansible role for validating and guiding you through a TripleO TLS
everywhere deployment


Role Variables
--------------

* `helper_report_path`: Is the path where the report of the helper run will
                        be stored. Defaults to **/tmp/report.txt**.


Example Playbook
----------------

    ---
    - hosts: all
      roles:
        - tripleo-tls-everywhere-helper
      tags:
        - common

Running this playbook
---------------------

This playbook is targetted at TripleO deployments. The following assumptions
are made:

* You are running this playbook from the undercloud host.
* You are using a dynamic inventory that includes all the hosts in TripleO
  (including the undercloud)
* The dynamic inventory was created with the `tripleo-ansible-inventory` tool.

As mentioned above, it is recommended that you use the
`tripleo-ansible-inventory` tool in order to run this playbook. When running
this tool, you might need to adjust the user for the undercloud.

You can run the tool as follows:

```
tripleo-ansible-inventory --static-yaml-inventory hosts.yaml
```

This will create an inventory file called **hosts.yaml**.

Edit this file to have the user match what you're using.

Finally, you can run the playbook as follows:

```
ansible-playbook -i hosts.yaml tripleo-tls-everywhere-helper/tests/verify-tls-everywhere.yaml
```

A report will be created in the path that `helper_report_path` specifies.

License
-------

Apache License 2.0

Author Information
------------------

* [Juan Antonio Osorio Robles](https://jaormx.github.io/)
