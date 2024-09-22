# Dockerfile for building and serving a Node.js application using Nginx

# Step 1: Build the application
FROM node:16.20.2 AS todo-image

# Set the working directory in the container
WORKDIR /app

# Copy all files from the current directory to the working directory in the container
COPY . .

# Install the application dependencies
RUN npm install

# Build the application (e.g., create optimized production build)
RUN npm run build

# Step 2: Serve the application using Nginx
FROM nginx:alpine

# Copy the build output from the previous stage to the Nginx HTML directory
COPY --from=todo-image /app/build /usr/share/nginx/html/

# Expose port 80 to allow external access
EXPOSE 80

# Start Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]
