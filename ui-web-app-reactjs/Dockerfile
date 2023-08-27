# Use an official Node.js runtime as the base image
FROM node:14 as build

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json to the container
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code to the container
COPY . .

# Build the React application
RUN npm run build

# Use a lightweight Node.js runtime as the final image
FROM node:14-alpine

# Set the working directory inside the container
WORKDIR /app

# Copy the built files from the previous stage to this stage
COPY --from=build /app/build ./build

# Expose the port your app is running on (adjust if needed)
EXPOSE 8070

# Command to run your application
CMD ["npm", "run", "start"]
