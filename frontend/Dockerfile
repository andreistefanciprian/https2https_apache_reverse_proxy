FROM debian:stretch

RUN apt-get update \
&& apt-get upgrade -y \
&& apt-get install -y --no-install-recommends apt-utils tree apache2 curl vim \
&& rm -rf /var/lib/apt/lists/*

COPY frontend/default_website.conf /etc/apache2/sites-available/default_website.conf
COPY ssl/. /etc/apache2/ssl/.

RUN a2enmod proxy proxy_http ssl \
&& a2dissite 000-default \
&& a2ensite default_website

EXPOSE 80
EXPOSE 443

# Start only HTTP page
# CMD ["apache2ctl", "-DFOREGROUND"]

# Start HTTPS page
CMD ["apache2ctl", "-DFOREGROUND", "-DSSL-ON"]
