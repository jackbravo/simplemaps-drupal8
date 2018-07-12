# Simple drupal 8 site with a OSM powered map

Since one of the requirements was using OSM for maps I decided to use the
[geofield](https://www.drupal.org/project/geofield) module along with the
[leaflet](https://www.drupal.org/project/leaflet) module. Otherwise I think the
[Geolocation](https://www.drupal.org/project/geolocation) module is a simpler
solution.

## Usage

First you need to [install composer](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-osx).

> Note: The instructions below refer to the [global composer installation](https://getcomposer.org/doc/00-intro.md#globally).
You might need to replace `composer` with `php composer.phar` (or similar) 
for your setup.

After that you need to install the dependencies:

```
composer install
```

Then you can install a simple site using sqlite extension (PHP pdo_sqlite
extension needs to be previously installed).

```
drupal site:install  minimal --langcode="en" --db-type="sqlite" --db-file="sites/default/files/.ht.sqlite" --site-name="Simple Maps" --site-mail="admin@example.com" --account-name="admin" --account-mail="admin@example.com" --account-pass="admin" --learning --uri="http://default" --no-interaction
```

This install a simple site with the minimal install profile. To install the site
configuration you then just need to run this command (thanks to Jesus Olivas
for his [simple blog](https://weknowinc.com/blog/how-install-drupal-8-existing-configuration)):

```
drupal config:import --no-interaction
drupal cr all
```

And you can even create some demo content using the command:

```
drupal create:nodes
```

And you can now test your site with the php server using

```
drupal server --verbose
```

And go to: http://127.0.0.1:8088

We are using the [drupal-composer](https://github.com/drupal-composer/drupal-project)
project.
