# Use the official Ubuntu image
FROM ubuntu:20.04

# Set the working directory
WORKDIR /app

# Update and install necessary packages
RUN apt-get update && apt-get install -y \
    nginx \
    supervisor \
    && rm -rf /var/lib/apt/lists/*

# Copy website files to Nginx default dir
COPY app/website/ /var/www/html/

# Install Node Exporter
COPY node_exporter /usr/local/bin

# Make Node Exporter executable
RUN chmod +x /usr/local/bin/node_exporter

# Copy Supervisor configuration file
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Expose necessary ports
EXPOSE 80
EXPOSE 9100

# Start Supervisor to manage both Nginx and Node Exporter
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/supervisord.conf"]

