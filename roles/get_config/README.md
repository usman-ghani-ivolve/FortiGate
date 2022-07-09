Role Name
=========

This role fetch information about router.

Requirements
------------

- FortiSO collection must be installed, use: ansible-galaxy collection install fortinet.fortios
- ansible>=2.9.0

Role Variables
--------------
:warning:	**Do not change values of written in italic.**

| Variables                      	|  Type  	|       Value      	| Comments                                                                                                                                                                                                	|
|--------------------------------	|:------:	|:----------------:	|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| ansible_network_os             	| string 	|     _fortios_    	|                                                                                                                                                                                                         	|
| ansible_httpapi_use_ssl        	|  bool  	|      _true_      	|                                                                                                                                                                                                         	|
| ansible_httpapi_validate_certs 	|  bool  	|      _false_     	|                                                                                                                                                                                                         	|
| ansible_httpapi_port           	|   int  	|       _443_      	|                                                                                                                                                                                                         	|
| config_selector                	| list   	| system_interface 	| List of configuration parameters to fetch. Refer this link to find more: https://docs.ansible.com/ansible/latest/collections/fortinet/fortios/fortios_configuration_fact_module.html#parameter-selector 	|

Example Playbook
----------------
A reference playbook with required variables for this role.

    ---
    - hosts: fortigate-01        
      roles:
        - role: get_config
          vars:
            ansible_network_os: 'fortios'
            ansible_httpapi_use_ssl: yes
            ansible_httpapi_validate_certs: no
            ansible_httpapi_port: 443
            config_selector: ["firewall_policy","firewall_vip"]