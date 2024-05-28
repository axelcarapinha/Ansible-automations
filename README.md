# Ansible-server-automation
Ansible automations for a fresh configuration on a CentOS server.

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    </li>
    <li>
      <a href="#use-cases">Use cases</a>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#Pre-requisites">Pre-requisites</a></li>
        <li><a href="#How-to-run">How to run</a></li>
      </ul>
    </li>
    <li><a href="#folder-structure">Folder Structure</a></li>
    <li><a href="#results">Results</a></li>
    <li><a href="#what-i-learned-until-now">What I learned until now!</a></li>
  </ol>
</details>

## About the project
Ansible playbooks and taskbooks for a CentOS server configuration and maintenance.
Feel free to customize to your needs!

## Use cases
- In a ⚡breeze⚡, you can give your server:
    - SSH honeypot 
    - Docker-CE
    - Firewall basic configuration
    - SSH settings configuration
    - Unix user for Ansible
  
Want to test yourself the power of Infrastructure as Code? Keep reading! 🚀


## Getting started 
### Pre-requisites
- Linux server (CentOS, sometimes Ubuntu is supported too)
- <a href="https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html">Ansible</a> 
- SSH client (OpenSSH was the used one)
  
### How to run 
1. Get the playbooks and taskbooks
```zsh
git clone https://github.com/axelcarapinha/Ansible-automations.git && cd Ansible-automations
```
2. Place the target IP addresses (_inventory_ file)
3. Edit the path to the Ansible keys: private key (_ansible.cfg_ file) and public key (*config_ansible-user.yml*).
4. RUN
```sh
nano roles/common/tasks/main.yml # Commented taskbooks will NOT be used (OPTIONAL)
ansible-playbook site.yml
```

## Folder Structure
```sh
.
├── ansible.cfg
├── inventory
├── README.md
├── roles
│   ├── 00_folder-template
│   │   ├── defaults
│   │   ├── files
│   │   ├── handlers
│   │   ├── meta
│   │   ├── tasks
│   │   │   └── main.yml
│   │   ├── templates
│   │   └── vars
│   │       ├── defaults
│   │       ├── files
│   │       ├── handlers
│   │       ├── meta
│   │       ├── tasks
│   │       └── templates
│   └── common
│       ├── files
│       │   └── sudoer_hermes
│       ├── handlers
│       │   └── main.yml
│       ├── tasks
│       │   ├── config_ansible-user.yml
│       │   ├── config_firewalld.yml
│       │   ├── config_honeypot.yml
│       │   ├── config_ssh.yml
│       │   ├── install_common.yml
│       │   ├── install_dnf.yml
│       │   ├── install_docker-ce.yml
│       │   └── main.yml
│       └── vars
│           └── main.yml
└── site.yml
```

## Results
![Sample results with a CentOS Azure virtual machine](results.png)

## What I learned until now!
Had fun knowing more about:
- Ansible
 - playbooks
 - roles
 - taskbooks
 - tags
 - good Ansible practices
 - Ansible loops
 - difference between _import_ and _include_
- Advantages of Infrastructure as Code
 - eased, consistent and predictable server configuration
 - unnified approach to cloud environments
 - eased maintenance and version control (less information security threats)
 - managing settings of network devices (routers, in this case)
- Information Security
  - (simple) honeypots 
  - iptables, nftables, firewalld and ufw (differences)
  - firewalld (using) and its "zones"

However, an interesting lesson I learned: code abstractions can be a double-edged sword, due to the absence of the underlying functions that may lead to a misuse of the final product (Ansible, in this case).
