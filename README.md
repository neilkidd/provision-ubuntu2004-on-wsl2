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
