Role Name:"uninstall"
=========

This role can be used to uninstall multiple  software:cmake,nodejs, opencv,qt,qtcreator

Requirements
------------


Role Variables
--------------
This role uses the following 3 variables that have to be provided from the calling playbook.
-{{host}}:host group or id address of the target machine(s).
-{{ installation_path }}:Directory path in the target/remote computer where the installation will be done. For example,"/opt/qtcreator"
-{{ executables_path_for_profile }}:Directory path of executables in the target/remote computer,which will be inserted in the path variable. For example,"/opt/qtcreator/bin".

Dependencies
------------


Example Playbook
----------------
The following playbook is  taken from "qt_creator_uninstall.yml" playbook.
---
- hosts: "{{host}}"
  gather_facts: no

  vars:
    - installation_path: /opt/qtcreator
    - executables_path_for_profile: /opt/qtcreator/bin
  roles:
      - uninstall
