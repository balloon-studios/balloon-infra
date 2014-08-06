Balloon Infra Setup
===================

Client Ansible Setup
--------------------

The envvar ANSIBLE_CONFIG points towards an ansible config file which itself
points onwards to client-specific code libraries, data, etc. You can manage
this envvar manually, or you can use the following tool & process.

* Check out https://github.com/balloon-studios/balloon-infra into ~/balloon/balloon/config-mgmt/
* mkdir -p ~/bin ; ln -s ~/balloon/balloon/config-mgmt/activate-ansible ~/bin/
* For each ~/balloon/$CLIENT using this setup:
    * mkdir -p ~/balloon/CLIENT
    * git clone CLIENT-INFRA-REPO ~/balloon/CLIENT/config-mgmt
    * ln -s ~/bin/activate-ansible ~/balloon/CLIENT/
    * ln -s ~/balloon/CLIENT ~/CLIENT # (optional step, for convenience, and is used below)

Then, to assume the role of a person using $CLIENT's ansible setup:

`user$ . ~/<CLIENT>/activate-ansible`

Now ansible will use the roles defined inside
~/balloon/CLIENT/config-mgmt/roles. Playbooks and inventories still have to be
referenced fully, but this shouldn't be onerous.
