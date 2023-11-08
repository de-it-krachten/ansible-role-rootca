[![CI](https://github.com/de-it-krachten/ansible-role-rootca/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-rootca/actions?query=workflow%3ACI)


# ansible-role-rootca

Provisions list of rootCA SSL certificates



## Dependencies

#### Roles
None

#### Collections
- ansible.windows
- ansible.windows

## Platforms

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- CentOS 7
- RockyLinux 8
- RockyLinux 9
- OracleLinux 8
- OracleLinux 9
- AlmaLinux 8
- AlmaLinux 9
- SUSE Linux Enterprise 15<sup>1</sup>
- openSUSE Leap 15
- Debian 11 (Bullseye)
- Debian 12 (Bookworm)
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Fedora 37
- Fedora 38
- Alpine 3
- Windows Server 2012 R2<sup>1</sup>
- Windows Server 2016<sup>1</sup>
- Windows Server 2019<sup>1</sup>
- Windows Server 2022<sup>1</sup>

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# List of root certificate files
rootca_certificates: []

# Url to be used for testing
rootca_test_url: ''

# Should we fail if the test fails?
rootca_test_fail: true
</pre></code>

### defaults/family-Debian.yml
<pre><code>
# File extention to use (pem/crt)
rootca_ext: crt

# Directory to place root certificates into
rootca_directory: /usr/share/ca-certificates/extra

# Command to execute to make OS import CA certificates
rootca_update_cmd: update-ca-certificates
</pre></code>

### defaults/family-Suse.yml
<pre><code>
# File extention to use (pem/crt)
rootca_ext: pem

# Directory to place root certificates into
rootca_directory: /etc/pki/trust/anchors

# Command to execute to make OS import CA certificates
rootca_update_cmd: update-ca-certificates
</pre></code>

### defaults/family-RedHat.yml
<pre><code>
# File extention to use (pem/crt)
rootca_ext: pem

# Directory to place root certificates into
rootca_directory: /etc/pki/ca-trust/source/anchors

# Command to execute to make OS import CA certificates
rootca_update_cmd: update-ca-trust
</pre></code>

### defaults/Alpine.yml
<pre><code>
# File extention to use (pem/crt)
rootca_ext: crt

# Directory to place root certificates into
rootca_directory: /usr/local/share/ca-certificates

# Command to execute to make OS import CA certificates
rootca_update_cmd: update-ca-certificates
</pre></code>

### defaults/Rocky.yml
<pre><code>
# File extention to use (pem/crt)
rootca_ext: pem

# Directory to place root certificates into
rootca_directory: /etc/pki/ca-trust/source/anchors

# Command to execute to make OS import CA certificates
rootca_update_cmd: update-ca-trust
</pre></code>

### defaults/family-Windows.yml
<pre><code>
# File extention to use (pem/crt)
rootca_ext: pem
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'rootca'
  hosts: all
  become: 'yes'
  vars:
    rootca_certificates:
      - tests/root1.crt
      - tests/root2.pem
  tasks:
    - name: Include role 'rootca'
      ansible.builtin.include_role:
        name: rootca
</pre></code>
