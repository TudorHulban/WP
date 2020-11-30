# WordPress
## Docker Run
Create sandbox:
```bash
docker-compose up -d
```
Clean with:
```bash
docker-compose down
```
Docker Compose file:
```yaml
version: '3.7'

services:  
  mysql:
    image: mysql:5.7
    container_name: database
    environment:
     - MYSQL_ROOT_PASSWORD=password
     - MYSQL_DATABASE=wordpress
     - MYSQL_USER=wordpress
     - MYSQL_PASSWORD=admin
    volumes:
     - dbdata=/var/lib/mysql
    ports:
      - 3306:3306

  wordpress:
        image: wordpress
        container_name: wp
        links:
         - mysql
        environment:
         - WORDPRESS_DB_PASSWORD=password
        ports:
         - 8080:80
        volumes:
         - type: bind
           source: ./docker-uploads.ini
           target: /usr/local/etc/php/conf.d/docker-uploads.ini

  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    container_name: pma
    links:
      - mysql
    environment:
      PMA_HOST: mysql
      PMA_PORT: 3306
      PMA_ARBITRARY: 1
    restart: always
    ports:
      - 8081:80

volumes:
  dbdata:
```
Extra settings file `docker-uploads.ini`.
```
# Allow HTTP file uploads
file_uploads = On
 
# Maximum size of an uploaded file
upload_max_filesize = 256M
 
# Maximum size of form post data
post_max_size = 64M
```
### Resources
```
https://devtidbits.com/2019/11/02/customise-wordpress-on-docker/
```

## Themes
Import Astra theme. Delete unused themes.
```
rm -rf t*
```
### Load starter template
Install Starter template, check library and pick Elementor templates.
### Resources
```
https://wordpress.org/plugins/astra-sites/
```

## Plugins SEO
### Yoast SEO
Check results at seobility.net.
```
https://wordpress.org/plugins/wordpress-seo/
```
#### Resources
```
https://speckyboy.com/on-page-seo/
```

## Plugins Analytics
### Slimstat
```
https://wordpress.org/plugins/wp-slimstat/
```

## Plugins Performance
### Autoptimize
Check results at GTmetrix, seositecheckup.com.
```
https://wordpress.org/plugins/autoptimize/
```
### Expire Headers
```
https://wordpress.org/plugins/far-future-expiry-header/
```
### Database Optimization
```
https://wordpress.org/plugins/rvg-optimize-database/
```

## Plugins Legal
### GDPR Cookie Consent
```
https://wordpress.org/plugins/cookie-law-info/
```
Disable show again tab.<br/>
Check cookies:
```
https://www.cookieserve.com/
```
Text:
```html
<div class="cli-bar-container cli-style-v2"><div class="cli-bar-message">Utilizăm cookie-uri si alte tehnologii similare pentru a imbunatati experienta dumneavoastră. de navigare si functionalitatea site-ului nostru. Continuarea navigarii implica acceptarea lor. </div><div class="cli-bar-btn_container">[cookie_settings margin="0px 10px 0px 5px"][cookie_button]</div></div>
```

## Localization
### Add language 
Go to Settings -> Site Language. Choose language needed. This is in order to automatically download language packs.<br/>
Revert to English after verifying the downloads in /wordpress/wp-content/languages.

### Add Plugin WPGlobus
```
https://wordpress.org/plugins/wpglobus/
```
From plugin settings add the language previously added.<br/>
Note: Deactivate plugin when performing general updates, ex. changing country or currency.

### Resources
```
https://docs.woocommerce.com/document/woocommerce-localization/
```

## Plugins Protection
### WP Content Copy Protection
Deactivate plugin while performing changes on site.
```
https://wordpress.org/plugins/wp-content-copy-protection/
```

## Resources
```
https://www.tutorialspoint.com/wordpress/index.htm
```
