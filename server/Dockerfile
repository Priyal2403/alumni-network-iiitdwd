# Use a lightweight Node.js base image for build
FROM node:18-alpine AS builder

# Set the working directory
WORKDIR /app

# Copy only package.json and package-lock.json for dependency installation
COPY server/package*.json ./

# Install dependencies
RUN npm install --only=production

# Copy the rest of the application code
COPY server/ . 

# Use a smaller, final image for running the app
FROM node:18-alpine AS runtime

# Set the working directory
WORKDIR /app

# Copy only the necessary files from the build stage
COPY --from=builder /app /app

# Expose the port the app will listen on
EXPOSE 3000

# Start the app
CMD ["node", "index.js"]
