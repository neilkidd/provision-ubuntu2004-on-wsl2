# Provision Ubuntu 2004 on WSL2

Automating provisioning Ubuntu 20.04 with Ansible on WSL 2

Uses ansible, in a pipenv, in a WSL 2 Ubuntu instance to provision locally.

Intended to be re-runnable (idempotent) to maintain and update when required.

## Getting Started

### Prerequisites

1. Windows 10.
1. WSL 2
1. Ubuntu 20.04 installed via Windows Store.

### Configure Python & pipenv

1. `sudo apt install --yes python3-pip`
1. `sudo pip3 install pipenv`

### Clone and Run

1. `git clone git@github.com:neilkidd/provision-ubuntu2004-on-wsl2.git`
1. `cd provision-ubuntu2004-on-wsl2`
1. `pipenv shell`
1. `pipenv install ansible --dev`
1. `ansible-galaxy install -r requirements.yml`
1. `ansible-playbook playbook.yml -i inventory --ask-become-pass`
1. Profit :smile:

## What is Installed?

- See the [playbook.yml](playbook.yml) task: `Install apt cmd line apps` for apt packages
- [yarn](tasks/yarn.yml)
- [tfenv](tasks/tfenv.yml)
- [aws vault](tasks/aws-vault.yml)
- [rbenv](tasks/rbenv.yml)


## Notes

|Description           | Command                                                                       |
|--------------------- | ----------------------------------------------------------------------------- |
|Find all local info   | `ansible localhost -m setup`                                                  |
|Run only rbenv        | `ansible-playbook playbook.yml -i inventory --ask-become-pass --tags "rbenv"` |

See [vars.yml](vars.yml) to configure which tasks get run.

## References

- [Jeff Geerling's Ansible for Devops](https://leanpub.com/ansible-for-devops/c/J2V7E1SOETu3)
- See [Brad's Pipenv Crash Course](https://youtu.be/6Qmnh5C4Pmo)
- Brad's [Pipenv cheatsheet](https://gist.github.com/bradtraversy/c70a93d6536ed63786c434707b898d55)
