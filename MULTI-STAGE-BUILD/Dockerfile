# Stage 1: Build stage using Node (can be used for tools like Vite, React, etc.)
FROM node:20-alpine AS builder

WORKDIR /app

# If you're using a build tool like Vite, React, or Vue:
# COPY package*.json ./
# RUN npm install
# COPY . .
# RUN npm run build

# In this basic example, just copy the static files directly
COPY ./src ./dist

# Stage 2: NGINX for serving static content
FROM nginx:stable-alpine AS production

# Copy built static files to nginx html directory
COPY --from=builder /app/dist /usr/share/nginx/html

# Copy custom nginx config
COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
