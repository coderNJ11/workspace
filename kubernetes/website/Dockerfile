FROM userxy2015/ngnix
LABEL maintainer="khirerishi@gmail.com"

COPY website /website
COPY nginx.conf /etc/nginx.conf

EXPOSE 80
ENTRYPOINT [ "sh" , "-c" , "echo 'Hello Docker' " ]
