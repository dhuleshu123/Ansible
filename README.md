# Ansible Playbooks & Automation Examples

A collection of hands-on Ansible playbooks covering core system administration tasks, file management, user configuration, scheduling, networking, and control flow.

## 📋 Repository Contents

### Core System & File Management

| File | Description |
| :--- | :--- |
| `first_pb.yml` | Basic introductory Ansible playbook structure. |
| `01_app_install.yml` | Installing and managing software packages. |
| `02_copy_files.yml` | Copying files from the control node to managed hosts. |
| `03_files_mod.yml` | Creating, modifying, and managing file attributes. |
| `04_change_permission.yml` | Updating file and directory ownership and permissions. |
| `10_download_file.yml` | Downloading files from remote URLs to target nodes. |

### Execution, Scheduling & Processes

| File | Description |
| :--- | :--- |
| `05_script_run.yml` | Transferring and executing shell scripts on remote servers. |
| `06_cron_jobs.yml` | Creating and scheduling automated cron jobs. |
| `07_cron_modify.yml` | Updating and managing existing cron entries. |
| `11_kill_process.yml` | Finding and terminating running system processes. |

### User & Security Management

| File | Description |
| :--- | :--- |
| `08_user_mgm.yml` | Creating, modifying, and removing system users and groups. |
| `09_set_passwd.yml` | Setting and updating encrypted user passwords. |
| `12_firewalld.yml` | Configuring firewall rules and ports using `firewalld`. |

### Logic, Loops & Roles

| File | Description |
| :--- | :--- |
| `13_conditions.yml` | Implementing conditional task execution using `when` statements. |
| `14_for_loop.yml` | Iterating over lists and items using `loop` / `with_items`. |
| `roles_demo.yml` | Structuring and executing reusable Ansible roles. |

### Production & Real-World Workflows
| :--- | :--- |
| `15_jinja2_templates.yml` | Generates dynamic host configurations via `.j2` templates and triggers service reloads with handlers. |
| `16_error_handling_blocks.yml` | Implements `block`, `rescue`, and `always` sections for automated failure recovery and cleanup. |
| `17_vault_secrets.yml` | Loads encrypted credentials safely from `ansible-vault` files while masking sensitive output with `no_log`. |
| `18_rolling_patch_reboot.yml` | Performs zero-downtime batch patching using `serial: 1` and conditional system reboots. |

### Additional Resources
* `Ansible.pdf` – Reference guide and notes on Ansible concepts and commands.
* `playbooks-20261120T080040Z-1-001.zip` – Archived bundle of the playbook files.

---

## 🚀 Prerequisites

* **Control Node:** Linux/macOS machine (or WSL on Windows) with **Ansible** installed (`ansible --version`).
* **Managed Nodes:** Target Linux servers accessible via **SSH**.
* **Authentication:** SSH key-based authentication configured between the control node and managed hosts, along with `sudo` privileges where required.

---

## ⚙️ Usage

1. **Clone the repository:**
   ```bash
   git clone https://github.com/dhuleshu123/Ansible.git
   cd Ansible
   ```

2. **Configure your inventory:**
   Ensure your target hosts are defined in `/etc/ansible/hosts` or create a custom `inventory.ini` file:
   ```ini
   [webservers]
   192.168.1.10 ansible_user=ubuntu
   192.168.1.11 ansible_user=ubuntu
   ```

3. **Verify connectivity:**
   ```bash
   ansible all -i inventory.ini -m ping
   ```

4. **Run a playbook:**
   ```bash
   ansible-playbook -i inventory.ini 01_app_install.yml
   ```
5. **Run Vault-Encrypted Playbooks:**
   ```bash
   ansible-playbook -i inventory.ini 17_vault_secrets.yml --ask-vault-pass
   ```   
   *(Add `--check` to perform a dry run before applying changes, or `-K` if a sudo password is required.)*

---

## 🤝 Contributing

Contributions, improvements, and additional playbook examples are welcome. Feel free to fork the repository and submit a pull request.
