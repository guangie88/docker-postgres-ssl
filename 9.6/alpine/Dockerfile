FROM postgres:9.6-alpine

LABEL maintainer="Chen Weiguang <chen.weiguang@gmail.com>"

# override this in your docker run command to customize
ADD ./ssl.conf /etc/postgresql-common/ssl.conf

# add the ssl config setup script
COPY pg_hba.conf /usr/local/share/postgresql/pg_hba.conf.sample
COPY postgresql.conf /usr/local/share/postgresql/postgresql.conf.sample
COPY server.crt server.key /var/ssl/

# override the original entrypoint script
COPY docker-entrypoint.sh /usr/local/bin/

RUN chown postgres.postgres /usr/local/share/postgresql/pg_hba.conf.sample \
    /usr/local/share/postgresql/postgresql.conf.sample \
    /var/ssl/server.key \
    /var/ssl/server.crt && \
    chmod 600 /var/ssl/server.key
