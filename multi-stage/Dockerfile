# Stage 1: Build Stage
FROM node:16 as builder

# Set working directory
WORKDIR /app

# Update npm to the latest version

# Copy package.json and package-lock.json files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy application source code
COPY . .

# Stage 2: Runtime Stage
FROM builder

# Set working directory
WORKDIR /app

# Copy only the built files and necessary dependencies from the build stage
COPY --from=builder /app ./

# Install only production dependencies
RUN npm install

# Expose application port
EXPOSE 3000

# Command to run the application
CMD ["node", "index.js"]

