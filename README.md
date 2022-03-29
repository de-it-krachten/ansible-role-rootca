[![CI](https://github.com/de-it-krachten/ansible-role-rootca/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-rootca/actions?query=workflow%3ACI)


# ansible-role-rootca

Provisions list of rootCA SSL certificates


Platforms
--------------

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- CentOS 7
- RockyLinux 8
- AlmaLinux 8<sup>1</sup>
- Debian 10 (Buster)
- Debian 11 (Bullseye)
- Ubuntu 18.04 LTS
- Ubuntu 20.04 LTS

Note:
<sup>1</sup> means no automated testing is performed on these platforms

Role Variables
--------------
<pre><code>
# List of root certificate files
rootca_certificates: []

# Url to be used for testing
rootca_test_url: ''

# Should we fail if the test fails?
rootca_test_fail: true
</pre></code>


Example Playbook
----------------

<pre><code>
- name: sample playbook for role 'rootca'
  hosts: all
  vars:
    rootca_certificates: ['tests/root1.crt', 'tests/root2.pem']
  tasks:
    - name: Include role 'rootca'
      include_role:
        name: rootca
</pre></code>
