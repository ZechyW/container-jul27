# Base environment
FROM node:14

# Env variables
ENV APP_DIR=/app APP_PORT=3000

# Set working directory
WORKDIR ${APP_DIR}

# `fortune` is the source directory;
# we copy the files we want into the _image's_ working directory
ADD main.js .
ADD package.json .
ADD package-lock.json .
# Directories need to have the destination name specified
ADD public public
ADD views views

# Dependencies
RUN npm install

## Run
# Health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 CMD curl -s -f http://localhost:${APP_PORT}/health > /dev/null || exit 1

# Expose the port for communication
EXPOSE ${APP_PORT}

# And go
ENTRYPOINT ["node", "main.js"]