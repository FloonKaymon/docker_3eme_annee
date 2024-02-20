# Créer un Dockerfile pour cette application en mode production

# utiliser l'image php:8.3-fpm
FROM php:8.3-fpm

# definir les variables d'environnement
ENV COMPOSER_ALLOW_SUPERUSER=1
ENV APP_ENV=prod

# installation des extensions
RUN apt-get update && apt-get install -y \
    libicu-dev \
    zip \
    unzip \
    git \
    nginx \
    && docker-php-ext-install intl pdo_mysql \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# exposer le port 80
EXPOSE 80

# on récupere les fichiers
COPY . /var/www/html

# on défini le répertoire de travail
WORKDIR /var/www/html

# execution de composer pour les dependances
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer install --no-dev --optimize-autoloader

RUN php bin/console asset-map:compile

# on nettoie le cache de symphony
RUN php bin/console cache:clear --env=prod

# on utilise l'user www-data
USER www-data




