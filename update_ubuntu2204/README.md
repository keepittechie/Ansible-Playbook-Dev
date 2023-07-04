## Instructions for Using the Ansible Playbook

To use the provided Ansible playbook, follow these steps:

Ensure that you have Ansible installed on your Ansible Controller. If you don't have it installed, refer to the Ansible documentation for instructions on how to install it: Ansible Installation Guide.

It is assumed you have these two tasks completed:
- Creating Key Pair on the Ansible controller
- Copy the Public Key to your Ubuntu Server nodes

## Configure

Open the inventory.yml file and define your inventory. For example, if you have two Ubuntu servers with their respective IP addresses, modify the inventory.yml file as follows:

```yaml
all:
  hosts:
    server1:
      ansible_host: <IP_ADDRESS_SERVER1>
    server2:
      ansible_host: <IP_ADDRESS_SERVER2>
  ```

Replace <IP_ADDRESS_SERVER1> and <IP_ADDRESS_SERVER2> with the actual IP addresses of your Ubuntu servers.

## Execute Playbook

Open a terminal and navigate to the "update_ubuntu2204" directory.

Execute the following command to run the playbook:

```bash
ansible-playbook -i inventory.yml playbook.yml
```

Make sure to replace playbook.yml with the actual name or path of your playbook file if it is different.

## Breakdown of Playbook

Ansible will start executing the tasks defined in the playbook on the specified Ubuntu servers.

- You will be prompted to enter the sudo password for the remote servers specified in the inventory file.
- The playbook will first update the package lists on the servers using the 'apt' module.
- Then, it will perform a distribution upgrade, removing any unused packages and cleaning the package cache.
- If a reboot is required after the upgrade, the servers will be rebooted.
- Finally, dependencies that are no longer required will be removed.

Monitor the output in the terminal to track the progress and completion of the playbook execution.

By following these instructions, you can use the provided Ansible playbook with the inventory.yml file to update and upgrade packages on your Ubuntu servers.
