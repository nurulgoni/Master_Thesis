Role Nmae:"opencv"
=========

This role will install OpenCV
Requirements
------------
There is a file "opencv_dep.csv" in the files directory  that contains a list of files. These files are required to be installed before before installation. These files resides in "/dir_path_of_dependency_files_in_control_server/opencv_dep" directory of control server.

Role Variables
--------------
This role uses the following 4 variables that have to be provided from the calling playbook.
-{{host}}:host group or id address of the target machine(s).
-{{ temp_dir_for_files_in_target_machine }}:Full path of the temprary diectory which will be created before insttallation and deleted after. For example,"/home/pi/for_rpi".
-{{ dir_path_of_dependency_files_in_control_server }}:Directory path in ansible server(control machine) where the installation files reside. For example, "/home/ubuntu_user/build_files"
-{{ installation_path }}:Directory path in the target/remote computer where the installation will be done. For example,"/opt/opencv_4.5.5" 


Dependencies
------------
For successfull OpenCv installation ,Cmake has to be installed first. "opencv" role depends on "cmake" role. So, in the "main.yml" of  meta directory  "cmake" role in included.

Example Playbook
----------------
The following playbook is  taken from "opencv_install.yml" playbook.

---
- hosts: "{{host}}"
  gather_facts: False
  vars:
    - temp_dir_for_files_in_target_machine: /home/pi/for_rpi
    - dir_path_of_dependency_files_in_control_server: /home/ngsharna/for_rpi
    - installation_path: /opt/opencv_4.5.5

  roles:
     - opencv


