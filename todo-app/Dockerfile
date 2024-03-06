# syntax=docker/dockerfile:1

FROM node:12-alpine 

RUN apk add --no-cache python2 g++ make 

WORKDIR /app 

#COPY . . 
COPY --chmod=g=u --chown=1001:0 . .

RUN yarn install --production

CMD ["node", "src/index.js"] 

EXPOSE 3000 

