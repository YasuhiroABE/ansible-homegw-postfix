YasuhiroABE.homegw-postfix
=========

This role sets up postfix and maildrop package for my gateway router.

The aim of this role is to relay mail from the internal network to the relay host and to accept mail from external host to this gateway host.

This role expects the host has the static ip address on both external and internal network interfaces.

Requirements
------------

This role is tested on the following platforms.

### Ansible
- Version 2.4

### Distributions
- Ubuntu 16.04
- Debian 9

Role Variables
--------------

### Default
    ## host ip address and netmask preffix for external and internal
	homegw_postfix_external_hostprefix: 172.16.0.1/24
	homegw_postfix_internal_hostprefix: 192.168.0.1/24

	## hostname and domain of global ip address
	homegw_postfix_external_hostname: 'www'
	homegw_postfix_external_domainname: 'ext.example.org'

	## hostname and domain of internal-private ip address
	homegw_postfix_internal_hostname: 'homegw'
	homegw_postfix_internal_domainname: 'example.org'

	## External SMTP server for mail relay.
	homegw_postfix_relayhost: smtp.example.org
	
Dependencies
------------

1. This role uses maildrop package for local mail delivery as MUA.

2. Listen 25 port on both internal and external IP address.

Example Playbook
----------------

    - hosts: all
	  vars:
    	homegw_postfix_external_hostprefix: 172.16.0.1/24
		homegw_postfix_internal_hostprefix: 192.168.0.1/24

		## hostname and domain of global ip address
		homegw_postfix_external_hostname: 'www'
		homegw_postfix_external_domainname: 'ext.example.org'

		## hostname and domain of internal-private ip address
		homegw_postfix_internal_hostname: 'homegw'
		homegw_postfix_internal_domainname: 'example.org'

		## External SMTP server for mail relay.
		homegw_postfix_relayhost: smtp.example.org
	  roles:
	  
License
-------

Apache License 2.0

Author Information
------------------

[Yasuhiro ABE](http://www.yasundial.org/foaf.xml)
