puppet_agent
============

Ansible role which installs and configures Puppet Agent.

The configuration of the role is done in such way that it should not be necessary
to change the role for any kind of configuration. All can be done either by
changing role parameters or by declaring completely new configuration as a
variable. That makes this role absolutely universal. See the examples below for
more details.

Please report any issues or send PR.


Examples
--------

```yaml
---

- name Example of how to use the role with default parameters
  hosts: myhost1
  vars:
    puppet_agent_server: 
    puppet_agent_environment: 
  roles:
    - puppet_agent

- name Example of how to customize the role
  hosts: myhost2
  vars:
    puppet_agent_config:
      # This is the section name
      agent:
        # This is the parameter in the "agent" section
        server: puppet.example.com
        environment: test
  roles:
    - puppet_agent
```


Role variables
--------------

List of variables used by the role:

```yaml
# Puppet version
puppet_agent_version: 6

# YUM repo URL
puppet_agent_yum_repo_url: http://yum.puppetlabs.com/puppet{{ puppet_agent_version }}/el/{{ ansible_facts.distribution_release }}/$basearch

# YUM repo GPG key
puppet_agent_yum_repo_gpgkey: https://yum.puppetlabs.com/RPM-GPG-KEY-puppet

# Package to be installed
puppet_agent_pkg: puppet-agent

# Service name
puppet_agent_service: puppet

# Main config file path
puppet_agent_config_file: /etc/puppetlabs/puppet/puppet.conf

# Final config
puppet_agent_config: {}
```



Dependencies
------------

- [`config_encoder_filters`](https://github.com/jtyr/ansible-config_encoder_filters)


License
-------

MIT


Author
------

Jiri Tyr
