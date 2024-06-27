# Ansible Configuration Readme

[defaults]
inventory = inventory.yaml  #specifies invetory location
remote_user = ec2-user      #sets default user for ssh connections
host_key_checking = false   #skips key verification; needed for automation of tasks
retry_files_enabled = false #ansible creates a file of hosts that failed during the execution of a playbook; meant for debugging
interpreter_python = auto_silent #auto detects python location and limits the warnings
localhost_warning = false   #turns off the default reminder that running tasks on the local host may be different than on remote hosts
deprecation_warnings = false
log_path = /home/ec2-user/ansible/ansible.log #specifies the location and of created logs

[privilege_escalation]
become = true
become_method = sudo        #can use sudo, su, pbrun
become_user = root          #sets the user account ansible should use; typically root.

[ssh_connection]
ssh_args = -o ControlMaster=auto -o ControlPersist=60s #for large-scale deployments/automation scenarios; keeps open and reuses ssh connection