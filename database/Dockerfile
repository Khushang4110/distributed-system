FROM mysql:8.0

ENV MYSQL_ROOT_PASSWORD=password
ENV MYSQL_DATABASE=mydatabase

# Copy initialization scripts into the Docker image
COPY schema.sql /docker-entrypoint-initdb.d/
COPY data.sql /docker-entrypoint-initdb.d/

EXPOSE 3306
