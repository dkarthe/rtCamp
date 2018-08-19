# How To Secure Nginx with Let's Encrypt on Ubuntu 

## Prerequisites
* One Ubuntu latest server set up by following this initial server setup for Ubuntu.
* Both of the following DNS records set up for our server. 
  
  An A record with ooioo.co pointing to our server's public IP address.
  
  An A record with www.ooioo.co pointing to our server's public IP address.
  
## Step 1 — Installing Certbot

First, add the repository.

`$ sudo add-apt-repository ppa:certbot/certbot`

`$ sudo apt-get update`

And finally, install Certbot's Nginx package with apt-get.
`$ sudo apt-get install python-certbot-nginx`

## Step 2 — Setting up Nginx
`$ sudo nano /etc/nginx/sites-available/default`

Save the file and quit your editor.

Then, verify the syntax of your configuration edits.

`$ sudo nginx -t`
If you get any errors, reopen the file and check for typos, then test it again.

Once your configuration's syntax is correct, reload Nginx to load the new configuration.

`$ sudo systemctl reload nginx`
Certbot will now be able to find the correct server block and update it. Next, we'll update our firewall to allow HTTPS traffic.

## Step 3 — Allowing HTTPS Through the Firewall
`$ sudo ufw status`
`$ sudo ufw allow 'Nginx Full`
`$ sudo ufw delete allow 'Nginx HTTP`

## Step 4 — Obtaining an SSL Certificate

`$ sudo certbot --nginx -d ooioo.co -d www.ooioo.co`

## Step 5 — Verifying Certbot Auto-Renewal

`$ sudo certbot renew --dry-run`


