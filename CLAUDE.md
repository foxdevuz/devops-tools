# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A collection of beginner-friendly DevOps tools, templates, and configurations. This is not a buildable application — it's a reference repository of reusable infrastructure-as-code playbooks, container definitions, CI/CD workflows, shell scripts, and configuration files.

There are no build commands, test suites, or linters to run.

## Repository Structure

- **IaC/Ansible/** — Ansible playbooks organized by purpose:
  - `Monitoring/` — Prometheus, Grafana, Alertmanager, node_exporter installation playbooks
  - `Databases/` — PostgreSQL, MySQL installation
  - `Docker/` — Docker installation
  - `WebServers/` — Nginx installation
  - `ProgrammingLanguages/` — PHP, Node.js installation
  - `NginxConfigFileCreate/` and `DockerComposeFileCreate/` — Templated config generation using Jinja2 templates + vars
  - `untitled/` — Work-in-progress playbooks (certbot, user management)
- **containers/Docker/** — Dockerfiles and docker-compose files for JS (React, Next), Python (Django), and databases
- **ci-cd/GithubActions/** — GitHub Actions workflow snippets and full examples (Docker builds, Telegram notifications, secret key setup)
- **configs/** — Ready-to-use config files for Monitoring (Grafana Alloy), Kubernetes (kubeadm), and Nginx
- **bash/** — Shell scripts for installing Kubernetes utilities and CRI-O
- **Monitoring/** — Grafana Alloy configuration files
- **web-servers/nginx/** — Nginx config examples (direct file, proxy pass)
- **testing-area/** — Scratch configs for testing (Prometheus, alert rules)

## Ansible Playbook Conventions

Each Ansible playbook directory typically contains:
- `install.yml` or `playbook.yml` — the main playbook
- `inventory.yml` or `inventory.ini` — target host inventory
- `vars/variables.yml` or `vars/vars.yml` — variables (when needed)
- `templates/*.j2` — Jinja2 templates (for config generation playbooks)

To run an Ansible playbook:
```
ansible-playbook -i <inventory-file> <playbook-file>
```
