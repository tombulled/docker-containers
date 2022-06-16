FROM alpine:3 as clone

RUN apk add --update git
RUN git clone --depth 1 --branch v22.06.1 https://github.com/bastienwirtz/homer.git

FROM node:lts-alpine as build

COPY --from=clone /homer /homer

WORKDIR /homer

RUN yarn install --frozen-lockfile
RUN yarn build

FROM bitnami/nginx:1.22.0

COPY --from=build /homer/dist /app
COPY --from=build /homer/dist/assets/config.yml.dist /app/assets/config.yml