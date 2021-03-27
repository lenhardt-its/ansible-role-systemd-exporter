# Ansible Role: snmp exporter

[![ubuntu-18](https://img.shields.io/badge/ubuntu-18.x-orange?style=flat&logo=ubuntu)](https://ubuntu.com/)
[![ubuntu-20](https://img.shields.io/badge/ubuntu-20.x-orange?style=flat&logo=ubuntu)](https://ubuntu.com/)
[![debian-9](https://img.shields.io/badge/debian-9.x-orange?style=flat&logo=debian)](https://www.debian.org/)
[![debian-10](https://img.shields.io/badge/debian-10.x-orange?style=flat&logo=debian)](https://www.debian.org/)
[![centos-7](https://img.shields.io/badge/centos-7.x-orange?style=flat&logo=centos)](https://www.centos.org/)
[![centos-8](https://img.shields.io/badge/centos-8.x-orange?style=flat&logo=centos)](https://www.centos.org/)

[![License](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg?style=flat)](https://opensource.org/licenses/MIT)
[![GitHub issues](https://img.shields.io/github/issues/OnkelDom/ansible-role-systemd-exporter?style=flat)](https://github.com/OnkelDom/ansible-role-systemd-exporter/issues)
[![GitHub tag](https://img.shields.io/github/tag/OnkelDom/ansible-role-systemd-exporter.svg?style=flat)](https://github.com/OnkelDom/ansible-role-systemd-exporter/tags)
[![GitHub action](https://github.com/OnkelDom/ansible-role-systemd-exporter/workflows/ansible-lint/badge.svg)](https://github.com/OnkelDom/ansible-role-systemd-exporter)

## Description

Deploy and manage systemd-exporter [Systemd exporter](https://github.com/povilasv/systemd_exporter) using ansible.

## Requirements

- Ansible >= 2.9 (It might work on previous versions, but we cannot guarantee it)
- Community Packages: `ansible-galaxy collection install community.general`

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `proxy_env` | {} | Proxy environment variables |
| `systemd_exporter_version` | "0.4.0" | Set exporter version |
| `systemd_exporter_web_listen_address` | "0.0.0.0" | Set exporter ip-adress |
| `systemd_exporter_web_listen_port` | 9558 | Set exporter listen-port |
| `systemd_exporter_log_level` | "warn" | Loglevel for the exporter |
| `systemd_exporter_log_format` | "json" | Logformat for the exporter |
| `systemd_exporter_allow_firewall` | false | Enabled/Disabled Firewalld and open the port |
| `systemd_exporter_binary_local_dir` | "/usr/local/bin" | Binary Path |
| `systemd_exporter_create_consul_agent_service` | "true" | Add consul agent config snipped |
| `systemd_exporter_system_user` | "{{ systemd-exporter_user | default('root') }}" | Set exporters system user |
| `systemd_exporter_system_group` | "{{ systemd-exporter_group | default('root') }}" | Set exporters system group |
| `systemd_exporter_collector_unit_whitelist` | ".+" | Regexp of systemd units to whitelist. Units must both match whitelist and not match blacklist to be included. |
| `systemd_exporter_collector_unit_blacklist` | ".+\\.(device)" | Regexp of systemd units to blacklist. Units must both match whitelist and not match blacklist to be included. |
| `systemd_exporter_collector_private` | "false" | Establish a private, direct connection to systemd without dbus. |
| `systemd_exporter_ccollector_user` | "false" | Connect to the user systemd instance. |
| `systemd_exporter_ccollector_enable_restart_count` | "false" | Enables service restart count metrics. This feature only works with systemd 235 and above. |
| `systemd_exporter_ccollector_enable_file_descriptor_size` | "false" | Enables file descriptor size metrics. Systemd Exporter needs access to /proc/X/fd files. |
| `systemd_exporter_ccollector_enable_ip_accounting` | "false" | Enables service ip accounting metrics. This feature only works with systemd 235 and above. |

## Example

### Playbook

```yaml
- hosts: all
  become: yes
  roles:
    - onkeldom.snmp_exporter
```

## Contributing

See [contributor guideline](CONTRIBUTING.md).

## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.
