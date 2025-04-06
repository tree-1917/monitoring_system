# use the official Ubuntu image for Docker hub 
FROM ubuntu:20.04 

# set the working Dir 
WORKDIR /app 

# Update and install Nginx 
RUN apt-get update && apt-get install -y  \
   nginx \ 
   && rm -rf /var/lib/apt/lists/*

# Install Node Exporter 
COPY node_exporter /usr/local/bin

# Expose Necessary Ports
EXPOSE 80 
EXPOSE 9100

# Start Nginx 
CMD nginx -g "daemon off;" & /usr/local/bin/node_exporter
