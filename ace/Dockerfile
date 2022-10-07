FROM ubuntu:20.04

RUN apt-get update && apt-get install -y \
    python3.8 \
    python3-pip \
    python3.8-dev \
    git \
    nano \
    wget \
    default-libmysqlclient-dev

# Register the version in alternatives
RUN update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.8 1

# Set python 3 as the default python
RUN update-alternatives --set python3 /usr/bin/python3.8

ENV PYTHONUNBUFFERED 1
WORKDIR /ace

#RUN adduser --disabled-password --gecos '' tasksuser
ADD wait-for-it.sh /ace/
RUN chmod +x /ace/wait-for-it.sh
COPY requirements.txt /ace
RUN pip3 install -r requirements.txt

#RUN mkdir -p /home/djangouser
#RUN adduser --disabled-password --gecos '' djangouser
#RUN chown djangouser /usr/local/bin/

# RUN apt-get clean && apt-get update && apt-get install -y locales
# RUN locale-gen en_CA.UTF-8
# COPY ./default_locale /etc/default/locale
# RUN chmod 0755 /etc/default/locale
# ENV LC_ALL=en_CA.UTF-8
# ENV LANG=en_CA.UTF-8
# ENV LANGUAGE=en_CA.UTF-8


COPY . /ace/

#RUN chmod -R 777 /django/tempOrdersFiles

#RUN chown djangouser /home/djangouser
#USER djangouser
#ENV HOME /home/djangouser
