# cifs-mount-role
This repository contains an ansible role for mounting remote CIFS shares on RedHat and Debian distros.

### Variables
Variables to set in `extra-vars.yml` before running:
- `host_group: ''` - just the name of the square-bracketed host group in the `hosts` file you wish to work on

- `mount_point: ''` - the explicit path of the mount point

- `share_name: ''` - UNC for the share

- `file_mode: ''` - octal ffile posix permission eg. 0755

- `dir_mode: ''` - octal directory posix permission eg. 0755

Example ansible cli command:

`ansible-playbook -i hosts --extra-var '@extra-vars.yml' playbook.yml --ask-vault-pass`
