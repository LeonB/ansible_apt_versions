# Ansible apt_versions

This action modules creates a new ansible fact `apt_versions` and populates it
with a list of all installed packages + the version number in different formats.

You can use this module to weave logic in playbooks without executing `command`
or `shell` actions everywhere.

## Examples

``` yml
- name: Gather facts
  action: apt_versions

- name: Conditional
  action: debug msg="Apache version is > 2.2"
  when: apt_versions.apache2.simple > "2.2"
```

``` yml
- name: Gather apache2 version fact
  action: apt_versions name=apache2

- name: set apache2 simple version fact
  set_fact: apache_version={{apt_versions.apache2.simple}}
```

## List of variables

- `apt_versions.{{package}}.version`
- `apt_versions.{{package}}.major`
- `apt_versions.{{package}}.minor`
- `apt_versions.{{package}}.simple`
