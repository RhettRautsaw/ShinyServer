# Shiny Server

[https://RhettRautsaw.app/](https://RhettRautsaw.app/)

This repository contains the html code for my [Digital Ocean](https://www.digitalocean.com/) Droplet [welcome page](https://RhettRautsaw.app/) which contains my Shiny applications and  my [RStudio Server](https://RhettRautsaw.app/rstudio). This repository also contains notes to remind myself how to run the damn thing. 

## Disclaimer

The code and asthetics of my server is based entirely on the work of [Dr. Saskia A. Otto](https://saskiaotto.de/).
Including her tutorials on how to setup the server:

- [Run Shiny Server on your own Digital Ocean Droplet - Part 1](https://www.marinedatascience.co/blog/2019/04/28/run-shiny-server-on-your-own-digitalocean-droplet-part-1/)
- [Run Shiny Server on your own Digital Ocean Droplet - Part 2](https://www.marinedatascience.co/blog/2019/04/28/run-shiny-server-on-your-own-digitalocean-droplet-part-2/index.html)

Which she built off of the tutorial by Dean Attali:

- [How to get your very own RStudio Server and Shiny Server with DigitalOcean](https://deanattali.com/2015/05/09/setup-rstudio-shiny-server-digital-ocean)

## Personal Notes

### Important Server Locations
The shiny apps are located here:: `/srv/shiny-server/`
- I prefer to just have my Shiny Apps listed in the hexagons on my welcome page, but you can have a shiny page html located here `/srv/shiny-server/index.html` for RhettRautsaw.app/shiny

The website html is managed by nginx. 
- The welcome page html is located here: `/var/www/html/`
- Once updated, you will need to restart nginx: `sudo service nginx restart`

### How to change the Droplet/Hostname
- Got to DigitalOcean.com and rename the Droplet
- On the server edit `/etc/hosts` and `/etc/hostname`

### How to change the custom URL:
- Buy a URL somewhere and then do [this](https://www.digitalocean.com/community/tutorials/how-to-point-to-digitalocean-nameservers-from-common-domain-registrars#registrar-namecheap)
- Go to your DigitalOcean.com and do [this](https://docs.digitalocean.com/products/networking/dns/how-to/add-domains/)
- Edit "server_name" in `/etc/nginx/sites-enabled/default`
	- Note that everything else is probably managed by Certbot
- Verify nginx syntax `sudo nginx -t` and correct any errors
- Reload nginx `sudo systemctl reload nginx`
- Obtain an SSL Certificate with Certbot
	- `sudo certbot --nginx -d example.com -d www.example.com`
