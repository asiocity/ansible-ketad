# Ansible Xishu Ketad Role

## Setup

### Requirements

- Ansible v2.10+
- When using Ansible on Windows, requires the `ansible.windows` collection to be installed:
  ```shell
  ansible-galaxy collection install ansible.windows
  ```

### Installation

Install from Ansible Galaxy:

```shell
ansible-galaxy install xishu.ketad
```

or just copy `xishu.ketad` role directory to `~/.ansible/roles/`

To deploy the Xishu Ketad on hosts, add the role, token, endpoints and other variables to your playbook:

```yaml
- hosts: servers
  roles:
    - { role: xishu.ketad, become: yes }
  vars:
    keta_url: "<YOUR_KETA_DB_URL>" # required, like: http://ketadb
    keta_token: "<YOUR_KETA_DC_TOKEN>" # required
    keta_endpoints: "<YOUR_KETA_DC_ENDPOINTS>" # required, like: ip1:port ip2:port
    keta_tags: "<YOUR_KETA_DC_TAGS>" # required
    keta_ketad_arch: "<YOUR_KETA_DC_ARCH>" # optional, default use host architecture
    keta_ketad_version: "<YOUR_KETA_DC_VERSION>" # optional, default use the lastest ketad
    keta_ketad_path: "<YOUR_KETAD_PATH>" # optional
    keta_ketad_boot: "<TRUE_OR_FALSE>" # optional, default false, only work with root user
    keta_region: "<YOUR_KETA_DC_REGION>" # optional
    keta_net_interface: "<YOUR_KETA_DC_NET_INTERFACE>" # optional
    keta_no_login: "<TRUE_OR_FALSE>" # optional, default false, only work with windows
```

You can use this `ansible-playbook` script like this:

```shell
# deploy
ansible-playbook installer.yaml

# host with password
ansible-playbook installer.yaml --ask-pass

# dry-run
ansible-playbook installer.yaml --check
```
