# Stage 1: Build environment
FROM maven as build

WORKDIR /app
COPY . .
RUN mvn install

# Stage 2: Runtime environment
FROM openjdk:11.0.10-jre-slim-buster AS runtime

WORKDIR /app

# Copy the built JAR from the build stage
COPY --from=build /app/target/eureka-0.0.1-SNAPSHOT.jar .

# Expose the required port
EXPOSE 1001

# Stage 3: Distroless image for runtime
FROM gcr.io/distroless/java11-debian11

WORKDIR /app

# Copy the JAR from the runtime stage
COPY --from=runtime /app/eureka-0.0.1-SNAPSHOT.jar .

# Define the command to run the application
CMD ["eureka-0.0.1-SNAPSHOT.jar"]
