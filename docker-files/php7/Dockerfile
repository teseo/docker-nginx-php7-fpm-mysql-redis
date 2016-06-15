################################################################################
# Base image
################################################################################

FROM php:7.0.7-fpm

################################################################################
# Work dir
################################################################################

WORKDIR /var/www

################################################################################
# Build instructions
################################################################################

# Install packages
RUN apt-get update && apt-get install -my \
  supervisor \
  wget

# Ensure that PHP5 FPM is run as root.
# RUN sed -i "s/user = www-data/user = root/" /etc/php/fpm/pool.d/www.conf
# RUN sed -i "s/group = www-data/group = root/" /etc/php/fpm/pool.d/www.conf

# # Pass all docker environment
# RUN sed -i '/^;clear_env = no/s/^;//' /etc/php/fpm/pool.d/www.conf
#
# # Get access to FPM-ping page /ping
# RUN sed -i '/^;ping\.path/s/^;//' /etc/php/fpm/pool.d/www.conf
# # Get access to FPM_Status page /status
# RUN sed -i '/^;pm\.status_path/s/^;//' /etc/php/fpm/pool.d/www.conf

RUN pecl install xdebug

RUN mkdir public

RUN echo "<?php phpinfo(); " > public/index.php

# Add configuration files
#COPY conf/supervisord.conf /etc/supervisor/conf.d/
COPY conf/php.ini /usr/local/etc/php/conf.d/xdebug-enabled.ini



################################################################################
# Ports
################################################################################

EXPOSE 9000

################################################################################
# Entrypoint
################################################################################

# ENTRYPOINT ["/usr/bin/supervisord -c /etc/supervisor/conf.d/supervisord.conf"]
#CMD ["php", "-a"]
