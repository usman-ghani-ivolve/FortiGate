Bootstrap
=========

This role configure DHCP.

Requirements
------------

- FortiSO collection must be installed, use: ansible-galaxy collection install fortinet.fortios
- ansible>=2.9.0

Role Variables
--------------
:warning:	**Do not change values of written in italic.**

| Variables                      	|  Type  	|                 Value                 	|                            Comments                           	|
|--------------------------------	|:------:	|:-------------------------------------:	|:-------------------------------------------------------------:	|
| ansible_network_os             	| string 	|               _fortios_               	|                                                               	|
| ansible_httpapi_use_ssl        	|  bool  	|                 _true_                	|                                                               	|
| ansible_httpapi_validate_certs 	|  bool  	|                _false_                	|                                                               	|
| ansible_httpapi_port           	|   int  	|                 _443_                 	|                                                               	|
| id                             	|   int  	|                   1                   	|                                                               	|
| interface                      	| string 	|                 port3                 	|                                                               	|
| default_gateway                	| string 	|             192.168.1.254             	|                                                               	|
| netmask                        	| string 	|             255.255.255.0             	|                                                               	|
| range_id                       	|   int  	|                   1                   	|                                                               	|
| start_ip                       	| string 	|              192.168.1.2              	|                                                               	|
| end_ip                         	| string 	|             192.168.1.253             	|                                                               	|
| dns_server1                    	| string 	|                8.8.8.8                	| If dns_server is not mentioned then set it's value to 0.0.0.0 	|
| dns_server2                    	| string 	|                8.8.4.4                	| If dns_server is not mentioned then set it's value to 0.0.0.0 	|
| dns_server3                    	| string 	|                0.0.0.0                	| If dns_server is not mentioned then set it's value to 0.0.0.0 	|
| dns_server4                    	| string 	|                0.0.0.0                	| If dns_server is not mentioned then set it's value to 0.0.0.0 	|
| ntp_server1                    	| string 	|              192.168.1.2              	| If ntp_server is not mentioned then set it's value to 0.0.0.0 	|
| ntp_server2                    	| string 	|                0.0.0.0                	| If ntp_server is not mentioned then set it's value to 0.0.0.0 	|
| ntp_server3                    	| string 	|                0.0.0.0                	| If ntp_server is not mentioned then set it's value to 0.0.0.0 	|
| lease_time                     	| string 	|                 864000                	|                                                               	|
| action                         	| string 	| add \| configure \| enable \| disable 	|                                                               	|

Example Playbook
----------------
A reference playbook with required variables for this role.

    ---
    - hosts: fortigate-01        
      roles:
        - role: dhcp
          vars:
            ansible_network_os: 'fortios'
            ansible_httpapi_use_ssl: yes
            ansible_httpapi_validate_certs: no
            ansible_httpapi_port: 443
            id: "1"
            interface: "port1"
            default_gateway: "192.168.1.254"
            netmask: "255.255.255.0"
            range_id: "1"
            start_ip: "192.168.1.2"
            end_ip: "192.168.1.253"
            dns_server1: "8.8.8.8"
            dns_server2: "8.8.4.4"
            dns_server3: "0.0.0.0"
            dns_server4: "0.0.0.0"
            ntp_server1: "0.0.0.0"
            ntp_server2: "0.0.0.0"
            ntp_server3: "0.0.0.0"  
            lease_time: "604800"
            action: "configure"