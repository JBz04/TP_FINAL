# Prérequis de la doc WordPress : un serveur web + PHP 8.3 ou supérieur.
FROM php:8.3-apache

# Bibliothèques système puis extensions PHP requises par WordPress
RUN apt-get update && apt-get install -y --no-install-recommends \
      wget ca-certificates \
      libpng-dev libjpeg62-turbo-dev libfreetype6-dev libzip-dev && \
    docker-php-ext-configure gd --with-jpeg --with-freetype && \
    docker-php-ext-install -j"$(nproc)" mysqli gd zip && \
    rm -rf /var/lib/apt/lists/*

# Module de réécriture d'URL, nécessaire aux permaliens
RUN a2enmod rewrite

WORKDIR /tmp

# Étape 1 : télécharger et extraire WordPress
RUN wget https://wordpress.org/latest.tar.gz
RUN tar xzf latest.tar.gz

# Étape 4 : déposer les fichiers dans la racine web
RUN cp -a /tmp/wordpress/. /var/www/html/
RUN rm -rf /tmp/wordpress /tmp/latest.tar.gz
RUN chown -R www-data:www-data /var/www/html

# Étape 3 : facultative selon la doc, l'installeur génère wp-config.php

EXPOSE 80

