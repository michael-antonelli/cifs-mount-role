# cifs-mount-role

This repo is for creating a series of simple ansible roles to mount a remote CIFS share on a RedHat or Ubuntu machine. Use the extra-vars.yml file to fill in the specific information about your mount point, add your hosts to the hosts file and then launch playbook.yml from the command line passing the hosts and exta-vars:

$ ansible-playbook -i hosts playbook.yml -e '@extra-vars.yml' 
