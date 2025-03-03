 ##Prerequisites
 ```bash
    sudo apt update
   sudo apt install -y ansible
```

##Target VM Details (Ensure SSH access is enabled)
Update inventory file with the VM's IP address.
Add the control machine’s SSH key to the authorized_keys on the VM.
```bash
ssh-copy-id ubuntu@<target-vm-ip>
```
##Docker Image for Angular App
A pre-built Angular container image should be available in Docker Hub or a private registry.
Example: myrepo/angular-app:latest


##Step-by-Step Execution
Update Ansible Inventory File
Create or update the Ansible inventory file (inventory.ini) with the target VM details.
```bash
[target_vm]
<target-vm-ip> ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/id_rsa
```

##Run the Playbook
Execute the Ansible playbook to install Docker and deploy Angular.
```bash
ansible-playbook -i inventory.ini install_docker_deploy_angular.yml
```

## Verifying Deployment
Expected output:
```bash
CONTAINER ID   IMAGE                     PORTS                  STATUS
123456789abc   myrepo/angular-app:latest  0.0.0.0:80->80/tcp     Running
```

##Access Angular App:
Open http://<target-vm-ip> in your browser.
