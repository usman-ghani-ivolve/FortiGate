Bootstrap
=========

This role bootstrap router with **default** configurations.

Requirements
------------

- FortiSO collection must be installed, use: ansible-galaxy collection install fortinet.fortios
- ansible>=2.9.0 must be installed, use: pip install ansible==2.10

Role Variables
--------------
:warning:	**Do not change values of written in italic.**

| Variables                      	|  Type  	|                   Value                  	|
|--------------------------------	|:------:	|:----------------------------------------:	|
| ansible_network_os             	| string 	|                 _fortios_                	|
| ansible_httpapi_use_ssl        	|  bool  	|                  _true_                  	|
| ansible_httpapi_validate_certs 	|  bool  	|                  _false_                 	|
| ansible_httpapi_port           	|   int  	|                   _443_                  	|
| tenant_id                      	| string 	|                  0000001                 	|
| public_key                     	| string 	| ssh-rsa 5KByH6B+= ubuntu@DESKTOP-5LGD9J0 	|
| admin_password                 	| string 	|                  letmein                 	|
| wan_ip                         	| string 	|              _10.82.21.200_              	|
| wan_subnet                     	| string 	|               _255.255.0.0_              	|
| wan_gateway                    	| string 	|               _10.82.1.250_              	|
| mgmt_ip                        	| string 	|                _10.0.0.50_               	|
| mgmt_gateway                   	| string 	|                _10.0.0.1_                	|
| mgmt_subnet                    	| string 	|              _255.255.255.0_             	|
| lan_ip                         	| string 	|               192.168.1.254              	|
| lan_subnet                     	| string 	|               255.255.255.0              	|
| dhcp_start                     	| string 	|                192.168.1.2               	|
| dhcp_end                       	| string 	|               192.168.1.253              	|
| dns_server                     	| string 	|                  8.8.4.4                 	|
| ntp_server                     	| string 	|                  0.0.0.0                 	|

Example Playbook
----------------
A reference playbook with required variables for this role.

    ---
    - hosts: fortigate-01        
      roles:
        - role: bootstrap
          vars:
            ansible_network_os: 'fortios'
            ansible_httpapi_use_ssl: yes
            ansible_httpapi_validate_certs: no
            ansible_httpapi_port: 443
            tenant_id: "000000"
            public_key: "ssh-rsa AAAAB3NzaC1yMph2Noy4jCutI9Vkc= ubuntu@DESKTOP-5LGD9J0"
            admin_password: "letmein"
            wan_ip: "10.82.21.200"
            wan_subnet: "255.255.0.0"
            wan_gateway: "10.82.1.250"
            mgmt_ip: "10.0.0.50"
            mgmt_gateway: "10.0.0.1"
            mgmt_subnet: "255.255.255.0"
            lan_ip: "192.168.1.254"
            lan_subnet: "255.255.255.0"
            dhcp_start: "192.168.1.10"
            dhcp_end: "192.168.1.253"
            dns_server: "8.8.8.8"
            ntp_server: "0.0.0.0"