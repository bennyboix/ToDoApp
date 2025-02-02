# Use a base image with PHP and Apache
FROM php:8.2-apache  

# Install necessary extensions (MySQLi and any others your app needs)
RUN apt-get update && apt-get install -y \
    libmariadb-dev \
    && docker-php-ext-configure mysqli --with-mysqli \
    && docker-php-ext-install mysqli \
    && docker-php-ext-enable mysqli # Ensure the extension is enabled

# Install other extensions as needed (e.g., for GD, cURL, etc.)
# Example:
# RUN apt-get install -y libpng-dev libjpeg62-turbo-dev libfreetype6-dev \
#     && docker-php-ext-configure gd --with-freetype --with-jpeg --with-png \
#     && docker-php-ext-install gd

# Copy your application code into the container
COPY . /var/www/html/

# Set file permissions (very important!)
RUN chown -R www-data:www-data /var/www/html \
    && chmod -R 755 /var/www/html/

# Expose port 80 (or the port your web server is listening on)
EXPOSE 80

# Set the working directory (optional but recommended)
WORKDIR /var/www/html

# Install Composer dependencies (if your project uses Composer)
# COPY composer.json composer.lock ./  # Copy Composer files first
# RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
# RUN composer install --no-interaction --no-dev --optimize-autoloader

# (Optional) Copy Apache configuration files if you have custom settings
# COPY apache-config.conf /etc/apache2/sites-available/000-default.conf
# RUN a2ensite 000-default.conf

# The CMD instruction is already defined in the php:*-apache base image
# and usually starts Apache.  You generally don't need to override it.
