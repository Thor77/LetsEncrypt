My Let's Encrypt setup
======================

## Assumptions
* OS using systemd as init-system
* [`simp_le`](https://github.com/kuba/simp_le) in `$PATH`

## Installation
* Copy `certrenew` to `/usr/local/bin/certrenew`
* Copy `letsencrypt@.{service,timer}` to `/etc/systemd/system/`
* Edit `EMAIL` and `WEBROOT` in `/usr/local/bin/certrenew`

## Usage
Obtaining a certificate for a new domain
```
systemctl start letsencrypt@<newdomain>
```
Activating renewal for a new domain
```
systemctl start letsencrypt@<newdomain>.timer
systemctl enable letsencrypt@<newdomain>.timer
```
