Role Name
=========

This role configure site-to-site vpn on router.

Requirements
------------

- FortiSO collection must be installed, use: ansible-galaxy collection install fortinet.fortios
- ansible>=2.9.0

Role Variables
--------------
```
ansible_network_os
ansible_httpapi_use_ssl
ansible_httpapi_validate_certs
ansible_httpapi_port
tunnel_name
address
address_group
remote_gw
psksecret
p1_intf
ike_version
p1_proposal
dhgrp
negotiate_timeout
p2_proposal
firewall
```

Example Playbook
----------------
A reference playbook with required variables for this role.

    ---
    - hosts: fortigate-01        
      roles:
        - role: vpn
          vars:
            ansible_network_os: 'fortios'
            ansible_httpapi_use_ssl: yes
            ansible_httpapi_validate_certs: no
            ansible_httpapi_port: 443
            tunnel_name: "site-2-site"
            address: [ 
              {
                name: '{{ tunnel_name }}-local-1', 
                subnet: '192.168.0.0', 
                netmask: '255.255.255.0'
              }, 
              {
                name: '{{ tunnel_name }}-remote-1', 
                subnet: '192.168.100.0', 
                netmask: '255.255.255.0'
              } 
            ]
            address_group: [ 
              { 
                name: '{{ tunnel_name }}-local', 
                member: '{{ tunnel_name }}-local-1' 
              },
              { 
                name: '{{ tunnel_name}}-remote',
                member: '{{ tunnel_name }}-remote-1'
              } 
            ] #1st index local and 2nd index remote always
            remote_gw: "10.82.3.125"
            psksecret: "4b7d62f964784846a0e58e4f56245d30237e71dfc10b759066ab2f69"
            p1_intf: "port1"
            ike_version: "2"
            p1_proposal: ['aes128-sha256']
            dhgrp: "14"
            negotiate_timeout: 30
            p2_proposal: ['aes128-sha256', 'aes128gcm']
            firewall: [ 
              {
                id: '20', 
                name: '{{ address_group[0].name }}',
                srcintf: 'port3',
                dstintf: '{{ tunnel_name }}',
                srcaddr: '{{ address_group[0].name }}',
                dstaddr: '{{ address_group[1].name }}'
              },
              {
                id: '21',
                name: '{{ address_group[1].name }}',
                srcintf: '{{ tunnel_name }}',
                dstintf: 'port3',
                srcaddr: '{{ address_group[1].name }}',
                dstaddr: '{{ address_group[0].name }}'
              }
            ]