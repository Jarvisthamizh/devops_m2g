FROM tlv-docker.us.int.genesyslab.com:5000/nginx:1.12.2

RUN rm /etc/nginx/nginx.conf && \
    rm -fr /etc/nginx/sites-available && \
    rm -fr /etc/nginx/sites-enabled && \
    mkdir /etc/nginx/sites-available && \
    mkdir /etc/nginx/sites-enabled

COPY nginx.conf /etc/nginx/
COPY sites-available/default /etc/nginx/sites-available/

RUN ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/default


