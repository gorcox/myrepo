SAS Viya Infrastructure Resource Kit (VIRK) - Home Directory Playbook

Introduction

This playbook verifies and possibly performs the changes needed for home directory creation by SAS Authentication
This playbook is for SAS 9 or Viya 3.3
Pre-requisites for running the pre-installation playbook

Before running this script you will need to:

Install ansible. Version 2.3.2 is recommended for deployment.
Make sure the user has sudo prvilileges
Be aware that the scripts makes modifications to the system when not run with the --check option.
The base inventory file that we've provided contains only localhost and will only run on the machine on which it was installed. To run the playbook against multiple machines you can update the inventory file to include additional hosts. See Ansible Documentation for how-to.
For SAS 9, SAS should be set for PAM authentication in sasauth.conf, /etc/pam.d/system-auth copied to sasauth. You should not use a softlink for sasauth in /etc/pam.d either
Running the script

To run the script, execute on the command line:

ansible-playbook gel.homedirectory.yml -i inventory
Useful optional arguments

--check: Executes a "dry run" of the playbook. Runs the playbook without making changes to the system. Any module instrumented to support ‘check mode’ will report what changes they would have made rather than making them.
-v through -vvvv: Allows you to increase the verbosity of the script output; -vvvv enables connection debugging.
-i <host-inventory-file>: Allows use of a different host inventory file instead of the default /etc/ansible/host file.
--tags <tag-name>: Runs only task(s) with specific tag(s)
--skip-tags <tag-name>: Skip task(s) with specific tag(s)
--list-tasks: Display all tags in a playbook
Support

While SAS Tech Support will not provide support for the content of VIRK, issues and/or pull requests in GitHub are welcome.

Index of tags for individual requirement checks within the playbook

To see a list of tasks you can run:

ansible-playbook gel.homedirectory.yml -i inventory --list-tasks
Example running only a specific check or configuration:

ansible-playbook gel.homedirectory.yml -i inventory --tags packages
These specific tags run the code that perform the download of oddjob and configure sasauth: While there are multiple tags for organizing the playbook this playbook should most likely be run it its entirety.

packages
service
script
authfilemodif
