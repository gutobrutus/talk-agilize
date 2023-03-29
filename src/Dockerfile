FROM node:lts-alpine3.16

ENV NODE_ENV production

RUN apk add --no-cache dumb-init && \
    mkdir -p /home/node/app && \
    chown -R node:node /home/node

WORKDIR /home/node/app

COPY --chown=node:node package*.json ./

RUN npm ci --omit=dev && \
    npm cache clean --force

USER node

COPY --chown=node:node . .

EXPOSE 3000

ENTRYPOINT ["dumb-init", "node", "app.js"]