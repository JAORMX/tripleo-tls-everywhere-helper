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

It is assumed that the playbook will be ran from the undercloud.

### Using the dynamic inventory

As mentioned above, it is recommended that you use the
`tripleo-ansible-inventory` tool in order to run this playbook. When running
this tool, you might need to adjust the user for the undercloud.

You can run the tool as follows:

```
tripleo-ansible-inventory --static-yaml-inventory hosts.yaml
```

This will create an inventory file called **hosts.yaml**.

Edit this file to have the undercloud `ansible_ssh_user` match what you're using.

Finally, you can run the playbook as follows:

```
ansible-playbook -i hosts.yaml tripleo-tls-everywhere-helper/tests/verify-tls-everywhere.yaml
```

A report will be created in the path that `helper_report_path` specifies.

### Manually writing an inventory

Note that it is also possible to write an inventory manually in order to run this.

For the undercloud; It would look as follows:

```
Undercloud:
  hosts:
    undercloud: {}
  vars:
    ansible_host: localhost
    ansible_ssh_user: stack
```

The main thing to note is to have a group called `Undercloud`.

Working with tags
-----------------

This role can be used in different stages of the deployment. This behavior is
controlled with Ansible tags. The default behavior (with no tags specified) is
to run all of the validations.

Here is a description of the existing tags, as well as what they mean in your
deployment:

* `pre-undercloud-deploy`: This is a stage where the user is about to deploy the
                           undercloud. This will check for correct settings in
                           the undercloud.conf file.


License
-------

Apache License 2.0

Author Information
------------------

* [Juan Antonio Osorio Robles](https://jaormx.github.io/)
