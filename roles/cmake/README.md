Role Nmae:"Cmake"
=========

This role will install CMake 3.22.0

Requirements
------------


Role Variables
--------------
This role uses the following 4 variables that have to be provided from the calling playbook.
-{{host}}:host group or id address of the target machine(s).
-{{ temp_dir_for_files_in_target_machine }}:Full path of the temprary diectory which will be created before insttallation and deleted after. For example,"/home/pi/for_rpi".
-{{ dir_path_of_dependency_files_in_control_server }}:Directory path in ansible server(control machine) where the installation files reside. For example, "/home/ubuntu_user/build_files"
-{{ installation_path }}:Directory path in the target/remote computer where the installation will be done. For example,"/usr/local/lib/cmake3.22/cmake" or "/opt/Qt6"

Dependencies
------------



Example Playbook
----------------
The following playbook is  taken from "cmake_install.yml" playbook.

---
- hosts: "{{host}}"
  vars:
    - temp_dir_for_files_in_target_machine: /home/pi/for_rpi
    - dir_path_of_dependency_files_in_control_server: /home/ngsharna/for_rpi
    - installation_path: /usr/local/lib/cmake3.22/cmakes
  roles:
      - cmake


