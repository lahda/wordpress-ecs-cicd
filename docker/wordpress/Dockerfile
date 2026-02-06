FROM wordpress:latest

# Installer des extensions PHP supplémentaires
RUN apt-get update && apt-get install -y \
    libzip-dev \
    zip \
    unzip \
    && docker-php-ext-install zip

# Configurer les permissions
RUN chown -R www-data:www-data /var/www/html

# Configuration personnalisée PHP
RUN echo "upload_max_filesize = 64M" > /usr/local/etc/php/conf.d/uploads.ini \
    && echo "post_max_size = 64M" >> /usr/local/etc/php/conf.d/uploads.ini \
    && echo "memory_limit = 256M" >> /usr/local/etc/php/conf.d/uploads.ini

# Exposer le port 80
EXPOSE 80

# Point d'entrée par défaut de l'image WordPress
CMD ["apache2-foreground"]