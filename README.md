[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

# ansible-role-cloudhealth

## Requirements

This module requires `httplib2` to be installed on the host machine. It can be
installed via `apt-get` (`sudo apt-get install python-httplib2`) or via `pip`
(`sudo pip install httplib2`) if not available in the distribution package
manager.

## Role Variables

### `cloudhealth_api_key`

The `cloudhealth_api_key` is used to identify yourself to our API. This
variable is **required**.

Go to the [Ansible Accounts](https://apps.cloudhealthtech.com/ansible_accounts)
page. If there is no accounts listed yet, create one by clicking on [*New
Account*](https://apps.cloudhealthtech.com/ansible_accounts/new).

Your API key will then be listed next to your account name on that [Ansible
Accounts](https://apps.cloudhealthtech.com/ansible_accounts)
page:

![Ansible Account API key](docs/ansible_account_api_key.png)

Define it in your playbooks like this:

```yaml
cloudhealth_api_key: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```

You can avoid to store your API key in your playbooks by setting it like this:

```yaml
cloudhealth_api_key: "{{ lookup('env','CLOUDHEALTH_API_KEY') }}"
```

Then, in your `~/.bashrc` file, add the following line and don't forget to
`source ~/.bashrc` or open a new terminal:

```bash
export CLOUDHEALTH_API_KEY=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```

Another option is to use
[Ansible Vault](http://docs.ansible.com/ansible/playbooks_vault.html) to store
the API key.

## Development environment

Start by setting your API key in an environment variable called
`CLOUDHEALTH_API_KEY`.

Then install [Vagrant](https://www.vagrantup.com/) and
[VirtualBox](https://www.virtualbox.org/) using your favorite package manager
and run:

```bash
vagrant up
```

This will spin up a minimal virtual machine and provision it with a test
playbook using that role.

If that step succeeds, syntax of the role is correct and all tasks are
successful on a bare machine.

To provision the virtual machine again, run the following:

```bash
vagrant up # Unnecessary if the VM is already running
vagrant provision
```

To run an ad-hocs command on that machine, for example to retrieve all facts
from it, run the following:

```bash
ansible all -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory -u vagrant --private-key .vagrant/machines/default/virtualbox/private_key -m setup
```

Once you are done with changes, you can run one of the following:

```bash
vagrant halt -f # Shuts down the VM for later re-use
vagrant destroy -f # Destroys the VM entirely
```
