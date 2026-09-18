FROM httpd:alpine

WORKDIR /usr/local/apach2/htdocs
COPY  index.html ./
COPY httpd.conf /usr/local/apache2/conf/httpd.conf

# Build : docker build -t mathisdesbonnet/docker_s7-tp1-client .
# Run : docker run -d -p 3000:3000 --network Docker_S7-TP1-Network --name=Docker_S7-TP1-Client mathisdesbonnet/docker_s7-tp1-client
# Default configuration retrieve command : docker exec Docker_S7-TP1-Client cat /usr/local/apache2/conf/httpd.conf