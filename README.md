# Makefile for Terraform users

This repository provides a Makefile to give you a simple interface for Terraform.

## Why?

- Simplify your CLI terraform runs
- Don't Repeat Yourself while typing terraform commands
- Easier adoption for people that are not used to Terraform
- Document common usage
- Unique entrypoint script for credentials management

## Installation

Simply download the `Makefile` and the `terraform.sh` files in your terraform configuration directory.

    wget -O Makefile https://raw.githubusercontent.com/paulRbr/terraform-makefile/master/Makefile
    wget -O terraform.sh https://raw.githubusercontent.com/paulRbr/ansible-makefile/master/terraform.sh

## Commands

This is the list of commands made available

~~~bash
> make
bootstrap                      make bootstrap # Install ansible (Ubuntu only)
cmdb                           make cmdb # Create HTML inventory report
console                        make console [env=hosts] [args=<ansible-console arguments>] # Run an ansible console
debug                          make debug host=hostname [env=hosts] [args=<ansible arguments>] # Debug a host's variable
dry-run                        make dry-run [playbook=setup] [env=hosts] [tag=<ansible tag>] [limit=<ansible host limit>] [args=<ansible-playbook arguments>] # Run a playbook in dry run mode
facts                          make facts group=all [env=hosts] [args=<ansible arguments>] # Gather facts from your hosts
install                        make install [roles_path=roles/] # Install roles dependencies
lint                           make lint [playbook=setup] [env=hosts] [args=<ansible-playbook arguments>] # Check syntax of a playbook
list                           make list [env=hosts] # List hosts inventory
run                            make run [playbook=setup] [env=hosts] [tag=<ansible tag>] [limit=<ansible host limit>] [args=<ansible-playbook arguments>] # Run a playbook
vault                          make vault file=/tmp/vault.yml [env=hosts] [args=<ansible-vault arguments>] # Edit or create a vaulted file
~~~

## Variables

This is the explanation of variables that can be passed to commands:


| Name      | Default | Description | Example |
| --------- | ------- | ----------- | ------- |
| `playbook`|`setup`  | Name of the playbook yaml file without the .yml extension | make dry-run playbook=starfish |
| `env`     | `hosts` | Name of the inventory you want to use | If you have an inventory file in `production/hosts` you will be able to `make run env=production` |
| `tag`     | -       | Specify a list of tags for your ansible run | `make dry-run tag=ssh` |
| `limit`   | -       | Limit the command to a subset of hosts with ansible's limit argument | `make dry-run limit=database` |
| `args`    | -       | Add ansible understandable arguments | `make dry-run args='--user=root'` |
