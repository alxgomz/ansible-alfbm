# Alfresco benchmark playbook

This ansible playbook allows one to easily deploy an Alfresco benchmark infrastructure on multiple servers.

## Requirements

### Software requirement

You of course need Ansible in order to use this playbook.
The playbook has been written and tested with Ansible 2.2 and 2.4. If using Ansible <2.4, some non-core modules are needed:

 * ansible-xml by cmprescott (requires python-lxml on remote end) # part of Ansible core since 2.4

This modules has been added to the playbook but you may want to remove it if using Ansible >=2.4 in order to benefit from the latest code for this module (remove it from the /library folder).

### Architectural requirement

 - ***This playbook doesn't deploy SSH keys so please make sure you're using it on nodes that already have the needed SSH keys.***
 - ***At the moment the target hosts need to have direct acces to internet as we are using public repos.***
 - All names used in the inventory file need to be fully qualified DNS names resolvable by all hosts.

## How to use:

Edit the _inventory_ file and add your (FQDN) hostnames to the appropriate section. If you don't understand the roles of each server, you should probably start reading [Derek Huley's documentation](https://github.com/AlfrescoBenchmark/alfresco-benchmark/tree/master/docs) about the [Alfresco benchmark framework](https://github.com/AlfrescoBenchmark).

To start using the playbook simply start it with:

```
$ ansible-playbook -i inventory alfbm.yml
```

If you're loging in as a normal user and need to "sudo", use the command bellow:

```
$ ansible-playbook -i inventory alfbm.yml -b -K
```

If some options need to be changed (e.g. java or tomcat version, etc...), edit the group_vars/all file or the host_vars/<HOSTNAME> if the variable is host specific.

If you need to check what selenium is doing with the browser, you need to:

 - Spawn a VNC server on the load driver where you need to see what's hapenning:

```
$ Xvnc :0 -SecurityTypes=None 
```

 - You should now be able to attach to the VNC server using any vnc client on display :0 (or by default port 5900).

## TODO

 * Make it possible to download software from the Ansible machine instead of target machine (in case target cannot access internet).
 * Allow Oracle JDK usage
 * Allow non-key based play of the book
 * automate VNC server attachment to the virtual X server to be able to see what selenium actually doing headless
 * Use ansible maven module instead of using the ugly URL download

