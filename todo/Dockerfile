# Use a base image with PHP and Apache (or your preferred web server)
# Or a specific version like php:8.2.27-apache
FROM php:8.2-apache


# Copy your application code into the container
COPY . /var/www/html/ # Copies everything in the current directory to /var/www/html/

# Set file permissions (important!)
RUN chown -R www-data:www-data /var/www/html \
    && chmod -R 755 /var/www/html/

# Expose port 80 (or the port your web server is listening on)
EXPOSE 9000

# (Optional) Set the working directory
WORKDIR /var/www/html

# (Optional) Any other commands you need, like installing dependencies with Composer
# Example:
# COPY composer.json composer.lock ./
# RUN composer install --no-interaction --no-dev --optimize-autoloader

# (Optional) Configure Apache (if needed)
# Example:
# COPY apache-config.conf /etc/apache2/sites-available/000-default.conf
# RUN a2ensite 000-default.conf

# The CMD instruction is already defined in the php:*-apache base image
# and usually starts Apache. You likely don't need to override it.