# Wordpress Sandbox

This composition will launch Wordpress and below email services:
* SMTP service on port 25, run by `smtp-sink`
* IMAP service on port 143, run by `courier-imap` (User : **smtp**, password: **smtp**)
* WEBMAIL service on port *8008*, run by `apache2` and `roundcube` at http://127.0.0.1:8008/webmail/

SMTP will accept all emails and store every emails receive on port 25 to only one mailbox. 
This mailbox can be read with a webmail available on port 8080 or with IMAP protocol available on standard port 143.

Usage :

```bash
git clone repo
cd repo
# docker-compose build # (optional step)
docker-compose up
```
Then you can configure apps to send emails to local port 25 and you can read received emails on http://127.0.0.1:8008/webmail/.<br/>
Verify PHP settings at:
```
http://localhost:8080/wp-admin/media-new.php
```
Tested with:
```
https://wordpress.org/plugins/wp-mail-smtp/
```

## Resources
```
https://www.wpdiaries.com/mail-functionality-for-official-docker-wordpress-image/#separate-container-without-dkim
https://medium.com/the-andela-way/how-to-setup-a-new-wordpress-project-with-docker-7f520f817b97
```
