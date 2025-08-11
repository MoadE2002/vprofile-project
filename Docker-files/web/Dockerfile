FROM nginx:alpine
LABEL "Project"="Vprofile"
LABEL "Author"="Moad"

# Copy the nginx configuration
COPY nginvproapp.conf /etc/nginx/conf.d/default.conf

# Expose port 80
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
