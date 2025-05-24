# Ansible AWS EC2 Automation Project

This project uses **Ansible** to automate the provisioning and management of AWS EC2 instances (2 Ubuntu + 1 Amazon Linux). It includes:

- EC2 creation with loops
- Secure access with passwordless SSH using `ssh-copy-id` and PEM file
- Usage of `vault` to store AWS access keys
- Shutdown automation based on conditions (e.g., if Debian OS)
- Uses `boto3` and `amazon.aws` collection for interacting with AWS

---

## Vault Usage

Sensitive data like AWS keys are stored securely in `group_vars/` using Ansible Vault.

---

## How to Run

Prerequisite: Install `boto3` and the `amazon.aws` Ansible collection.

### Install Required Python Libraries

pip install boto3 

### Install AWS Ansible Collection

ansible-galaxy collection install amazon.aws

---

### 1️⃣ Create EC2 Instances

ansible-playbook create-ec2.yml --vault-password-file vault.pass -i inventory.ini

---

### 2️⃣ Set Up Passwordless SSH

Use the following command to configure SSH access using your `.pem` key file:

ssh-copy-id -i /path/to/your-key.pem ubuntu@<public-ip>

Repeat this for each EC2 instance.

---

### 3️⃣ Shutdown Debian-Based Instances

ansible-playbook shutdown.yml -i inventory.ini

---

## .gitignore Recommendation

Make sure to exclude sensitive files from your Git repository by adding the following lines to `.gitignore`:

vault.pass
group_vars/

---

## Author

Sharathchandra Telugu  
GitHub: https://github.com/Sharathchandra3

---

