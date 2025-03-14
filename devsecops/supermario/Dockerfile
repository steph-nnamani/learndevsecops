# WEZVA TECHNOLOGIES - ADAM - +91-9739110917 #
FROM nginx:stable-alpine

#setting working derectory
WORKDIR /mario

#creating environment variables
ENV NAME=SUPER-MARIO
ENV PORT=80

#copying files into container
COPY . /mario

#removing Unnecessary files
RUN rm -rf /usr/share/nginx/html/*

#copying files into browser serving path
RUN cp -r /mario/* /usr/share/nginx/html/

## creating volume for access logs from the host
# sets up two persistent storage areas inside the container to hold log data, 
# providing durability and flexibility for log management.
VOLUME /var/log/nginx/ /var/log/mario-logs

#expose port of container
EXPOSE 80

#Start Nginx when the container has provisioned
CMD ["nginx", "-g", "daemon off;"]

# Starts Nginx: The command launches the Nginx web server.
# Runs in the Foreground: The -g "daemon off;" flag instructs Nginx not 
# to run as a background daemon. In a container environment, keeping the 
# process in the foreground is essential so that the container remains 
# running.
# By running in the foreground, Docker can properly monitor and manage 
# the Nginx process, ensuring that if Nginx stops, the container stops as well.


# MANAGING THE VOLUME EXTERNALLY
# If you want the second volume (/var/log/mario-logs) to be attached directly 
# to a directory on your host machine, you can override the Dockerfile's 
# default volume behavior at runtime by using a bind mount. 
# This means you'll map a specific directory on your host to the container's 
# /var/log/mario-logs directory.

# For example, when running the container, you can use:
# docker run -v /path/on/host/mario-logs:/var/log/mario-logs your-image

# This way, the first volume remains managed by Docker, while the second is 
# attached to your host machine as required.

