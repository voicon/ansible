* ansible works

vi /etc/ansible/ansible.cfg

turn on host_key_checking = False by uncomment to not check key when ssh: ECDSA key fingerprint

set static ip for servers:

vi /etc/sysconfig/network-scripts/ifcfg-enp***

Add: IPADDR=192.168.xxx.xxx

systemctl restart network

** playbook.yml
-
  name: Play 1
  hosts: localhost
  tasks:
    - name: Execute command 'date'
      command: date
    - name: Execute script on server
      script: test.sh
-
  name: Play 2
  hosts: localhost
  tasks:
    - name: Install web service
      yum:
        name: httpd
        state: present
    - name: start web server
      service:
        name: httpd
        state: started

** modules: command, script, yum, service, ...

** ansible-playbook playbook.yml
*** ansible-playbook --help

