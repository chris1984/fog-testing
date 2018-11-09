# Fog-testing

Ansible role to do regression testing of fog-vsphere against Foreman

## Build Status

https://travis-ci.org/chris1984/fog-testing.svg?branch=master

## Requirements

* Python >= 2.6
* PyVmomi
* Ansible 2.7

## Role Variables

* Variables are all in role/defaults/main.yml

```yaml
---
hammer_user: Username for hammer
hammer_password: Password for hammer
hostgroup_id: Hostgroup ID
location_id: Location ID
org_id: Organization ID
cr_id: Compute Resource ID
cp_id: Compute Profile ID
ptable_id: Partition Table ID
fog_version: Fog version that you are testing with on Foreman
fogpatch_url: URL to GitHub Patch to download and test
revert_vm: Put true if you want to revert the VM snapshot after testing
vcenter_hostname: FQDN of vCenter
vcenter_username: vCenter username
vcenter_password: vCenter password
vcenter_datacenter: Datacenter in vCenter containing the VM
vcenter_folder: Folder path to VM
vcenter_vm_name: VM name
vcenter_snapshot_name: Name of snapshot to revert back to upon finish
```

## Example Playbook

```yaml
---
- name: Start fog-vsphere regression testing
  hosts: localhost
  become: true
  remote_user: root

  roles:
    - chris1984.fog_testing
```

### License

MIT

### Author Information

* Chris Roberts - chrobert@redhat.com  - https://www.linkedin.com/in/croberts84/
* Work at Redhat on the Foreman/Katello projects and also maintain fog-vsphere.