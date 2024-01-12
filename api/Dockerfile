# Build stage
FROM node:16-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Production stage
FROM gcr.io/distroless/nodejs:16
WORKDIR /app
COPY --from=builder /app/build ./build
CMD ["node", "build/index.js"]