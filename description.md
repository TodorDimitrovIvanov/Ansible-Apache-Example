# Task: Create an Ansible project to deploy and configure a web application on multiple environments.
This task covers inventory management, playbook structure, roles, variables at different levels, templates, handlers, vault usage, and tags. It provides a realistic scenario for applying your Ansible knowledge in a DevOps context
## Requirements:
1. __Inventory__:
* Create a YAML inventory with three groups: dev, staging, and prod
* Each group should have at least two hosts
* Use group_vars for environment-specific variables

2. __Playbook__:
* Create a main playbook that includes roles
* Implement three roles: common, webserver, and app
* Use tags for selective execution

3. __Roles__:
* common: Install basic packages and set up NTP
* webserver: Install and configure Apache
* app: Deploy a simple HTML application

4. __Variables__:
* Use host_vars for host-specific configurations
* Implement group variables for each environment
* Create global variables for shared settings

5. __Templates__:
* Use a Jinja2 template for the Apache virtual host configuration
* Create a template for the HTML application that includes environment-specific content

6. __Handlers__:
* Implement handlers to restart services when configurations change

7. __Vault__:
* Use Ansible Vault to encrypt sensitive data (e.g., database passwords)

## Detailed Instructions:
1. Create the project structure:
```
ansible_project/ 
├── inventories/
│   └── environments.yml
├── group_vars/
│   ├── all.yml
│   ├── dev.yml
│   ├── staging.yml
│   └── prod.yml
├── host_vars/
│   └── [hostname].yml
├── roles/
│   ├── common/
│   ├── webserver/
│   └── app/
├── templates/
│   ├── vhost.conf.j2
│   └── index.html.j2
├── site.yml
└── ansible.cfg
```
2. Write the inventory file (inventories/environments.yml) with the required groups and hosts.
3. Create group_vars files for each environment and all.yml for global variables.
4. Develop the roles:
    * common: Tasks for basic setup
    * webserver: Apache installation and configuration
    * app: Application deployment
5. Create the main playbook (site.yml) that includes all roles and uses tags.
6. Implement templates for Apache configuration and the HTML application.
7. Use Ansible Vault to encrypt sensitive information in group_vars files.
8. Write host_vars files for any host-specific configurations.
9. Test your playbook:
```
ansible-playbook -i inventories/environments.yml site.yml --ask-vault-pass
```
10. Try running specific parts of your playbook using tags
```
ansible-playbook -i inventories/environments.yml site.yml --tags "webserver,app" --limit dev
```
