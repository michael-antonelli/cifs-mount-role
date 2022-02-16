# cifs-mount-role
This repository contains an ansible role for mounting remote CIFS shares on RedHat and Debian distros.

### Hosts
Add the hosts you want to run this on to `hosts`. The default heading is `cif_mount_role`.

e.g.
```[cifs_mount_role]
servername.domain
```

### Secrets
Add secrets to the plaintext file `secrets/vault.yml` and then exncrypt that file using `ansible-vault`:
- `vault_share_password: ''` - The user's password

- `vault_share_username: ''` - The user with permission to mount the share

- `vault_uid: ''` - UID for the user specified above

Once this file has had the variable definitions added run `$ ansible-vault encrypt secrets/vault.yml` and select a password. This password will by typed when `playbook.yml` is run, or it can be placed in a credential file and passed to the `ansible-playbook` command with the `--vault-password-file` option. See [Ansible's Documentation](https://docs.ansible.com/ansible/latest/user_guide/vault.html#passing-a-single-password) for more details.

**THE MOUNT MODULE IS RUN WITH THE `no_log` OPTION SO IT WILL NOT PRINT SECRETS TO LOGS. IF YOU RUN THIS PLAYBOOK IN DEBUG MODE WITH THE `-vvv` FLAG THAT OPTION IS IGNORED AND SECRETS WILL BE PRINTED IN PLAINTEXT TO LOGS AND DEBUG OUTPUT. NEVER RUN THIS PLAY IN DEBUG MODE ON PRODUCTION WITH YOUR SECRETS!**

### Variables
Variables to set in `extra-vars.yml` before running:
- `host_group: ''` - just the name of the square-bracketed host group in the `hosts` file you wish to work on

- `mount_point: ''` - the explicit path of the mount point

- `share_name: ''` - UNC for the share

- `file_mode: ''` - octal ffile posix permission eg. 0755

- `dir_mode: ''` - octal directory posix permission eg. 0755


### Run
Example ansible cli command:

`$ ansible-playbook -i hosts --extra-var '@extra-vars.yml' playbook.yml --ask-vault-pass`
