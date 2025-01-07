# Project: Intelligent Platform for AI Model Management and Information Retrieval

## General Description:
This project is an application designed to enhance the use of local and cloud-based Large Language Models (LLMs), including OpenAI and Grok, integrated with a Retrieval-Augmented Generation (RAG) system. It offers a user-friendly interface developed in Streamlit, with advanced capabilities for:

 - **Managing AI models through a dynamic selector.**

 - **Incorporating vector databases for efficient information storage and retrieval.**

 - **Ensuring security and ease of use with secure tunneling and customizable configurations.**

This app helps experiment with various models to determine the best action based on resources, model choice, budget, and cloud services.

## Key Features

1. **Main Framework**: 
   - **Pure Python** along with **Streamlit** for the user-friendly interface.

2. **Databases**:
   - **Firebase**:To store email validation in the account page.
   - **Chromadb**: Vector databases that store embeddings represented as numeric vectors.

3. **Models**:
   - **OpenAI Embeddings**: Vector database for embeddings generated by OpenAI.
   - **Ollama Embeddings**: Embeddings generated by local Ollama models.

4. 🔒 **Secure Tunneling**:
   - **Ngrok**:  Creation of a secure tunnel (puerto `4040`) to share the application without vulnerabilities.

5. **Model Selector**:
   - **Option to choose from:**
     - OpenAI
     - Grok
     - Custom local models.

6. **Customization**:
   - **Easy update of the Ngrok token in Ngrok** `ngrok.yml`file.
   - **Selection of default models from the** `.env`file.

## Configuration

1. **Configure environment variables**
   - Edit the  `.env` file with the following content:
     ```env
     MODEL_LIST=Meta models that suit you
     ```

2. **Configure Ngrok:**
   - Edith the archivo `ngrok.yml` with your token:
     ```yaml
     authtoken: YOUR_NGROK_TOKEN
     ```
---
# Omnia Open Source Setup Guide

This guide provides step-by-step instructions for setting up Omnia Open Source using Docker, Nginx, and Certbot for SSL. Copy the commands directly to your terminal to streamline the installation.

---

## Prerequisites

- Ensure you have `sudo` privileges on your system.
- Verify you are running a supported Linux distribution (e.g., Ubuntu).

---

## Installation Steps

### Step 0: local host 8080  and also the safe tunnel with ngrok at port 4040
```bash
docker-compose up
```

   
### Step 1: Check Disk Space
```bash
df -h
```

### Step 2: Update the system 
```bash
sudo apt update
```

### Step 3: install Docker
```bash
sudo apt install docker.io
```

### Step 4: start and enable dockers
```bash
sudo systemctl start docker
sudo systemctl enable docker
```

### Step 5: Install Docker Compose
```bash
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version

```

### Step 6: Add your user to the Docker group
```bash
whoami # Identify the user
sudo usermod -aG docker user

```

### Step 7: log out and log back in that way the changes can take effect
```bash
exit
```

### Step 8: Install Git
```bash
sudo apt install -y git
```

### Step 9: clone the repository and change from directory
```bash
git clone https://github.com/Josh1313/OmniaOpenSource.git
cd OmniaOpenSource
```

### Step 10: Docker Comands to stop or run the app
```bash
docker-compose up 
or 
docker-compose up -d
docker-compose down
docker-compose start
docker-compose stop
```

### Step 11: Install  Nginx

```bash
sudo apt install -y nginx
```

### Step 12: configure Nginx
```bash
sudo nano /etc/nginx/sites-available/OmniaOpenSource
```

### Step 13: Paste the following Nginx configuration:
```bash
server {
    server_name YOUR-DOMAIN-NAME;


    location / {
        proxy_pass http://localhost:8080;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}

```

### Step 14: Exit
```bash
Save and exit: CTRL+O, ENTER, CTRL+X
```

### Step 15: Enable the site:
```bash
sudo ln -s /etc/nginx/sites-available/OmniaOpenSource /etc/nginx/sites-enabled/
sudo nginx -t
```

### Step 16: Install Cerbot
```bash
sudo apt install -y certbot python3-certbot-nginx
```

### Step 17:  Set up SSL with Certbot
```bash
sudo certbot --nginx -d YOUR-DOMAIN-NAME
```

### Step 18:  Update Nginx configuration with SSL
```bash
sudo nano /etc/nginx/sites-available/OmniaOpenSource

```

### Step 19: Replace with the following configuration:
```bash
server {
    listen 443 ssl;
    server_name omniaopensource.zapto.org;

    #ssl_certificate /etc/letsencrypt/live/omniaopensource.zapto.org/fullchain.pem;
    #ssl_certificate_key /etc/letsencrypt/live/omniaopensource.zapto.org/privkey.pem;
    include /etc/letsencrypt/options-ssl-nginx.conf;
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem;

    location / {
        proxy_pass http://localhost:8080;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}

server {
    listen 80;
    server_name omniaopensource.zapto.org;

    return 301 https://$host$request_uri; # Redirigir HTTP a HTTPS
}


```

### Step 20: Restart Nginx
```bash
sudo nginx -t
sudo systemctl restart nginx
```

### Step 21: TEST APP
```bash
http://YOUR EXTERNAL API:8080

```

