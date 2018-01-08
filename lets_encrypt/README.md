# Let's Encrypt Certificates

Cheatsheet for handling [Let's Encrypt](https://letsencrypt.org/) Certificates.

## Install Let's Encrypt Certificate on a nginx Server.

### Preconditions

- Server is prepared (see below)
- nginx Server Block config file is existing (e.g. /etc/nginx/sites-available/domain.com)

### Let's do it:

```
// Obtain certificate for server block (virtual host):
certbot --nginx -d domain.com -d www.domain.com
```
```
// Add this line to server block config file, somewhere in server section:
// IS DONE BY NEW VERSION OF CERTBOT AUTOMATICALLY!!! NOT NECCASSARY ANYMORE!
// ssl_dhparam /etc/ssl/certs/dhparam.pem;
```
```
// Enable HTTP2
// Change line in nginx server block config file
listen 443 ssl;
// zu
listen 443 ssl http2;
```
```
// nginx config test and reload:
nginx -t
systemctl reload nginx
```

## Prepare Server with nginx for Let's Encrypt

### Preconditions:

- Server with Ubuntu 16.04 or newer
- nginx Webserver installed and running

For more details see e.g. here:
- https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-16-04 
- https://www.digitalocean.com/community/questions/letsencrypt-for-multiple-domains-on-nginx)

### Let's do it:

```
// Install certbot:
add-apt-repository ppa:certbot/certbot
apt-get update
apt-get install python-certbot-nginx
```

```
// If not done automatically by certbot (check before doing this step):
openssl dhparam -out /etc/ssl/certs/dhparam.pem 2048
```

```
// nginx config test and reload:
nginx -t
systemctl reload nginx
```

```
// Cronjob for automatic Renewal of certificates:
crontab -e
=> add this line (time can be different):
26 4 * * * /usr/bin/certbot renew --quiet
```