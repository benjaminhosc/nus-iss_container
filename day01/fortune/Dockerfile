ARG NODE_VERSION=22

FROM node:${NODE_VERSION}
## How to build

# Create a dir /app and cd /app
WORKDIR /app

# Inside /app
# Copy my src

# Copy from local container
COPY main.js .
COPY package*.json .
COPY public public
COPY views views

# install node modules
RUN npm ci

# How to run
ENV APP_PORT=5000 APP_DIR=/app

# What are th exposed port
EXPOSE ${APP_PORT}

VOLUME ${APP_DIR}/public

# Run the application
ENTRYPOINT node main