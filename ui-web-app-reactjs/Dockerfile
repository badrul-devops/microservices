# Stage 1: Build the application
FROM node:8 AS builder

WORKDIR /app
COPY package.json package-lock.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Create a Distroless-based image for production
FROM gcr.io/distroless/nodejs:16

WORKDIR /app
COPY --from=builder /app/package.json /app/package-lock.json ./
COPY --from=builder /app/dist /app/dist

EXPOSE 8090

CMD ["dist/app.js"]  
