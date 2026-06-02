# Imagen a usar
FROM php:8.2-apache

RUN apt-get update &&\ 
    apt-get install -y vim

# copiamos todos los ficheros en el directorio en cuestion
COPY src /var/www/html
# Exponemos el puerto 80
EXPOSE 80
# Quien lo ha realizado
LABEL maintainer="JL Gonzalez <jlgs@cifpvirgendegracia.com>"
