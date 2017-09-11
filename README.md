# docker-lamp-php-5

Legacy Lamp docker server for old PHP projects.

# Docker && docker-compose installation instructions:

Install docker && docker-compose in your host machine:

    Follow Docker installation guide: https://docs.docker.com/engine/installation
    Follow Docker-compose installation guide: https://github.com/docker/compose/releases

docker-lamp-php-5 it's made from two docker containers, one for PHP & Apache and another one for MySQL instance. 

It uses docker and docker-compose. php-5.5, apache2.4 & mysql-5.5 but it can be customized easily to your needs.

# Customization

* Customize the docker-compose.yml file to fit your needs. 

* Change your PHP Version:
    
    This image is prepared to work with php-5.5-apache versions. It was also tested with 5.4.**, but 5.3.* and 5.6.* should work also. 
    Just edit:
     
     -> *docker/Dockerfile*
     
    And change it accordingly (php-5.X-apache)and you are good to go.
    
    * **Note**: Same applies for mysql version, as long as the image name exists in the docker hub, you can customize it.
    
# Install PHP Extensions

* Add one line for each extra extension you want to install, in the "Install PHP Extensions" section of your "*docker/Dockerfile*".
    For example, adding:
    
    RUN docker-php-ext-install gettext
    
    Would install gettext PHP extension into your server.
    
    List with all the extensions allowed to be installed via docker-php-ext-install command:
    
    https://gist.github.com/chronon/95911d21928cff786e306c23e7d1d3f3
    
    * **Note1**: Sometimes, an extension install will throw an error as it requires some package to be installed via apt.
For example, mcrypt extension requires the libmcrypt-dev package to be installed, so if you want to install this extension
it would require to add the mentioned package in the "Install PHP extension dependencies" section.
    
    * **Note2**: Mysql & curl extensions are shipped by default. (Inside the Dockerfile and inside the image itself).
    
# Install PHP Extensions using PECL (for extensions not available via docker-php-ext-install)

* Add one line for each extra extension you want to install, in the "Install PECL Extensions" section of your "*docker/Dockerfile*".
    For example, adding:
    
    RUN docker-php-pecl-install xdebug-2.5.4
    
    Would install xdebug version 2.5.4 (which works OK with PHP 5.5, configured in this package by default).
    
    List with all the extensions allowed to be installed via docker-php-pecl-install command:
    
    https://pecl.php.net/ (Browsable & Searchable).
    
# Install Xdebug via PECL.

* Just uncomment the example provided in the "*docker/Dockerfile*" and customize the "*docker/xdebug-ini-overrides.ini*" to fit your needs.
    
# Configure Apache

* You can use shipped docker/php.ini, provide yours, or customize the provided by this package, it will be loaded automatically.
* To configure Vhosts, copy your configuration file into the docker folder, and see the example in the "*docker/Dockerfile*".
* To enable apache modules (for example, rewrite), see the example in the "*docker/Dockerfile*".
    
    
    
    