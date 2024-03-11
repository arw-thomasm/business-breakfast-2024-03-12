# syntax=docker/dockerfile:1
FROM node:12-alpine 

LABEL com.arrow.version="0.0.1-beta"
LABEL vendor="Arrow ECS Austria"
LABEL com.arrow.release-date="2024-03-07"
LABEL com.arrow.version.is-production="no"
LABEL comment="This application does NOT run on OpenShift"

RUN apk add --no-cache python2 g++ make 

WORKDIR /app 

COPY . . 

RUN yarn install --production

EXPOSE 3000 

CMD ["node", "src/index.js"]