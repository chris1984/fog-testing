# Fog-testing

Ansible role to do regression testing of fog-vsphere against Foreman

## Build Status

[![Build Status](https://travis-ci.org/chris1984/fog-testing.svg?branch=master)](https://travis-ci.org/chris1984/fog-testing)

## Requirements

* Python >= 2.7
* PyVmomi
* Ansible 2.8
* vCenter 6.7
* ESXi 6.7

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
medium_id: Installation medium ID
os_id: Operating system ID
override_fog: Put true if you want to test a specfic version of fog-vsphere than on the machine
image_name: Name of the Image in Foreman
test_pr: Put true if running in PR test mode.
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
update_foreman: Put true if you want to perform a yum update * and then an installer run with the --upgrade flag
install_foreman: Put true if you want to perform a fresh install of Foreman and laydown the configs/databases instead of using a snapshot
vm_timeout: 567 # Configurable timeout for waiting before starting more VM creation tasks
downstream: Put true if this is a Red Hat Satellite 6 build to pull in internal bits
```

## Example Playbook

```yaml
---
- name: Start fog-vsphere regression testing
  hosts: localhost
  become: true
  remote_user: root
  gather_facts: no
  serial: 1

  roles:
    - chris1984.fog_testing
```

### License

MIT

### Author Information

* Chris Roberts - chrobert@redhat.com  - https://www.linkedin.com/in/croberts84/
* Work at Redhat on the Foreman/Katello projects and also maintain fog-vsphere.
