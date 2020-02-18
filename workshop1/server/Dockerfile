FROM node:latest

ENV DB_HOST=nwdb DB_PORT=3306 DB_USER=root DB_PASSWORD=changeit
ENV APP_PORT=3000 APP_ROOT=/app

# create the $APP_ROOT directory
# go inside the directory
WORKDIR ${APP_ROOT}

# copy my file from notebook into ${APP_DIR}
ADD main.js .
ADD package.json .
ADD package-lock.json .
ADD public public
ADD views views
ADD config config

# install dependencies
# this will use package.json
RUN npm install

# configure healthchecks
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
    CMD curl -s -f http://localhost:${APP_PORT}/health || exit 1 

# what port is this application using
EXPOSE ${APP_PORT}

# command to execute
ENTRYPOINT ["node", "main.js"]
# additional customizations
# CMD ["3000"]


