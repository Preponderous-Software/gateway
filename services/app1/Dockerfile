FROM nginx:alpine

# Copy custom configuration
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Copy website files
COPY html/ /usr/share/nginx/html/

# Expose port
EXPOSE 8000

# Update nginx config to listen on port 8000
RUN sed -i 's/listen 80/listen 8000/g' /etc/nginx/conf.d/default.conf