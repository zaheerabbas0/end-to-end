#FROM nginx:latest
#COPY nginx.conf /etc/nginx/conf.d/default.conf
#CMD ["nginx", "-g", "daemon off;"]
FROM nginx:latest

# Remove the default config
RUN rm /etc/nginx/conf.d/default.conf

# Copy custom configuration
COPY nginx.conf  /etc/nginx/nginx.conf:ro

# Ensure correct permissions
RUN chmod 644 /etc/nginx/nginx.conf

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
