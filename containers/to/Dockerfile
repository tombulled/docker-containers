FROM alpine:3 as clone

RUN apk add --update git

RUN git config --global advice.detachedHead false

RUN git clone --depth 1 --branch v0.1.0 https://github.com/tombulled/to.git
RUN git clone --depth 1 --branch v0.1.0 https://github.com/tombulled/to-ui.git

FROM node:lts-alpine as build

COPY --from=clone /to-ui /ui

WORKDIR /ui

RUN npm install
RUN npm run build

FROM bitnami/nginx:1.22.0

WORKDIR /app

COPY --from=clone /to /app/api
COPY --from=build /ui/build /app/ui

# NOTE: It feels wrong having two services in the same container.
# I think this approach should be scrapped.