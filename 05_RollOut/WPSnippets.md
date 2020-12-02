### Show last update instead of published date for blog entries
Kadence theme already has the functionality in Customizer -> Single Blog Post -> Meta.
Additional CSS:
```css
span time.updated {
	  display: block !important;
}

span time.updated::before {
  content: "Ultima updatare la ";
}


span time.entry-date.published {
	display: none !important;
}
```
### Disable plugins or theme installation
```php
define('DISALLOW_FILE_MODS',true);
```
in wp-config.php.
