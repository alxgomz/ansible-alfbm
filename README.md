# Alfresco benchmark playbook

This ansible playbook allows one to easily deploy an Alfresco benchmark infrastructure on multiple servers.

## Requirements

The playbook has been written and tested with Ansible 2.2. Some additionnal modules have been added to the playbook:

 * ansible-xml by cmprescott (requires python-lxml on remote end)
 * selenium

At the moment the target hosts need to have direct acces to internet as we are using public repos.

## How to use:

Edit the _inventory_ file and add your hosts to the appropriate section. If you don't understand the roles of each server, you should probably start reading [Derek Huley's documentation](https://github.com/AlfrescoBenchmark/alfresco-benchmark/tree/master/docs) about the [Alfresco benchmark framework](https://github.com/AlfrescoBenchmark).

## TODO

 * Make it possible to download software from the Ansible machine instead of target machine (in case target cannot access internet).
 * Allow Oracle JDK usage
 * RedHat like environments
