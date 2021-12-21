[![CI](https://github.com/de-it-krachten/ansible-role-rootca/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-rootca/actions?query=workflow%3ACI)


# ansible-role-rootca

Provisions list of rootCA SSL certificates


Platforms
--------------

Supported platforms

- CentOS 7
- CentOS 8
- Debian 10 (Buster)
- Debian 11 (Bullseye)
- Ubuntu 18.04 LTS
- Ubuntu 20.04 LTS



Role Variables
--------------
<pre><code>
# List of root certificate files
rootca_certificates: []
</pre></code>


Example Playbook
----------------

<pre><code>
- name: Converge
  hosts: all
  vars:
    rootca_certificates:
      - tests/root1.crt
      - tests/root2.pem
  tasks:
    - name: Include role 'ansible-role-rootca'
      include_role:
        name: ansible-role-rootca
</pre></code>
