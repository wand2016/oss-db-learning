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

RUN make world
# RUN make check
RUN make install-world

ENV PATH "$PATH:/usr/local/pgsql/bin"
ENV PGDATA=/var/lib/postgresql/data
WORKDIR /var/lib/postgresql/

RUN useradd -M -d /var/lib/postgresql/ postgres
RUN chmod 700 .
RUN chown postgres:postgres .

USER postgres
RUN initdb -E UTF-8
