Balloon Infra Setup
===================

Client Ansible Setup
--------------------

The envvar ANSIBLE_CONFIG points towards an ansible config file which itself
points onwards to client-specific code libraries, data, etc. You can manage
this envvar manually, or you can use the following tool & process.

### Setup for boxen users

Add the relevant client project(s) to your personal manifest and run `boxen`.

eg. add `include projects::marks-and-spencer`


### Manual setup

* Get `activate-ansible`:
    * `git clone git@github.com:balloon-studios/balloon-infra.git $HOME/balloon/balloon/config-mgmt`
    * `mkdir -p $HOME/bin`
    * `ln -s $HOME/balloon/balloon/config-mgmt/bin/activate-ansible $HOME/bin/`
    * add `$HOME/bin` to your `$PATH` in your shell setup
* For each client using this setup:
    * `mkdir -p $HOME/balloon/<CLIENT>`
    * `git clone <CLIENT-INFRA-REPO> $HOME/balloon/<CLIENT>/config-mgmt`
    * `ln -s $HOME/bin/activate-ansible $HOME/balloon/<CLIENT>/`
    * `ln -s $HOME/balloon/<CLIENT> $HOME/<CLIENT>` (optional step, for convenience, and is used below)


### Using

To assume the role of a person using $CLIENT's ansible setup:

`user$ . ~/<CLIENT>/activate-ansible`

Now ansible will use the roles defined inside
`~/balloon/CLIENT/config-mgmt/roles`. Playbooks and inventories still have to be
referenced fully, but this shouldn't be onerous.
