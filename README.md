[![Generic badge](https://img.shields.io/badge/BUILD-PASS-BLUE.svg)](https://shields.io/)
# Wordpress_with_remote_DB_ansible

## About

An Ansible playbook to build a Wordpress site with its database on a remote server. You can also build a http only server or a mysql only server with this playbook.( for AWS EC2 instances )

## Prerequisites

- Ansible should be installed.
- Know a basic idea on seting up Ansible Inventory File.

## To Use The Code

- ```sh
   git clone https://github.com/ManuGeorge96/Wordpress_with_remote_DB_ansible.git
  ```
- ```sh
    cd  Wordpress_with_remote_DB_ansible
  ```  
- Setting Up Inventory File
  -  Create a file <b>hosts</b>.
  -  Include below line on the file ( edit credentials )
     - ```sh
        WP ansible_host=WP_SERVER_IP_HERE ansible_user=SSH_USER_ON_SERVER ansible_ssh_port=SSH_PORT ansible_ssh_private_key_file=PATH_TO_PRIVATE_KEY
        DB ansible_host=DB_SERVER_IP_HERE ansible_user=SSH_USER_ON_SERVER ansible_ssh_port=SSH_PORT ansible_ssh_private_key_file=PATH_TO_PRIVATE_KEY
       ```
- Edit Required Data's on <b>main.yml</b> file.
  ```sh
    users: USER_NAME
    db_name: WP_DB_NAME
    db_user: WP_DB_USER
    db_pass: WP_DB_PASSWORD
    domain: DOMAIN_NAME
    mysql_root: MYSQL_ROOT_PASSWORD
  ```  
-  ```sh
     ansible-playbook -i hosts main.yml  
   ```
- For Building only a HTTP Server Without Wordpress or Database side,
  ```sh
   ansible-playbook -i hosts main.yml --tags=http_only
  ```
- For Building only a MySQL Server Without HTTP and Wordpress Databaes,
  ```sh
    ansible-playbook -i hosts main.yml --tags=mysql_only
  ```  
    
