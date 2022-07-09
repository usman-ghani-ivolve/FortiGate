Role Name
=========

This role configure Elastic IP on router.

Requirements
------------

- FortiSO collection must be installed, use: ansible-galaxy collection install fortinet.fortios
- ansible>=2.9.0

Role Variables
--------------
:warning:	**Do not change values of written in italic.**

| Variables                      	|  Type  	|     Value     	| Comments                         	|
|--------------------------------	|:------:	|:-------------:	|----------------------------------	|
| ansible_network_os             	| string 	|   _fortios_   	|                                  	|
| ansible_httpapi_use_ssl        	|  bool  	|     _true_    	|                                  	|
| ansible_httpapi_validate_certs 	|  bool  	|    _false_    	|                                  	|
| ansible_httpapi_port           	|   int  	|     _443_     	|                                  	|
| id                             	| int    	|       1       	| Fortigate Virtual IP ID          	|
| extip                          	| string 	|  10.82.21.201 	| value range: 10.82.21.201 - 210  	|
| mappedip                       	| string 	|  192.168.1.2  	| Private IP Adress assigned to VM 	|
| extintf                        	| string 	|    _port1_    	| WAN Port of Fortigate            	|
| action                         	| string 	| add \| remove 	| Add or remove Elastic IP         	|

Example Playbook
----------------
A reference playbook with required variables for this role.

    ---
    - hosts: fortigate-01        
      roles:
        - role: elastic_ip
          vars:
            ansible_network_os: 'fortios'
            ansible_httpapi_use_ssl: yes
            ansible_httpapi_validate_certs: no
            ansible_httpapi_port: 443
            id: "5"
            extip: "10.82.6.21"
            mappedip: "192.168.1.2"
            extintf: "port1"
            action: "add"