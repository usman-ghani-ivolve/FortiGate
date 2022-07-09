Role Name
=========

This role configure nat on router.

Requirements
------------

- FortiSO collection must be installed, use: ansible-galaxy collection install fortinet.fortios
- ansible>=2.9.0

Role Variables
--------------
:warning:	**Do not change values of written in italic.**

| Variables                      	|  Type  	|                 Value                 	| Comments                                                      	|
|--------------------------------	|-------	|---------------------------------------	|---------------------------------------------------------------	|
| ansible_network_os             	| string 	|               _fortios_               	|                                                               	|
| ansible_httpapi_use_ssl        	|  bool  	|                 _true_                	|                                                               	|
| ansible_httpapi_validate_certs 	|  bool  	|                _false_                	|                                                               	|
| ansible_httpapi_port           	|   int  	|                 _443_                 	|                                                               	|
| id                             	| int    	| 10                                    	| Firewall Policy ID                                            	|
| srcintf                        	| list   	| ["name": "port3, "name": "port1"]     	| 'name' key doesn't change in entire list. Only value changes. 	|
| dstintf                        	| list   	| ["name": "port1"]                     	|                                                               	|
| srcaddr                        	| list   	| ["name": "all"]                       	|                                                               	|
| dstaddr                        	| list   	| ["name": "all"]                       	|                                                               	|
| service                        	|        	| ["name": "ALL"]                       	|                                                               	|
| schedule                       	|        	| always                                	|                                                               	|
| action                         	|        	| add \| configure \| enable \| disable 	|                                                               	|

Example Playbook
----------------
A reference playbook with required variables for this role.

    ---
    - hosts: fortigate-01        
      roles:
        - role: nat
          vars:
            ansible_network_os: 'fortios'
            ansible_httpapi_use_ssl: yes
            ansible_httpapi_validate_certs: no
            ansible_httpapi_port: 443
            id: "50"
            srcintf:  ["name": "port1"]
            dstintf: ["name": "port3"]
            srcaddr: ["name": "all"]
            dstaddr: ["name": "webserver vips"]
            service: ["name": "ALL"]
            schedule: "always"
            action: "add"
