Windows Exporter
================

An Ansible role for install, configure and update [Windows Exporter](https://github.com/prometheus-community/windows_exporter).

Requirements
------------

- Supported version of Ansible: 2.9 and highter.
- `pywinrm` is a python library for connection Ansible to Windows hosts via [WinRM](https://docs.ansible.com/ansible/latest/user_guide/windows_winrm.html).
- List of all supported platforms described in role meta.

Role Variables
--------------

- `windows_exporter_version` The specific version of Windows Exporter to download (default: `0.18.1`).
- `windows_exporter_package_name` Windows Exporter package name.
- `windows_exporter_download_url` URL to download Windows Exporter package.
- `windows_exporter_listen_address` The IP address to bind to (default: `0.0.0.0`).
- `windows_exporter_listen_port` The port to bind to (default: `9182`).
- `windows_exporter_metrics_path` The path at which to serve metrics (default: `metrics`).
- `windows_exporter_log_level` Windows Exporter logging level (default: `info`).
- `windows_exporter_collectors_enabled` Comma-separated list of collectors to use (default: `[defaults]`).
- `windows_exporter_collector` Flags for collectors (default: `''`).

Dependencies
------------

None.

Example Playbook
----------------

Install, configure `Windows Exporter` and specify a custom query for service collector.

  ```yaml
  ---
  - name: 'Setup Windows Exporter'
    hosts: windows_exporter

    roles:
      - role: antmelekhin.windows_exporter
        windows_exporter_collectors_enabled: '[defaults],memory'
        windows_exporter_collector:
          - name: service
            flags:
              services-where: Name='windows_exporter'
  ```

License
-------

MIT

Author Information
------------------

Melekhin Anton.
