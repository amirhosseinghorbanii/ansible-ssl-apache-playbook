# Ansible SSL Apache Playbook

This Ansible playbook automates the process of enabling SSL on an Apache server and deploying SSL certificates securely.

## ✅ Features

- Enables the `ssl` module in Apache
- Creates a secure directory for SSL certificates
- Copies certificate and key files to the target directory
- Updates Apache virtual host configuration with new certificate paths
- Restarts Apache and verifies HTTPS service availability

## 📁 Directory Structure

```
ansible-ssl-apache-playbook/
├── ssl_playbook.yml
├── certificate/
│   ├── server.crt
│   └── server.key
└── README.md
```

## ⚙️ Prerequisites

- Ansible installed on the control node
- Target host accessible over SSH
- Apache2 installed on the target system
- SSL certificate and private key available

## 🚀 How to Use

1. Clone the repository:

   ```bash
   git clone https://gitlab.com/your-namespace/ansible-ssl-apache-playbook.git
   cd ansible-ssl-apache-playbook
   ```

2. Replace the certificate files in the `certificate/` directory with your actual `.crt` and `.key`.

3. Create an inventory file named `inventory`:

   ```ini
   [AmirHossein]
   192.168.1.10 ansible_user=root
   ```

4. Run the playbook:

   ```bash
   ansible-playbook -i inventory ssl_playbook.yml
   ```

## 🔐 Notes

- Make sure the SSL certificate and key are valid and match your domain.
- This playbook uses `/tmp/000-default.conf` as the Apache config file — adjust the path if necessary.
- For production, secure your playbook and certificate files properly and avoid hardcoding paths.

## 🧪 Test

After running the playbook, you can test HTTPS access using:

```bash
curl -k https://<your-server-ip>
