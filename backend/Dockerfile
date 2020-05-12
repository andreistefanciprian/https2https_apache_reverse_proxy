FROM debian:stretch

RUN apt-get update \
&& apt-get upgrade -y \
&& apt-get install -y --no-install-recommends apt-utils tree apache2 curl vim \
&& rm -rf /var/lib/apt/lists/*

COPY backend/default_website.conf /etc/apache2/sites-available/default_website.conf
COPY backend/index.html /var/www/html/index.html

RUN a2enmod proxy proxy_http ssl \
&& a2dissite 000-default \
&& a2ensite default_website

EXPOSE 443

# Start Apache2
CMD ["apache2ctl", "-DFOREGROUND"]
