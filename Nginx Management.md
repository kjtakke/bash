# Nginx Management 

| Command | Description |
|---------|-------------|
| `sudo systemctl start nginx` | Start the Nginx service |
| `sudo systemctl stop nginx` | Stop the Nginx service |
| `sudo systemctl restart nginx` | Restart Nginx |
| `sudo systemctl reload nginx` | Reload Nginx without dropping connections |
| `sudo systemctl status nginx` | Check Nginx service status |
| `sudo nginx -t` | Test Nginx configuration for syntax errors |
| `sudo nginx -s reload` | Reload Nginx (alternative method) |
| `sudo nginx -s stop` | Stop Nginx (alternative method) |
| `sudo journalctl -u nginx --no-pager | tail -n 50` | View the last 50 lines of Nginx logs |
| `sudo tail -f /var/log/nginx/access.log` | Monitor access logs in real-time |
| `sudo tail -f /var/log/nginx/error.log` | Monitor error logs in real-time |
| `sudo ufw allow 'Nginx Full'` | Allow HTTP & HTTPS traffic through UFW |
| `sudo ufw allow 80/tcp` | Allow HTTP traffic only |
| `sudo ufw allow 443/tcp` | Allow HTTPS traffic only |
| `sudo systemctl enable nginx` | Enable Nginx to start at boot |
| `sudo systemctl disable nginx` | Disable Nginx from starting at boot |
| `sudo nano /etc/nginx/nginx.conf` | Edit the main Nginx configuration file |
| `sudo nano /etc/nginx/sites-available/default` | Edit the default server block configuration |
| `sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/` | Enable a virtual host |
| `sudo rm /etc/nginx/sites-enabled/example.com` | Disable a virtual host |
| `sudo certbot --nginx -d example.com -d www.example.com` | Obtain and install an SSL certificate with Certbot |
| `sudo certbot renew --dry-run` | Test SSL certificate renewal |
| `sudo certbot renew` | Renew SSL certificates manually |
| `sudo kill -HUP $(cat /var/run/nginx.pid)` | Gracefully reload Nginx using its PID |

> **Note:** Replace `example.com` with your actual domain name where needed.