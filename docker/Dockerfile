FROM php:5.5-apache

# Install PHP extension dependencies (if any)
#RUN apt-get update \
#    && apt-get -y --no-install-recommends install <package_name>

# Configure PHP extensions
# Usually this isn't needed, only used in some special cases. intl, for example.
# RUN docker-php-ext-configure <package_name>

# Install PHP extensions
# Package names full list: https://gist.github.com/chronon/95911d21928cff786e306c23e7d1d3f3
#RUN docker-php-ext-install <package_name>

# Copy custom command docker-php-pecl-install
# This command is used to install extensions from PECL where are not available via docker-php-ext-install
#RUN docker-php-pecl-install <package_name-version> (versions available in PECL repository allowed)

# Copy PHP configuration
# Edit docker/php.ini and customize to your needs
COPY docker/php.ini /usr/local/etc/php/php.ini

# Configure Apache VHOSTS
#COPY docker/mysite.com.conf /etc/apache2/sites-available/mysite.com.conf
#RUN a2ensite <mysite.com.conf>

# Activate Apache modules
#RUN a2enmod <module_name>
#RUN service apache2 restart

# Set the workdir
WORKDIR /var/www/docker-lamp-php-5