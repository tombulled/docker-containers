FROM alpine:3 as intermediate

LABEL stage=intermediate

RUN apk add --update git
RUN git clone --depth 1 --branch v3.9.0 https://github.com/carloscuesta/gitmoji.git

FROM node:18

COPY --from=intermediate /gitmoji /gitmoji

WORKDIR /gitmoji

RUN npm install
RUN npm run build

ENTRYPOINT ["npm", "run", "start", "--", "-p", "8080"]