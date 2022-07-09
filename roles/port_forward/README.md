Role Name
=========

This role configure port forwarding on router.

Requirements
------------

- FortiSO collection must be installed, use: ansible-galaxy collection install fortinet.fortios
- ansible>=2.9.0

Role Variables
--------------
:warning:	**Do not change values of written in italic.**

| Variables                      	|  Type  	|                 Value                 	| Comments                                                      	|
|--------------------------------	|:------:	|:-------------------------------------:	|---------------------------------------------------------------	|
| ansible_network_os             	| string 	|               _fortios_               	|                                                               	|
| ansible_httpapi_use_ssl        	|  bool  	|                 _true_                	|                                                               	|
| ansible_httpapi_validate_certs 	|  bool  	|                _false_                	|                                                               	|
| ansible_httpapi_port           	|   int  	|                 _443_                 	|                                                               	|
| id                             	| int    	| 10                                    	| Firewall Policy ID                                            	|
| extip                          	| string 	| 10.82.21.200                          	| 'name' key doesn't change in entire list. Only value changes. 	|
| extport                        	| string 	| 2222                                  	|                                                               	|
| mappedip                       	| string 	| 192.168.1.2                           	|                                                               	|
| mappedport                     	| string 	| 22                                    	|                                                               	|
| extintf                        	| string 	| port1                                 	|                                                               	|
| protocol                       	| string 	| tcp \| udp                            	|                                                               	|
| srcintf                        	| string 	| port1                                 	|                                                               	|
| dstintf                        	| string 	| port3                                 	|                                                               	|
| srcaddr                        	| string 	| all                                   	|                                                               	|
| action                         	| string 	| add \| configure                      	|                                                               	|

Example Playbook
----------------
A reference playbook with required variables for this role.

    ---
    - hosts: fortigate-01        
      roles:
        - role: port_forward
          vars:
            ansible_network_os: 'fortios'
            ansible_httpapi_use_ssl: yes
            ansible_httpapi_validate_certs: no
            ansible_httpapi_port: 443
            id: "1"
            extip: "20.30.40.50"
            extport: "3333"
            mappedip: "192.168.1.4"
            mappedport: "22"
            extintf: "port1"
            protocol: "tcp"
