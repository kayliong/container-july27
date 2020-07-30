# This image will be base on node js 14
FROM node:14

# create env variable to define my workspace
ENV APP_DIR=/app APP_PORT=3000

# create and cd into app dir
# mkdir
# cd
WORKDIR ${APP_DIR}

# copy the Fortune file into /app
# Add local image
ADD main.js .
ADD package.json .
ADD package-lock.json .

# copy the directories
ADD public public
ADD views views 

# install dependencies - package.json
RUN npm install

# add health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=4s --retries=3 \
    CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1

# the port we are exposing
EXPOSE ${APP_PORT}

# run the application
ENTRYPOINT ["node", "main.js"]