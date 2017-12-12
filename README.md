<h1><b>SAS Viya Infrastructure Resource Kit (VIRK) - Home Directory Playbook</b></h1>

<h2>Introduction</h2>

This playbook verifies and possibly performs the changes needed for home directory creation by SAS Authentication
This playbook is for SAS 9 or Viya 3.3
Pre-requisites for running the Home Directory playbook

<h2>Before running this script you will need to:</h2>

Install ansible. Version 2.3.2 is recommended for deployment.
Make sure the user has sudo prvilileges
Be aware that the scripts makes modifications to the system when not run with the --check option.
The base inventory file that we've provided contains only localhost and will only run on the machine on which it was installed. To run the playbook against multiple machines you can update the inventory file to include additional hosts. See Ansible Documentation for how-to.
For SAS 9, SAS should be set for PAM authentication in sasauth.conf, /etc/pam.d/system-auth copied to sasauth. You should not use a softlink for sasauth in /etc/pam.d either

</a><h2>Running the script</h2>

To run the script, execute on the command line:

ansible-playbook gel.homedirectory.yml -i inventory
Useful optional arguments

<ul>
<li><code>--check</code>: Executes a "dry run" of the playbook. Runs the playbook without making changes to the system. Any module instrumented to support ‘check mode’  will report what changes they would have made rather than making them.</li>
<li><code>-v through -vvvv</code>: Allows you to increase the verbosity of the script output; -vvvv enables connection debugging.</li>
<li><code>-i &lt;host-inventory-file&gt;</code>: Allows use of a different host inventory file instead of the default /etc/ansible/host file.</li>
<li><code>--tags &lt;tag-name&gt;</code>: Runs only task(s) with specific tag(s)</li>
<li><code>--skip-tags &lt;tag-name&gt;</code>: Skip task(s) with specific tag(s)</li>
<li><code>--list-tasks</code>: Display all tags in a playbook</li>
</ul>

</a><h2>Support</h2>

While SAS Tech Support will not provide support for the content of VIRK, issues and/or pull requests in GitHub are welcome.

</a><h2>Index of tags for individual requirement checks within the playbook</h2>


<p>To see a list of tasks you can run:</p>
<
><code>ansible-playbook gel.homedirectory.yml -i inventory --list-tasks
</code></pre>
<p>Example running only a specific check or configuration:</p>
<pre><code>ansible-playbook gel.homedirectory.yml -i inventory --tags memory_check
</code></pre>
<p>These specific tags run the code that perform the home directory configuration checks and changes:</p>
<ul>
<li>service</li>
<li>script</li>
<li>authfilemodif</li>

