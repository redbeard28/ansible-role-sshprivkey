ANSIBLE-ROLE-SSHPRIVKEY
=======================

Ansible role deploy ssh private key.


## Howto use this role?
This role need to be include in a playbook. 

Call this **Galaxy** role  like this:

````bash
ansible-galaxy install -r requirements.yml 
````

Inside requirements.yml
````yaml
# from GitHub, overriding the name and specifying a specific tag
- src: redbeard28.sshprivkey
````

More info => [Ansible Docs](https://docs.ansible.com/ansible-container/roles/access.html)

## Requirements

 * Ansible 2.9+


Role Variables
--------------

```yaml
---
myprivatekey: "{{ vault_myprivatekey }}"
mypubkey: "{{ vault_mypubkey }}"
```

Dependencies
------------

You must provide an ansible vault to fullfil those two vars.
For molecule:
```bash
ansible-vault create $home/ansible-role-sshprivkey/molecule/resources/.vault_mysecrets
```

create a txt file with your vault password:
```bash
$home/ansible-role-sshprivkey/.vault_passwd 
```


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      roles:
         - { role: redbeard28.sshprivkey, tags: mytags }


Molecule testing framework
--------------------------

You can use molecule to test this role.
```bash
ANSIBLE_VAULT_PASSWORD_FILE=$home/ansible-role-sshprivkey/.vault_passwd namespace=redbeard28 image=debian tag=buster-basetools molecule converge
ANSIBLE_VAULT_PASSWORD_FILE=$home/ansible-role-sshprivkey/.vault_passwd namespace=redbeard28 image=debian tag=buster-basetools molecule verify
```

Author Information
------------------

Jeremie CUADRADO[¹](mailto:info@redbeard-consulting.fr) from Redbeard-Consulting
