# Overview

FortiAnalyzer Ansible Playbooks

## Bootstrap

- Create API key

    config system admin user
        edit ansible
            set profileid Super_User
            set user_type api
            set rpc-permit read-write
        next
    end

    execute api-user generate-key ansible

- Run commands

    python -m venv .venv
    source .venv/bin/activate
    pip install --upgrade pip
    pip install -r requirements.txt

- Install collections (alternative to requirements.yml)

    ansible-galaxy collection install fortinet.fortianalyzer:1.9.0

- Install collections

    ansible-galaxy collection install -r requirements.yml

- Collections installed at (not on venv):

    /Users/draks/.ansible/collections/ansible_collections/fortinet/fortios

- Fix multithread on MacOS
    
    # if error
    # objc[66485]: +[__NSCFConstantString initialize] may have been in progress in another thread when fork() was called.
    export OBJC_DISABLE_INITIALIZE_FORK_SAFETY=YES

- Run playbook

    source .venv/bin/activate
    ./faz_fact_sys_status.yml

# References

- https://ansible-galaxy-fortianalyzer-docs.readthedocs.io
- https://galaxy.ansible.com/ui/repo/published/fortinet/fortianalyzer/

# Requirements

    ansible-galaxy collection install -r requirements.yml
