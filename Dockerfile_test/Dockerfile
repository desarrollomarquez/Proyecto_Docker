###########################################################
# Dockerfile to build Odoo ERP container images
# Based on Ubuntu 16.04
############################################################
FROM ubuntu:16.04
MAINTAINER Diego Marquez "desarrollo.marquez@gmail.com"
RUN apt-get update &&\
    apt-get install -y ssh wget nano curl nginx postgresql
RUN  apt-get install -y  ca-certificates subversion git bzr bzrtools python3-pip postgis libssl-dev libffi-dev && \
     apt-get install -y python3-dev python3-pyinotify python3-renderpm  build-essential supervisor gcc g++
RUN apt-get install -y python3-dateutil python3-feedparser python-libxslt1 \
    python3-lxml python3-mako python3-openid python3-psycopg2  \
    python3-pydot python3-pyparsing python3-reportlab python3-simplejson python3-tz python3-vatnumber \
    python3-werkzeug  python3-yaml  python3-docutils \
    python3-psutil python3-mock python3-unittest2 python3-jinja2 python3-pypdf2 python3-decorator   python3-openpyxl \
    python3-requests python3-passlib python3-pil xfonts-base xfonts-75dpi && \
    apt-get install -y libx11-dev libgl1-mesa-dev libglu1-mesa-dev libxrandr-dev libxext-dev && \
    apt-get install -y cmake xorg-dev && \
    chmod -R 777 /usr/share/nginx/html/ && \
    apt-get install -y nodejs node-clean-css node-less && \
    apt-get install -y npm && \
    npm install -g less less-plugin-clean-css  && \
    ln -s /usr/bin/nodejs /usr/bin/node
RUN  pip3 install setuptools Babel decorator docutils ebaysdk feedparser gevent greenlet html2text Jinja2 lxml Mako MarkupSafe mock num2words ofxparse passlib Pillow psutil psycogreen psycopg2 pydot pyparsing PyPDF2 pyserial python-dateutil python-openid pytz pyusb PyYAML qrcode reportlab requests six suds-jurko vatnumber vobject Werkzeug XlsxWriter xlwt xlrd numpy pandas
ADD https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.2/wkhtmltox-0.12.2_linux-trusty-amd64.deb /opt/
RUN dpkg -i /opt/wkhtmltox-0.12.2_linux-trusty-amd64.deb  && \
    cp /usr/local/bin/wkhtmltopdf /usr/bin && \
    cp /usr/local/bin/wkhtmltoimage /usr/bin
USER root
RUN useradd -d /opt/odoo -m -s /bin/bash -p odoo odoo
EXPOSE 22 8069 8071 80 8088 8072 443 8073 8070 8000 9000 9001
