FROM ubuntu:18.04

WORKDIR /work

RUN apt-get update -y
RUN apt-get install -y wget
RUN apt-get install -y build-essential
RUN apt-get install -y libreadline6-dev
RUN apt-get install -y zlib1g-dev

RUN wget https://ftp.postgresql.org/pub/source/v12.1/postgresql-12.1.tar.gz
RUN tar -xvzf postgresql-12.1.tar.gz

WORKDIR /work/postgresql-12.1

RUN apt-get install -y libssl-dev
RUN ./configure --with-openssl

RUN make
# RUN make check
RUN make install
RUN ls /usr/local/pgsql/bin
