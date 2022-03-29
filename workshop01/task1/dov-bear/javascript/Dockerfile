ARG NODE_VER=17

FROM node:${NODE_VER}

# BUILD STAGE

LABEL "name" = "myappjs"

ARG APP_DIR=/app

RUN mkdir $APP_DIR

WORKDIR $APP_DIR

COPY ["package.json", "package-lock.json*", "./"]

RUN npm ci --production

COPY . .

ENV APP_PORT=3000

EXPOSE ${APP_PORT}

HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 CMD curl -s -f http://localhost:${APP_PORT} || exit 1

CMD [ "node", "main.js" ]
