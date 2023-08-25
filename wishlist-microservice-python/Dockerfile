# Stage 1: Build environment
FROM python:3 AS builder

# Set the working directory
WORKDIR /app

# Copy the current directory contents into the container
COPY . .

# Install dependencies
RUN pip install flask flask_cors

# Stage 2: Runtime environment with Distroless
FROM gcr.io/distroless/python3:nonroot AS runtime

# Copy only the necessary files from the builder stage
COPY --from=builder /app/index.py .

# Expose the required port
EXPOSE 1003

# Set the user to non-root (required for Distroless)
USER nonroot:nonroot

# Define the command to run the application
CMD ["index.py"]
