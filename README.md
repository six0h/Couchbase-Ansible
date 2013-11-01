Couchbase Ansible Playbook
===========================

This project contains sample playbooks to manage Couchbase cluster.
Note: the current scripts are only working on Ubuntu/Debian for now

Install Main Node
-----------------

###Initial Settings

Update the tasks/group_vars/all.yml file with any variables you'll need to make available to all playbooks.

###Install the main node for a cluster

Each inventory file in /inventories contains hostnames for each node. Each node will be configured to use this hostname for Couchbase. The hostname provided in [cbmain] will be the first node configured with a bucket.

###Provision the main node:
<pre>$ ansible-playbook -i inventories/$env tasks/couch-main.yml</pre>

$env == vagrant, staging, or production

Install as many additional nodes as you need
--------------------------------------------

In compliment to the main node, the hostnames specified in the [cbnode] section will be configured by this playbook. A Couchbase server will be installed and added to the cluster on all hosts listed in this file.

###To provision them:
<pre>$ ansible-playbook -i inventories/$env tasks/couch-node.yml</pre>


Uninstall Couchbase Cluster
---------------------------

Uninstall the Couchbase server and delete all files (Warning you will lose your data)


Run the Ansible command
<pre>
ansible-playbook -i ./hosts ./couchbase-uninstall.yml
</pre>

