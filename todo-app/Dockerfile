# syntax=docker/dockerfile:1

FROM node:12-alpine 

RUN apk add --no-cache python2 g++ make 

WORKDIR /app 

#COPY . . 
COPY --chown 1001:0 . .

RUN yarn install --production \
 && chmod -R g=u .

CMD ["node", "src/index.js"] 

EXPOSE 3000 

