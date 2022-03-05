# nginx-reverse-proxy

Reverse proxy configuration for NginX.

This repository includes an example for both an http and an https webserver, but can be used for any app.

## Setup

### 1. /etc/nginx

Place the configuration files inside the /etc/nginx/sites-available folder. 

### 2. Ports 

Inside each configuration file, adapt the port number on which you want NginX to listen. 
And include desired options such as http2, ssl, directives for IPv4 and/or IPv6... 

In this example:
- 3000: http listening port
- 4000: https listening port
- 5000: myapp listening port

### 3. Server name

Set the server name of your app equal to your domain names. 
And include both the domain name with and without www

### 4. SSL & Logs

Adapt the location of the SSL certificates (if applicable).

Edit the paths to the access and error logs. 
It is not mandatory to have logs, but recommended for troubleshooting.

### 5. Proxy settings

Adapt the proxy_pass and proxy_redirect directives. 
The port number has to match the port number on which your other app is listening (e.g. a NodeJS or Apache app's port number).
The following header directives are used to pass request header information to your listening app.

### 6. Test 

Test the configuration. 

    sudo nginx -t

### 7. Enable 

Make a symbolic link to each configuration file from inside /etc/nginx/sites-enabled folder 

    ln -s /etc/nginx/sites-enabled/myapp /etc/nginx/sites-available/myapp

Restart the daemon.

    sudo systemctl restart nginx.service