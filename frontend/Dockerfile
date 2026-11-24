
# Stage 1: Build Quasar
FROM node:22-alpine AS builder

WORKDIR /app

# Copy project files first
COPY . .

# Install dependencies
RUN npm ci --legacy-peer-deps

# Build Quasar
RUN npm run build

# Stage 2: Nginx
FROM nginx:1.27-alpine

COPY --from=builder /app/dist/spa /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
