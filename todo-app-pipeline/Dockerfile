# syntax=docker/dockerfile:1
FROM node:12-alpine 

LABEL com.arrow.version="0.0.1-beta"
LABEL vendor="Arrow ECS Austria"
LABEL com.arrow.release-date="2024-03-07"
LABEL com.arrow.version.is-production="no"
LABEL comment="This application runs on OpenShift"

RUN apk add --no-cache python2 g++ make 

WORKDIR /app 

COPY --chown=1001:0 . .

RUN yarn install --production \
 && chmod -R g=u .

EXPOSE 3000 

CMD ["node", "src/index.js"]