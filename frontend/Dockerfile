# Stage 1: Build the frontend
FROM node:18 AS nodejs

# Set the working directory
WORKDIR /app

# copy package.json & package-lock.json to download all dependencies
COPY package.json package-lock.json ./

# Instal frontend dependencies
RUN npm install

# Copy the rest of the frontend files
COPY . .

# Build the frontend application
RUN npm run build

# Stage 2: Serve the frontend
FROM nginx:alpine

# Copy the build artifacts from the previous stage
COPY --from=nodejs /app/build  /usr/share/nginx/html

# Expose port 80 to access the frontend
EXPOSE 80

# Start Nginx to serve the frontend
CMD ["nginx", "-g", "daemon off;"]
