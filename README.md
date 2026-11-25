# Ansible inventory to Rocket Remote Desktop CSV

This playbook creates a semicolon-delimited Rocket Remote Desktop connection import file.

Rules:

- Windows-like `os_type` values create an `RDP` connection, port 3389 by default.
- Linux-like `os_type` values create an `SSH` connection, port 22 by default.
- A non-empty `imm_hostname` creates an additional `HTTP/S` connection, port 443 by default.
- The playbook runs on the controller only and does not connect to inventory hosts.

Run:

```bash
ansible-playbook -i inventory.example.yml generate_rocket_csv.yml
```

Generated file:

```text
output/rocket-connections.csv
```

Before the first bulk import, create one RDP, SSH, and HTTP/S connection manually in Rocket Remote Desktop 2026 and export them to CSV. Compare the exported protocol names and headers with the generated file. Override `rocket_https_protocol` if your build uses a different HTTP/S token.
