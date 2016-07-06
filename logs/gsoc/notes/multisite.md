Multisite WordPress installation
================================

This notepad will contain any of my personal notes or observations about working with WordPress multisite networks in specific correlation to Fedora and my GSoC proposal.


## Background

A multisite / network WordPress installation is a series of WordPress sites "chained" together. They all share a "common" base and unique layers on top. This means they share the same core updates to WordPress and plugins, but have their own unique theming and posts separate from each other.


## Prerequisites

Needed to get a WordPress installation up and running:
* httpd / nginx
* php
* php-mysql
* mariadb-server

_Other notes_
* Start, enable httpd + mariadb-server
* Using httpd over nginx because that's what Fedora uses


## Beginning install

* Take backups for existing application
* All plugins recommended to be disabled

### `wp-config.php`
* lineinfile / template:
 * define('DB_NAME', 'name');
 * define('DB_USER', 'user');
 * define('DB_PASSWORD', 'pass');
 * define('DB_HOST', 'localhost');
 * define( 'WP_ALLOW_MULTISITE', true );


## Installing network

* Adding new sites is completely manual
 * Have to do it from WP interface??


### `wp-config.php`
```
define('MULTISITE', true);
define('SUBDOMAIN_INSTALL', true);
define('DOMAIN_CURRENT_SITE', 'b1.stg.derezzed.justinwflory.com');
define('PATH_CURRENT_SITE', '/');
define('SITE_ID_CURRENT_SITE', 1);
define('BLOG_ID_CURRENT_SITE', 1);
```

### `.htaccess`
```
RewriteEngine On
RewriteBase /
RewriteRule ^index\.php$ - [L]

# add a trailing slash to /wp-admin
RewriteRule ^wp-admin$ wp-admin/ [R=301,L]

RewriteCond %{REQUEST_FILENAME} -f [OR]
RewriteCond %{REQUEST_FILENAME} -d
RewriteRule ^ - [L]
RewriteRule ^(wp-(content|admin|includes).*) $1 [L]
RewriteRule ^(.*\.php)$ $1 [L]
RewriteRule . index.php [L]

```

## Using _WordPress MU Domain Mapping_ plugin

This plugin allows a user to map a WordPress site to another domain. Hypothetically, using this plugin, you could have the Fedora Magazine be magazine.fedoraproject.org, but map the domain to fedoramagazine.org. I tried setting this up in my test installation, and noticed a few things.

* Plugin last officially updated over two years ago
* Last commit to project repository was 14 months ago
* Existing documentation / [guide](http://ottopress.com/2010/wordpress-3-0-multisite-domain-mapping-tutorial/) for using and installing the plugin was written for either an older version of WordPress or older version of plugin

After messing around with it in my test installation, I had issues getting the multi-domain feature to work. Mapping the domains did not appear to have an immediate effect on my installation, and seems like it would have required me to still use my root domain as the base WordPress installation so to first add another site on the same domain (e.g. requiring WordPress to be installed on fedoraproject.org first).

While this plugin would likely accomplish the multi-domain feature as desired, the complications with installing it and concerns over its long-term stability are uncertain. For the time being, it would probably be best to move over this plugin.


## Conclusionary notes

* Multisite networ feature requires using the *SAME* domain across all blogs, e.g. `fedoraproject.org`.
* Would be easy to set up blogs for `*.fedoraproject.org`
 * `fedoramagazine.org` would present difficulties
 * Not possible to do something like `magazine.fedoraproject.org` and use DNS for fedoramagazine.org? Not sure, this is probably still WordPress specific
* _jflory7's judgment_: It will be better to focus on refining the existing playbook for a per-WordPress installation setup (seems like Magazine and Community Blog will need to remain separate because of the different domains - this seems to be the case regardless of whether the sub-domain or directory method is chosen).