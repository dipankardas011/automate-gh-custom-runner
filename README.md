# GitHub Custom Runner Automation

## Purpose
When you don't have money to burn for achieving the highly scalable github custom runner infra (aka using Kubernetes)
It is also much more sustainable, only send amount of energy and resources as you require

You can append terraform which (Create and Destroy infra). Thus, achieve true 0 to X nodes and back to 0 nodes. [Refer Implementation in ksctl](https://github.com/ksctl/ksctl/tree/main/test/gh-runner) [Usage](https://github.com/ksctl/ksctl/blob/main/.github/workflows/e2e.yml)

## How it works

You provide it runnernames and it will bootstrap node(s)

It all depends on you if you want to make each runner to exist on different machine its possible
If you want it to make bootstrap multiple runners inside one machine (use when you have huge machine)

It creates a user same as runnerName you had given, and it bootstraps to the directory `~/actions-runner`

## Usage methods

### working with the github registration token

```bash
export ORG_REGISTRATION_TOKEN="" # registration token already present
ansible-playbook -i ~/inventory.ini add-runners.yml --tags all,use_reg_token
```

```bash
export ORG_REGISTRATION_TOKEN="" # registration token already present
ansible-playbook -i ~/inventory.ini rm-runners.yml --tags all,use_reg_token
```

### working with the github pat token to generate the registration token

```bash
export GH_TOKEN="" # to generate the registration token using the GH_PAT api key
ansible-playbook -i ~/inventory.ini add-runners.yml --tags all
```

```bash
export GH_TOKEN="" # to generate the registration token using the GH_PAT api key
ansible-playbook -i ~/inventory.ini rm-runners.yml --tags all
```
