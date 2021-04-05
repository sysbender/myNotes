# myNote - ansible

# 1. install Ansible

1. enable wsl on windows 10
2. install centos (download centos 7), create user, add to wheel (sudoers), groupinstall desktop
3. install python3
4. install ansible as a normal user
5. try ansible
```
# create inventory file , ssh access through key
[example]
ip or hostname

```
pip3 install ansible
 

# 2. Ansible for the Windows Admin by Jeremy Murrah

## Terminology
* task 
* play = task + hosts
* playbook = plays
* hosts/inventory = machines
* vars/facts = variables - stored in a file or retrieved from a host
* list - in json/yaml, array in powershell
* dictionary - in json/yamal = hashtable in powershell
　

## ansible-playbook command line

```
ansible-playbook [options] playbook.yml 
--step : confirmation before each task
--limit : ignore inventory file/group , against specified machines
-v(vvvv) : 
-e : extra variable individially or @filename
--check : run but won't make any change
```

 # 3. module development
## module search path
* module name  - test_module.py or test_module.sh or test_module.what
* search path - 
1. env var : ANSIBLE_LIBRARY; 
2. command line option : --module-path
3. "./library"

* boilerplate 
```
def main():
  module = AnsibleModule(
    argument_spec = dict( input = dict(required=True) , ),
    supports_check_mode = False
  )
  from ansible.module_utils.basic import *
  main()

```
ansible will generate code from that template:
about 1600 lines code, copy to the target system, execute it.

* argument_spec is a dict, and get populated by the parameter provided in YAML file.

has three parameters:
1. argument_spec= dict(),
   ```
      mandatory_var = dict(required = True),
      mandatory_var_not_logged = dict(required =True, no_log = True )
      mandatory_var_with_3_options = dict(choices=[1,2,3])
      optional_var1=dict(),
      optional_var2=dict(),
      optional_var3=dict(),
      optional_var_with_default=dict( default='blaar),
      optional_var_with_type_check=dict(required=True, type='bool'),
      optional_var_with_alias=dict(required=True, aliases=['whatever']),
   ```
```
   
- name: Test Module Development
  hosts: localhost
  gather_facts: False
  tasks:
  - name: Test Module
    test_module:
      mandatory_var: value1
```
2. required_one_of = [[]],
3. mutually_exclusive = [[]]

# 4. ansible ad-hoc
```

* get parameter

# ansible-doc

# list connection
ansible-doc -t connection -l
# module-name args
ansible -m copy -a "src=/etc/hosts dest=/tmp/hosts" --check --diff localhost

```

# 5. ansible playbook

## format
```
# two layer:
---   # indicator start of yaml
-     # list symbol
play  # layer 1
task  # layer 2

```

example

```
#playbook.ymml
hosts: localhost
tasks:
- copy:
    src: "/etc/hosts"
    dest: "/tmp/hosts"
```
* short hand - put them in one line
```
#playbook.ymml
hosts: localhost
tasks:
- copy:    src: "/etc/hosts"    dest: "/tmp/hosts"
```

ansible-playbook playbook.yml

```
---

- name: this is the first playbook
  gather_facts: no
  hosts: localhost
  tasks:
  - copy: src="/etc/hosts" dest="/tmp/hosts"
```

## yaml syntax

* list

```
fruits:
- apple
- orange
- mango
```


* dictionary

```
martin:
 name: Martin dev
 job: developer
 skill: elite
```


# inventory

without specifying inventory file, can only use localhost 
different inventory file type:
1. py -
2. ini - 
3. yml - 

```
# to get the inventory ignore extensions - .orig, .ini, .cfg, .retry
ansible-config list

# to list all inventory
ansible-inventory --list

# tree view of inventory
ansible-inventory --graph
```
# 9. best practice

consist style
* tagging
* whitespace
* name of tasks, plays, vairables, roles
* directory layout


```
# inventory - meaningful name
cos72 ansible_host=192.168.1.72
cos73 ansible_host=192.168.1.73


# groups
[cos]
cos[1:2]

# variable - 16 places you can put variables
apache_port : 80

# use name lable - for documenting

- hosts: web
  name: installs and starts apache
  
  tasks:
  - name: install apache packages
    yum:
      name: httpd
      state: latest
      
  - name: starts apache service
    service:
      name: httpd
      state: started
      enabled: yes
      
      
      
# block - organise and group tasks; enable rollbacks 

- block:
    copy:
      src: critical.conf
      dest: /etc/critical/crit.conf
      
    service:
      name: critical
      state: restarted
      
  rescue:
    command: shutdown -h now
    
#execute option

-vvvv
--step
--check
--diff
--start-at-task

--list-tasks
--list-tags
--list-hosts
--syntax-check

#avoid - command, shell, raw

# smoke tests -check
-name: check for proper response
uri:
  url: http://localhost/myapp
  return_content: yes
register: result
until: '"hello world" in result.content'
retries: 10
delay: 1







```