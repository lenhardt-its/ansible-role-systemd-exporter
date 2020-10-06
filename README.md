# Ansible Role: snmp exporter

## Description

Deploy and manage prometheus [Systemd exporter](https://github.com/povilasv/systemd_exporter) using ansible.

## Requirements

- Ansible >= 2.6 (It might work on previous versions, but we cannot guarantee it)

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
| `systemd_exporter_firewalld_state` | "disabled" | Enabled/Disabled Firewalld and open the port |
| `systemd_exporter_binary_local_dir` | "/usr/local/bin" | Binary Path |
| `systemd_exporter_create_consul_agent_service` | "true" | Add consul agent config snipped |
| `systemd_exporter_system_user` | "{{ prometheus_user | default('root') }}" | Set exporters system user |
| `systemd_exporter_system_group` | "{{ prometheus_group | default('root') }}" | Set exporters system group |
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
    - ansible-role-snmp-exporter
```

## Contributing

See [contributor guideline](CONTRIBUTING.md).

## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.
