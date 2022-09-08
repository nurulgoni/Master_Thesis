Role Nmae:"qt_creator"
=========

This role will install QtCreator6.0.0

Requirements
------------


Role Variables
--------------
This role uses the following 5 variables that have to be provided from the calling playbook.
-{{host}}:host group or id address of the target machine(s).
-{{ temp_dir_for_files_in_target_machine }}:Full path of the temprary diectory which will be created before insttallation and deleted after. For example,"/home/pi/for_rpi".
-{{ dir_path_of_dependency_files_in_control_server }}:Directory path in ansible server(control machine) where the installation files reside. For example, "/home/ubuntu_user/build_files"
-{{ installation_path }}:Directory path in the target/remote computer where the installation will be done. For example,"/opt/qtcreator" or "/opt/Qt6"
-{{ executables_path_for_profile }}:Directory path of executables in the target/remote computer,which will be inserted in the path variable. For example,"/opt/qtcreator/bin".

Dependencies
------------



Example Playbook
----------------
The following playbook is  taken from "qt_creator_install.yml" playbook.

---
- hosts: "{{host}}"
  vars:
    - temp_dir_for_files_in_target_machine: /home/pi/for_rpi
    - dir_path_of_dependency_files_in_control_server: /home/ngsharna/for_rpi
    - installation_path: /opt/qtcreator
    - executables_path_for_profile: /opt/qtcreator/bin
  roles:
     - qt_creator
 
