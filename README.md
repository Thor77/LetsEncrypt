My Let's Encrypt setup
======================

## Assumptions
* OS using systemd as init-system
* [`simp_le`](https://github.com/zenhack/simp_le) in `$PATH`
* `account_key.json` (`private_key.json` from [certbot](https://certbot.eff.org/)) in `/etc/letsencrypt/`

## Installation
* Copy `certrenew` to `/usr/local/bin/certrenew`
* Copy `letsencrypt@.{service,timer}` to `/etc/systemd/system/`
* Edit `EMAIL` and `WEBROOT` in `/usr/local/bin/certrenew`

## Usage
Obtaining a certificate for a new domain
```
systemctl start letsencrypt@<newdomain>
```
Your cert-data (`fullchain.pem` and `key.pem` by default) is located in `/etc/letsencrypt/<newdomain>/`

Activating renewal for a new domain
```
systemctl start letsencrypt@<newdomain>.timer
systemctl enable letsencrypt@<newdomain>.timer
```
