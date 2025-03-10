# Use Node.js 16 (recommended for better compatibility)
FROM node:16-alpine

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json first (for better caching)
COPY package.json package-lock.json ./

# Install dependencies using npm ci (more reliable for production)
RUN npm ci --legacy-peer-deps

# Copy the rest of the application files
COPY . .

# Build the React app for production
RUN npm run build

# Install 'serve' globally to serve the built files
RUN npm install -g serve

# Expose the frontend port
EXPOSE 3000

# Healthcheck to ensure the container is healthy
HEALTHCHECK --interval=30s --timeout=10s --start-period=5s \
  CMD curl -f http://localhost:3000 || exit 1

# Command to serve the React app
CMD ["serve", "-s", "build", "-l", "3000"]
