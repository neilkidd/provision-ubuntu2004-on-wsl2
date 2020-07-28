# provision-ubuntu2004-on-wsl2

Automating provisioning ubuntu 20.04 with Ansible on WSL 2

## What

The time is now, I hope, to have consistent Windows / Linux hybrid environment"

## Why

Automate as mush as is pragmatic and share it. This repo is standing on the shoulders of giants.

## How

Use ansible, in a pipenv, in the WSL 2 ubuntu instance to provision locally. Very russian doll...

## Random notes

1. Install Ansible in a pypenv
1. Run the playbook locally.
1. Profit

#### Python3 and Pipenv

- See [Brad's Pipenv Crash Course](https://youtu.be/6Qmnh5C4Pmo)
- Brad's [Pipenv cheatsheet](https://gist.github.com/bradtraversy/c70a93d6536ed63786c434707b898d55)

#### Ansible in the Pipenv

`sudo apt install --yes python3-pip`  
`sudo pip3 install pipenv`  
`pipenv shell`  
`pipenv install ansible --dev`  

#### Starting a session

- `cd working_dir`
- `pipenv shell`

`ansible-playbook test.yml --connection=local`

Find all local info
`ansible localhost -m setup --connection=local`

`ansible-playbook playbook.yml --ask-become-pass -e 'ansible_python_interpreter=/usr/bin/python3'`

```
(provision-ubuntu2004-on-wsl2) neil@NK-MT-X1:~/code/nk/provision-ubuntu2004-on-wsl2$ ansible-playbook playbook.yml --connection=local --ask-become-pass
BECOME password: 
[WARNING]: No inventory was parsed, only implicit localhost is available
[WARNING]: provided hosts list is empty, only localhost is available. Note that the implicit localhost does not match 'all'

PLAY [localhost] ************************************************************************************************************************************

TASK [Gathering Facts] ******************************************************************************************************************************
ok: [localhost]

TASK [Update apt cache if needed.] ******************************************************************************************************************
[WARNING]: Updating cache and auto-installing missing dependency: python3-apt
fatal: [localhost]: FAILED! => {"changed": false, "msg": "Could not import python modules: apt, apt_pkg. Please install python3-apt package."}

PLAY RECAP ******************************************************************************************************************************************
localhost                  : ok=1    changed=0    unreachable=0    failed=1    skipped=0    rescued=0    ignored=0
```