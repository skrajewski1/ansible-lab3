---
- hosts: ws
  become: true
    
  tasks:
    - name: Check if directory exists
      stat:
        path: /opt/aws
      register: directory_exists

    - name: Print directory exists
      debug:
        msg: "Directory /opt/aws exists: {{ directory_exists.stat.exists }}"
      when: directory_exists.stat.exists

    - name: Find a file
      find:
        file_type: file
        hidden: yes
        patterns: "devops"
        paths:
          - /home
          - /opt
          - /usr/local
        recurse: yes
      register: devops_file

    - name: Print if found devops
      debug:
        msg: "Found devops file at: {{ devops_file.files | map(attribute='path') | list}}"
      when: devops_file.matched > 0
