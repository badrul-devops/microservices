# Stage 1: Build environment
FROM node:14 AS builder

# Set the working directory
WORKDIR /app

# Copy the current directory contents into the container
COPY . .

# Install dependencies
RUN npm install

# Stage 2: Runtime environment with Distroless
FROM gcr.io/distroless/nodejs20-debian11 AS runtime

# Set the working directory
WORKDIR /app

# Copy only the necessary files from the builder stage
COPY --from=builder /app/index.js .
COPY --from=builder /app/node_modules ./node_modules

# Expose the required port
EXPOSE 1004

# Define the command to run the application
CMD ["index.js"]
