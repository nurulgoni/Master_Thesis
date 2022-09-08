Role Nmae:"qt"
=========

This role will install Qt6.2.0

Requirements
------------
There is a file "qt_dep.csv" in the files directory  that contains a list of files. These files are required to be installed before before installation. These files resides in "/dir_path_of_dependency_files_in_control_server/qt_dep" directory of control server.


Role Variables
--------------
This role uses the following 5 variables that have to be provided from the calling playbook.
-{{host}}:host group or id address of the target machine(s).
-{{ temp_dir_for_files_in_target_machine }}:Full path of the temprary diectory which will be created before insttallation and deleted after. For example,"/home/pi/for_rpi".
-{{ dir_path_of_dependency_files_in_control_server }}:Directory path in ansible server(control machine) where the installation files reside. For example, "/home/ubuntu_user/build_files"
-{{ installation_path }}:Directory path in the target/remote computer where the installation will be done. For example,"/usr/local/lib/cmake3.22/cmake" or "/opt/Qt6"
-{{ executables_path_for_profile }}:Directory path of executables in the target/remote computer,which will be inserted in the path variable. For example,"/opt/Qt6/bin".

Dependencies
------------



Example Playbook
----------------
The following playbook is  taken from "qt_install.yml" playbook.

---
- hosts: "{{host}}"
  vars:
    - temp_dir_for_files_in_target_machine: /home/pi/for_rpi
    - dir_path_of_dependency_files_in_control_server: /home/ngsharna/for_rpi
    #do not change the following installation path. 
    #It is required to be same  installation path that was used during the build. 
    #These  both path has to be adjusted.
    - installation_path: /opt
    - executables_path_for_profile: /opt/Qt6/bin
  roles:
      - qt
