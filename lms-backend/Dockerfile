# Use official Node.js 20 image
FROM node:20-bookworm-slim

# Install FFmpeg
RUN apt-get update && \
    apt-get install -y ffmpeg && \
    rm -rf /var/lib/apt/lists/*

# Create application directory
WORKDIR /app

# Copy package files first (Docker layer caching)
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy application source code
COPY . .

# Create runtime directories
RUN mkdir -p storage/uploads storage/processed logs

# Expose application port
EXPOSE 5000

# Start the backend
CMD ["npm", "run", "dev"]