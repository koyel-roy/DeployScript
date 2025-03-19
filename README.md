## Project Deployment Guide
## 1. Install Ansible and sshpass  
Ensure that **Ansible** and **sshpass** are installed on your machine:

### ✅ Install Ansible  
```bash
sudo apt update
sudo apt install ansible -y

### 1. Ansible Ping Test
To verify Ansible connectivity with the target server, run the following command:

```bash
ANSIBLE_HOST_KEY_CHECKING=False ansible -i inventory.ini 10.11.21.88 -m ping
```
**Expected Output:**
```
10.11.21.28 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
```

### 2. Moving Required Files
Transfer the following files from your local machine to the remote server using **WinSCP**:
- `inventory.ini`
- `deploy.yaml`

### 3. Running Ansible Playbook
Run the following command to execute the deployment playbook:

```bash
ansible-playbook -i inventory.ini deploy.yaml --ask-become-pass
```

### 4. Nginx Configuration (if required)
If this Nginx configuration is not already set up on the server, add the following block:

```nginx
server {
  listen 3000;
  server_name 10.11.21.88;

  root /var/www/react_app;
  index index.html;

  location / {
    try_files $uri /index.html;
  }

  # Optional: Add this to handle React app static files
  location /static/ {
    alias /var/www/react_app/static/;
  }
}
```

**Commands to Apply Nginx Configuration:**
```bash
ls -l /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl restart nginx
sudo ufw allow 3000/tcp
sudo ufw reload
```

### 5. Important Manual Configuration Steps
- **Postgres Setup:**
  - Configure password authentication for the `postgres` user.
  - Assign `superuser` privileges to the `postgres` user.
  - Set up a Postgres backup strategy.

- **`credentials.json` Configuration:**
  - Ensure the correct path to `credentials.json` is mentioned in each `GWService` class.

- **UI Configuration:**
  - Update the `route.js` file to reference the current server or host.

- **Firewall Configuration:**
  - Check if the backend port is blocked by the firewall and allow it if necessary.

- **Starting the Backend:**
  Run the following command to start the backend manually:

```bash
sudo java -jar /opt/DataModelAPI/data-model-api-0.0.1-SNAPSHOT.jar
```

- **`application.properties` Configuration:**
  - Ensure it contains the updated Postgres and MongoDB connection URLs, usernames, and passwords.
  - Localhosted databases can be used, but password authentication is mandatory.



