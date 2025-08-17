# Stage 1: Build the application
# it copies all the files form directory and builds the application
FROM node:18-alpine AS builder

WORKDIR /app

COPY package*.json ./

RUN npm install
COPY ../../../.. .

RUN npm run build

# Stage 2: Production-ready image with PM2
# it gets build from the builder stage
# and uses pm2 to run the application
FROM node:18-alpine

RUN npm install -g pm2

WORKDIR /app

COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app .

EXPOSE 3000

CMD ["pm2-runtime", "npm", "--", "start"]