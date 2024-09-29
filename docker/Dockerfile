FROM python:3.11-slim
ENV PYTHONUNBUFFERED 1

RUN apt-get update && apt-get install -y \
    apache2 \
    apache2-dev \
    libapache2-mod-wsgi-py3 \
    default-libmysqlclient-dev \
    build-essential \
    pkg-config \
    default-mysql-client \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /project
COPY ./project /project

COPY requirements.txt .
RUN pip install --upgrade pip
RUN pip install --no-cache-dir -r requirements.txt

COPY ./docker/apache/django-apache.conf /etc/apache2/sites-available/000-default.conf
COPY ./docker/apache/ports.conf /etc/apache2/ports.conf

# Enable the WSGI module for Apache
RUN a2enmod wsgi

# Command to start Apache in the foreground
CMD ["apachectl", "-D", "FOREGROUND"]