FROM ubuntu:20.04
RUN apt-get -y update && apt-get -y upgrade && apt-get -y install nginx && apt-get -y clean
#COPY default /etc/nginx/sites-available/default
RUN rm -r /var/www/
RUN mkdir -p /var/www/trust.com/img
COPY index.html /var/www/trust.com/
COPY img.jpg /var/www/trust.com/img
RUN chmod -R 754 /var/www/trust.com
RUN useradd viktor
RUN groupadd gonsh
RUN usermod -aG gonsh viktor
RUN chown -R viktor:gonsh /var/www/trust.com
#RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -i 's!/var/www/html!/var/www/trust.com!g' /etc/nginx/sites-enabled/default
#sed -i 's/ЧТО ЗАМЕНИТЬ/НА ЧТО ЗАМЕНИТЬ/g' имя_файла) и заменить в файле /etc/nginx/sites-enabled/default следующую подстроку (/var/www/html) так, чтобы она соответствовала (/var/www/company.com) (Д)
RUN sed -i 's!www-data!viktor!g' /etc/nginx/nginx.conf
EXPOSE 80/tcp
CMD ["/usr/sbin/nginx", "-g", "daemon off;"]
