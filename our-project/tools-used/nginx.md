# NGINX

Nginx (pronounced "engine-x") is a **free, open-source web server and reverse proxy**. Renowned for its efficiency, stability, and versatility, it excels in handling high volumes of concurrent user requests while maintaining a minimal resource footprint. Beyond its core functionality as a web server, Nginx can also act as a reverse proxy, load balancer, and more, offering a flexible solution for diverse web hosting needs. Its extensive configuration options empower you to tailor Nginx to your specific requirements.

### Installation

**Download Nginx:**

* Visit the official Nginx website: [http://nginx.org/en/download.html](http://nginx.org/en/download.html).
* Download the appropriate installer for your system (32-bit or 64-bit).

**Install Nginx:**

* Run the downloaded installer and follow the on-screen instructions. It's recommended to choose the "typical" installation type.

**Configure Nginx:**

* The installer typically places the configuration file at `C:\nginx\conf\nginx.conf`. Open it with a text editor.
* **Server Block:** Locate the `server` block and modify the following:
  * `listen 80;`: Change the port if needed (default is 80).
  * `server_name localhost;`: Replace `localhost` with your desired domain name (if applicable).
  * `root C:/nginx/html;`: Change the path to your website's files.
* **Save the configuration file.**

**Start Nginx:**

* Open a Command Prompt window as administrator.
* Navigate to the Nginx installation directory (e.g., `cd C:\nginx`).
* Run the command: `nginx.exe`

**Test Your Website:**

* Open your web browser and navigate to `http://localhost` (or your chosen domain name) to verify if your website is accessible.

### **Configuring Virtual Hosts**

Virtual hosts, also known as server blocks in Nginx, allow you to host multiple websites on a single server. Here's a step-by-step guide to configuring virtual hosts:

* Open your Nginx configuration file (`nginx.conf`). This file is typically located in the `conf` directory of your Nginx installation.
* Within the `http` block of the configuration file, define multiple `server` blocks. Each `server` block represents a virtual host.
* For each `server` block, specify the `listen` directive followed by the desired port number (e.g., 80 for HTTP).
* Use the `server_name` directive to specify the domain name or hostname associated with the virtual host.
* Inside each `server` block, configure the `location` directive to define the root directory and default files for the website.

Example:

```nginx
nginxCopy codeserver {
    listen 80;
    server_name example.com;
    root /var/www/example.com;
    index index.html;
    
    location / {
        try_files $uri $uri/ =404;
    }
}
```

### **Enabling HTTPS**

HTTPS encrypts communication between clients and your server, providing security for sensitive data. Follow these steps to enable HTTPS in Nginx:

* Obtain an SSL/TLS certificate for your domain name. You can generate a self-signed certificate for testing purposes or purchase one from a trusted Certificate Authority (CA).
* Update the `server` block for each virtual host to listen on port 443, the default port for HTTPS.
* Specify the paths to your SSL certificate and private key files using the `ssl_certificate` and `ssl_certificate_key` directives, respectively.
* Configure SSL protocols and ciphers to ensure secure connections. You can use the `ssl_protocols` and `ssl_ciphers` directives for this purpose.

Example:

```nginx
nginxCopy codeserver {
    listen 443 ssl;
    server_name example.com;
    root /var/www/example.com;
    index index.html;
    
    ssl_certificate /path/to/certificate.crt;
    ssl_certificate_key /path/to/private.key;
    
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers HIGH:!aNULL:!MD5;
    
    location / {
        try_files $uri $uri/ =404;
    }
}
```

### **Setting Up Reverse Proxy**

A reverse proxy forwards client requests to backend servers, allowing you to distribute incoming traffic and improve performance. Here's how to set up reverse proxying in Nginx:

* Define a new `server` block for the desired hostname or URL endpoint.
* Inside the `location` block, use the `proxy_pass` directive to specify the URL of the backend server where requests should be forwarded.
* Optionally, configure additional proxy headers such as `Host`, `X-Real-IP`, and `X-Forwarded-For` to provide additional information to the backend server.

Example:

```nginx
nginxCopy codeserver {
    listen 80;
    server_name proxy.example.com;
    
    location / {
        proxy_pass http://backend_server;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```
