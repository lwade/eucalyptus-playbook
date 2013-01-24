This is a placeholder for Eucalyptus Ansible playbooks. Work in progress! :) Requires Ansible 0.9 for the ec2 module. 

# Eucalyptus Core Playbook

This is currently named eucalyptus.yml in the master branch (check testing for the bleeding edge stuff).  At the moment it only deploys the NC.

Assuming your systems are configured to use sudo and your userid is added to the sudoers file with full superuser permissions, along with your ssh public key on the servers, run with:

	 ansible-playbook eucalyptus.yml --private-key=/home/<me>/.ssh/<mykey> -s --ask-sudo-pass

The playbook currently only installs an NC.  It uses a hosts group "nc", ensure this is declared in /etc/ansible/hosts before running (or edit it out).  Future revisions will rely on tags for Eucalyptus components.

# Eucalyptus User Console Playbook

This is named eucalyptus-userconsole.yml and uses the Ansible EC2 module to go and launch an instance in Euca/EC2 and then install and configure the Eucalyptus User Console

euca2ools are a dependency for ec2 module and it is run locally like so (assuming you have [local]localhost defined in /etc/ansible/hosts):

	ansible-playbook eucalyptus-userconsole.yml -v --private-key=YOUR_INSTANCE_PRIVATE_KEY

If you're using an Ubuntu image, edit the user line in the playbook's second section so that the login is as "ubuntu" rather than root.

# Eucalyptus Reporting Playbook

This is named eucalyptus-reporting-ec2.yml and again uses the Ansible EC2 module to go and launch an instance in Euca/EC2 and configure the Eucalyptus Reporting Archive (Data Warehouse)

	ansible-playbook eucalyptus-reporting-ec2.yml -v --private-key=YOUR_INSTANCE_PRIVATE_KEY

# Cloud credentials for workload deployment (see examples dir).  Ensure the following environmental variables are set:

access_key: ACCESSKEYHERE
secret_key: SEEKRITKEYHERE
ec2_url: http://<euca-clc-ip>:8773/services/Eucalyptus



