FROM alpine:3 as intermediate

LABEL stage=intermediate

RUN apk add --update git
RUN git clone --depth 1 --branch 4.9.5 https://github.com/carbon-app/carbon.git

FROM node:18

COPY --from=intermediate /carbon /carbon

WORKDIR /carbon

RUN yarn install
RUN npm run-script build

ENTRYPOINT ["npm", "run-script", "start"]