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

License
-------

Apache License 2.0

Author Information
------------------

* [Juan Antonio Osorio Robles](https://jaormx.github.io/)
