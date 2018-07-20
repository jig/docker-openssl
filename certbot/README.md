# Letsencrypt with certbot and nginx on AWS (with Docker)

Select an AWS Ubuntu image and a micro (free tier available).

When logged I install this:

```bash
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get install -y wget emacs24-nox curl dnsutils
curl -fsSL get.docker.com | sh
sudo usermod -aG docker ubuntu
```

Configure security groups allowing incoming traffic to 80 (HTTP) and 443 (HTTPS) ports.

And configure Route 53 with a new DNS name pointing to the IP Address provided to your machine.

Then load this Docker image from the Hub:

```bash
docker run -p 443:443 -p 80:80 -ti jordi/letsencrypt
```

It already contains a barebones nginx installation, the certbot and the certbot plugin for nginx.

You can start your nginx with:

```bash
nginx
```

And connect to http://dns-name-here to check everything works.

Then you can configure it to use HTTPS, using certbot:

```bash
certbot --nginx
```

Then you can connecto to https://dns-name-here using HTTPS. And your browser must show it _in green_.
