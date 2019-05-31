FROM debian
WORKDIR /var/www/docker3os.com
RUN apt-get -qq update && \
    apt-get autoclean && \
    apt-get install -y nginx && \
    rm -rf /var/www/* && \
    mkdir /var/www/docker3os.com && \
    mkdir /var/www/docker3os.com/img 

COPY index.html /var/www/docker3os.com

COPY img.jpg /var/www/docker3os.com/img

RUN chmod -R 754 /var/www/docker3os.com && \
    useradd david && \
    groupadd tazagumov && \
    usermod -aG tazagumov david && \
    chown -R david:tazagumov /var/www/docker3os.com

RUN sed -i 's/html/docker3os.com/g' /etc/nginx/sites-enabled/default && \
    sed -i 's/www-data/david/g' /etc/nginx/nginx.conf && \
    sed -i 's/index.htm/index.html/g' /etc/nginx/sites-enabled/default

CMD ["nginx","-g","daemon off;"]
