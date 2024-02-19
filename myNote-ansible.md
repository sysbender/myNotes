
# myNote-ansible

# 1. install Ansible

1.  enable wsl on windows 10
2.  install centos (download centos 7), create user, add to wheel (sudoers), groupinstall desktop
3.  install python3
4.  install ansible as a normal user
5.  try ansible

```
# create inventory file , ssh access through key
[example]
ip or hostname

```

pip3 install ansible

## config

configheck current config  
`` `ansible --version``

`

config file priority:

-   `export ANSIBLE_CONFIG=/tmp/myansible.cfg`
-   `./ansible.cfg`
-   `~/.ansible.cfg`
-   `/etc/ansible/ansible.cfg`


## inventory
inventory file can be in different format : 
- hosts : default ini
- hosts.yml : yml
- hosts.json : json
override the inventory file in the ansible.cfg from command line
`ansible -i hosts`
override variable
`ansible -e 'ansible_port=2222'`


- ansible inventory
	```shell
	# from command
	ANSIBLE_HOST_KEY_CHECKING=False ansible all -m ping
	# in cfg
	host_key_checking = False
	# list hosts in group
	ansible centos --list-hosts
	```
- connect via root
	```
	centos1 ansible_user=root ansible_port=2222
	ansible all -m command -a 'id' -o
	```
- connect via sudo
		`ubuntu1 ansible_become=true ansible_become_pass=password`
- hostvars
	```
	[centos]
	centos[1:3]
	[centos:vars]
	ansible_user=root
	```
- inventory range
	`ubuntu[1:3`
- group vars
- inventory children groups
	```
	[linux:children]
	centos
	ubuntu
	```
## modules

- setup module - collect facts
	- automatically execute
	- reference as `setup` or `ansible.builtin.setup`
	- `ansible centos1 -m setup`
- file module
	- `ansible all -m file -a 'path=/tmp/test state=touch'`
	- `ansible all -m file -a 'path=/tmp/test state=file mode=600'`
- copy module
	`ansible all -m copy -a 'remote_src=yes src=/tmp/test dest=/tmp/test1'`
- command module - default module
	`ansible all -a 'hostname' -o`
- 

- color notation used during Ansible execution
	-  Red - failure
	- Yellow : success with changes
	- Green: success no changes
- idempotence
	- results are the same repeat an operation many times
- ansible-doc
	`ansible-doc file`

## playbook
- YAML
	- structure
	- indentation
	- quotes : 
	- multiline value 
		- `|`
		- `>` ends with new line
		- `>-`  
	- boolean
	- list and dictionary
- playbook sections
- playbook variables
- playbook facts
- Jinja2 template
- playbook creating and execute
# 2. Ansible for the Windows Admin by Jeremy Murrah

## Terminology

-   task
play = task + hosts-   playbook = plays
-   hosts/inventory = machines
-   vars/facts = variables - stored in a file or retrieved from a hostli>
-   * list - in json/yaml, array in powershell
-   dictionary - in json/yamal = hashtable in powershell

ansible-playbook [options] playbook.yml  
–step : confirmation before each task  
–limit : ignore inventory file/group , against specified machines  
-v(vvvv) :  
-e : extra variable individially or @filename  
–check : run but won’t make any change  

# 3. module development

``` ansible will generate code from that template:  
about 1600 lines code, copy to the target system, execute it.

-   argument_spec is a dict, and get populated by the parameter provided in YAML file.

has three parameters:

1.  argument_spec= dict(),
    
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

2.  required_one_of = [[]],
3.  3. mutually_exclusive = [[]]

# 4. ansible ad-hoc

```

* get paransible-doc

```

# list connection

ansible-doc -t connection -l

# module-name args

ansible -m copy -a “src=/etc/hosts dest=/tmp/hosts” --check --diff localhost

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

-   short hand - put them in one line

```
#playbook.ymml
hosts: localhost
tasks:
- copy:    src: "/etc/hosts"    dest: "/tmp/hosts"

```

ansible-playbook playbook.yml

```
---

```

-   name: this is the first playbook  
    gather_facts: no  
    hosts: localhost  
    tasks:
    -   copy: src="/etc/hosts" dest="/tmp/hosts"  
        

## yaml syntax

-   list

```
fruits:
- apple
- orange
- mango

```

-   dictionary

```
martin:
 name: Martin dev
 job: developer
 skill: elite

```

-   value can span multiple line with pipe | or great than >> (indentation will be ignored)

1.  pipe - will keep the new line and any trailing space
2.  great than will fold newline to spaces

## ansible configure file

search order

-   * ANSIBLE_CONFIG - env variable
-   * ansible.cfg - in current directory (will not load if the folder is writable)
-   ~/.ansible.cfg - in home dir
-   /etc/ansible/ansible.cfg

options in config file:

-   ansible_connection=local
-   ansible_connection=winrm
-   * ansible_port=5555
-   * ansible_password
-   ansible_winrm_transport: basic

## inventory

conbe written in ini or yaml format  
no standard ssh port :  [webserver.com:2222](http://webserver.com:2222/)  
ansible glob pattern - range: www[1:5] , db-[a:f]  
set connect type and user on a per host basis:  [node1.mydomain.com](http://node1.mydomain.com/)  ansible_connection=winrmansible_user=admin

### apply variable to a group of hosts

```

```
[bad_group]
node1 
node2

```

[bad_group:vars]  
ntp_server=[ntp1.mydomain.com](http://ntp1.mydomain.com/)  
[proxy=proxy1.mydomain.com](http://proxy=proxy1.mydomain.com/)

### two default group

1.  all
2.  ungrouped

### inventory plugin

plugin - support dynamic list from azure, aws, …

```
# to list available inventory plugins
ansible-doc -t inventory -l

```

#list aansible module  
ansible-doc -l

list parameters of a module  
ansible-doc -s module_name  

without specifying inventory file, can only use localhost  
different inventory file type:

1.  py -
2.  ini -
3.  yml -

```
# to get the inventory ignore extensions - .orig, .ini, .cfg, .retry
ansible-config list

```

# to list all inventoransible-inventory --list

# tree view of inventory

ansible-inventory --graph  

## ansbile face

```

ansible node1 -m setup

```

# write facts to a file

-   name: writes to a file named  
    host: node1  
    become: true  
    remote_user: root  
    tasks:
    -   name:  
        copy :  
        dest: /tmp/facts.txt  
        content: “{{ansible_all_ipv4_addresses}} {{}}”

# ansible variables

# 8. window

```
#check ps version

```

$PSVersionTable

# winrm

## winrm listener

## winrm service configuration

### configureRemotingForAnsible.ps1 in ansible repo

setup http/https listeners with a self-signed certificate and baisc authentification

winrm get winrm/config  
winrm set winrm/config/service @{AllowUnencrypted=“true”}

# not work:

winrm set winrm/config/service/auth @{Basic=“true”}

# work (network profile set to private )

set-item -Force WSMan:\localhost\Service\AllowUnencrypted $True

# [www.guruoye.net](http://www.guruoye.net/)

```
#window inventory

[windows]
win10

[windows:vars]
ansible_user=xxx
ansbile_password=xxx
ansible_port=5986
ansible_connection=winrm
ansible_winrm_server_cert_validation=ignore


```

```

ansible -m win_ping all

ansible windows -i hosts -m facts

ansible windows -i hosts -m win_chocolatey -a “name=notepadplusplus state=present”

```




domain user:
svc-ansible

winrm:
 listener:
	http: 5985
	https: 5986
	
 authentication 
	basic
	certificate
	ntlm
	kerberos
	CredSSP - modern, 
	
	
		#powershell
		winrm enumerate winrm/config/listener
		winrm get winrm/config/Service
		wget https://raw.githubusercontent.com/ansible/ansible/devel/examples/scripts/ConfigureRemotingForAnsible.ps1 -Outfile ConfigureRemotingForAnsible.ps1 
		# enable credSSP and disable basic
		
		.\ConfigureRemotingForAnsible.ps1 -EnableCredSSP -DisableBasicAuth -Verbose
		
		
		# remove http
		 Get-ChildItem -Path WSMan:\localhost\Listener | Where-Object { $_.keys -eq "Transport=HTTP"} | Remove-Item -Recurse -Force
		 
		 # restart winrm
		 restart-service winrm 
		 
		 # give service account access - add to local admin group 
		 
		 
========================



	 
		 
[web]
win10

[web:vars]
ansbile_user=""
ansible_password=""
ansbile_connection=winrm
ansible_winrm_transport=credssp
ansiblewinrm_server_cert_validation=ignore




```

### manage windows like Linux with Ansible

win modules

-   win_chocolatey!
    
-   win_package
    
-   not win_msi
    
-   win_dsc
    
-   win_reboot - reboot and wait for connection
    
-   wait_for_connection - second half of the reboot
    
-   * win_updates - category_names, reboot, blacklist
    
-   win_iis_website
    
-   win_iis_webapp
    
-   win_regedit - individual key/value
    
-   * win_regmerge - bulk import
    
-   win_service -
    
-   win_domain - create domain, join,
    
-   win_dns_client - change dns server
    
-   * win_owner - set owner
    
-   win_acl -
    

### Ansible for the windows admin

# 9. best practice

consist style

-   tagging
-   whitespace
-   name of tasks, plays, vairables, roles
-   * directory layout

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







</code></pre>
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjU5NjY1OTkxLDM3NzE3NDUxLDE5Njg5NT
g4OCwtMTA4OTc0NzU1MywtMTQ5MTUzNjA4OSw1MzY3MjgwNjQs
MTE5MTk0MTE3NywtNDU3MDMxNzgsMTA0NDM3NDYzOCw1MTAwMD
g0NDUsNzc3MTQwMTM1LDM2MzMwMjY2MSwxODczODMxNTcyLC0y
MzA4MzYxNzYsLTE1NzQ3NDM1MTRdfQ==
-->