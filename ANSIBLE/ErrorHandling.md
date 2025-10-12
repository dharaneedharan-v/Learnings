
### Error Handling in Ansible
- Dealing with errors and failures in Ansible playbooks.
- Error handling techniques and best practices.

[x] Demonstrating error handling in practical scenarios.



Example : 

```yaml
---
- hosts: all
  become: true
  #gather:True # This will get the details of the Managed Nodes.  

  tasks:
    - name: Install security updates
      ansible.builtin.apt:
        name: "{{ item }}"
        state: latest
      loop:
        - openssl
        - openssh
      ignore_errors: yes 
    - name: Check if docker is installed
      ansible.builtin.command: docker --version
      register: output # To get the Output to Stored In the Variable. 
      ignore_errors: yes     # Check if there is a Error 
    - ansible.builtin.debug:
        var: output
    - name: Install docker
      ansible.builtin.apt:
        name: docker.io
        state: present
      when: output.failed
        
```
