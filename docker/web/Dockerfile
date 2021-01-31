FROM nginx:1.15.6

COPY default.conf /etc/nginx/conf.d/default.conf
# COPY /c/work/photozou/docker-compose-laravel/docker/web/default.conf /etc/nginx/conf.d/default.conf
# COPY ./docker/web/default.conf /etc/nginx/conf.d/default.conf
RUN apt-get update \
&& apt-get install -y \
git \
zip \
unzip \
vim
# Define working directory
WORKDIR /etc/nginx

CMD ["nginx", "-g", "daemon off;"]

# Expose ports.
EXPOSE 80