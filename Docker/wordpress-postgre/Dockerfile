FROM ubuntu:20.04

# Criando as variáveis
ENV WORDPRESS_VERSION 6.1.1
ENV ADMINER_VERSION 4.7.7 

RUN apt-get update && apt-get install -y \
    curl \
    apache2 \
    php \
    libapache2-mod-php \
    php-pgsql \
    certbot \
    software-properties-common \
    postgresql-client

# Baixar e instalar o WordPress
RUN curl -O https://wordpress.org/wordpress-${WORDPRESS_VERSION}.tar.gz \
    && tar xzvf wordpress-${WORDPRESS_VERSION}.tar.gz \
    && rm -f wordpress-${WORDPRESS_VERSION}.tar.gz \
    && mv wordpress /var/www/html/

# Configurar o Apache para usar o WordPress
RUN a2enmod rewrite \
    && chown -R www-data:www-data /var/www/html/wordpress \
    && sed -i 's#DocumentRoot /var/www/html#DocumentRoot /var/www/html/wordpress#' /etc/apache2/sites-available/000-default.conf \
    && sed -i 's#<Directory /var/www/>#<Directory /var/www/html/wordpress/>#' /etc/apache2/apache2.conf \
    && sed -i 's#AllowOverride None#AllowOverride All#' /etc/apache2/apache2.conf

# Instalar o certificado SSL do Let's Encrypt com o exemplo de um site
RUN certbot --apache -d localhost

# Baixar e instalar o Adminer
RUN curl -O https://github.com/vrana/adminer/releases/download/v${ADMINER_VERSION}/adminer-${ADMINER_VERSION}-en.php \
    && mv adminer-${ADMINER_VERSION}-en.php /var/www/html/adminer.php


# porta para conexão
EXPOSE 80
EXPOSE 9000

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]

