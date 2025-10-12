- Create AWS Resources using Ansible (Collections)

- Understanding Ansible variables and their scope with an example
- Jinja2 Templating - Utilizing advanced templating features
- Variable precedence: How Ansible resolves conflicts between - different variable sources.
- Hands-on: Using variables in playbooks and roles.

---


# Setup EC2 Collection and Authentication

## Install boto3

```
pip install boto3
```

## Install AWS Collection

```
ansible-galaxy collection install amazon.aws
```

## Setup Vault 

1. Create a password for vault

```
openssl rand -base64 2048 > vault.pass
```

2. Add your AWS credentials using the below vault command

```
ansible-vault create group_vars/all/pass.yml --vault-password-file vault.pass
```

----

You can declare the varible in 22 possible ways.

Best practise Use the default and vars and in the Playbook Section mention the Vars and Finally use the extas replace the what are the varibles intially declared it will be replaced if we use the Extras ( high Precedences)

----

Understanding variable precedence
Ansible does apply variable precedence, and you might have a use for it. Here is the order of precedence from least to greatest (the last listed variables override all other variables):

Command-line values (for example, -u my_user, these are not variables)

Role defaults (as defined in Role directory structure) 1

Inventory file or script group vars 2

Inventory group_vars/all 3

Playbook group_vars/all 3

Inventory group_vars/* 3

Playbook group_vars/* 3

Inventory file or script host vars 2

Inventory host_vars/* 3

Playbook host_vars/* 3

Host facts and cached set_facts 4

Play vars

Play vars_prompt

Play vars_files

Role vars (as defined in Role directory structure)

Block vars (for tasks in block only)

Task vars (for the task only)

include_vars

Registered vars and set_facts

Role (and include_role) params

include params

Extra vars (for example, -e "user=my_user")(always win precedence)