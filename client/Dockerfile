# Stage 1: Build the React app
FROM node:18-alpine AS builder

# Set the working directory
WORKDIR /app

# Copy only package.json and package-lock.json to install dependencies
COPY client/package*.json ./

# Install only production dependencies to minimize image size
RUN npm install --legacy-peer-deps

# Copy the rest of the application code
COPY client/ .

# Build the React app for production
RUN npm run build

# Stage 2: Serve the app with a lightweight server
FROM nginx:alpine AS runtime

# Copy the built files from the builder stage to the nginx web server
COPY --from=builder /app/build /usr/share/nginx/html

# Expose port 80 for serving the app
EXPOSE 80

# Start nginx to serve the React app
CMD ["nginx", "-g", "daemon off;"]
