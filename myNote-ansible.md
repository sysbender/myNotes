---


---

<h1 id="mynote-ansible">myNote-ansible</h1>
<h1 id="install-ansible">1. install Ansible</h1>
<ol>
<li>enable wsl on windows 10</li>
<li>install centos (download centos 7), create user, add to wheel (sudoers), groupinstall desktop</li>
<li>install python3</li>
<li>install ansible as a normal user</li>
<li>try ansible</li>
</ol>
<pre><code># create inventory file , ssh access through key
[example]
ip or hostname

</code></pre>
<p>pip3 install ansible</p>
<h2 id="config">config</h2>
<p>  configheck current config<br>
<code>
`ansible --version</code></p>
<p>`

config file priority:</p>
<ul>
<li>
- export ANSIBLE_CONFIG=/tmp/myansible.cfg</li>
<li>./ansible.cfg</li>
<li>~/.ansible.cfg</li>
<li>
- /etc/ansible/ansible.cfg</li>
</ul>
<h1 id="ansible-for-the-windows-admin-by-jeremy-murrah">2. Ansible for the Windows Admin by Jeremy Murrah</h1>
<h2 id="terminology">Terminology</h2>
<ul>
<li>task</li>play = task + hosts</li>
<li>playbook = plays</li>
<li>hosts/inventory = machines</li>
<li>vars/facts = variables - stored in a file or retrieved from a hostli>
<li>
* list - in json/yaml, array in powershell</li>
<li>dictionary - in json/yamal = hashtable in powershell</li>
</ul>
<h2 id="ansible-playbook-command-lineansible-playbook command line</h2>
<pre><code>

ansible-playbook [options] playbook.yml 
--step : confirmation before each task
--limit : ignore inventory file/group , against specified machines
-v(vvvv) : 
-e : extra variable individially or @filename
--check : run but won't make any change
</code></pre>
<h1 id="module-development">3. module development</h1>
<h2 id="module-search-pathmodulesearch path</h2>
<ul>
<li>
* module name  - test_module.py or test_module.sh or test_module.what</li>
<li>
* search path -</li>
</ul>
<ol>
<li>env var : ANSIBLE_LIBRARY;</li>
<li>command line option : --module-path</li>
<li>“./library”</li>
</ol>
<ul>
<li>boilerplate</li>
</ul>
<pre><code>def main():
  module = AnsibleModule(
    argument_spec = dict( input = dict(required=True) , ),
    supports_check_mode = False
  )
  from ansible.module_utils.basic import *
  main()

</code></pre>
<p>```
ansible will generate code from that template:<br>
about 1600 lines code, copy to the target system, execute it.</p>
<ul>
<li>argument_spec is a dict, and get populated by the parameter provided in YAML file.</li>
</ul>
<p>has three parameters:</p>
<ol>
<li>argument_spec= dict(),<pre><code>   mandatory_var = dict(required = True),
   mandatory_var_not_logged = dict(required =True, no_log = True )
   mandatory_var_with_3_options = dict(choices=[1,2,3])
   optional_var1=dict(),
   optional_var2=dict(),
   optional_var3=dict(),
   optional_var_with_default=dict( default='blaar),
   optional_var_with_type_check=dict(required=True, type='bool'),
   optional_var_with_alias=dict(required=True, aliases=['whatever']),
</code></pre>
</li>
</ol>
<pre><code>   
- name: Test Module Development
  hosts: localhost
  gather_facts: False
  tasks:
  - name: Test Module
    test_module:
      mandatory_var: value1
</code></pre>
<ol start="2">
<li>required_one_of = [[]],</li>
<li>
3. mutually_exclusive = [[]]</li>
</ol>
<h1 id="ansible-ad-hoc">4. ansible ad-hoc</h1>
<pre><code>
* get paransible-doc

# list connection
ansible-doc -t connection -l
# module-name args
ansible -m copy -a "src=/etc/hosts dest=/tmp/hosts" --check --diff localhost

</code></pre>
<h1 id="ansible-playbook">5. ansible playbook</h1>
<h2 id="format">format</h2>
<pre><code># two layer:
---   # indicator start of yaml
-     # list symbol
play  # layer 1
task  # layer 2

</code></pre>
<p>example</p>
<pre><code>#playbook.ymml
hosts: localhost
tasks:
- copy:
    src: "/etc/hosts"
    dest: "/tmp/hosts"
</code></pre>
<ul>
<li>short hand - put them in one line</li>
</ul>
<pre><code>#playbook.ymml
hosts: localhost
tasks:
- copy:    src: "/etc/hosts"    dest: "/tmp/hosts"
</code></pre>
<p>ansible-playbook playbook.yml</p>
<pre><code>---

- name: this is the first playbook
  gather_facts: no
  hosts: localhost
  tasks:
  - copy: src="/etc/hosts" dest="/tmp/hosts"
</code></pre>
<h2 id="yaml-syntax">yaml syntax</h2>
<ul>
<li>list</li>
</ul>
<pre><code>fruits:
- apple
- orange
- mango
</code></pre>
<ul>
<li>dictionary</li>
</ul>
<pre><code>martin:
 name: Martin dev
 job: developer
 skill: elite
</code></pre>
<ul>
<li>value can span multiple line with pipe | or great than &gt;> (indentation will be ignored)</li>
</ul>
<ol>
<li>pipe - will keep the new line and any trailing space</li>
<li>great than  will fold newline to spaces</li>
</ol>
<h2 id="ansible-configure-file"> 

## ansible configure file</h2>
<p>

search order</p>
<ul>
<li>
* ANSIBLE_CONFIG - env variable</li>
<li>
* ansible.cfg - in current directory (will not load if the folder is writable)</li>
<li>~/.ansible.cfg - in home dir</li>
<li>/etc/ansible/ansible.cfg</li>
</ul>
<p>

options in config file:</p>
<ul>
<li>ansible_connection=local</li>
<li>ansible_connection=winrm</li>
<li>
* ansible_port=5555</li>
<li>
* ansible_password</li>
<li>ansible_winrm_transport: basic</li>
</ul>
<h2 id="inventory">inventory</h2>
<p>conbe written in ini or yaml format<br>
no standard ssh port : <a href="http://webserver.com:2222">webserver.com:2222</a><br>
ansible glob pattern - range: www[1:5] , db-[a:f]<br>
set connect type and user on a per host basis: <a href="http://node1.mydomain.com">node1.mydomain.com</a> ansible_connection=winrmansible_user=admin</p>
<h3 id="apply-variable-to-a-group-of-hosts">apply variable to a group of hosts</h3>
<pre><code>
```
[bad_group]
node1 
node2

[bad_group:vars]
ntp_server=ntp1.mydomain.com
proxy=proxy1.mydomain.com


</code></pre>
<h3 id="two-default-group">two default group</h3>
<ol>
<li>all</li>
<li>ungrouped</li>
</ol>
<h3 id="inventory-plugin">inventory plugin</h3>
<p>plugin - support dynamic list from azure, aws, …</p>
<pre><code># to list available inventory plugins
ansible-doc -t inventory -l

#list aansible module
ansible-doc -l

list parameters of a module
ansible-doc -s module_name
</code></pre>
<p>without specifying inventory file, can only use localhost<br>
different inventory file type:</p>
<ol>
<li>py -</li>
<li>ini -</li>
<li>yml -</li>
</ol>
<pre><code># to get the inventory ignore extensions - .orig, .ini, .cfg, .retry
ansible-config list

# to list all inventoransible-inventory --list

# tree view of inventory
ansible-inventory --graph
</code></pre>
<h2 id="ansbile-face">ansbile face</h2>
<pre><code>
ansible node1 -m setup

# write facts to a file

- name: writes to a file named 
  host: node1
  become: true
  remote_user: root
  tasks:
  - name:
    copy :
      dest: /tmp/facts.txt
      content: "{{ansible_all_ipv4_addresses}}  {{}}"

</code></pre>
<h1 id="ansible-variables">ansible variables</h1>
<h1 id="window">8. window</h1>
<pre><code>#check ps version

$PSVersionTable

# winrm

## winrm listener

## winrm service configuration

### configureRemotingForAnsible.ps1  in ansible repo
setup http/https listeners with a self-signed certificate and baisc authentification

winrm get winrm/config
winrm set winrm/config/service @{AllowUnencrypted="true"}

# not work: 
winrm set winrm/config/service/auth @{Basic="true"}

# work (network profile set to private )
set-item -Force WSMan:\localhost\Service\AllowUnencrypted $True

# www.guruoye.net



</code></pre>
<pre><code>#window inventory

[windows]
win10

[windows:vars]
ansible_user=xxx
ansbile_password=xxx
ansible_port=5986
ansible_connection=winrm
ansible_winrm_server_cert_validation=ignore

</code></pre>
<p>```

ansible -m win_ping all</p>
<p>

ansible windows -i hosts -m facts</p>
<p>

ansible windows -i hosts -m win_chocolatey -a “name=notepadplusplus state=present”</p>
<pre><code>



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



</code></pre>
<h3 id="manage-windows-like-linux-with-ansible">manage windows like Linux with Ansible</h3>
<p>
win modules</p>
<ul>
<li>
<p>win_chocolatey!</p>
</li>
<li>
<p>win_package</p>
</li>
<li>
<p>not win_msi</p>
</li>
<li>
<p>win_dsc</p>
</li>
<li>
<p>win_reboot - reboot and wait for connection</p>
</li>
<li>
<p>wait_for_connection - second half of the reboot</p>
</li>
<li>
<p>
* win_updates - category_names, reboot, blacklist</p>
</li>
<li>
<p>win_iis_website</p>
</li>
<li>
<p>win_iis_webapp</p>
</li>
<li>
<p>win_regedit - individual key/value</p>
</li>
<li>
<p>
* win_regmerge - bulk import</p>
</li>
<li>
<p>win_service -</p>
</li>
<li>
<p>win_domain - create domain, join,</p>
</li>
<li>
<p>win_dns_client - change dns server</p>
</li>
<li>
<p>
* win_owner - set owner</p>
</li>
<li>
<p>win_acl -</p>
</li>
</ul>
<h3 id="ansible-for-the-windows-admin">Ansible for the windows admin</h3>
<h1 id="best-practice">



# 9. best practice</h1>
<p>

consist style</p>
<ul>
<li>tagging</li>
<li>whitespace</li>
<li>name of tasks, plays, vairables, roles</li>
<li>
* directory layout</li>
</ul>
<pre><code>


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
eyJoaXN0b3J5IjpbLTE1NzQ3NDM1MTRdfQ==
-->